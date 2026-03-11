# Scroll-Reveal Article Sections

**Date**: 2026-03-11
**Status**: Approved

## Problem

Blog and guide articles wrap the entire article body in a single `ScrollReveal`, so when entering the page, the content area is invisible until the user scrolls to it. The hero section also waits for scroll, even though it's above the fold.

## Design

### Behavior

1. **Hero section** (title, tags, excerpt, author, date, featured image): Stagger-animates immediately on page load without waiting for scroll.
2. **First content section** (everything before the first h2/h3 heading): Visible immediately, no animation.
3. **Subsequent content sections** (each h2 or h3 heading + content until the next heading): Scroll-reveals with staggered fade-up animation (heading first, then body content with +100ms delay).

### Content Splitting

A utility function `splitContentBySections(content: string)` splits the raw markdown string:

- Scans line by line
- Tracks fenced code block state — lines starting with 3+ backticks or tildes toggle in/out of code block mode (indented code blocks are not tracked, acceptable for MDX content)
- Splits on lines matching `^## ` or `^### ` only when outside code blocks
- Returns `string[]` where the first element is intro content (before first heading) and each subsequent element starts with its heading line
- Each section must be self-contained valid MDX. The splitter does not validate that JSX tags or markdown structures are properly closed within each section

### Component Changes

**`ScrollReveal.tsx`** — Add `immediate?: boolean` prop:
- When `true`, initializes `isVisible = false` then sets to `true` after a `requestAnimationFrame` to ensure the CSS transition triggers (hidden-to-visible stagger effect is intentional for hero entrance)
- Skips IntersectionObserver entirely
- Same animation styles and timing apply

**`BlogContent.tsx`** — Split and render sections:
- **Remains a server component** (no `"use client"` directive). `ScrollReveal` (client) is rendered as a wrapper around `MDXRemote` output, not the other way around. This is valid in Next.js: server components can render client components as wrappers.
- Calls `splitContentBySections(content)` to get sections array
- First section: rendered without `ScrollReveal` wrapper (immediately visible)
- Subsequent sections: heading line (first line up to first `\n`) rendered in one `ScrollReveal` with `animation="fade-up"`, body (remaining lines) rendered in a second `ScrollReveal` with `animation="fade-up"` and `delay={100}`. If body is empty (heading-only section), only the heading `ScrollReveal` is rendered.
- Each `<MDXRemote>` call receives the same `components` map and `mdxOptions` (including `remarkGfm`) as the current single call
- Removed the `firstSectionImmediate` prop — first section always renders without wrapper

**`blog/[slug]/page.tsx`** — Hero changes:
- All hero `ScrollReveal` wrappers get `immediate` prop added
- The `ScrollReveal` wrapper around `<BlogContent>` is removed (BlogContent handles its own reveals now)

**`guides/[slug]/page.tsx`** — Same changes as blog page.

### Files Modified

| File | Change |
|------|--------|
| `components/ui/ScrollReveal.tsx` | Add `immediate` prop |
| `components/blog/BlogContent.tsx` | Split content, per-section scroll-reveal |
| `app/[locale]/blog/[slug]/page.tsx` | `immediate` on hero, remove content wrapper |
| `app/[locale]/guides/[slug]/page.tsx` | Same as blog page |

### Edge Cases

- **No headings in content**: Entire content renders as the first (immediate) section
- **Heading inside code block**: Code block tracking prevents false splits
- **Empty sections**: Skipped (no empty wrappers rendered)
- **Content before any heading**: Rendered as first section (immediate)

### Not in Scope

- Changing animation types or durations
- Modifying sidebar behavior
- Changing related posts / newsletter section animations
- Changes to markdown content files
