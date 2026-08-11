# gache-cdn

Public image host for @gache.beauty Instagram auto-publishing.
Served via jsDelivr to the Instagram Graph API (which requires public JPEG URLs).

    https://cdn.jsdelivr.net/gh/AdamRyu-V/gache-cdn@main/gache/<file>.jpg

Published by `AdamRyu-V/aesthetik-publisher`. Marketing assets only, no secrets.
Card masters live in Picasso_Cowork/05.SNS Card News/gache/.

## Rules

- **JPEG only.** The Graph API rejects PNG. Convert with `prepare_images.py`.
- **Version the filename whenever the content changes** (`G03-1.jpg` -> `G03v2-1.jpg`).
  jsDelivr caches aggressively, so re-uploading under the same name keeps serving the old
  image and the wrong version gets published. HTTP 200 does not catch this; verify with
  `shasum -a 256` against the local file.
- Large pushes fail with HTTP 400. Set `git config http.version HTTP/1.1` and retry.
