---
name: citation-writer
description: Write a CITATION.cff file (Citation File Format) so academics and researchers can properly cite your software in papers. Structured process: gather metadata → format per CFF spec → validate → self-review. Use when the user wants to add citation support, says "citation", "CITATION.cff", "cite this project", "学术引用", or "how to cite this software".
---

# Citation Writer — Academic Citation for Software

A simple process for creating CITATION.cff files that make your software citable in academic papers.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Relevance Check

<HARD-GATE>
CITATION.cff is ONLY for projects that could be cited in research papers.
Skip if: this is a personal blog, a game mod, a config repo, or a learning project.
Proceed if: this is a library, framework, tool, dataset, or algorithm that researchers might reference.
</HARD-GATE>

### Phase 1: Metadata Gathering

Ask **one at a time**:

**Q1: Who are the authors?**
Format: `given-name family-name`. At minimum, the project creator. Order matters — first author gets top billing.

**Q2: What's the official title?**
Use the project name as it should appear in a paper's reference list.

**Q3: Any DOI?**
If the project has a Zenodo/GitHub DOI or published paper DOI. If no: "Leave blank — I'll generate one from Zenodo later."

**Q4: Version?**
Current release version. If no release yet: leave as "0.1.0" or omit.

### Phase 2: Draft

```yaml
cff-version: 1.2.0
title: Project Name
message: >-
  If you use this software in your research, please cite it using the
  metadata below.
type: software
authors:
  - given-names: FirstName
    family-names: LastName
    email: user@example.com
    orcid: https://orcid.org/0000-0000-0000-0000
    affiliation: University/Company Name (optional)
repository-code: https://github.com/USER/REPO
url: https://project-website.com
abstract: >-
  One-paragraph description of what the software does — similar to
  an abstract in a paper.
keywords:
  - keyword1
  - keyword2
  - keyword3
license: MIT
version: 1.0.0
date-released: 2026-06-07
```

**Field notes:**

| Field | Required? | Notes |
|-------|:--:|-------|
| `cff-version` | Yes | Always `1.2.0` (latest CFF spec) |
| `title` | Yes | Project name as it should appear in citations |
| `message` | No | Shown when someone views the citation file on GitHub |
| `type` | Yes | Almost always `software` |
| `authors` | Yes | At least one author. Include ORCID if available |
| `repository-code` | No | Link to source code |
| `url` | No | Project website (not the same as repo URL) |
| `abstract` | No | Helps researchers understand what they're citing |
| `keywords` | No | Helps discoverability in academic search |
| `license` | No | SPDX identifier |
| `version` | No | The version being cited |
| `date-released` | No | YYYY-MM-DD of this release |
| `doi` | No | Digital Object Identifier (from Zenodo, Figshare, or journal) |
| `identifiers` | No | Other identifiers like ISBN, arXiv ID |
| `references` | No | Related papers/software that should also be cited |

### Phase 3: Self-Review

```
[ ] cff-version is 1.2.0 (latest)
[ ] All authors explicitly agreed to be listed
[ ] Author names use given-names + family-names (not just a GitHub handle)
[ ] ORCID IDs are valid URLs (if included)
[ ] DOI is correct (if included) — not a repo URL, a real DOI
[ ] YAML is valid (check indentation, no tabs)
[ ] Abstract is descriptive enough for a researcher to understand
[ ] Keywords are relevant (not generic like "software", "tool")
```

### Phase 4: Validation

```bash
# Validate with the official CFF tool (if installed)
cffconvert --validate
```

If `cffconvert` is not available, manually check:
- YAML syntax (consistent indentation, colons followed by space)
- All URLs are valid and accessible
- Date format is YYYY-MM-DD

### Phase 5: Zenodo DOI (Optional but Recommended)

For projects without a DOI, set up automatic archiving:
1. Go to https://zenodo.org → Sign in with GitHub
2. Enable the repository for auto-archiving
3. Create a GitHub Release → Zenodo auto-archives and assigns a DOI
4. Add the DOI to CITATION.cff

With Zenodo auto-archiving, every GitHub Release gets a unique DOI.

### Phase 6: User Review

> "CITATION.cff ready. When someone views the repo on GitHub, they'll see a 'Cite this repository' button. For a real DOI, set up Zenodo auto-archiving — takes 5 minutes."

---

## GitHub Integration

When CITATION.cff is in the repo root, GitHub automatically shows:
- A "Cite this repository" button in the sidebar
- Both APA and BibTeX formats, auto-generated from your CFF file

Users can click → copy → paste into their paper. No extra setup needed.

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| List yourself as sole author if others contributed | Add anyone who made significant contributions as co-author |
| GitHub handle as author name | Use real given-names + family-names |
| "v1.0.0" instead of "1.0.0" in version field | No "v" prefix in version |
| Repo URL as DOI | Leave empty or set up Zenodo for a real DOI |
| Skip ORCID if you have one | ORCID uniquely identifies you across publications |

## Platform Integration

| Platform | Effect |
|----------|--------|
| **GitHub** | Auto-shows "Cite this repository" in sidebar |
| **GitLab** | Recognizes CITATION.cff; shows citation widget |
| **Zenodo** | Auto-archives releases + assigns DOI |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
