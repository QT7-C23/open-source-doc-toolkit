---
name: governance-writer
description: Write a GOVERNANCE.md documenting project decision-making, maintainer roles, voting procedures, and conflict resolution. Based on the Minimum Viable Governance (MVG) template used by CNCF projects. Structured thinking process: assess team size → choose governance model → define roles and process → self-review. Use when the user wants to create governance docs, define decision-making, says "governance", "project governance", "decision making policy", or "how are decisions made".
---

# Governance Writer — Project Decision-Making Documentation

A disciplined process for writing governance documentation. Start simple, scale up.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Team Assessment

<HARD-GATE>
Do NOT write GOVERNANCE.md until you know:
1. How many maintainers actively participate
2. Whether there's an existing informal decision process
3. Whether an external entity (company, foundation) has authority
</HARD-GATE>


### Phase 0.5: Study Real-World Examples (MANDATORY)

Before writing, clone and study the equivalent file or workflow from established open-source projects. Extract what real projects actually do — not what templates say they should do. Present findings before proceeding.

### Phase 1: Model Selection

Ask **one at a time**:

**Q1: What's the team structure?**
- A) BDFL (Benevolent Dictator for Life) — one person has final say
- B) Core maintainers + consensus — small team, informal
- C) Formal voting with elected roles — larger team, formal

**Q2: Who owns the project?**
- A) Individual
- B) Company
- C) Foundation (CNCF, Apache, etc.)
- D) Community (no single owner)

### Phase 2: Draft

**For BDFL (most solo projects):**

```markdown
# Governance

## BDFL
[Name] ([@handle]) is the BDFL (Benevolent Dictator for Life) of this project.

As BDFL, [Name] has the final say on:
- Project direction and scope
- Major architectural decisions
- Maintainer selection
- Code of Conduct enforcement

The BDFL delegates day-to-day decisions to maintainers and trusts contributors to make good choices. The BDFL role is a commitment to stewardship, not a license to be a jerk.

## Conflict Resolution
If the BDFL cannot continue, they will appoint a successor. If no successor is appointed, maintainers will select a new BDFL by consensus.

## Changes to Governance
Changes to this document require BDFL approval.
```

**For consensus-based team:**

```markdown
# Governance

## Roles

| Role | Description |
|------|-------------|
| **Lead** | Sets direction, breaks deadlocks, manages releases |
| **Maintainer** | Reviews/merges PRs, triages issues, participates in design |
| **Contributor** | Anyone who submits accepted PRs |

## Decision Making
- **Lazy consensus**: proposals are considered accepted after [N] days if no maintainer objects
- **RFC for major changes**: significant changes require a written proposal and discussion
- **Voting**: if consensus can't be reached, maintainers vote. Majority wins. Lead breaks ties.
- **Quorum**: at least [N] maintainers must participate for a vote to be valid

## Becoming a Maintainer
1. Sustained contributions over [N] months
2. Nominated by any existing maintainer
3. 2/3 maintainer approval

## Removing a Maintainer
- Voluntary: maintainer steps down
- Inactive: no activity for [N] months → moved to alumni
- Conduct: Code of Conduct violation → immediate removal by lead after investigation

## Changes to Governance
Changes require 2/3 maintainer approval and a public comment period of [N] days.

## Conflict of Interest
Maintainers must disclose relevant conflicts. The lead (or remaining maintainers, if the lead is conflicted) decides on recusal.

## Transparency
- Major decisions are documented in [GitHub Discussions / mailing list / ADRs]
- Meeting notes are public (if applicable)
- Financial decisions (if applicable) are reported transparently
```

### Phase 3: Self-Review

```
[ ] Governance model matches actual team size (not aspirational)
[ ] "BDFL" is not used as an excuse for ignoring community feedback
[ ] Removal and succession paths are documented
[ ] Conflict of interest policy exists
[ ] Voting thresholds are clear (not "we'll vote when needed")
[ ] Document is honest about who really makes decisions
[ ] No governance theater — if BDFL always wins, just say so
```

---

## When to Skip

| Situation | Action |
|-----------|--------|
| Solo project, no external contributors expected | Skip. BDFL = you, no doc needed. |
| Company project where company policy already governs | Link to company policy |
| Team of 2-3, no governance disputes expected | Skip until you grow |

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| Create elaborate governance for a 3-person team | MVG (Minimum Viable Governance) — keep it simple |
| BDFL in name but community-run in practice | Be honest about who's actually in charge |
| No removal/succession path | What happens if the BDFL disappears? |
| "We'll figure it out when it happens" | Write the process now, when there's no conflict |
### Phase 4: User Review

> "GOVERNANCE.md ready. Key check: does the model actually match how decisions are made today? If BDFL always wins, just say so — governance theater helps no one."

## Platform Adaptations

| Platform | Notes |
|----------|-------|
| **GitHub** | Standard location; link from CONTRIBUTING |
| **GitLab / Gitee** | Same file, same structure |
| **Foundation-backed** | Reference foundation charter; document delegates to it |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
