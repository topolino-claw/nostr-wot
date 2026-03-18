# Guides Status

Last updated: 2026-03-18

## Summary

| # | Guide | Difficulty | Published | Last Reviewed | Featured Images | Inline Images | Screenshots Status |
|---|-------|-----------|-----------|--------------|----------------|---------------|-------------------|
| 0.1 | what-is-nostr | beginner | ✅ | 2026-03-13 | ✅ feat/preview/og | 2 SVG diagrams | ✅ Complete |
| 0.2 | why-nostr-is-resilient | beginner | ✅ | 2026-03-13 | ✅ feat/preview/og | 2 SVG diagrams | ✅ Complete |
| 0.3 | nostr-for-beginners | beginner | ✅ | 2026-03-13 | ✅ feat/preview/og | — | ⚠️ No inline images |
| 1 | getting-started | beginner | ✅ | 2026-03-18 | ✅ feat/preview/og | 3 screenshots | ✅ Complete |
| 2 | managing-identity | beginner | ✅ | 2026-03-18 | ✅ feat/preview/og | 4 screenshots | ✅ Complete |
| 3 | understanding-wot | beginner | ✅ | 2026-03-11 | ✅ feat/preview/og | — | ❌ Pending (2 screenshots needed) |
| 4 | customizing-trust | intermediate | ✅ | 2026-03-11 | ✅ feat/preview/og | — | ❌ Pending (2 screenshots needed) |
| 5 | setting-up-wallet | beginner | ✅ | 2026-03-11 | ✅ feat/preview/og | — | ❌ Pending (5 screenshots needed) |
| 6 | zapping-auto-approve | beginner | ✅ | 2026-03-11 | ✅ feat/preview/og | — | ❌ Pending (4 screenshots needed) |
| 7 | lightning-address | beginner | ✅ | 2026-03-11 | ✅ feat/preview/og | — | ❌ Pending (3 screenshots needed) |
| 8 | site-permissions | intermediate | ✅ | 2026-03-18 | ✅ feat/preview/og | 5 screenshots | ✅ Complete |
| 9 | wot-playground | intermediate | ✅ | 2026-03-11 | ✅ feat/preview/og | — | ❌ Pending (5 screenshots needed) |

## Detailed Screenshot Status

### ✅ Complete

#### what-is-nostr
- `broadcast-diagram.svg` — inline SVG diagram
- `relay-nodes.svg` — inline SVG diagram

#### why-nostr-is-resilient
- `centralized-vs-nostr.svg` — inline SVG diagram
- `outage-timeline.svg` — inline SVG diagram

#### getting-started
- `setup-wizard.jpg` — first-time setup wizard
- `key-creation.jpg` — 12-word seed phrase / recovery screen
- `import-key.jpg` — import existing key screen

#### managing-identity
- `extension-main.jpg` — extension popup / identity overview
- `identity-tab.jpg` — identity tab with profile details
- `edit-profile.jpg` — edit profile modal
- `lock-screen.jpg` — vault locked / password entry

#### site-permissions
- `pending-request.jpg` — pending permission in popup
- `request-details.jpg` — request details (Read Profile Information)
- `permission-request.jpg` — NIP-07 sign event request with 4 options
- `permissions-list.jpg` — list of sites with granted permissions
- `permissions-detail.jpg` — per-site permission detail + revoke all

---

### ❌ Pending Screenshots

#### nostr-for-beginners
- No inline images added yet (content is step-by-step text flow, lower priority)

#### understanding-wot
- Trust graph visualization with labeled elements
- Extension popup showing trust scores / hop badges on profiles

#### customizing-trust
- Trust formula settings panel (hop decay, path weight, max hops)
- Hop decay slider in different positions (or single settings panel)

#### setting-up-wallet
- Wallet setup screen showing 3 connection options
- Quick Setup result (wallet view with balance)
- NWC connection string input
- LNbits configuration fields
- Wallet balance + transaction history

#### zapping-auto-approve
- Zap button + extension popup with payment request
- Zap confirmation popup
- Auto-approve threshold setting
- Transaction history with zap entries

#### lightning-address
- Claim form with username input
- Prompt to add Lightning Address to Nostr profile
- Incoming zap notification

#### wot-playground
- Playground loading with trust graph rendering
- Full trust graph with color-coded hops
- Node detail panel for a 2nd-degree contact
- Hop filter controls
- Search bar with highlighted result

---

## Notes

- All guides are `published: true` — they are live on nostr-wot.com
- Featured/preview/og images exist for all 12 guides
- PR #3 (topolino-claw → nostr-wot/nostr-wot) is open with these changes pending merge
- Preview environment: https://preview-nostr-wot.fabri.lat/guides
- Screenshots added 2026-03-18 session: getting-started (3), managing-identity (4), site-permissions (5)
