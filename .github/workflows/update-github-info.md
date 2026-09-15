---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine: copilot
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
tools:
  github:
    toolsets:
      - repos
  web-fetch:
  edit:
safe-outputs:
  create-pull-request:
    max: 1
    draft: true
---

# Update GitHub Info

Keep Mona's GitHub Info website current with concise, practical updates from official GitHub sources.

## Research

1. Use the GitHub repository API tools to read `notes/mona-notes.md` and `site/content/github-info.md`. Do not read repository guidance or reference files with terminal, the GitHub CLI, or sandboxed shell commands.
2. Use `web-fetch` to read the public GitHub Agentic Workflows guidance at `https://raw.githubusercontent.com/github/gh-aw/main/.github/aw/github-agentic-workflows.md`.
3. Use `web-fetch` to read `https://github.blog/latest/`.
4. Use `web-fetch` to read `https://github.blog/changelog/`.
5. Use `web-fetch` to read `https://awesome-copilot.github.com/workflows/`.

## Update

Review the fetched material against the existing content. Update `site/content/github-info.md` with a small set of useful, current items, keeping summaries short and practical, preserving the existing editorial structure, and citing the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows source for every item derived from those sites. Do not change unrelated files or invent facts that are not supported by the fetched sources.

Use the `edit` tool to make the file change. After editing, review the resulting diff and confirm that the update is limited to `site/content/github-info.md`.

## Proposal

When the content file has a meaningful update, use the `create-pull-request` safe output to open a pull request for Mona to review. Include a concise title and body summarizing the sources consulted and the main updates. Do not write directly to `main`, push directly to `main`, or merge the pull request. If no meaningful update is available, do not open an empty pull request and report that no change was needed.
