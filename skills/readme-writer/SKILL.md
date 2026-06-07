---
name: readme-writer
description: Write professional, platform-agnostic README.md documentation for any project — GitHub, GitLab, Gitee, self-hosted, or standalone. Follows a structured thinking process: audience assessment → interview → outline → section-by-section drafting → self-review. Use when the user wants to create, improve, or rewrite a README, project documentation, says "write a README", "improve my README", "帮我写README", "写项目文档", or asks about documentation structure.
---

# README Writer — Professional Project Documentation

A disciplined thinking process for writing project documentation that works everywhere, not just GitHub.

## Core Philosophy

A README is a **product landing page** — it must answer three questions in 10 seconds:
1. What does this project do?
2. Is it relevant to me?
3. How do I try it immediately?

It must serve TWO readers simultaneously:
- **Humans**: visual hierarchy, context, progressive disclosure
- **AI agents**: structured format, clear section boundaries, copy-paste-able code

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Explore Before Writing

<HARD-GATE>
Do NOT write a single line of the README until you have:
1. Explored the project (files, structure, existing docs)
2. Understood what the project actually does
3. Identified the primary audience
</HARD-GATE>

Run these checks:
- `ls` the project root — what's actually there?
- Check if README already exists (read it if so)
- Check for existing docs (`/docs`, `CONTRIBUTING.md`, `ARCHITECTURE.md`)
- Identify tech stack (package.json, pyproject.toml, go.mod, etc.)
- Check for license file

### Phase 0.5: Study Real-World Examples (MANDATORY — Do Not Skip)

Before writing, study at least ONE successful README from a similar project type. Extract what works, not just "what sections they have."

**Repository references to study (clone and grep structure):**

| Project Type | Study This Repo | Key Takeaway |
|-------------|-----------------|--------------|
| **Tool/App** | `tonhowtf/omniget` | Problem-first framing, "The small things that add up" human touch, conversational section names |
| **Library/Plugin** | `mattpocock/skills` | "Why These Exist" philosophy, categorized tree structure, Quickstart promises speed |
| **AI/ML** | `AUTOMATIC1111/stable-diffusion-webui` | Feature-first layout, extensive install guides |
| **Framework** | `vercel/next.js` | Clean install → quick tutorial → deep docs architecture |
| **Monorepo** | `facebook/react` | Modular structure, links to per-package docs |

**Patterns to extract from real READMEs:**

1. **Problem-first framing** (OmniGet style): Open with "The problem this solves" — make the user feel understood before listing features
2. **Conversational section names** (OmniGet style): "How it feels day-to-day" beats "User Experience". "The small things that add up" beats "Additional Features"
3. **"Why These Exist" framing** (Matt Pocock style): For collections/toolkits, explain the philosophy before the catalog
4. **Speed promise** (Matt Pocock style): "Quickstart (30-second setup)" — give a concrete time
5. **Category buckets** (Matt Pocock style): For repos with 5+ items, organize by purpose, not alphabetically

Run these checks:
- `git clone --depth 1 <reference-repo> /tmp/ref-study && grep "^##" /tmp/ref-study/README.md` — extract section structure
- Note which sections appear FIRST (not "what sections exist", but "what order")
- Note the TONE: formal (Anthropic) vs human (OmniGet) vs problem-solver (Matt Pocock)
- Identify 1-2 specific techniques to borrow for THIS project's README
- Present findings to the user and get confirmation before drafting

### Phase 1: Audience & Genre Assessment

Ask these questions **one at a time**. Never batch them.

**Q1: Who is the primary reader?**
- A) New users trying the project for the first time
- B) Contributors who will modify/extend the code
- C) API consumers integrating the project as a dependency
- D) Evaluators deciding whether to adopt the project

**Q2: What project type is this?**
- A) CLI tool / utility
- B) Library / SDK / framework
- C) Web application / SaaS
- D) Game / mod / creative project
- E) AI/ML model or dataset
- F) Configuration / dotfiles / template

**Q3: Where will this README live?**
- A) GitHub/GitLab/Gitee (renders Markdown with badges, Mermaid, etc.)
- B) npm/PyPI/Cargo registry (limited Markdown, no HTML)
- C) Standalone file in a distributed package
- D) Documentation website landing page

Based on answers, determine the **Diataxis weighting**:

| Primary Reader | Tutorial | How-To | Reference | Explanation |
|:---|---:|---:|---:|---:|
| New user | 40% | 40% | 10% | 10% |
| Contributor | 10% | 20% | 30% | 40% |
| API consumer | 5% | 30% | 55% | 10% |
| Evaluator | 5% | 20% | 10% | 65% |

Present the weighting to the user and get confirmation before proceeding.

### Phase 2: Outline Agreement

Present the proposed section structure based on project type. The user MUST approve the outline before drafting begins.

**Standard sections** (all project types):
1. Title + One-liner
2. Badges (stars, license, CI, version)
3. Quick Start (3 steps max, copy-paste ready)
4. Features
5. Installation
6. Usage Examples
7. License

**Conditional sections** (add based on project type + audience):

| Section | When to Include |
|---------|----------------|
| Demo GIF/Screenshot | Has visual output |
| Why This Project? | Has competitors |
| Architecture (Mermaid) | Multi-component system |
| API Reference | Library/SDK |
| Configuration | Has config files |
| FAQ / Troubleshooting | Common issues exist |
| Contributing | Open to PRs |
| Star History | Public GitHub repo |
| Roadmap | Active development |
| Security | Handles sensitive data |
| Changelog | Versioned releases |
| Acknowledgments | Uses others' work |

### Phase 3: Section-by-Section Drafting

Draft ONE section at a time. After each section, briefly present it and ask "Does this look right?" before moving to the next.

**Drafting order** (most important first):
1. Title + One-liner (the hook — spend time here)
2. Quick Start (the #1 conversion lever)
3. Features
4. Installation
5. Usage Examples
6. Conditional sections
7. Badges
8. License

**Section quality rules:**
- Title: `# ProjectName` only, no emoji, no tagline
- One-liner: ≤120 characters. Must answer "what, who, why different"
- Quick Start: exactly 3 steps (install → configure → run). Must work when copy-pasted
- Code blocks: always specify language. Every code block must be runnable
- Paragraphs: max 5 lines. Use tables and lists over walls of text
- Images: always include alt text. GIFs ≤5MB, ≤20 seconds

### Phase 4: Self-Review Gate

Before showing the user the final README, run this checklist:

```
[ ] One-liner answers "what, who, why" in ≤120 chars
[ ] Quick Start is exactly 3 copy-paste steps
[ ] All code blocks specify language and are runnable
[ ] No placeholder text, TODOs, or "Coming soon"
[ ] All links work (relative paths resolved)
[ ] License section present and correct
[ ] No wall-of-text paragraphs (>5 lines)
[ ] Images have alt text
[ ] README works on target platform (check rendering limitations)
[ ] AI-readable: clear headers, structured data, copy-paste examples
[ ] Human-readable: visual hierarchy, context, not overwhelming
```

Fix any issues BEFORE presenting to the user.

### Phase 5: User Review Gate

> "README written. Please review it at `<path>` and let me know if you want any changes."

Only proceed to finalize after user approval.

---

## Platform-Specific Adaptations

### GitHub/GitLab/Gitee
- Full Markdown + Mermaid + badges supported
- Use `<details>` for collapsible sections
- Add star history chart
- Set GitHub Topics

### npm/PyPI/Cargo Registry
- Stripped-down Markdown, limit HTML
- No Mermaid, no collapsible sections
- Link to external docs for deep content
- Keep under 500 lines (some registries truncate)

### Standalone File
- Self-contained: no external image dependencies (or inline them)
- Assume no CSS rendering (plain Markdown viewer)
- Include version and date at top

### Documentation Website
- Short landing page (~200 words) + link to full docs
- Focus on "why" and "quick start"
- Use `docs/` folder structure for deep content

---

## Section Templates

### Quick Start (the most important section)

```markdown
## 🚀 Quick Start

### Prerequisites
- [Requirement 1]
- [Requirement 2]

### 1. Install
\```bash
command-to-install
\```

### 2. Configure
\```bash
command-to-configure
\```

### 3. Run
\```bash
command-to-run
\```

> ⚡ **Done!** [What the user should see]
```

For multi-platform, use tab-style or separate subsections:
```markdown
### Install

**Windows:**
\```powershell
winget install project
\```

**macOS:**
\```bash
brew install project
\```

**Linux:**
\```bash
curl -sSL https://install.project.com | sh
\```
```

### Features Table

```markdown
## ✨ Features

| Category | Feature | Description |
|----------|---------|-------------|
| 🔧 Core | [Feature] | [One-line] |
| ⚡ Performance | [Feature] | [One-line] |
| 🔒 Security | [Feature] | [One-line] |
```

### Architecture (Mermaid)

```markdown
## 🏗️ Architecture

\```mermaid
graph LR
    A[Input] --> B[Core]
    B --> C[Output]
    B --> D[Storage]
\```
```

### Badges

```markdown
[![Stars](https://img.shields.io/github/stars/USER/REPO?style=social)](https://github.com/USER/REPO)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![CI](https://img.shields.io/github/actions/workflow/status/USER/REPO/ci.yml)](https://github.com/USER/REPO/actions)
```

### License

| Scenario | License |
|----------|---------|
| "Anyone can use freely" | MIT |
| "Share improvements back" | GPL-3.0 |
| "Free for OSS, paid for commercial" | AGPL-3.0 |
| "Just credit me" | Apache-2.0 |
| "Do whatever" | Unlicense |

Default to MIT unless user specifies otherwise.

---

## Anti-Patterns (Never Do These)

| ❌ Don't | ✅ Do |
|----------|------|
| Start writing before understanding the project | Phase 0: explore first |
| Batch multiple questions at once | One question per turn |
| "This project is simple, it doesn't need a structured README" | Every project goes through the full process |
| Placeholder text ("Coming soon", "TODO") | Remove the section or add real content |
| Wall of text >5 lines per paragraph | Tables, lists, short paragraphs |
| No demo/output example at top | CLI: terminal screenshot. Web: product GIF |
| Generic "PRs welcome" | Specific contributing steps |
| README >1000 lines | Push deep content to `/docs`, link out |
| Stale dates everywhere | Remove dates or keep current |
| Mix user docs and dev docs | Separate into README vs CONTRIBUTING |

---

## Progressive Disclosure Structure

```
Level 1 — README (30 seconds)
    What + Why + Quick Start + License
         ↓
Level 2 — /docs (5 minutes)
    Guides, Tutorials, Examples
         ↓
Level 3 — /docs/reference (on demand)
    API Reference, Architecture, Deep Dives
         ↓
Level 4 — Source Code (when needed)
    Inline comments, module-level docs
```

The README is Level 1. It should be complete but brief — **link out** to deeper docs, don't inline them.

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
