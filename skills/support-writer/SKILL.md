---
name: support-writer
description: Write a SUPPORT.md that tells users where to get help — GitHub Discussions, Discord, Stack Overflow, documentation, or commercial support. Structured thinking process: assess support channels → define scope → document expectations → self-review. Use when the user wants to create a support policy, says "SUPPORT.md", "support policy", "where to get help", or wants to direct users to the right support channel.
---

# Support Writer — Help Channel Documentation

A simple, honest document that tells users where to get help. Prevents issues from becoming support tickets.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Channel Audit

<HARD-GATE>
Do NOT write SUPPORT.md until you know:
1. What support channels actually exist and are actively monitored
2. What the maintainer's support capacity is
3. Whether there's any commercial/paid support option
</HARD-GATE>

Don't list channels that aren't actually monitored. A dead Discord badge is worse than no badge.

### Phase 1: Single Question

> "What support channels do you actively monitor? Pick all that apply: A) GitHub Discussions, B) Discord/community chat, C) Stack Overflow tag, D) Email, E) Commercial/paid support, F) Documentation only"

### Phase 2: Draft

```markdown
# Support

## How to Get Help

| Channel | Best For | Response Time |
|---------|----------|---------------|
| [GitHub Discussions](link) | Questions, usage help, ideas | Usually within [N] days |
| [Documentation](link) | How-to, API reference | Self-serve |
<!-- Add only channels the user actually monitors -->

## Before You Ask for Help
1. Search [existing discussions](link) — your question may already be answered
2. Read the [FAQ](link) or [documentation](link)
3. Provide: what you're trying to do, what you've tried, relevant code/error messages

## Bug Reports vs Support Questions
- **Bug**: something is broken → [Open an issue](link)
- **Question**: how do I do X → [Ask in Discussions](link)
- **Security issue**: → [Report privately](SECURITY.md)

## Commercial Support
[Only include if applicable]

[Company/individual] offers paid support, consulting, and custom development.
Contact: [email/website]

## Community Support
[Only include if applicable]

Our community helps each other. Please:
- Be patient — everyone here is volunteering
- Be respectful — read our [Code of Conduct](CODE_OF_CONDUCT.md)
- Help others when you can
```

### Phase 3: Self-Review

```
[ ] Every channel listed is actually monitored (not aspirational)
[ ] Response time promises are realistic
[ ] Link to documentation is correct
[ ] Difference between bug report and support question is clear
[ ] Commercial support section included only if applicable
[ ] No dead links to abandoned Discord servers or forums
```

---

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| List a Discord server you never check | Only list channels you're active in |
| "Email me anytime" as a solo maintainer | Set expectations: "I respond within 3-5 days" |
| No distinction between bugs and questions | Use Discussions for questions, Issues for bugs |
### Phase 4: User Review

> "SUPPORT.md ready. Test every channel link — are they all pointing to live, monitored destinations?"

## Platform Adaptations

| Platform | Notes |
|----------|-------|
| **GitHub** | SUPPORT.md auto-linked in community profile |
| **GitLab / Gitee** | Same file, same structure |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
