# Cram Sheet — pure memorization facts

The stuff that's just "know it or miss it." Final review on Day 5 and the morning of the exam.

## Numbers
- 100 minutes · pass = 700/1000 scaled · ~40–60 questions (unofficial)
- GitHub Free: 2,000 Actions minutes/mo · 500 MB Packages · unlimited public+private repos · unlimited collaborators
- Commit subject line convention: ≤ ~50 chars
- Retakes: 24h after 1st fail, then 14 days, max 5 per 12 months

## Ladders & lists
- Repo roles: **Read → Triage → Write → Maintain → Admin**
- Personal plans: Free, Pro · Org plans: Free, Team, Enterprise (Pro is personal-only)
- Copilot: Free/Pro (individual) · Business/Enterprise (org-managed) · agents, Agent Mode, multi-model
- Issue closing keywords: close, closes, closed, fix, fixes, fixed, resolve, resolves, resolved (+ `#N`)
- Common Actions triggers: `push`, `pull_request`, `issues`, `schedule`, `workflow_dispatch`, `release`
- Actions hierarchy: **event → workflow → job → step**, jobs run on **runners** (`runs-on: ubuntu-latest`)
- Review states: **Comment · Approve · Request changes** (never on your own PR)
- Merge strategies: **merge commit** (two-parent node, preserves history) · **squash** (one new combined commit) · **rebase** (linear replay, new SHAs)
- Discussion categories: Announcements, General, Ideas, Polls, Q&A, Show and tell
- Watch options: All activity · Participating and @mentions · Custom · Ignore
- PR tabs: Conversation · Commits · Checks · Files changed
- CODEOWNERS valid locations: root · `.github/` · `docs/`
- Community files: README, LICENSE, CONTRIBUTING, CODE_OF_CONDUCT, CODEOWNERS, SECURITY
- 2FA methods: TOTP app, SMS, security key, **passkey** (+ recovery codes!)
- Repo visibility: Public · Private (· Internal — orgs/enterprises only)

## One-liners
- Git = distributed version control tool (local). GitHub = hosting + collaboration platform around Git.
- `git fetch` downloads refs only; `git pull` = fetch + merge; `git status` never contacts the server.
- Fork = server-side linked copy (cross-account PRs). Clone = local copy. Branch = pointer inside one repo. Template = new repo, clean single-commit history, "generated from" label.
- Base branch receives; compare/head branch provides.
- Draft PR: can't merge until "Ready for review."
- github.dev: `.` key, free, no terminal/compute. Codespace: cloud VM, terminal, devcontainer (`.devcontainer/devcontainer.json`), Ubuntu default, billed while active.
- Dependabot alerts + dependency graph: free everywhere. Secret/code scanning: free public only, GHAS for private.
- Saved replies: personal account scope, `Ctrl+.` in a comment box.
- Secret gist ≠ private (URL access); public gist can never become secret; gists are clonable/forkable Git repos.
- Profile README: public repo named exactly your username.
- Search: `mentions:USER` · `review-requested:USER` · notification filter `reason:mention`.
- Keyboard: `t` = file finder · `.` = github.dev · `/` = slash commands in issue/PR/discussion bodies.
- Projects (new): table/board/roadmap layouts, custom fields, auto-workflows, insights, two-way issue sync.
- EMU = Enterprise Managed Users — identities provisioned/controlled via the company IdP.
- InnerSource = open-source working practices applied to an org's internal/private repos.
- Marketplace = actions + apps. Sponsors = funding maintainers/projects.
- GitHub Desktop = GUI Git client (clone, commit, push, PR); GitHub Mobile = triage on the go (notifications, issues, PR review) — neither replaces the full web feature set.
- GitHub Flow: branch → commit → open PR (early is fine/draft) → review → merge → delete branch → deploy from main.
