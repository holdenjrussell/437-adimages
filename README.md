# 437-adimages

PUBLIC image CDN repo for 437 (shop437.com). Everything in this repo is
consumed via
`https://raw.githubusercontent.com/holdenjrussell/437-adimages/main/<path>`
URLs so images render inside Claude chats, claude.ai sandboxes, Google
Slides/Docs URL fetchers, and Slack image blocks without auth.

PUBLIC-SAFE CONTENT ONLY. Screenshots of publicly served ads and emails,
public brand assets, and public storefront product photos qualify.
Never commit: customer data, internal dashboards, revenue numbers,
unreleased creative under embargo, credentials, or anything the brand
would not show a stranger.

## Layout

| Path | Contents | Producer |
|---|---|---|
| `brand/` | 437 logo variants (PNG + SVG) and palette card | Seeded at setup from the studio brand kit; updated manually |
| `products/<handle>.jpg` | Public storefront product photos, one per product handle | Seeded from the public product-catalog snapshot; refreshed by the publish wrapper |
| `emails/<slug>-<sha8>.png` | Rendered screenshots of publicly sent 437 emails, content-addressed | Klaviyo studio render pipeline via the publish wrapper |
| `previews/<ad_id>.jpg` | Full rendered ad unit (identity header, copy, media/poster, CTA card) per publicly served ad | Ad-preview screenshot job (fast-follow) |

## Conventions

- `main` branch only; consumers hardcode `/main/` in raw URLs.
- Filenames are stable IDs (product handle, ad id, slug + content-hash
  prefix), never human-edited names, so URLs are predictable from
  warehouse rows.
- JPEG for screenshots and product photos (size), PNG/SVG for brand
  assets and email renders (fidelity).
- Producers commit with machine identities and push immediately after
  capture; a file that is not pushed does not exist as far as consumers
  are concerned.
- Keep files reasonably sized (target < 1 MB per image). raw GitHub
  serves large files slowly and some consumers cap fetch sizes.

## Index metadata

The warehouse keeps index metadata per producer lane (capture time,
source, file path, status, public URL). The repo itself carries no
metadata beyond filenames; the DB row is the source of truth, the repo
is delivery.
