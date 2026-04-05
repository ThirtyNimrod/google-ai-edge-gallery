---
name: markdown-qa
description: Upload one or more Markdown (.md) files and ask questions about their content.
metadata:
  homepage: ""
  require-secret: false
---

# Markdown QA

This skill lets the user upload Markdown files via a visible webview UI, stores them locally in the webview's `localStorage`, and provides a headless processor that answers questions about uploaded files.

Usage:
- If no files are uploaded the skill returns a `webview` prompting the user to upload files.
- After uploading, invoke the skill again with a question; the headless runner will read uploaded files from `localStorage`, select relevant sections, and return a concise answer with provenance.

Implementation notes:
- `assets/webview.html` — visible UI for uploading `.md` files (saves to `localStorage['markdown_uploads_v1']`).
- `scripts/index.html` — headless runner implementing `window.ai_edge_gallery_get_result(data, secret)`.
