---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine: copilot
tools:
  github:
    toolsets:
      - repos
  web-fetch:
  edit:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    max: 1
    base-branch: main
---

# Update GitHub Info

Refresh Mona's GitHub information page with concise, practical guidance for developers.

1. Use GitHub repository API tools to read `notes/mona-notes.md` and `site/content/github-info.md`. Do not use terminal, CLI, or sandboxed commands to read repository guidance or reference files.
2. Use `web-fetch` to read:
  - https://github.blog/latest/
  - https://github.blog/changelog/
  - https://awesome-copilot.github.com/workflows/
3. Identify only current, developer-relevant updates supported by those sources. Preserve the existing Markdown structure and editorial angle, and cite the source for every added or materially changed item.
4. Edit only `site/content/github-info.md`. Do not make unrelated changes.
5. Use the `create_pull_request` safe output to open a pull request for Mona to review. Summarize the sources and changes in the pull request body. Do not write directly to `main`.