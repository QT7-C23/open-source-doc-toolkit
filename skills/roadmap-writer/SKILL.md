---
name: roadmap-writer
description: Write clear, honest project roadmaps (ROADMAP.md) that communicate direction without over-promising. Structured thinking process: audit current state → categorize by timeline → write with confidence levels → self-review. Use when the user wants to create a roadmap, plan future features, communicate project direction, says "roadmap", "路线图", "project plan", or "what's next".
---

# Roadmap Writer — Honest Project Planning

A disciplined process for writing roadmaps that set expectations, not create debt.

## Core Philosophy

A roadmap is a **communication tool**, not a binding contract. Every item must carry a confidence level so readers know what's real vs aspirational.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Audit Current State

<HARD-GATE>
Do NOT write a roadmap until you have:
1. Listed all features the project currently HAS
2. Identified existing open issues and feature requests
3. Assessed the maintainer's available bandwidth
</HARD-GATE>

Check:
- Open issues labeled `enhancement` or `feature`
- Existing milestone tags on GitHub/GitLab
- Recent commit velocity (how fast things actually ship)
- Any existing TODO.md, ROADMAP.md, or project board


### Phase 0.5: Study Real-World Examples (MANDATORY)

Before writing, clone and study the equivalent file or workflow from established open-source projects. Extract what real projects actually do — not what templates say they should do. Present findings before proceeding.

### Phase 1: Intention Gathering

Ask **one at a time**:

**Q1: Timeline scope?**
- A) Short-term only (next 1-2 releases) — safest, most honest
- B) Short + medium (next 3-6 months)
- C) Full vision (short + medium + long-term) — only if you're confident

**Q2: How public is this?**
- A) Public ROADMAP.md — visible to all users
- B) Internal only — team-facing, not user-facing
- C) GitHub Project board — live, not a static document

**Q3: How confident are you about the items?**
The roadmap should reflect reality. Be honest.

### Phase 2: Categorization

For each planned item, assign a confidence level:

| Level | Label | Meaning | When to Use |
|-------|-------|---------|-------------|
| 🟢 **Committed** | "Will ship next release" | Actively being worked on. You'd bet money on it. | Only items with assigned contributors + active branches |
| 🟡 **Planned** | "Aiming for in the next 2-3 releases" | Clear plan, but not started. >70% likely. | Top feature requests with scoped designs |
| 🔵 **Exploring** | "Investigating feasibility" | Idea exists, no plan yet. <50% likely. | Community suggestions, nice-to-haves |
| ⚪ **Aspirational** | "Long-term vision" | Would be cool someday. No timeline. | Moonshots, "one day" ideas |

### Phase 3: Draft ROADMAP.md

```markdown
# Roadmap

> This roadmap represents our current thinking. Priorities may shift based on community feedback and maintainer availability.

## 🟢 Committed (Next Release)

| Feature | Description | Target |
|---------|-------------|--------|
| [Feature] | [One-line] | vX.Y.0 |
| [Feature] | [One-line] | vX.Y.0 |

## 🟡 Planned (Next 1-3 Months)

| Feature | Description | Why It Matters |
|---------|-------------|----------------|
| [Feature] | [One-line] | [User benefit] |
| [Feature] | [One-line] | [User benefit] |

## 🔵 Exploring (No Timeline)

| Idea | Status | How You Can Help |
|------|--------|------------------|
| [Idea] | Researching | [What we need to know] |
| [Idea] | Needs design | [Link to discussion] |

## ⚪ Aspirational (Long-Term Vision)

- [Idea] — when [condition]
- [Idea] — if demand exists

---

## How Items Get On (and Off) This Roadmap

- Community suggestions → 🔵 Exploring
- Upvoted by 10+ users + scoped design → 🟡 Planned
- Assigned contributor + active work → 🟢 Committed

Items that lose momentum move back a tier. We'd rather be honest than aspirational.

## What Won't Happen
[Optional: list things people ask for that you've decided NOT to do. Saves everyone time.]
- ...
```

### Phase 4: Self-Review

```
[ ] Every committed item has an actual contributor assigned (not "someone")
[ ] Planned items have a clear user benefit stated
[ ] No item is in both committed AND exploring (one status only)
[ ] What Won't Happen section is honest (not empty or sarcastic)
[ ] Timeline estimates are realistic (2× your gut feel)
[ ] Links to issues/discussions work
[ ] No marketing-speak — plain, clear language
```

### Phase 5: User Review

> "Roadmap ready at `ROADMAP.md`. Key question: do the committed items accurately reflect what you're actually working on right now?"

---

## When NOT to Write a Roadmap

| Situation | Action |
|-----------|--------|
| Pre-release (0.x) | "Roadmap: Get to 1.0. Nothing else matters." |
| Solo maintainer, no users yet | Skip. Ship features, not documents. |
| Project is stable/maintenance mode | Write a "What won't happen" list instead. More honest. |
| You don't know what's next | Don't fake it. Say "No roadmap yet — open an issue with your ideas." |

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| "Coming Q3 2026" for ideas you haven't designed | Use confidence levels honestly |
| 50 items in committed | 2-3 committed max. If you have more, you're not being honest about bandwidth |
| Delete items that didn't ship | Update status. "Moved back to exploring" is fine |
| Copy a startup's visionary roadmap | Solo maintainers can't promise "AI integration by Q4" |

## Platform Adaptations

| Platform | Notes |
|----------|-------|
| **GitHub** | Standard ROADMAP.md; link from README |
| **GitLab** | Use milestone boards as live roadmap complement |
| **Gitee / others** | Same Markdown, same structure |

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| "Coming Q3 2026" for ideas you haven't designed | Use confidence levels honestly |
| 50 items in committed | 2-3 committed max |
| Delete unshipped items silently | Update status — "Moved back to exploring" is fine |
| Solo maintainer with a 100-item roadmap | Ship features, not documents |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
