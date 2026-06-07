---
name: contributing-writer
description: Write professional CONTRIBUTING.md and PR templates following open-source best practices. Structured thinking process: assess project setup → define workflow → document standards → self-review. Use when the user wants to create contributing guidelines, set up PR templates, says "contributing guide", "how to contribute", "贡献指南", "PR template", or wants to accept community contributions.
---

# Contributing Writer — Professional Contribution Guidelines

A disciplined process for writing contribution documentation that actually gets used.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Assess Readiness

<HARD-GATE>
Do NOT write CONTRIBUTING.md until you have verified:
1. The project actually accepts contributions
2. The development setup is documented (or will be in this file)
3. There are tests (or test requirements are defined)
</HARD-GATE>

Check:
- `git remote -v` — public repo?
- Existing CI? Test commands?
- Code style config (`.editorconfig`, `eslint`, `prettier`, `rustfmt`, `black`, etc.)
- Existing `CONTRIBUTING.md` (read if exists)

### Phase 1: Intention Gathering

Ask **one at a time**:

**Q1: Contribution level?**
- A) "I'll review and merge, but anyone can submit PRs" (standard OSS)
- B) "I'm actively looking for contributors to help build features"
- C) "Internal team only, this is just for process documentation"

**Q2: Code style enforcement?**
- A) Automated via linter/formatter + CI
- B) Documented conventions (manual review)
- C) No strict style

**Q3: Test requirements for PRs?**
- A) Must pass existing tests
- B) Must add tests for new features
- C) Testing is optional/encouraged

### Phase 2: Draft CONTRIBUTING.md

Standard structure (tailor based on Phase 1 answers):

```markdown
# Contributing to [Project]

Thanks for your interest in contributing!

## Code of Conduct
This project follows our [Code of Conduct](CODE_OF_CONDUCT.md).

## How to Contribute

### Reporting Bugs
1. Search [existing issues](link) first
2. Use the bug report template
3. Include: steps to reproduce, expected vs actual behavior, environment

### Suggesting Features
1. Search [existing discussions](link) first
2. Open a feature request issue
3. Describe the problem you're solving, not just the solution

### Pull Requests
1. Fork the repo
2. Create a branch: `feat/short-description` or `fix/short-description`
3. Make your changes
4. Add/update tests if applicable
5. Ensure all tests pass: `npm test` (or relevant)
6. Run the linter: `npm run lint` (or relevant)
7. Commit using conventional commits
8. Push and open a PR
9. Link any relevant issues

## Development Setup
\```bash
# Clone
git clone <repo-url>
cd <project>

# Install dependencies
<install-command>

# Run tests
<test-command>

# Run linter
<lint-command>
\```

## Commit Convention
We use [Conventional Commits](https://www.conventionalcommits.org/):
- `feat:` new feature
- `fix:` bug fix
- `docs:` documentation
- `style:` formatting
- `refactor:` code restructuring
- `test:` adding tests
- `chore:` build/tooling

## Code Style
[Describe conventions or link to config files]

## Testing
[Describe test requirements]

## License
By contributing, you agree your contributions will be licensed under [LICENSE NAME].
```

### Phase 3: PR Template (Optional)

If the project uses GitHub PR templates (Phase 1 answers suggest yes):

Create `.github/PULL_REQUEST_TEMPLATE.md`:

```markdown
## Description
[What does this PR do?]

## Related Issues
Closes #[issue-number]

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] Tests pass locally
- [ ] New tests added (if applicable)
- [ ] Manual testing performed

## Checklist
- [ ] Code follows style conventions
- [ ] Commit messages follow conventional commits
- [ ] Documentation updated if needed
```

### Phase 4: Self-Review

```
[ ] Development setup commands actually work when copy-pasted
[ ] Commit convention matches what the project actually uses
[ ] Test commands are correct for this project
[ ] Lint commands are correct for this project
[ ] No "TBD" or placeholder text in commands
[ ] License reference matches actual LICENSE file
[ ] Links point to real URLs (not "link" placeholder)
[ ] PR template (if created) is in correct directory
[ ] Tone is welcoming, not gatekeeping
```

### Phase 5: User Review

> "CONTRIBUTING.md ready at `.github/CONTRIBUTING.md`. Please review the development setup and test commands — these need to be accurate."

---

## Platform Adaptations

| Platform | Differences |
|----------|-------------|
| **GitHub** | `.github/` folder, PR templates, issue templates |
| **GitLab** | `.gitlab/` folder, merge request templates |
| **Gitee** | Same as GitHub structure |

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| "PRs welcome!" with no guidance | Give exact steps with commands |
| Wrong test/lint commands | Verify commands work before writing |
| Generic template copied from elsewhere | Tailor to this project's actual setup |
| Gatekeeping tone ("must follow these 100 rules") | Welcoming tone ("here's how to get started") |
| Skip development setup section | This is the #1 thing contributors need |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
