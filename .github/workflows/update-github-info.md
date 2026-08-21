---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
strict: true
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
    read-only: true
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    draft: true
    max: 1
---

# Update GitHub Info

Keep the GitHub Info website current with concise, practical updates for developers.

## Research

1. Read `notes/mona-notes.md` and follow its editorial guidance.
2. Use the web-fetch tool to read https://github.blog/latest/.
3. Use the web-fetch tool to read https://github.blog/changelog/.
4. Use the web-fetch tool to read https://awesome-copilot.github.com/workflows/.
5. Use the GitHub repository tools to read relevant repository guidance and reference files. Do not use terminal, CLI, or sandboxed commands for this repository research.

## Update

Review the current content in `site/content/github-info.md`, then update that file with useful, concise information based on the official sources. Use https://awesome-copilot.github.com/workflows/ as an additional source for Awesome Copilot workflows. Mention the source whenever a change comes from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows. Keep the existing editorial angle and avoid unsupported claims.

## Pull Request

After making and reviewing the change, open one draft pull request for Mona to review using the `create_pull_request` safe output. Include a concise title and a body that summarizes the content changes and links to the official sources consulted. Do not write directly to `main`. Call `create_pull_request` only once, when the final changes and PR details are ready, then stop.