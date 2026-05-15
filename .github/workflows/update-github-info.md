---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.

on:
  workflow_dispatch: {}

  # Daily at 09:17 UTC
  schedule:
    - cron: '17 9 * * *'

safe-outputs:
  # Require PR creation instead of direct repository writes
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false

tools:
  # Allow editing repository files
  edit: {}

  # Allow fetching approved web sources
  web-fetch: {}

network:
  allowed:
    - github.com
    - github.blog

  blocked: []
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/

Update `site/content/github-info.md` with concise,
practical updates for readers and include source context when content comes
from the GitHub Blog or GitHub Changelog.

Open a pull request for Mona to review. 
Use a pull request title that mentions Mona or GitHub Info. 
Do not write directly to `main`; rely on `safe-outputs` with `create-pull-request`.
