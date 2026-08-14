# Day 1 — Git & GitHub Basics (Domain 1, 25–30%)

The biggest domain on the exam gets the first full day. Also today: **book the exam** — Pearson VUE slots and the OnVUE pre-check take lead time.

## Mission 0 — Book the exam (15 min, do it first)

Follow [docs/exam-facts.md → Registration](../docs/exam-facts.md). Key gotchas: personal Microsoft account, name exactly matching your government ID, run the OnVUE system pre-check today if testing from home.

---

## Mission 1.1 — GitHub Flow, entirely on the web (~15 min)

*Covers: GitHub Flow, branching, Markdown, PR anatomy, base vs compare, merge commits.*

1. Open this repo on github.com. Use the **branch dropdown** (top-left of the file list) → type `day1/markdown-practice` → "Create branch … from …".
2. On that branch: **Add file → Create new file** → path `notes/markdown-cheatsheet.md`. Write it in Markdown using ALL of: an H1 and an H2, a bulleted list, a task list (`- [x]` / `- [ ]`), a link, a fenced code block with a language tag, a table, and an emoji shortcode like `:rocket:`. Use the **Preview** tab to check rendering. Commit to your branch.
3. Open **Pull requests → New pull request**. Read the selector carefully: **base** = the branch that RECEIVES your change; **compare** = the branch with your commits. Create the PR with a short description.
4. Tour the four PR tabs — **Conversation, Commits, Checks, Files changed** — and note what each shows.
5. **Merge pull request** using the default **"Create a merge commit"**, then click **Delete branch**.

**Claude verifies:** merged PR exists; file is on the default branch with all Markdown elements; branch deleted; merge commit visible.

## Mission 1.2 — Local round-trip: clone, commit, push (~15 min)

*Covers: Git vs GitHub, distributed version control, remotes, staging.*

```bash
git clone https://github.com/mbillah4797/Github-foundations-.git
cd Github-foundations-
git remote -v            # "origin" = alias for the GitHub URL
git log --oneline -5     # full history came with the clone (distributed VCS!)
git switch -c day1/local-notes
echo "Commits I made locally on $(date)" > notes/local-log.md
git status               # untracked file (red)
git add notes/local-log.md
git status               # staged (green) — the three states: modified → staged → committed
git commit -m "Add local notes from Day 1"
git push -u origin day1/local-notes   # -u sets upstream tracking
```

Then on github.com: open a PR from `day1/local-notes` and merge it (any strategy).

**Claude verifies:** the branch and merged PR exist; commit SHA on GitHub matches your local `git log`.

## Mission 1.3 — fetch vs pull lab (~10 min)

*Covers: the most-tested Git command distinction.*

1. On github.com, edit `notes/local-log.md` directly on the default branch — add a line, commit via web UI.
2. Locally (on the default branch): `git status` → still says "up to date"! **`git status` never contacts the server.**
3. `git fetch origin` → now `git status` says "behind by 1 commit."
4. Prove fetch didn't touch your files: `cat notes/local-log.md` (no new line yet), but `git log HEAD..origin/HEAD --oneline` shows the web commit.
5. `git merge` → file updated. That two-step is exactly what `git pull` does in one command.
6. Make a second web edit, then run `git pull` and confirm one command did both.

**Claude verifies:** you paste the `git status` output from steps 2 and 3 in chat.

## Mission 1.4 — Read the commit graph: merge vs rebase (~15 min)

*Covers: commit-DAG questions ("which commands produced this history?").*

```bash
git switch -c day1/graph-a && echo a > graph.txt && git add . && git commit -m "A1"
git switch - && git switch -c day1/graph-b && echo b > graph2.txt && git add . && git commit -m "B1"
git switch day1/graph-a && git merge day1/graph-b     # two-parent merge commit
git log --graph --oneline --all -10                   # see the diamond
git switch day1/graph-b && git rebase day1/graph-a    # replay B1 onto A — NEW SHA
git log --graph --oneline --all -10                   # now linear
git switch <default-branch> && git branch -D day1/graph-a day1/graph-b   # throwaway, no push
```

Watch B1's SHA change after the rebase — **rebase rewrites commits**.

**Claude verifies:** paste both `git log --graph` outputs; quiz on reading them.

## Mission 1.5 — Slash commands + an issue (~5 min)

1. Open **Issues → New issue**, title "Day 1 field notes."
2. In the body type `/` and use the **/table** and **/code** slash commands; also use the formatting toolbar. Submit.

**Claude verifies:** issue exists with a table and code block.

## Mission 1.6 — Concept quiz in chat

No hands-on — Claude quizzes: Git vs GitHub, why version control, personal vs organization vs enterprise accounts, when GitHub Desktop / GitHub Mobile fit, GitHub Flow order of operations.

## Bonus (if energy remains) — Profile README

Create a public repo named exactly `mbillah4797` with a README.md → it renders on your profile. Small exam fact, nice permanent artifact.
