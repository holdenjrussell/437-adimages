# previews/ — rendered ad units

Contract for this directory (publisher lands in a fast-follow):

- One `previews/<ad_id>.jpg` per publicly served Meta ad: the FULL
  rendered ad unit (identity header, primary text, media or video poster
  frame, CTA card), captured logged-out via the Graph API previews-edge
  iframe, trimmed, JPEG-compressed.
- `<ad_id>` is the platform ad id (stable machine id), so raw URLs are
  predictable from warehouse rows:
  `https://raw.githubusercontent.com/holdenjrussell/437-adimages/main/previews/<ad_id>.jpg`
- Filled by the ad-preview screenshot publisher job. The job keeps an
  index table in the warehouse (`hermes_warehouse`, `mcp_reporting`
  surface) recording capture time, status, and `public_url`; treat the
  index row's captured-at, not the URL bytes, as freshness truth
  (raw GitHub CDN caches fixed-key paths).
- Only ads that have actually served publicly may appear here. Unlaunched
  or embargoed creative never lands in this directory.
