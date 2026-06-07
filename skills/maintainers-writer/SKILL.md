---
name: maintainers-writer
description: Write a MAINTAINERS.md documenting who maintains the project, their roles, decision-making process, and how to become a maintainer. Structured thinking process: identify current maintainers → define roles → document process → self-review. Use when the user wants to document project leadership, define maintainer roles, says "MAINTAINERS.md", "maintainer list", "project leadership", or "who runs this project".
---

# Maintainers Writer — Project Leadership Documentation

A document that answers "who's in charge" and "how do I become one". Only useful when a project has multiple maintainers or expects to grow.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Relevance Check

<HARD-GATE>
Do NOT create MAINTAINERS.md if:
- The project has ONE maintainer (just put your name in README)
- The project doesn't accept external contributors
- There's no plan to grow the maintainer team

If solo: "Maintained by @username" in README is sufficient.
</HARD-GATE>

### Phase 1: Single Question

> "Who are the current maintainers, and what are their areas of responsibility?"

### Phase 2: Draft

```markdown
# Maintainers

## Current Maintainers

| Name | GitHub | Role | Focus Area | Time Zone |
|------|--------|------|------------|-----------|
| [Name] | [@handle] | Lead | Overall direction | UTC+8 |
| [Name] | [@handle] | Core | Backend, API | UTC-5 |

## Alumni
<!-- Former maintainers who've moved on -->
| Name | GitHub | Tenure |
|------|--------|--------|
| [Name] | [@handle] | 2024-2026 |

## Roles & Responsibilities

| Role | Responsibilities |
|------|-----------------|
| **Lead** | Sets project direction, makes final decisions on disagreements, manages releases, handles CoC enforcement |
| **Core** | Reviews and merges PRs, triages issues, participates in design discussions |
| **Triager** | Labels and responds to issues, helps with reproduction |

## Decision Making
- **Consensus preferred**: maintainers discuss and aim for agreement
- **Lead decides**: if consensus can't be reached, the lead makes the call
- **RFC for major changes**: significant changes go through an RFC process ([link to RFC template/discussion])

## Becoming a Maintainer

Maintainers are contributors who have shown sustained, high-quality contributions.

The path:
1. **Contribute consistently** — several quality PRs over time
2. **Show good judgment** — helpful code reviews, constructive discussions
3. **Be nominated** — any existing maintainer can nominate you
4. **Consensus** — existing maintainers agree (majority vote, no strong objections)

Reach out to any maintainer if you're interested in this path.

## Maintainer Commitment

Maintainers are expected to:
- Respond to issues/PRs in their focus area within [N] days
- Participate in occasional design discussions
- Follow the [Code of Conduct](CODE_OF_CONDUCT.md)
- Help onboard new contributors

Maintainers who become inactive for [N] months may move to alumni status. This is not a punishment — life happens, and alumni are always welcome back.
```

### Phase 3: Self-Review

```
[ ] Every listed maintainer has explicitly agreed to be listed
[ ] Roles and responsibilities are clear (not vague "helps out")
[ ] Decision-making process is documented (avoid "we'll figure it out")
[ ] Path to becoming a maintainer is concrete, not "be excellent"
[ ] Alumni section exists (or is intentionally omitted for new projects)
[ ] Time zones listed (important for response expectations)
[ ] No personal contact info beyond GitHub handles (unless explicitly approved)
```

---

## When to Skip

| Situation | Action |
|-----------|--------|
| Solo maintainer | "Maintained by @username" in README |
| Company-internal project | This doc is for open-source community governance |
| Just getting started | Write when you have 2+ maintainers, not before |

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| List people who left without their consent in alumni | Ask before listing anyone, including alumni |
| "Become a maintainer by being excellent" | Give concrete criteria: N PRs, reviews, months of contribution |
| No decision-making process documented | Even "lead decides" is better than no process |
### Phase 4: User Review

> "MAINTAINERS.md ready. Verify: has every listed person agreed? Are time zones and roles accurate?"

## Platform Adaptations

| Platform | Notes |
|----------|-------|
| **GitHub** | Standard location; link from CONTRIBUTING |
| **GitLab / Gitee** | Same file, same structure |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
