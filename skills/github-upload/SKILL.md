---
name: github-upload
description: Standardized workflow for creating and uploading a project to GitHub — git init, .gitignore, README, license, commit conventions, first push. Follows a structured thinking process with audit-then-act phases. Use when the user wants to "upload to GitHub", "create a GitHub repo", "push to GitHub", "初始化仓库", "上传到GitHub", or "make this a git repo".
---

# GitHub Upload — Standardized Repository Creation

A disciplined thinking process for putting any project on GitHub correctly, the first time. Platform-agnostic core — works for GitHub, GitLab, Gitee, and self-hosted Git.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — Project Audit

<HARD-GATE>
Do NOT create a repo, commit, or push until you have:
1. Fully explored the project directory
2. Verified no sensitive files will be committed
3. Confirmed the user's intentions (public/private, repo name, license)
</HARD-GATE>

Run these checks:
- `ls -la` the project root — what's actually there?
- Check for existing `.git` directory (`git status` — already a repo?)
- Check for existing `.gitignore` and evaluate coverage
- Scan for sensitive files: `.env`, `*.pem`, `credentials.*`, `secrets.*`, API keys in source
- Check for large files (>50MB) that should use Git LFS
- Check if `gh` CLI is installed and authenticated: `gh auth status`

### Phase 1: Intention Gathering

Ask these questions **one at a time**:

**Q1: Repository name?**
Default: current directory name. Accept or override.

**Q2: Visibility?**
- A) Public (visible to everyone — recommended for OSS)
- B) Private (only you and collaborators)

**Q3: License?**
- A) MIT (recommended — "use freely")
- B) Apache-2.0 ("credit me")
- C) GPL-3.0 ("share improvements back")
- D) No license for now

**Q4: Do you want to exclude any files beyond the standard .gitignore?**

### Phase 2: .gitignore Generation

Based on project type (detected from files in Phase 0), generate or verify `.gitignore`:

| Project Type | Template |
|-------------|----------|
| Python | `__pycache__/`, `*.pyc`, `*.egg-info/`, `dist/`, `.venv/` |
| Node.js | `node_modules/`, `dist/`, `.env` |
| Java/Maven | `target/`, `*.class`, `.idea/` |
| Rust | `target/`, `*.rs.bk` |
| Mixed/generic | Manual best-effort |

**Always add these universal ignores:**
```gitignore
.env
.env.*
*.log
.DS_Store
Thumbs.db
.vscode/
.idea/
*.swp
*.swo
```

Present the generated `.gitignore` summary to the user and get approval before writing.

### Phase 3: README

Use `readme-writer` skill to generate a professional README.md.

### Phase 4: License

If the user chose a license in Phase 1, create the `LICENSE` file:
- Download license text from `https://choosealicense.com/licenses/<license>/` or use embedded template
- Verify license badge in README matches

### Phase 5: First Commit

Review what will be committed:
```bash
git status
```

Flag any files that shouldn't be included (update `.gitignore` if needed).

**Commit message format** (Conventional Commits):
```
init: initial project setup

- Project structure and files
- .gitignore for <project-type>
- README with quick start, features, license
- LICENSE (<license-name>)
```

### Phase 6: GitHub Repository

**If `gh` CLI is installed and authenticated:**
```bash
gh repo create <repo-name> --<public|private> --source=. --remote=origin --push
```

**Otherwise**, guide the user:

1. Go to `https://github.com/new`
2. Name: `<repo-name>`
3. **DO NOT** check "Add a README file" (we already have one)
4. **DO NOT** check "Add .gitignore" (we already have one)
5. Create → GitHub shows push instructions
6. Run:
   ```bash
   git remote add origin https://github.com/<user>/<repo-name>.git
   git branch -M main
   git push -u origin main
   ```

### Phase 7: Post-Upload Self-Review

```
[ ] README renders correctly on target platform
[ ] .gitignore is working — no sensitive files visible
[ ] Branches visible — default is `main` (not `master`)
[ ] Repository has description set
[ ] GitHub Topics configured (if on GitHub)
[ ] LICENSE file matches badge in README
[ ] No large binary files accidentally committed
[ ] About section filled in (website, topics)
```

Fix any issues BEFORE telling the user it's done.

### Phase 8: User Verification

> "Repository is live at `https://github.com/<user>/<repo-name>`. Please verify the README, .gitignore, and license look correct."

---

## Existing Repositories

If the project already has git history:

**Phase 0-4 are the same.** Then:

### If already on GitHub (just needs a better README/etc.):
1. Make changes on a branch
2. Commit with `docs:` prefix
3. Push and open a PR
4. Wait for user to merge

### If local git but never pushed:
Skip Phase 5-6. Just:
```bash
git remote add origin <url>
git branch -M main
git push -u origin main
```

### If existing commits are messy:
Offer `--force` push (but warn clearly):
> "⚠️ This will overwrite the remote history. Only do this if no one else has cloned/forked the repo. Continue?"

---

## Platform Adaptations

| Platform | Differences |
|----------|-------------|
| **GitLab** | Use `glab` CLI instead of `gh`; default branch may be `master` (offer to rename to `main`) |
| **Gitee** | No API CLI; manual repo creation; push URL format: `git@gitee.com:user/repo.git` |
| **Self-hosted Gitea** | Manual creation; push URL is server-specific |
| **Bitbucket** | Default branch is `master`; no `gh` CLI support |

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| `git add .` without reviewing | `git status` first, flag suspicious files |
| Push `.env` / secrets / keys | Catch in Phase 0 and add to `.gitignore` |
| Push large binaries without LFS | Flag in Phase 0, offer Git LFS setup |
| Default branch `master` | Use `git branch -M main` |
| Empty/pre-written default commit message | Use conventional commits format |
| "Initialize README" on GitHub (creates conflict) | Create README locally first |
| Skip license | Include MIT by default unless user says no |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
