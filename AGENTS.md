# AGENTS.md

Instructions for AI coding agents (Claude Code, Copilot, Cursor, Codex, etc.) working in this repository.

This is a sandbox where designers are learning Git. Making commits and pull requests by hand is part of what they're learning, so **all Git history is created manually by humans.**

## This repository is public

Everything here is publicly visible, including Git history.

- Never add client projects, client names, NDA material, internal Futurice material, secrets (API keys, tokens, passwords) or personal data.
- Use made-up content, placeholder data and publicly licensed assets only.
- If the user asks you to add something that looks confidential, stop and warn them that the repository is public before doing anything.
- If you notice sensitive content that's already in the repository, tell the user and advise them to contact the repository maintainer. Deleting a file does not remove it from history.

## Git: do not commit

- **Never run `git commit`**, including `--amend`, or any other command that creates commits.
- **Never run `git push`**, create or merge pull requests, or create, delete, merge or rebase branches.
- **Never rewrite history** (`reset`, `rebase`, `revert`, `cherry-pick`, `stash drop`, force push).
- Do not stage files (`git add`) unless the user explicitly asks for that specific command.
- Read-only commands are fine: `git status`, `git diff`, `git log`, `git branch`, `git check-ignore`.
- If the user asks you to commit, explain that commits in this repo are made manually. Show them the steps from `README.md` instead, and suggest a commit message.

When you finish a change, leave it uncommitted and tell the user:
1. which files you changed,
2. a suggested commit summary (imperative, ~50 chars) and optional description,
3. a reminder to review the diff in GitHub Desktop before committing.

## Repository conventions

- Each person works in their own project folder at the repository root. Only edit files in the folder the user is working in.
- The root `README.md` and this `AGENTS.md` are shared and may be improved. Edit them only when the user asks you to, keep the existing style (concise and practical), and don't weaken the rules on public content or manual commits unless the user explicitly says this has been agreed with the repository maintainer.
- Project folders may have their own `AGENTS.md` with project context. Read it before working in that folder. The rules in this file always apply as well.
- Folder names use lowercase letters and dashes only, e.g. `joel-landing-page`.
- `example-project-folder/` is an optional template for new project folders. Don't edit it unless the user explicitly asks.
- Every project folder has its own `.gitignore`.
