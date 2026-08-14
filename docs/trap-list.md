# The Trap List — 15 topics test-takers most often miss

Compiled from writeups by people who took the exam (2024–2026). Each entry: the trap, then the fact that defuses it. These get drilled hands-on during the week and rapid-fire quizzed on Day 5.

## 1. Plan tiers: Free vs Pro vs Team vs Enterprise
**Trap:** plausible distractors about which plan includes what.
**Facts:** *Free* is the only plan existing for BOTH personal and organization accounts. **Pro is personal-only**; organization plans are Free / Team / Enterprise. GitHub Free includes unlimited public AND private repos, unlimited collaborators, 2,000 Actions minutes/month, 500 MB Packages storage. Free is generous — know what actually requires paying.

## 2. Saved replies scope
**Trap:** answer choice claims saved replies are set at the org or enterprise level for all users.
**Fact:** saved replies belong to your **personal user account**, reusable by you across all issues/PRs.

## 3. Gist visibility
**Trap:** "convert your public gist to secret."
**Facts:** a public gist can **never** become secret (one-way). Secret gists are **not private** — anyone with the URL can view. Gists are full Git repos: clonable and forkable.

## 4. Fork vs branch vs new repo (scenario questions)
**Fact pattern:** same-team, same-repo work → **branch**. Outside contributor without write access, or diverging community variant → **fork**. Unrelated project → new repo. Forks are server-side copies linked to upstream; clones are local copies; branches live inside one repo.

## 5. Commit-graph reading
**Trap:** shown a commit DAG, pick the command sequence that produced it.
**Facts:** merge creates a two-parent commit; rebase replays commits linearly with **new SHAs**; reset moves the branch pointer. Also: tracked vs untracked file states; ~50-character commit subject-line convention.

## 6. Actions trigger events
**Trap:** surprisingly detailed memorization of workflow triggers.
**Facts:** know at minimum `push`, `pull_request`, `issues`, `schedule` (cron), `workflow_dispatch` (manual), `release`. Events → workflows → jobs → steps; jobs run on runners.

## 7. github.dev vs Codespaces
**Facts:** github.dev = free web editor, opened with the **`.` key** (or swapping the URL), **no terminal, no compute** — edit and commit only. Codespaces = cloud VM with terminal, runs code, configurable via **dev containers**, default image is Ubuntu Linux, personal accounts get a free monthly quota, billed for compute while active, auto-stops when idle.

## 8. Copilot tiers and what Copilot is NOT
**Facts:** Free/Pro for individuals; **Business/Enterprise** are managed by an org/enterprise (policy management, IP indemnity). Jan-2026 guide adds Copilot **agents, Agent Mode, multi-model support**. Trap pairing: vulnerability/dependency alerts are **Dependabot / code scanning**, not Copilot.

## 9. Security features: free vs paid (GHAS)
**Facts:** **Dependabot alerts + dependency graph: free on ALL repos.** Secret scanning and code scanning: free on **public** repos; require **GitHub Advanced Security** on private repos. Scenario questions ask which feature/plan combo satisfies a requirement.

## 10. Repository roles and org roles
**Facts:** the ladder is **Read < Triage < Write < Maintain < Admin**. Triage: manage issues/PRs but no code writes. Maintain: most settings but not destructive ones. Common traps live between Triage/Write and Maintain/Admin. Org moderators: hide comments, interaction limits, block users.

## 11. PR mechanics: base vs compare, CODEOWNERS
**Facts:** the **base** branch RECEIVES the changes; the **compare (head)** branch HAS your commits. CODEOWNERS auto-requests reviews; valid locations: repo root, `.github/`, or `docs/`. **You cannot approve your own PR.** Draft PRs cannot be merged until marked ready.

## 12. Search & notification qualifiers
**Facts:** `mentions:USERNAME` (issues mentioning someone), `review-requested:USERNAME` (PRs awaiting review), `reason:mention` (notification inbox filter), `is:issue is:open`, `label:"bug"`, `milestone:v1.0`. Watch options: All activity / Participating and @mentions / Custom / Ignore.

## 13. Projects (new) vs Projects Classic
**Facts:** new Projects = table + board + roadmap **layouts**, custom fields, built-in workflow automations (e.g., item closed → Done), insights/charts, two-way sync with issues/PRs. Classic lacks these.

## 14. Discussions vs Issues
**Facts:** Discussions = open-ended Q&A, announcements, polls, ideas — with categories and **mark-as-answer**. Issues = actionable, trackable work. A discussion **can be converted to an issue**. Issue closing keywords: `close/closes/closed`, `fix/fixes/fixed`, `resolve/resolves/resolved` + `#N` in a PR description or commit message on the default branch.

## 15. Profile README
**Fact:** works only from a **public** repo named **exactly your username** containing a README.md.

## Bonus traps
- `git fetch` downloads only; `git pull` = fetch + merge. `git status` never contacts the server.
- Issue **forms** (structured YAML in `.github/ISSUE_TEMPLATE/`) vs issue **templates** (prefilled Markdown). Templates apply at creation time.
- Fine-grained PATs can be scoped to a repo/org; GitHub Apps = fine-grained permissions vs OAuth apps acting as a full user.
- Wiki visibility follows the repo; editing can be restricted to collaborators.
- Marketplace sells/lists **actions AND apps**. Sponsors funds maintainers. InnerSource = open-source practices applied inside an org's private repos.
