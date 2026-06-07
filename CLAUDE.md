# CLAUDE.md

This repo is a Claude Code skill collection — 14 documentation-writing skills installable as a marketplace plugin.

## Installation

```bash
npx skills add QT7-C23/open-source-doc-toolkit
```

Or manually: copy `skills/*` to `~/.claude/skills/`.

## Skill Architecture

Every skill in this collection follows the same workflow pattern:
1. **Phase 0: Hard Gate** — audit context before writing
2. **Phase 1: Q&A** — one question at a time, AskUserQuestion visual UI
3. **Phase 2-3: Draft** — section-by-section with approval checkpoints
4. **Phase 4: Self-Review** — structured checklist before user sees output
5. **Phase 5: User Review** — final approval gate

Skills are platform-agnostic — they adapt to GitHub, GitLab, Gitee, npm, PyPI, and standalone docs.