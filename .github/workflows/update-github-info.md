---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
engine: copilot
model: gpt-5.4
'on':
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
tools:
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Tell the agent to:
- read `notes/mona-notes.md`
- web fetch https://github.blog/latest/
- web fetch https://github.blog/changelog/
- web fetch https://awesome-copilot.github.com/workflows/
- read external public guidance with web-fetch
- read repository guidance or reference files with GitHub repository API tools instead of terminal, CLI, or sandboxed commands

Use the following sources and guidance:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Review the official GitHub Blog, GitHub Changelog, and Awesome Copilot workflows content to understand recent product and platform updates. Summarize the most relevant updates in plain, concise language that fits the tone of the site and matches Mona's notes.

Update `site/content/github-info.md` with practical, useful changes for readers. Include source context when the content comes from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows and keep the update accurate and concise.

Open a pull request for Mona to review. Use `safe-outputs` with `create-pull-request` so the agent can propose changes without writing directly to `main`. Do not write directly to `main`; rely on the pull request flow.

Before finalizing the update, confirm the repository guidance and any relevant public content has been reviewed with the approved tools, and keep the final patch focused on the website content only.
