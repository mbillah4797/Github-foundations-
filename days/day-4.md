# Day 4 — Security, Administration & the GitHub Community (Domains 6 & 7, ~15–25% combined)

Lock the repo down like an admin, watch Git push get rejected by a ruleset, trip a Dependabot alert on purpose — then do the classic open-source fork dance and ship a live website.

## Mission 4.1 — Account security: 2FA (+ passkeys) (~10 min)

1. Settings → **Password and authentication** → Enable two-factor authentication → **Set up using an app** (TOTP) → scan QR → confirm code.
2. **Download the recovery codes** (that's the exam-tested fallback).
3. Look at the **passkey** option on the same page — passkeys are explicitly in the Jan-2026 objectives.

**Claude verifies:** you confirm in chat (Claude can't see your security settings — correctly so!).

## Mission 4.2 — Ruleset + CODEOWNERS: watch a push get rejected (~20 min)

1. Settings → **Rules → Rulesets → New branch ruleset**: name `protect-main`, Enforcement **Active**, target **Include default branch**.
2. Rules: check **Require a pull request before merging** (required approvals **0** — you can't approve your own PR, itself an exam fact), keep **Restrict deletions** and **Block force pushes** on. Save.
3. Try to defeat it locally on `main`:
   ```bash
   echo test >> README.md && git commit -am "direct push test" && git push
   ```
   → **rejected** with a `GH013: repository rule violations` error. Read it, then undo: `git reset --hard origin/main`.
4. Do it right: branch `chore/ruleset-test` → push → PR → notice CODEOWNERS auto-involves you as owner → merge. Change reaches `main` only via PR.
5. Drill: repo permission ladder **Read < Triage < Write < Maintain < Admin**; org roles/teams; **EMU** = enterprise identities managed via the company IdP; org-wide Copilot policies live at org level.

**Claude verifies:** ruleset active; the sanctioned PR merged; quiz on the ladder.

## Mission 4.3 — Security tab: Dependabot alert on purpose (~20 min)

1. Security tab → **Set up a security policy** → commit `SECURITY.md`.
2. Settings → **Advanced Security / Code security**: enable **Dependabot alerts**, **Dependabot security updates**, **secret scanning push protection** (free on public repos).
3. Plant a known-vulnerable pin — add `package.json`:
   ```json
   {"name":"seclab","version":"1.0.0","dependencies":{"lodash":"4.17.19"}}
   ```
   (plus a lockfile if you have npm locally: `npm install`, commit both).
4. Watch **Security → Dependabot alerts** light up; if security updates are on, Dependabot opens a version-bump PR — review and merge it.
5. Matrix drill: Dependabot alerts + dependency graph = free everywhere; secret/code scanning = free **public** only, **GHAS** needed for private.

**Claude verifies:** SECURITY.md present; Dependabot alert and/or bump PR visible.

## Mission 4.4 — Visibility & collaborators (~10 min)

1. Create throwaway **private** repo `visibility-lab` (note options: Public/Private — **Internal** exists only in orgs/enterprises).
2. Settings → Danger Zone → **Change visibility** → Public. Read the warning carefully.
3. Settings → **Collaborators → Add people** → invite someone (invitation sits **Pending** — that's enough).
4. Clean up: cancel invite, **delete** the repo (type-the-name confirmation).

**Claude verifies:** you narrate; Claude checks the repo appeared/disappeared.

## Mission 4.5 — The open-source fork dance (~20 min)

1. Fork **github.com/octocat/Spoon-Knife** (GitHub's official practice repo) — note the "forked from" label.
2. ```bash
   git clone https://github.com/mbillah4797/Spoon-Knife.git && cd Spoon-Knife
   git remote add upstream https://github.com/octocat/Spoon-Knife.git
   git remote -v   # origin = YOUR fork, upstream = the source
   ```
3. Branch `add-my-line`, append a line to `index.html`, commit, `git push -u origin add-my-line`.
4. **Compare & pull request**: the form shows base repository `octocat/Spoon-Knife` ← head repository `mbillah4797/Spoon-Knife` — a **cross-fork PR**. Create it (Spoon-Knife exists for exactly this; it just stays open).
5. Note the **Sync fork** button on your fork; run `git fetch upstream` once.

**Claude verifies:** fork exists, cross-fork PR open under your account.

## Mission 4.6 — Gist, Wiki, and a live Pages site (~25 min)

1. **Gist:** [gist.github.com](https://gist.github.com) → public gist `git-cheatsheet.md`. Edit it (adds a **revision**), check the Revisions tab. Clone it (`git clone https://gist.github.com/<id>.git`) — gists ARE git repos. Facts: public → secret is impossible; secret ≠ private.
2. **Wiki:** repo Settings → Features → Wikis on → create Home + a `Study-Notes` page linked with `[[Study-Notes]]`. Wiki visibility follows the repo.
3. **Pages:** add `docs/index.md` (any Markdown) + `docs/_config.yml` containing `theme: jekyll-theme-cayman`. Settings → **Pages** → Deploy from a branch → `main` / `/docs` → Save. Watch the `pages-build-deployment` run in Actions, then visit **https://mbillah4797.github.io/Github-foundations-/**.

**Claude verifies:** gist public + revisions; wiki pages; Pages site returns 200.

## Mission 4.7 — Community surfaces + templates (~15 min)

1. **Follow** a user and an org (e.g. `github`); browse github.com/trending; add a star to a **stars List** named `learning`.
2. Add `.github/ISSUE_TEMPLATE/bug_report.yml` — an issue **form** (structured YAML, auto-applies `labels: [bug]`, required textarea "Steps to reproduce"). Contrast with Markdown issue **templates**.
3. Add `.github/pull_request_template.md` with a checklist. Open any new issue/PR → chooser + prefill appear (templates apply at creation time).
4. Skim github.com/marketplace and github.com/sponsors; write one wiki sentence on **InnerSource** (open-source practices inside org/private repos).

**Claude verifies:** templates exist and fire; stars list; drill quiz on Marketplace/Sponsors/InnerSource.
