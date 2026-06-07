---
name: release-writer
description: Write professional, platform-agnostic release notes, CHANGELOG.md, and version announcements following Semantic Versioning and Keep a Changelog standards. Follows a structured thinking process: audit changes → classify by impact → determine version bump → draft changelog → write release notes → self-review. Use when the user wants to write release notes, create a CHANGELOG, bump a version, prepare a release, says "release notes", "changelog", "发版说明", "更新日志", or "what version should this be".
---

# Release Writer — Professional Release Documentation

A disciplined thinking process for writing release notes and changelogs that work everywhere — GitHub Releases, GitLab, Gitee, npm, PyPI, standalone CHANGELOG.md.

## Core Philosophy

A release announcement must answer three questions instantly:
1. What changed? (overview in one scan)
2. Should I upgrade? (breaking changes? security fixes?)
3. How do I upgrade? (migration steps)

Two audiences, like the README:
- **Humans**: scannable, context-rich, upgrade path clear
- **Machines**: structured format, parseable, semantic versioning compliant

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Audit Before Writing

<HARD-GATE>
Do NOT write a single line of release notes until you have:
1. Identified ALL changes since the last release (git log, merged PRs, closed issues)
2. Classified every change by type and impact
3. Determined the correct version bump
</HARD-GATE>

Run these checks:
- `git log <last-tag>..HEAD --oneline` to list all commits
- `git log <last-tag>..HEAD --merges --oneline` for merged PRs
- Check if CHANGELOG.md already exists (read it)
- Check existing version tag format (`v1.0.0` vs `1.0.0`)
- Check if there's a release config file (`.version-bump.json`, `release-please.yml`, etc.)


### Phase 0.5: Study Real-World Examples (MANDATORY)

Before writing, clone and study the equivalent file from a top-tier open source repo. Extract what real projects actually write — not what templates say they should write. Present findings before drafting.

### Phase 1: Change Classification

Classify EVERY change. One change = one classification:

| Type | Description | Version Bump | Example |
|------|-------------|:--:|---------|
| **BREAKING** | API change, removed feature, renamed config, dropped platform support | MAJOR | "Removed `--legacy` flag" |
| **Added** | New feature, new endpoint, new option | MINOR | "Added `--output json` support" |
| **Changed** | Behavior change (not breaking), performance improvement, dependency update | MINOR or PATCH | "Improved startup time by 40%" |
| **Deprecated** | Feature will be removed in future | MINOR | "`--old-flag` deprecated, use `--new`" |
| **Removed** | Deprecated feature now removed | MAJOR | "Removed v1 API endpoints" |
| **Fixed** | Bug fix | PATCH | "Fixed crash on empty input" |
| **Security** | Vulnerability fix | PATCH (always) | "Fixed XSS in search bar" |
| **Docs** | Documentation-only changes | (skip version bump) | "Updated API reference" |
| **Chores** | CI, build, tooling (no user impact) | (skip from changelog) | "Upgraded CI to Node 22" |

### Phase 2: Version Determination

Based on Phase 1 classification, determine the version bump:

```text
Any BREAKING  → MAJOR      (1.x.x → 2.0.0)
Any Added/Changed/Deprecated, no BREAKING  → MINOR  (1.2.x → 1.3.0)
Only Fixed/Security  → PATCH  (1.2.3 → 1.2.4)
Only Docs/Chores  → no release needed
```

If on `0.x.x` (pre-1.0), the rules are relaxed:
- `0.2.0 → 0.3.0` for MINOR changes
- `0.2.1 → 0.2.2` for PATCH changes
- Treat any significant API change as MINOR until 1.0

Ask the user one question:
> "Based on these changes, the version bump should be **[MAJOR/MINOR/PATCH]: X.Y.Z → A.B.C**. Does this look right?"

### Phase 3: CHANGELOG Entry

Follow **Keep a Changelog** format (https://keepachangelog.com):

```markdown
## [1.3.0] - 2026-06-07

### Added
- New `--output json` option for structured output.
- Support for Python 3.14.

### Changed
- Default timeout increased from 30s to 60s.
- Improved startup performance by 40%.

### Deprecated
- `--legacy-mode` is deprecated. Use `--mode standard` instead.

### Fixed
- Fixed crash when input file is empty (#42).
- Fixed incorrect error message on timeout (#38).

### Security
- Updated dependency `requests` to patch CVE-2026-1234.
```

**Formatting rules:**
- Version header: `## [X.Y.Z] - YYYY-MM-DD` (ISO date format)
- Group by type: Added → Changed → Deprecated → Removed → Fixed → Security
- Each entry: past tense, one line, ends with period
- Reference issues/PRs: `(#123)` at end of line
- Skip empty groups (no "None" or "—")
- Link versions at bottom (if on GitHub): `[1.3.0]: https://github.com/...`

If CHANGELOG.md exists, prepend the new entry at the top (after the title line).
If CHANGELOG.md doesn't exist, create it with header and "Unreleased" section.

### Phase 4: Release Notes (GitHub/GitLab Release Body)

Release notes are more narrative than CHANGELOG. Structure:

```markdown
## 🎉 Highlights
[A 1-2 sentence summary of the most exciting thing in this release]

## ⚠️ Breaking Changes
[If any: what broke, why, how to migrate. Be specific with code examples.]

## 🚀 What's New
### [Feature Group 1]
- Bullet list of features
### [Feature Group 2]
- ...

## 🐛 Bug Fixes
- ...

## 🔒 Security
- ...

## 📦 Installation
\```bash
npm install package@latest
\```

## 🙏 Contributors
Thanks to @user1, @user2 for this release.

---

**Full Changelog**: https://github.com/user/repo/compare/v1.2.3...v1.3.0
```

For non-GitHub platforms (npm, PyPI, etc.): strip Markdown that won't render, keep it plain-text friendly.

### Phase 5: Self-Review Gate

Before finalizing:

```
[ ] Every change in git log since last tag is accounted for
[ ] Version bump follows SemVer correctly
[ ] Breaking changes are clearly flagged with migration path
[ ] Security fixes are highlighted
[ ] No placeholder text or "Various fixes"
[ ] CHANGELOG entry uses Keep a Changelog format
[ ] Release notes tell a story (not just a list)
[ ] Upgrade path is clear (if breaking changes exist)
[ ] Links are correct (compare URL, issue references)
[ ] Date is today's date in YYYY-MM-DD format
```

Fix any issues BEFORE presenting to user.

### Phase 6: User Review Gate

> "Release notes and CHANGELOG ready for vX.Y.Z. Changelog entry added to CHANGELOG.md. Please review and let me know if you want changes."

Only tag and push after user approval.

---

## Platform-Specific Adaptations

### GitHub Releases
- Full Markdown + emoji + images
- Link to compare view: `/compare/v1.2.3...v1.3.0`
- Attach binary artifacts if applicable

### npm Registry
- Release notes go in the publish command: `npm publish --note="..."`
- CHANGELOG.md is separate (linked from npm page)
- Keep release notes under 500 chars (npm truncates)

### PyPI
- Release notes are plain text (rendered as monospace)
- No emoji, no images, no code blocks with language tags
- Use ASCII-art for emphasis: `=== Highlights ===`

### GitLab Releases
- Same as GitHub, use GitLab compare URL format: `/compare/v1.2.3...v1.3.0`

### Internal/Monorepo
- Prefix version with component: `@scope/package@1.3.0`
- Cross-reference other components' versions

---

## Pre-1.0 vs Post-1.0

| Aspect | Pre-1.0 (0.x) | Post-1.0 |
|--------|---------------|----------|
| Breaking changes | Minor version bump OK | Must be major |
| Stability promise | "Expect changes" | Must document migration |
| CHANGELOG | Simpler, less formal | Keep a Changelog strict |
| Release notes | Can be casual | Should be professional |
| Upgrade guide | Optional | Required for breaking changes |

---

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| "Various bug fixes and improvements" | List each fix with issue reference |
| Skip breaking change documentation | Flag with ⚠️ and provide migration steps |
| Forget to update CHANGELOG | Always update CHANGELOG.md before tagging |
| Commit without version bump | Bump version in code + tag + CHANGELOG all at once |
| Release notes = git log dump | Group by type, add narrative, highlight key changes |
| Skip security fix flagging | Always highlight security fixes prominently |
| Date formats: `2026-6-7` or `6/7/26` | Always `YYYY-MM-DD` (ISO 8601) |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
