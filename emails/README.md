# emails/ — rendered 437 email screenshots

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

## Index

| File | Raw URL |
|---|---|
| `summer-set-email-02a28384.png` | https://raw.githubusercontent.com/holdenjrussell/437-adimages/main/emails/summer-set-email-02a28384.png |
