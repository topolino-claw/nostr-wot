# SEO Schema Enhancements + Citation Infrastructure

## Summary

Add missing structured data schemas (FAQPage, BreadcrumbList, enriched Author), build citation/bibliography MDX components for GEO optimization, upgrade AccordionList to support rich content, and create comprehensive content authoring documentation.

## Part 1: Schema Quick Wins

### 1A. FAQPage Schema (homepage + download page)

Add `FAQPage` JSON-LD wrapping existing FAQ items. No content changes - just structured data output alongside existing accordion content.

**Files:** `app/[locale]/page.tsx`, `app/[locale]/download/page.tsx`

### 1B. Enrich Blog Author Schema

Current `BlogPosting` JSON-LD has minimal author (`name` only). Enrich with:
- `url` (njump.me link from npub)
- `affiliation` (Organization: Nostr Web of Trust)
- `sameAs` (Twitter, GitHub, LinkedIn URLs from frontmatter socials)

**File:** `app/[locale]/blog/[slug]/page.tsx`

### 1C. BreadcrumbList Schema

Add `BreadcrumbList` JSON-LD to blog posts and guide posts.
- Blog: Home > Blog > [Post Title]
- Guides: Home > Guides > [Guide Title]

**Files:** `app/[locale]/blog/[slug]/page.tsx`, `app/[locale]/guides/[slug]/page.tsx`

## Part 2: Citation & Bibliography Infrastructure

### 2A. New MDX Components

Add to `components/blog/BlogContent.tsx` component map:

- **`Citation`** - Inline citation marker `[1]` linking to bibliography entry. Props: `id` (number), `href` (optional anchor link).
- **`Bibliography`** - Renders numbered reference list. Props: `children` (list of `BibEntry`).
- **`BibEntry`** - Single bibliography entry. Props: `id`, `authors`, `title`, `source`, `url`, `year`.
- **`Statistic`** - Highlighted stat with source. Props: `value`, `label`, `source`, `sourceUrl`.
- **`ExpertQuote`** - Styled blockquote with attribution. Props: `quote`, `author`, `title`, `organization`, `avatar` (optional).

### 2B. `<cite>` Tag Support

Add `cite` to the MDX component map with appropriate styling.

### 2C. Upgrade AccordionList for Rich FAQ Answers

Change `answer` field from plain string to support HTML/JSX rendering using `dangerouslySetInnerHTML` or a render prop pattern. This enables links, bold text, and citations in FAQ answers.

## Part 3: Documentation

### 3A. Content Authoring Guide

Create `docs/content-authoring-guide.md` covering:
- WikiLink component usage and best practices
- Citation system: `Citation`, `Bibliography`, `BibEntry` usage
- `Statistic` and `ExpertQuote` component usage
- FAQ authoring with rich content
- SEO structured data overview (what's auto-generated vs manual)
- GEO optimization best practices (citing sources, adding statistics, expert quotes, authoritative tone)
- Content checklist for new blog posts

## Implementation Order

1. FAQPage schema (homepage + download)
2. Enriched blog author schema
3. BreadcrumbList schema
4. New MDX components (Citation, Bibliography, BibEntry, Statistic, ExpertQuote, cite)
5. AccordionList rich content upgrade
6. Content authoring documentation
