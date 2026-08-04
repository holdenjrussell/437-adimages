# emails/ — rendered 437 email screenshots

Two filename shapes coexist in this directory, one per render lane:

## `<slug>-<sha8>.png` — studio lane (sent emails)

Screenshots of publicly sent 437 emails, rendered by the Klaviyo studio
pipeline. Content-addressed: each file is named `<slug>-<sha8>.png`,
where `<slug>` is the studio artifact slug and `<sha8>` is the first 8
hex chars of the content-addressed artifact directory
(`~/klaviyo-warehouse/artifacts/studio/<slug>/<sha256>/desktop.png` on
the ops machine). A changed email renders to a NEW hash and therefore a
new URL, which sidesteps raw GitHub CDN caching.

Publisher contract: the publish wrapper
(`~/.hermes/apps/437-mcp/scripts/publish_adimages.sh`) syncs any new
`desktop.png` renders from the studio artifacts directory into this
directory and pushes. Only renders of emails that were actually sent to
the public list belong here.

## `<template_id>.jpg` — template-library lane

Full-page renders of the reusable Klaviyo template library (every row in
the warehouse's `public.templates` mirror), produced by
`~/klaviyo-warehouse/scripts/email_render_sync.py`: script tags
stripped, headless Chromium at a 680px viewport, height capped at
12,000px, JPEG quality 80, target under 1MB. Keyed by the durable
Klaviyo template id, so the URL is predictable from any warehouse row:

    https://raw.githubusercontent.com/holdenjrussell/437-adimages/main/emails/<template_id>.jpg

Index of record: `visual_archive.email_renders` in the
`klaviyo_warehouse` Postgres (status, dimensions, source-HTML sha256,
`rendered_at`, `public_url`). Because the key is FIXED per template, a
re-render reuses the same URL and the raw GitHub CDN may serve stale
bytes briefly — treat `rendered_at` in the index, not the URL bytes, as
freshness truth.

CRITICAL semantics: template-library renders are NOT campaign sends.
Only the studio lane's content-addressed `<slug>-<sha8>.png` files prove
what an email actually sent looked like.

Both lanes write to this directory only through the shared exclusive
flock on `~/.hermes/tmp/437-adimages-git.lock`; neither lane ever
rewrites the other lane's files.

## Index

| File | Raw URL |
|---|---|
| `summer-set-email-02a28384.png` | https://raw.githubusercontent.com/holdenjrussell/437-adimages/main/emails/summer-set-email-02a28384.png |
