# Public 437 Instagram post visuals

`<media_id>.jpg` is the normalized cover or poster for one public,
first-party 437 Instagram feed post. Image and carousel posts use their feed
image; videos use the public poster thumbnail. Filenames are stable Instagram
media IDs, so the durable URL is:

```text
https://raw.githubusercontent.com/holdenjrussell/437-adimages/main/social/<media_id>.jpg
```

This lane contains public pixels only. Captions, engagement metrics, and
comment analysis remain structured MCP/warehouse data and are not baked into
the JPEG. Stories, DMs, drafts, comments, private or embargoed media, and
creator UGC not owned by 437 are excluded.

The producer validates and normalizes every source to RGB JPEG, caps the
longest edge at 1600 px and the file at 1.5 MB, then stamps the warehouse
`public_url` only after the exact content hash has been pushed successfully.
