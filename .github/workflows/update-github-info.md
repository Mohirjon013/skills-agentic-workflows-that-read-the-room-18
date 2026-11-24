---
name: update-github-info
description: Propose practical GitHub Info updates from the official GitHub Blog and Changelog.
intent: Keep GitHub Info useful and current with practical updates from official GitHub sources for Mona.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
strict: true
network:
  allowed:
    - github.blog
    - github.com
tools:
  edit: {}
  web-fetch: {}
engine:
  id: copilot
  copilot-sdk: true
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    reviewers:
      - mona
    draft: false
    base-branch: main
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info for Mona

Read `notes/mona-notes.md` and `site/content/github-info.md`. Fetch both official sources:

- https://github.blog/latest/
- https://github.blog/changelog/

Use only recent, verifiable information that gives developers practical GitHub guidance and fits the site's themes. Keep the update short, preserve existing useful content, and link each new claim to its source. Edit only `site/content/github-info.md`.

If either source cannot be fetched or the evidence is insufficient, use `report_incomplete` and do not propose a change. If there is no useful, non-duplicate update, use `noop` with a brief reason. For a meaningful change, open a pull request through the configured safe output for Mona (`mona`) to review. Never write directly to `main` or use another write mechanism.

Check the GitHub Changelog for recent updates.
