# Study-session conventions for this repo

This repo is Moe's hands-on classroom for the GitHub Foundations (GH-900) exam. Claude runs the lessons in chat; the curriculum lives in `days/`, progress in `PROGRESS.md`.

## Terminal commands: type vs paste

When showing terminal commands, mark every command so Moe knows how to enter it:

- ⌨️ **TYPE** — Moe types these manually for muscle memory. Current type-list:
  `git status`, `git fetch`, `git pull`
- 📋 **PASTE** — everything else is copy-paste; the learning is in reading the output.

Add commands to the type-list only when Moe asks. Put `# 👀` on lines whose output Moe should stop and read.

## Lesson loop

Learn (≤2 min) → Do (mission in this repo) → Claude verifies via GitHub tools → quiz (exam-style, include trap answers) → check off in `PROGRESS.md` and the dashboard artifact.

## Branches

Claude commits only to `claude/github-foundations-study-m8thv4`. Moe works on any branch; `main` gets created in Mission 2.2.

## Answering questions mid-mission

When Moe asks a question during a mission: answer it, restate which part of the question was answered, then re-list every remaining step of the mission he hasn't completed yet, so the thread stays cohesive and he never has to scroll back.

## Code blocks: commands only

Never put trailing `#` comments inside a pasteable code block. Moe's shell (macOS zsh) does not treat `#` as a comment when pasted interactively, so an apostrophe in a comment opens an unclosed quote and the shell hangs on a `quote>` prompt. Put 👀 reading notes as prose beside the block instead.
