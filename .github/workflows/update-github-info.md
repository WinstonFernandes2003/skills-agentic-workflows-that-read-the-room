---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
engine: copilot
permissions:
  contents: read
  pull-requests: read
tools:
  github:
  web-fetch:
  edit:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
---

# Update GitHub Information

Keep the repository's GitHub information current for Mona to review.

1. Read `notes/mona-notes.md`.
2. Use the web-fetch tool to read https://github.blog/latest/.
3. Use the web-fetch tool to read https://github.blog/changelog/.
4. Use the GitHub repository API tools to read any repository guidance or
   reference files you need. Do not use the terminal, GitHub CLI, or sandboxed
   shell commands for repository guidance or reference-file access.
5. Update `site/content/github-info.md` with accurate, relevant information
   based on the notes and fetched GitHub sources. Preserve the existing format
   and avoid unrelated changes.
6. Use the `create-pull-request` safe output to propose the update in a pull
   request for Mona to review. Do not write directly to `main`.

Do not compile this workflow or create a generated `.lock.yml` file.
