---
name: security-policy-writer
description: Write a SECURITY.md with vulnerability reporting process, supported versions, and disclosure policy. Structured thinking process: assess project sensitivity → define reporting channel → document version support → self-review. Use when the user wants to create a security policy, set up responsible disclosure, says "security policy", "SECURITY.md", "安全策略", "vulnerability reporting", or "responsible disclosure".
---

# Security Policy Writer — Vulnerability Reporting

A disciplined process for writing security policies that protect both users and maintainers.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Sensitivity Assessment

<HARD-GATE>
Do NOT write a security policy until you have assessed:
1. Does this project handle user data, credentials, or tokens?
2. Is it a library that other projects depend on?
3. Is there a real security surface (network, file I/O, authentication)?
</HARD-GATE>

If answers are all "no" (e.g., a static site generator, a learning project), the policy can be minimal. If "yes" to any, it needs to be more thorough.


### Phase 0.5: Study Real-World Examples (MANDATORY)

Before writing, clone and study the equivalent file or workflow from established open-source projects. Extract what real projects actually do — not what templates say they should do. Present findings before proceeding.

### Phase 1: Intention Gathering

Ask **one at a time**:

**Q1: How do you want to receive vulnerability reports?**
- A) Email (private, recommended for small projects)
- B) GitHub Security Advisories (built-in, private, recommended for GitHub-hosted projects)
- C) Both

**Q2: What versions do you actively support with security patches?**
- A) Latest release only (most common for solo/small projects)
- B) Latest major version + previous major version
- C) LTS (if the project has long-term support releases)

**Q3: What's your expected response time?**
- A) "As soon as possible, typically within 48 hours" (standard)
- B) "Within 7 days" (hobby project)
- C) "Within 24 hours" (critical infrastructure)

### Phase 2: Draft SECURITY.md

**For projects that DO handle sensitive data:**

```markdown
# Security Policy

## Supported Versions

| Version | Supported          |
|---------|--------------------|
| 2.x     | ✅ Active support  |
| 1.x     | ⚠️ Security only   |
| < 1.0   | ❌ End of life     |

## Reporting a Vulnerability

**Please do NOT open a public issue for security vulnerabilities.**

Instead, report them privately:

- **GitHub**: Use the [Security Advisory](https://github.com/USER/REPO/security/advisories/new) form
- **Email**: security@example.com (PGP key: [link])

We aim to acknowledge your report within 48 hours and provide a timeline for resolution.

## Disclosure Policy

1. Reporter submits vulnerability privately
2. Maintainer acknowledges within 48 hours
3. Maintainer validates and develops a fix
4. Fix is released as a patch version
5. Public disclosure 30 days after fix is released (or coordinated with reporter)

We request that you not publicly disclose the vulnerability until we have had reasonable time to address it.

## Security Best Practices for Users

- Always use the latest version
- [Any project-specific security guidance]
```

**For projects that do NOT handle sensitive data (minimal version):**

```markdown
# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability, please email [EMAIL] or use the [GitHub Security Advisory](https://github.com/USER/REPO/security/advisories/new) form.

Please do NOT create a public issue.

## Supported Versions

Only the latest release receives security updates.

## Acknowledgments

We appreciate responsible disclosure. With your permission, we'll credit you in the release notes.
```

### Phase 3: Self-Review

```
[ ] Contact method is filled in (email or GitHub advisory link)
[ ] Supported versions table is accurate (not aspirational)
[ ] Response time promise is realistic
[ ] Disclosure timeline is reasonable (not "immediately" and not "never")
[ ] No security vulnerabilities disclosed in the policy itself (don't list known issues)
[ ] PGP key link works (if email-based reporting)
[ ] GitHub advisory URL is correct (USER/REPO)
```

### Phase 4: User Review

> "SECURITY.md ready. Test the reporting flow: try submitting a test advisory through GitHub to make sure the link works."

---

## When NOT to Write a Security Policy

| Situation | Action |
|-----------|--------|
| Learning/demo project with no real users | Skip. A policy promises things you can't deliver. |
| Static content (blog, portfolio) | Skip. "No security surface" is the honest answer. |
| Project already has SECURITY.md | Update supported versions, don't duplicate. |

## Platform Setup

### GitHub Security Advisories (Recommended)
Settings → Security → Enable "Private vulnerability reporting". This adds a "Report a vulnerability" button to the repo. Then the SECURITY.md just needs to link to it.

### Email-Based
Use a dedicated email if possible. Add PGP key for encrypted reporting (optional but professional). Don't use a personal email you check once a week.

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| Promise 24-hour response as a solo maintainer | Promise 48-72 hours — deliverable |
| Claim "v1.x is supported" when you have no v1.x test infrastructure | Only list versions you actually test |
| List known vulnerabilities in SECURITY.md | That's what advisories are for |
| "Email me" without providing an email | Fill in every placeholder |
| Skip SECURITY.md for libraries that 1000 projects depend on | Libraries need this MORE, not less |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
