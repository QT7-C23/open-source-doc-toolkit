---
name: coc-writer
description: Write a CODE_OF_CONDUCT.md using the Contributor Covenant (industry standard) with project-specific adaptations. Structured process: identify need → select template → customize enforcement → self-review. Use when the user wants to add a code of conduct, create a safe community, says "code of conduct", "CoC", "行为准则", or "community guidelines".
---

# Code of Conduct Writer — Community Standards

A simple process for adopting and customizing a code of conduct. Don't overthink this — use the established standard with minimal customization.

## Core Philosophy

Every public project that accepts contributions should have a code of conduct. It sets expectations and gives you a framework for handling problems. The industry standard is the **Contributor Covenant** — use it unless you have a specific reason not to.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Need Assessment

<HARD-GATE>
Do NOT create a CoC until you confirm:
1. This is a project that accepts community contributions
2. The maintainer is willing to enforce it
3. There's a contact method for reports
</HARD-GATE>

A CoC without enforcement is worse than no CoC.


### Phase 0.5: Study Real-World Examples (MANDATORY)

Before writing, clone and study the equivalent file or workflow from established open-source projects. Extract what real projects actually do — not what templates say they should do. Present findings before proceeding.

### Phase 1: Single Question

Ask this question **one at a time**:

> "We'll use the Contributor Covenant v2.1 (industry standard, used by Linux, Kubernetes, React, Rails). Any specific concerns you want addressed beyond the standard? If not, we proceed with the standard template."

99% of projects should just say "no" and use it as-is. If yes, note the concern and adapt the enforcement section.

### Phase 2: Create CODE_OF_CONDUCT.md

```markdown
# Contributor Covenant Code of Conduct

## Our Pledge
We as members, contributors, and leaders pledge to make participation in our
community a harassment-free experience for everyone, regardless of age, body
size, visible or invisible disability, ethnicity, sex characteristics, gender
identity and expression, level of experience, education, socio-economic status,
nationality, personal appearance, race, religion, or sexual identity
and orientation.

We pledge to act and interact in ways that contribute to an open, welcoming,
diverse, inclusive, and healthy community.

## Our Standards
Examples of behavior that contributes to a positive environment:
- Demonstrating empathy and kindness toward other people
- Being respectful of differing opinions, viewpoints, and experiences
- Giving and gracefully accepting constructive feedback
- Accepting responsibility and apologizing to those affected by our mistakes
- Focusing on what is best for the overall community

Examples of unacceptable behavior:
- The use of sexualized language or imagery, and sexual attention or advances
- Trolling, insulting or derogatory comments, and personal or political attacks
- Public or private harassment
- Publishing others' private information without explicit permission
- Other conduct which could reasonably be considered inappropriate

## Enforcement Responsibilities
Project maintainers are responsible for clarifying and enforcing our standards
of acceptable behavior and will take appropriate and fair corrective action in
response to any behavior that they deem inappropriate, threatening, offensive,
or harmful.

## Scope
This Code of Conduct applies within all community spaces, and also applies when
an individual is officially representing the community in public spaces.

## Enforcement
Instances of abusive, harassing, or otherwise unacceptable behavior may be
reported to the project maintainer at **[INSERT EMAIL]**.
All complaints will be reviewed and investigated promptly and fairly.

## Attribution
This Code of Conduct is adapted from the [Contributor Covenant][homepage],
version 2.1, available at
https://www.contributor-covenant.org/version/2/1/code_of_conduct.html.

[homepage]: https://www.contributor-covenant.org
```

### Phase 3: Enforcement Setup

The CoC needs a real enforcement path. Ask:

> "What email should I use for CoC reports? (Can be a personal email, or create a dedicated one like `conduct@yourdomain.com`).

If no dedicated email: use the maintainer's GitHub-linked email. Remind them to update it when circumstances change.

### Phase 4: Self-Review

```
[ ] Enforcement email is filled in (not "[INSERT EMAIL]")
[ ] README links to CODE_OF_CONDUCT.md (add to badge row or contributing section)
[ ] Attribution and version are correct (Contributor Covenant 2.1)
[ ] Template language is appropriate for project scope (not overkill for a solo project)
[ ] Maintainer understands they are the enforcement point
```

### Phase 5: Link Integration

Update README to link to the CoC:
```markdown
## 🤝 Contributing
Please read our [Code of Conduct](CODE_OF_CONDUCT.md) and [Contributing Guide](CONTRIBUTING.md).
```

## When NOT to Write a CoC

| Situation | Action |
|-----------|--------|
| Private/personal project | Skip. CoC is for communities. |
| No external contributors expected | Skip. Add when you need it. |
| Project already has CoC | Update link, don't duplicate. |

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| Write a custom CoC from scratch | Use Contributor Covenant — it's battle-tested |
| Leave placeholder email | Fill it in or don't publish the CoC |
| Add CoC then ignore reports | Don't add CoC if you can't enforce |
### Phase 5: User Review

> "CODE_OF_CONDUCT.md ready. Verify: is the enforcement email reachable? Does README link to it?"

## Platform Adaptations

| Platform | Notes |
|----------|-------|
| **GitHub** | Recognized in community profile; auto-linked |
| **GitLab / Gitee** | Same file, same structure |

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| Custom CoC from scratch | Use Contributor Covenant — battle-tested |
| Placeholder email | Fill it in or don't publish |
| Add CoC then ignore reports | Don't add if you can't enforce |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
