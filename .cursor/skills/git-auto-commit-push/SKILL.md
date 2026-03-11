---
name: git-auto-commit-push
description: Queries repository changes, stages all files, commits with a concise English message (≤30 words), and pushes. Use when the user asks to commit changes, push code, save work to git, or sync changes to remote.
---

# Git Auto Commit & Push

## Workflow

1. **Query changes**: Run `git status` and `git diff` to inspect modified/added/deleted files.
2. **Summarize**: Generate a concise commit message that captures the key changes.
3. **Stage**: Run `git add .` (or `git add -A`).
4. **Commit**: Run `git commit -m "<message>"`.
5. **Push**: Run `git push`.

## Commit Message Rules

- **Language**: Pure English only.
- **Length**: ≤30 words.
- **Style**: Imperative mood, concise. Focus on what changed, not why.
- **Format**: Prefer `type: brief description` (e.g., `docs: update sidebar`, `fix: correct typo in analysis`).

## Message Examples

| Changes | Good Message |
|---------|--------------|
| Updated _sidebar.md | `docs: update sidebar links` |
| Added PonyAI analysis, fixed Meituan typos | `feat: add PonyAI analysis, fix Meituan typos` |
| Modified 3 analysis files | `chore: update analysis documents` |

## Edge Cases

- **No changes**: Report "No changes to commit" and skip add/commit/push.
- **Uncommitted changes exist**: Proceed with workflow.
- **Push fails** (e.g., need pull): Run `git pull --rebase` then `git push`, or report the error to the user.
