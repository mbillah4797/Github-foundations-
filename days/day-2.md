# Day 2 — Repositories & Collaboration (Domains 2 & 3, ~20–30% combined)

Today the repo grows community files and you drive the full collaboration toolkit: issues, PR review mechanics, all three merge strategies, discussions, and notifications.

## Mission 2.1 — Community standards sweep (~20 min)

*Covers: README, LICENSE, CONTRIBUTING, CODE_OF_CONDUCT, CODEOWNERS structure questions.*

1. **Add file → Create new file** → type `LICENSE` as the filename → GitHub offers **"Choose a license template"** → pick MIT. Commit.
2. Add `CONTRIBUTING.md` (2–3 lines on how to contribute) and `CODE_OF_CONDUCT.md` (Insights → Community Standards → "Add" proposes the Contributor Covenant for you).
3. Add `.github/CODEOWNERS` containing exactly: `* @mbillah4797` (valid CODEOWNERS locations: root, `.github/`, `docs/` — exam fact).
4. Open **Insights → Community Standards** and watch the checklist go green. Also tour **Insights → Contributors / Traffic**.

**Claude verifies:** all files present; community checklist state.

## Mission 2.2 — Give this repo a `main` (repo administration) (~5 min)

This repo's default branch is still the study branch (first branch ever pushed). Fix that like an admin:

1. Branch dropdown → type `main` → create from the current default branch.
2. **Settings → General → Default branch** → switch (⇄) to `main`.

From now on, `main` is the trunk. (Exam angle: default branch is a repo setting; new clones and PRs target it.)

**Claude verifies:** default branch is `main`.

## Mission 2.3 — Template repo vs fork (~15 min)

1. **Settings → General** → check **Template repository** on this repo.
2. Repo home → green **Use this template → Create a new repository** → name it `from-template-lab`.
3. `git clone` it and run `git log --oneline`: **one fresh initial commit** — templates copy content, not history, and show "generated from …".
4. Contrast with a fork (you'll fork Spoon-Knife on Day 4): forks keep FULL upstream history and a "forked from" link for cross-repo PRs.
5. Delete `from-template-lab` afterward if you like (Settings → Danger Zone) — deleting a repo is also exam-relevant admin.

**Claude verifies:** template flag on; you paste the `git log` output from the template copy.

## Mission 2.4 — Issue lifecycle with auto-close (~15 min)

1. New issue: "Fix typo in README" → sidebar: add the `bug` label, assign yourself, then **⋯ → Pin issue**.
2. In the issue's **Development** sidebar → **Create a branch** (accept suggested name) → check out locally.
3. Fix any small thing in README.md, commit, push.
4. Open the PR; in the description write exactly `Closes #<issue-number>`. Confirm the issue appears under Development.
5. Merge → the issue closes itself ("closed as completed" via the PR).

Valid keywords: close/closes/closed, fix/fixes/fixed, resolve/resolves/resolved.

**Claude verifies:** issue auto-closed by the merged PR, labeled, assigned, pinned.

## Mission 2.5 — Merge strategy triathlon (~25 min)

*The single highest-yield Git exercise for this exam.*

1. Settings → General → Pull Requests: ensure merge commits, squash, AND rebase are all allowed.
2. **Branch 1** `demo/merge`: 2 commits touching `merge.txt` → PR → **Create a merge commit**.
3. **Branch 2** `demo/squash`: **3 commits** touching `squash.txt` → PR → **Squash and merge** (3 become 1).
4. **Branch 3** `demo/rebase`: 2 commits touching `rebase.txt` — record their SHAs (`git log --oneline -2`) → PR → **Rebase and merge**.
5. Inspect: `git switch main && git pull && git log --graph --oneline -15`. Confirm:
   - a two-parent "Merge pull request" commit (strategy 1),
   - ONE combined commit whose original 3 SHAs are gone (strategy 2),
   - 2 linear commits with **new SHAs** vs what you recorded (strategy 3 — rebase rewrites).

**Claude verifies:** reads the commit graph on GitHub and checks all three signatures.

## Mission 2.6 — Draft PR, review states, suggested changes (~15 min)

1. Branch `demo/review`, tweak a README line, push, and choose **Create draft pull request** (dropdown next to the green button). Note: merge button disabled — drafts can't merge.
2. Click **Ready for review** — the timeline records it.
3. Files changed → click a line's `+` → use the **±** "Add a suggestion" button → Start a review → Finish review. Note the three states — **Comment / Approve / Request changes** — and that Approve is disabled on your OWN PR (exam fact).
4. In Conversation, **Commit suggestion**, then merge.

**Claude verifies:** timeline shows draft→ready, a review with a suggestion, and the suggestion commit.

## Mission 2.7 — Discussions + notifications (~15 min)

1. Settings → General → Features → enable **Discussions**.
2. Note default categories (Announcements, General, Ideas, Polls, Q&A, Show and tell). Create a **Q&A**: "Which merge strategy should teams default to?" — answer it yourself → **Mark as answer** (green badge). Create a **Poll** and vote.
3. On a discussion: sidebar → **Convert to issue**; on another → **⋯ → Pin discussion**.
4. Set the repo's **Watch** button to **Custom** (Issues only) and read all the options.
5. Visit github.com/notifications → filter with `reason:mention`, `is:issue`; save a custom filter for this repo.

**Claude verifies:** answered Q&A badge, converted issue, pinned discussion exist.

## Mission 2.8 — Micro-drills (~5 min)

- Press `t` in the repo (file finder) and `.` (github.dev opens — close it, that's Day 3 material).
- Star a repo (e.g. `github/docs`) and check your stars tab.
- Avatar menu → **Feature preview** → toggle something on/off.
