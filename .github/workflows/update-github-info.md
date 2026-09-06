---
name: update-github-info
description: Keep the GitHub Info page current with official GitHub updates.
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  edit:
  github:
    toolsets: [repos]
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com

safe-outputs:
  create-pull-request:
    draft: true
    title-prefix: "[github-info] "
---

# Update GitHub Info

Read `notes/mona-notes.md` and follow its editorial guidance.

Use the GitHub repository API tools to read repository guidance and reference files. Do not use terminal, CLI, or sandboxed commands for those reads.

Use the web-fetch tool to fetch both:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Review the latest official updates and update `site/content/github-info.md` with short, practical information that helps developers learn GitHub faster. Mention the source whenever an item comes from the GitHub Blog or GitHub Changelog, and preserve Mona's existing editorial angle and Markdown structure.

Only make focused changes to `site/content/github-info.md`. When there is a meaningful update, create exactly one draft pull request with a concise title and body that summarizes the changes and links to the official sources. Open the pull request for Mona to review. Do not write directly to the default branch. If there is no meaningful update, do not change files and use the appropriate no-op response.