# Day 3 — Modern Development & Project Management (Domains 4 & 5, ~15–25% combined)

Actions, Copilot, Codespaces, github.dev — then Projects, milestones, labels, and saved replies.

## Mission 3.1 — First GitHub Actions workflow (~15 min)

1. On `main`, **Add file** → `.github/workflows/hello.yml`:

```yaml
name: hello
on:
  push:
  workflow_dispatch:
jobs:
  hello:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: echo "Hello from $GITHUB_REPOSITORY"
```

2. Committing to `main` fires the **`push` event** immediately. Open the **Actions tab** → click the run → expand the job → read each step's log.
3. Trigger manually: Actions → hello → **Run workflow** (that's **`workflow_dispatch`**).
4. Vocabulary while you look at it: **event → workflow → job → step**, running on a **runner** (`ubuntu-latest`). Other common events: `pull_request`, `schedule` (cron), `issues`, `release`.
5. Notice the green check on the commit in the Commits list.

**Claude verifies:** two successful runs — one `push`, one `workflow_dispatch`.

## Mission 3.2 — Marketplace action + status badge (~10 min)

1. Browse [github.com/marketplace?type=actions](https://github.com/marketplace?type=actions) → open `actions/setup-node` (note versioning + docs — Marketplace hosts **actions and apps**).
2. Add to your workflow's steps:

```yaml
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: node --version
```

3. Commit; confirm the run log prints the Node version.
4. Actions → hello → **⋯ → Create status badge** → paste the Markdown at the top of README.md. Reload: badge says **passing**.

**Claude verifies:** badge in README + run log shows the node version.

## Mission 3.3 — github.dev vs Codespaces + devcontainer (~25 min)

1. On the repo press **`.`** → **github.dev** loads (free, instant). Edit a file, commit via the Source Control panel. Try to open a terminal — **there isn't one**. github.dev = editor only, no compute.
2. Now **Code (green button) → Codespaces → Create codespace on main** → a cloud VM with a real terminal. Run `ls`, `node --version`; commit and push FROM the terminal.
3. Command Palette → **"Codespaces: Add Dev Container Configuration Files"** → pick Node.js → Rebuild. Commit the `.devcontainer/devcontainer.json`.
4. Lifecycle walk: [github.com/codespaces](https://github.com/codespaces) → **Stop** your codespace (disk kept, no compute billing) → **Delete**. Facts: auto-stop on idle; billed for compute only while active; default image is Ubuntu; personal accounts get a free monthly quota.

**Claude verifies:** one commit authored via github.dev, one pushed from a codespace, `.devcontainer/devcontainer.json` on main.

## Mission 3.4 — Copilot hands-on + tier drill (~15 min)

1. [github.com/settings/copilot](https://github.com/settings/copilot) → enable **Copilot Free** (or your existing plan).
2. In a codespace or VS Code: create `fizzbuzz.js`, type a comment `// return fizzbuzz output for 1..n`, accept the ghost-text with Tab. Ask Copilot Chat to explain the code. Commit and push.
3. Tier drill (chat quiz): **Free/Pro = individuals**; **Business/Enterprise = org-managed** (policy controls, IP indemnity, org-wide enablement); Jan-2026 additions: **Copilot agents, Agent Mode, multi-model support**. Trap: dependency/vulnerability alerts are Dependabot's job, not Copilot's.

**Claude verifies:** the Copilot-assisted commit exists.

## Mission 3.5 — GitHub Project end-to-end (~20 min)

1. Profile → **Projects → New project** → Board template → name it `Foundations Tracker`.
2. **+ Add item → Add item from repository** → pull in this repo's open issues.
3. Flip the view between **Board / Table** (note **Roadmap** exists) — layouts are per-view.
4. Add a **custom field**: New field → Single select `Priority` (P1/P2/P3); set values; **group by Priority**.
5. **⋯ → Workflows**: confirm **"Item closed → Status: Done"** is on.
6. Close a tracked issue in the repo → reopen the project → its card moved to **Done** by itself.
7. Open the project's **Insights** (chart icon) — that's "project insights" on the exam.

Also create a **milestone** (`v1.0`, due before exam day) and attach 2 open issues; filter issues with `milestone:v1.0` and `label:bug`.

**Claude verifies:** issues linked to the project, milestone with progress bar, filters return correctly.

## Mission 3.6 — Saved replies (~5 min)

1. [github.com/settings/replies](https://github.com/settings/replies) → add "Triage ack": *"Thanks for the report! Triaged and added to the backlog."*
2. On any issue: comment box → saved-reply icon (or **Ctrl+.**) → insert, edit before posting, post.
3. Exam trap: saved replies are **personal-account** scoped — never org/enterprise allocated.

**Claude verifies:** the comment matching your saved reply text.
