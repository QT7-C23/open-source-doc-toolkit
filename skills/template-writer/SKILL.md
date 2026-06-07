---
name: template-writer
description: Write professional GitHub issue templates (bug report, feature request) and pull request templates using YAML forms with required field validation. Structured thinking process: assess project type → select template categories → draft YAML forms → configure template chooser → self-review. Use when the user wants to create issue templates, PR templates, set up .github workflows, says "issue template", "PR template", "bug report form", or "feature request form".
---

# Template Writer — Issue & PR Templates

A disciplined process for creating GitHub `.github/` templates that improve issue quality and reduce triage burden.

## Core Philosophy

A blank issue box produces garbage. Structured forms produce actionable reports. Every required field should earn its place — if the maintainer doesn't need it to diagnose the issue, don't make the reporter fill it out.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Project Assessment

<HARD-GATE>
Do NOT create templates until you have verified:
1. This project actually receives (or expects) external issues/PRs
2. The maintainer knows what information they typically need to diagnose bugs
3. The tech stack is understood (for environment fields)
</HARD-GATE>

Check:
- Does the project have open issues? What's the typical quality?
- What does the maintainer always ask when triaging? (That goes in the template.)
- What's the project's tech stack? (Determines environment dropdown options.)
- Existing `.github/` folder? Existing templates?


### Phase 0.5: Study Real-World Examples (MANDATORY)

Before writing, clone and study the equivalent file or workflow from established open-source projects. Extract what real projects actually do — not what templates say they should do. Present findings before proceeding.

### Phase 1: Intention Gathering

Ask **one at a time**:

**Q1: What templates do you need?**
- A) Bug report + Feature request (minimum, 99% of projects)
- B) Bug + Feature + Question redirect (recommended)
- C) Bug + Feature + Docs improvement + Custom
- D) PR template only

**Q2: Where should questions go?**
- A) GitHub Discussions (recommended — keeps issues actionable)
- B) Discord/community chat
- C) Nowhere — questions can be issues (solo projects)

**Q3: What are the environment options for bug reports?**
- Generated from project type (OS, runtime version, framework version, browser)

### Phase 2: Template Creation

#### 2a: Bug Report (`01-bug-report.yml`)

```yaml
name: Bug Report
description: Report a bug or unexpected behavior
title: "[Bug]: "
labels: ["bug", "needs-triage"]
body:
  - type: markdown
    attributes:
      value: |
        Thanks for taking the time to report a bug!
        Please fill out the form below to help us reproduce and fix the issue.

  - type: textarea
    id: description
    attributes:
      label: Describe the bug
      description: A clear and concise description of what the bug is.
      placeholder: "When I do X, Y happens instead of Z..."
    validations:
      required: true

  - type: textarea
    id: steps
    attributes:
      label: Steps to reproduce
      description: Numbered steps to trigger the bug.
      placeholder: |
        1. Go to '...'
        2. Run '...'
        3. See error
      render: markdown
    validations:
      required: true

  - type: textarea
    id: expected
    attributes:
      label: Expected behavior
      description: What did you expect to happen?
    validations:
      required: true

  - type: textarea
    id: actual
    attributes:
      label: Actual behavior
      description: What actually happened? Include error messages.
      render: text

  - type: dropdown
    id: os
    attributes:
      label: Operating System
      options:
        - Windows 11
        - Windows 10
        - macOS (latest)
        - Linux (Ubuntu/Debian)
        - Linux (Fedora/Red Hat)
        - Linux (Arch)
        - Other
    validations:
      required: true

  - type: input
    id: version
    attributes:
      label: Version
      description: Output of `command --version`
      placeholder: "v1.2.3"
    validations:
      required: true

  - type: textarea
    id: logs
    attributes:
      label: Relevant log output
      description: Paste any error messages or log output.
      render: shell

  - type: checkboxes
    id: checks
    attributes:
      label: Before submitting
      options:
        - label: I've searched existing issues and this is not a duplicate
          required: true
        - label: I'm using the latest version
          required: true
```

#### 2b: Feature Request (`02-feature-request.yml`)

```yaml
name: Feature Request
description: Suggest a new feature or improvement
title: "[Feature]: "
labels: ["enhancement"]
body:
  - type: textarea
    id: problem
    attributes:
      label: Problem statement
      description: What problem would this feature solve? Why do you need it?
      placeholder: "I'm always frustrated when..."
    validations:
      required: true

  - type: textarea
    id: solution
    attributes:
      label: Proposed solution
      description: How should it work? Include example API usage or CLI command.
      placeholder: |
        ```bash
        $ tool new-feature --flag value
        ```
    validations:
      required: true

  - type: textarea
    id: alternatives
    attributes:
      label: Alternatives considered
      description: What other solutions have you considered or tried?

  - type: dropdown
    id: contribute
    attributes:
      label: Would you be willing to contribute this feature?
      options:
        - "Yes, I can submit a PR"
        - "Maybe, with guidance"
        - "No, just suggesting"
    validations:
      required: true
```

#### 2c: Template Chooser (`config.yml`)

```yaml
blank_issues_enabled: false
contact_links:
  - name: Security Vulnerability
    url: https://github.com/USER/REPO/security/advisories/new
    about: Report security issues privately — do NOT open a public issue
  - name: Questions & Discussions
    url: https://github.com/USER/REPO/discussions
    about: Ask questions here — we use Discussions for Q&A
  - name: Documentation
    url: https://USER.github.io/REPO
    about: Check the docs before filing an issue (if docs site exists)
```

#### 2d: PR Template (`pull_request_template.md`)

```markdown
## Summary
<!-- Brief description of what this PR does and why -->

## Related Issues
- Closes #

## Type of Change
- [ ] Bug fix (non-breaking)
- [ ] New feature (non-breaking)
- [ ] Breaking change
- [ ] Documentation update

## Testing
<!-- How did you test this? -->

## Checklist
- [ ] Code follows project conventions
- [ ] Self-reviewed
- [ ] Tests pass: `<test-command>`
- [ ] Documentation updated (if needed)
```

### Phase 3: Self-Review

```
[ ] Bug template requires: description, steps, expected, actual, version
[ ] Environment dropdowns match project's actual target platforms
[ ] Feature template requires problem statement (not just "I want X")
[ ] config.yml has blank_issues_enabled: false
[ ] config.yml redirects questions to the right place
[ ] Security advisory link is correct (USER/REPO)
[ ] PR template has test command filled in (not placeholder)
[ ] Labels are consistent (bug/enhancement/needs-triage)
[ ] No unnecessary required fields (don't gatekeep reporters)
```

### Phase 4: User Review

> "Templates ready in `.github/ISSUE_TEMPLATE/` and `.github/pull_request_template.md`. Test the flow: try creating a test issue to see the template chooser."

---

## Platform Adaptations

| Platform | Templates Location |
|----------|-------------------|
| **GitHub** | `.github/ISSUE_TEMPLATE/*.yml` + `.github/pull_request_template.md` |
| **GitLab** | `.gitlab/issue_templates/*.md` + `.gitlab/merge_request_templates/*.md` |
| **Gitee** | Same as GitHub structure |

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| 10 required fields for a bug report | 5-6 essential fields maximum |
| "Describe the bug" as the only field | Structured fields for steps, expected, actual |
| Markdown templates with no validation | YAML forms with `validations: required: true` |
| Blank issues enabled for active projects | `blank_issues_enabled: false` — force structure |
| Same template for bug and feature | Separate forms for different intents |
| "Version: latest" without version command | Ask for actual output: `tool --version` |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
