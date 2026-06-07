---
name: opensource-publish
description: Guide for publishing open-source projects to community platforms — Weblate (translation), Open Collective (funding), Codecov (coverage), ReadTheDocs (docs), and more. Follows a structured assessment-then-act workflow. Use when the user wants to set up translations, accept donations, add coverage tracking, host documentation, or integrate any open-source community service. Triggers on: "weblate", "open collective", "opensource setup", "开源平台", "翻译平台", "code coverage", "funding", "donations", "readthedocs".
---

# Open-Source Platform Publishing

A disciplined process for connecting your project to the open-source ecosystem. Don't set up a platform just because it exists — only add what your project actually needs.

## Core Philosophy

Every platform adds maintenance burden. Each badge = a promise to keep it working. Be selective.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Project Maturity Check

<HARD-GATE>
Do NOT suggest platforms until you understand:
1. The project's current stage (pre-release, active, mature)
2. Whether the user has bandwidth for ongoing maintenance
3. What problem each platform solves for THIS specific project
</HARD-GATE>

Pre-release (0.x): suggest ONLY Weblate (if multilingual). Skip everything else.
Active (1.x+): suggest based on actual need. Be selective.
Mature: suggest the full suite if appropriate. Still be selective.


### Phase 0.5: Study Real-World Examples (MANDATORY)

Before writing, clone and study the equivalent file or workflow from established open-source projects. Extract what real projects actually do — not what templates say they should do. Present findings before proceeding.

### Phase 1: Need Assessment

Ask these questions **one at a time**:

**Q1: Does your project have user-facing text that could benefit from volunteer translators?**
- Yes → Webate (Phase 2)
- No → skip Weblate

**Q2: Do you want to accept financial contributions from your users?**
- Yes → GitHub Sponsors (simpler) or Open Collective (transparent) (Phase 3)
- No → skip funding

**Q3: Do you have automated tests running in CI?**
- Yes → Codecov or Coveralls for coverage tracking (Phase 4)
- No → skip — set up tests first, then come back

**Q4: Does your documentation extend beyond the README?**
- Yes → ReadTheDocs or GitHub Pages (Phase 5)
- No → skip — your README is enough for now

**Q5: Do you want a space for community Q&A beyond Issues?**
- Yes → GitHub Discussions (Phase 6)
- No → skip

**Q6: Do you actively want to build a real-time chat community?**
- Yes → Discord server + badge (Phase 7)
- No → skip — only do this if you're ready to moderate

Only proceed to phases the user said yes to.

---

### Phase 2: Weblate — Translation Platform

Pre-requisite: your project must already have translation/i18n files.

**If no translation files exist yet**, guide the user to create them:

| Ecosystem | File Format | Example Path |
|-----------|------------|--------------|
| Flutter/Dart | `.arb` | `l10n/app_en.arb` |
| Web/React/i18next | JSON | `public/locales/en/translation.json` |
| Python/gettext | `.po` | `locale/en/LC_MESSAGES/messages.po` |
| Android | XML | `res/values/strings.xml` |
| Simple/Generic | JSON | `src/i18n/en.json` |

**Setup:**
1. User goes to `https://hosted.weblate.org` → GitHub login → "Add new translation project"
2. Configure source repo URL, file mask, source language
3. Weblate auto-detects strings + creates translation PRs
4. Add badge to README:
   ```markdown
   [![Translation status](https://hosted.weblate.org/widgets/<project>/-/open-graph.png)](https://hosted.weblate.org/engage/<project>/)
   ```

**Post-setup:** verify the badge renders, PR a test translation to confirm the pipeline works.

---

### Phase 3: Funding

**Option A: GitHub Sponsors** (simplest, zero third-party)
- Settings → Sponsor button → "Set up sponsor button"
- Add `FUNDING.yml` to repo root
- Badge: already built into GitHub sidebar

**Option B: Open Collective** (transparent expenses, fiscal host)
- Go to `https://opencollective.com` → GitHub login
- Create Collective → link repo → set fiscal host
- Badge:
  ```markdown
  [![Open Collective backers](https://img.shields.io/opencollective/backers/<project>?label=backers)](https://opencollective.com/<project>)
  ```

Recommendation: start with GitHub Sponsors (zero friction). Add Open Collective only if you have recurring expenses to manage transparently.

---

### Phase 4: Code Coverage

Pre-requisite: tests exist and run in CI.

**Codecov** (recommended):
1. User signs up at `https://codecov.io` with GitHub
2. Add coverage generation to CI (e.g., `pytest --cov` or `nyc --reporter`)
3. Add Codecov upload action to CI workflow
4. Badge:
   ```markdown
   [![codecov](https://codecov.io/gh/<user>/<repo>/branch/main/graph/badge.svg)](https://codecov.io/gh/<user>/<repo>)
   ```

**Coveralls** (alternative): Same concept. Less popular in 2026 but still functional.

---

### Phase 5: Documentation Hosting

Only if docs extend beyond README.

**ReadTheDocs** (for Sphinx/MkDocs):
1. User imports project at `https://readthedocs.org`
2. Auto-builds on every push
3. Docs live at `https://<project>.readthedocs.io`

**GitHub Pages** (for static sites or simple MD):
1. Settings → Pages → Source: `Deploy from a branch`
2. Point to `/docs` folder or `gh-pages` branch
3. Site at `https://<user>.github.io/<repo>`

---

### Phase 6: GitHub Discussions

Settings → Features → Enable Discussions.

**Categories to create:**
- 💬 General (Q&A)
- 💡 Ideas (feature requests)
- 🙏 Q&A (help/support)

Only enable this if you want to actively participate. An empty forum is worse than no forum.

---

### Phase 7: Community Chat

**Only create a Discord server if:**
- You have 50+ active users
- You're ready to moderate (it WILL need moderation)
- You or someone will be present regularly

If conditions met: create server → add badge:
```markdown
[![Discord](https://img.shields.io/discord/<server-id>?color=5865F2&logo=discord&logoColor=white)](https://discord.gg/<invite>)
```

If conditions NOT met: skip this. Badge without an active community is worse than no badge.

---

### Phase 8: README Integration & Self-Review

After setting up any platform:
1. Add badge to README badge row
2. Add dedicated section if major (e.g., "## 🌍 Translations")
3. Run this checklist:

```
[ ] Each badge renders correctly on target platform
[ ] Each badge links to the correct page
[ ] Privacy: no API keys or secrets exposed in README
[ ] Maintenance: user has access to each platform dashboard
[ ] Consistency: badge style matches (all `style=social` or all `style=flat`)
[ ] No dead platforms: every badge links to an active service
```

### Phase 9: User Verification

> "I've set up the following platforms for your project: [list]. Please verify each one works by opening the dashboard links. Any issues?"

---

## Platform Selection Matrix

| Project Stage | Suggested Platforms |
|--------------|-------------------|
| Pre-release (0.x) | Weblate only (if multilingual). Nothing else. |
| Active solo (1.x) | Weblate + GitHub Sponsors + Codecov |
| Active team (1.x+) | All assessed platforms if needed |
| Mature (2.x+) | Full suite — but only if you have bandwidth |
| Archived/Stable | None — just maintain existing badges |

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| Suggest every platform to a solo project | Use Phase 1 questions, be selective |
| Add Discord badge without active server | Skip Discord unless you're ready to moderate |
| Set up Codecov without CI tests | Tests first, coverage second |
| "Why not set up all of them?" | Each = maintenance burden |
| Badge soup (10+ badges in README) | Badge row ≤6 shields, link rest |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
