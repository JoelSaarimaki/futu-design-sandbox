# futu-design-sandbox

Test repository for Futurice designers. A safe place to learn Git: make folders, commit things, break things. Nothing here is production.

> [!WARNING]
> **This repository is public.** Anyone on the internet can see everything in it, including the full history of past commits.
> **Never add:**
> - client projects, client names, or anything under NDA
> - internal Futurice material that isn't meant to be public
> - passwords, API keys, tokens or other secrets
> - personal data (names, emails, photos of real people without consent)
>
> Use made-up content, public assets and placeholder data only. Deleting a file later does **not** remove it from Git history. If something sensitive gets pushed, tell the repository maintainer right away, and revoke the key if it was a secret.

**Contents**
- [Setup](#setup): get access, clone the repo, create your project folder
- [Git guide](#git-guide): key concepts, branches, commits, pull requests, `.gitignore`, troubleshooting
- [VS Code and merge conflicts](#vs-code-and-merge-conflicts): Git in VS Code and resolving conflicts

---

## Setup

### 1. Get access

Send your GitHub username to the repository maintainer and ask to be added as a collaborator. Without access you can clone the repo but can't push your branches.
You'll get an invitation by email and on GitHub (bell icon → *Notifications*). **Accept it** before continuing.
(No GitHub account yet? Create one at [github.com/signup](https://github.com/signup) first.)

### 2. Install GitHub Desktop and clone the repo

1. Install **[GitHub Desktop](https://desktop.github.com/)** and sign in with your GitHub account
   (*File → Options → Accounts* on Windows, *GitHub Desktop → Settings → Accounts* on Mac).
2. Clone this repo: *File → Clone repository → URL* and paste
   `https://github.com/JoelSaarimaki/futu-design-sandbox`
   Choose where to save it on your computer and click **Clone**.
3. Open the folder: *Repository → Show in Explorer / Show in Finder*.

> Prefer the console? Same thing:
> ```bash
> git clone https://github.com/JoelSaarimaki/futu-design-sandbox.git
> cd futu-design-sandbox
> ```

### 3. Create your project folder

Everyone works inside **their own folder** at the root of the repo. Don't edit other people's folders.

**Naming rules:** lowercase letters and dashes only. No spaces, capitals, or special characters (å, ä, ö, etc.).

| ✅ Good                     | ❌ Bad                      |
| -------------------------- | -------------------------- |
| `joel-landing-page`        | `Joel Landing Page`        |
| `icon-experiments`         | `Icon_Experiments`         |
| `onboarding-flow-test`     | `onboarding flow (v2)`     |

Every project folder needs its **own `.gitignore`** file. See [What is `.gitignore`?](#what-is-gitignore)

You can start from scratch or copy [`example-project-folder/`](example-project-folder), a template for small AI-driven projects that already includes a `.gitignore`. Don't edit the example folder itself.

Then follow the [branch → commit → pull request](#branches-commits-and-pull-requests) workflow to get your folder onto GitHub.

### Rules of the sandbox

1. **The repository is public.** No client projects, confidential material, secrets or personal data, ever.
2. Work only inside **your own folder**. The root `README.md` and `AGENTS.md` are the exception (see below).
3. Folder names: **lowercase-with-dashes**.
4. Every folder has its **own `.gitignore`**.
5. **Never commit directly to `main`.** Use a branch and a pull request.
6. **Commit manually.** Review your changes yourself; AI tools don't commit (see [`AGENTS.md`](AGENTS.md)).

### Improving these instructions

The root `README.md` and `AGENTS.md` belong to everyone. If something is unclear, missing or wrong, improve it. Editing them is good practice for the Git workflow:

1. Create a branch, e.g. `joel/readme-clarify-gitignore`.
2. Edit `README.md` and/or `AGENTS.md`. Keep the text short and practical.
3. Commit with a clear message, e.g. `Clarify how to show hidden files on Mac`.
4. Open a pull request and ask someone to review it.

Changes to the rules (public repo, manual commits, branches and pull requests) should be agreed with the repository maintainer.

---

## Git guide

### Key concepts

- **Repository (repo):** a project folder whose history Git tracks. This sandbox is one.
- **Commit:** a saved snapshot of your changes, with a short message describing them.
- **Push:** upload your commits to GitHub so others can see them.
- **Pull:** download other people's commits to your computer.
- **Branch:** a parallel version of the project where you can work without affecting `main`.
- **Pull request (PR):** a request on GitHub to merge your branch into `main`, where others can review it first.
- **`.gitignore`:** a text file listing files Git should *not* track.

The everyday loop is: **Update `main` → create a branch → commit → push → open a pull request → merge.**

> **All commits are made manually by you.** If you use AI tools (Claude, Copilot, Cursor…), let them edit files, but review and commit the changes yourself. See [`AGENTS.md`](AGENTS.md).

### Branches, commits and pull requests

`main` is the shared version everyone sees. **Never commit directly to `main`.** Do your work on a branch and get it into `main` through a pull request. This is how most software teams work.

#### Create a branch

Always start from an up-to-date `main`.

**GitHub Desktop:**
1. *Current branch* (top bar) → select **main**.
2. Click **Fetch origin**, then **Pull origin** if it appears.
3. *Current branch* → **New branch**. Name it `your-name/short-description`, lowercase with dashes, e.g. `joel/landing-page-hero`.
4. Click **Create branch**. You're now working on it — check the *Current branch* label.

**Console:**
```bash
git switch main
git pull
git switch -c joel/landing-page-hero
```

One branch = one topic. Start a new branch for each new piece of work.

#### Make good commits

You make every commit yourself, after checking what's in it.

**Before committing**
- Look through every changed file in the *Changes* tab (console: `git status` and `git diff`).
- Untick anything unrelated, temporary or private. Commit only what belongs to this change.

**Keep commits small.** One logical change per commit, e.g. "add icons" and "fix button colors" go in two commits, not one. Small commits are easier to review and easier to undo.

**Write a clear message**
- **Summary:** short (about 50 characters), in the imperative mood, as if completing the sentence *"This commit will…"*: `Add hero section mockup`, `Fix button contrast on dark mode`.
- **Description (optional):** a blank line after the summary, then *why* you made the change and anything a reviewer should know.
- Avoid vague messages like `update`, `fix`, `stuff`, `wip`.

```
Add hero section mockup

First version of the landing page hero with headline,
CTA button and background illustration. Copy is placeholder.
```

**GitHub Desktop:** fill in *Summary* and *Description* at the bottom left → **Commit to joel/landing-page-hero**.

**Console:**
```bash
git status
git diff
git add joel-landing-page
git commit -m "Add hero section mockup" -m "First version of the landing page hero. Copy is placeholder."
```

**Push your branch** so it's backed up on GitHub. Click **Publish branch** the first time, then **Push origin** after later commits.

```bash
git push -u origin joel/landing-page-hero   # first time
git push                                    # after that
```

#### Open a pull request

1. In GitHub Desktop click **Create Pull Request** (or *Branch → Create Pull Request*). GitHub opens in your browser.
2. Check that the base is **main** and the compare branch is yours.
3. Write a **title** (like a good commit summary) and a **description**:
   ```markdown
   ## What
   Landing page hero section: headline, CTA and illustration.

   ## Why
   Testing layout options for the new landing page.

   ## How to review
   Open joel-landing-page/index.html in a browser.

   ## Screenshots
   (drag images here)
   ```
4. Add a colleague under **Reviewers** and click **Create pull request**.
5. **Handle feedback** by making more commits on the same branch and pushing them. The pull request updates automatically.
6. **Merge** once it's approved: click **Merge pull request** on GitHub, then **Delete branch**.
7. **Clean up locally:** in GitHub Desktop switch to **main** and **Pull origin**. Console:
   ```bash
   git switch main
   git pull
   git branch -d joel/landing-page-hero
   ```

### What is `.gitignore`?

A `.gitignore` is a plain text file that tells Git which files to **leave out**. Ignored files stay on your computer, but Git doesn't track them, they don't show up in GitHub Desktop's *Changes* list, and they never get pushed to GitHub.

**Why it matters:** projects produce files that don't belong in a shared, public repository:
- **Secrets** like `.env` files with API keys. Critical in a public repo.
- **Generated files** like exports, renders and build output, which can be recreated.
- **Large files** like `.psd` or video. Git is made for text and small files, and big files make the repo slow for everyone.
- **Personal clutter** like `.DS_Store`, editor settings and logs.

**Where it lives:** a `.gitignore` applies to the folder it's in and everything below it. In this repo each project folder has its **own** `.gitignore`, so you decide what's ignored in your project without affecting anyone else's.

#### How it works

One pattern per line. Lines starting with `#` are comments.

```gitignore
# OS junk
.DS_Store
Thumbs.db

# Secrets
.env

# Exports and big source files
exports/
*.psd
*.mp4
```

| Pattern          | Ignores                                              |
| ---------------- | ---------------------------------------------------- |
| `notes.txt`      | any file named `notes.txt` in this folder or below   |
| `*.psd`          | all `.psd` files                                     |
| `exports/`       | the whole `exports` folder                           |
| `/draft.png`     | only `draft.png` directly in this folder             |
| `!keep-this.psd` | exception: *do* track this file even if `*.psd` is ignored |

For a fuller example, see [`example-project-folder/.gitignore`](example-project-folder/.gitignore).

#### Things to know

- **It's a hidden file.** Names starting with a dot are hidden by default. Show them with `Cmd + Shift + .` in Finder (Mac), or *View → Show → Hidden items* in Explorer (Windows). Edit the file in any plain-text editor.
- **Creating one from scratch** is easiest in the console (GitHub Desktop: *Repository → Open in Command Prompt / Terminal*):
  ```bash
  touch joel-landing-page/.gitignore          # Mac / Git Bash
  ```
  ```powershell
  New-Item joel-landing-page/.gitignore       # Windows PowerShell
  ```
- **Git doesn't track empty folders.** A `.gitignore` is often the first file in a new folder, which also makes the folder show up in Git.
- **It only affects untracked files.** If a file was committed *before* you added it to `.gitignore`, Git keeps tracking it. Stop tracking it with the command below (the file stays on your disk), then commit:
  ```bash
  git rm --cached joel-landing-page/big-file.psd
  git rm -r --cached joel-landing-page/exports/   # a whole folder
  ```
- **Check why a file is or isn't ignored:**
  ```bash
  git check-ignore -v joel-landing-page/big-file.psd
  ```

### When something goes wrong

| Problem                                   | Fix                                                                 |
| ----------------------------------------- | ------------------------------------------------------------------- |
| Push fails with "permission denied" / 403 | You don't have collaborator access yet. Ask the repository maintainer to add you, then accept the invitation. |
| Push rejected / "newer commits on remote" | Click **Pull origin**, then **Push origin** again.                  |
| Committed to `main` by accident (not yet pushed) | *History* tab → right-click the commit → **Undo commit**. Create a new branch; GitHub Desktop offers to bring your changes along. Commit there. |
| Want to throw away uncommitted changes    | Right-click the file in *Changes* → **Discard changes**.            |
| Committed something by mistake (not yet pushed) | *History* tab → right-click the commit → **Undo commit**.     |
| Committed a huge file                     | Add it to your folder's `.gitignore`, then `git rm --cached <file>` and commit. |
| Merge conflict                            | See [Resolving merge conflicts](#resolving-merge-conflicts). |
| Totally stuck                             | Ask in the team channel — this is a sandbox, nothing is broken for good. |

Useful console commands for looking around:
```bash
git status          # what has changed?
git log --oneline   # recent commits
git diff            # exact line changes not yet committed
```

---

## VS Code and merge conflicts

**[Visual Studio Code](https://code.visualstudio.com/)** is a free code editor that's handy for editing text files like `README.md`, `AGENTS.md`, `.gitignore` and code prototypes. It also has Git built in.

### Git in VS Code

Open the whole repository with *File → Open Folder…*, or from GitHub Desktop with *Repository → Open in Visual Studio Code*.

- The **Source Control** view (branch icon in the left sidebar, or `Ctrl + Shift + G` / `Cmd + Shift + G`) lists changed files. Click a file to see what changed.
- The current branch is shown in the bottom-left corner. Click it to switch branches.
- You *can* commit, push and pull from VS Code too, but in this repo we recommend sticking to GitHub Desktop for that, so you have one place to review your commits.
- Optional: the **GitLens** extension shows who changed each line and when. Install it from the *Extensions* view (`Ctrl + Shift + X` / `Cmd + Shift + X`).

**Make VS Code your editor in GitHub Desktop:** *File → Options → Integrations* (Windows) or *GitHub Desktop → Settings → Integrations* (Mac) → *External editor* → **Visual Studio Code**. GitHub Desktop will then open files and conflicts directly in VS Code.

### Resolving merge conflicts

A **merge conflict** happens when two branches change the same lines of the same file, and Git can't decide which version to keep. It typically shows up when you pull `main` into your branch, or when a pull request can't be merged.

1. **GitHub Desktop** shows a dialog listing the conflicted files. Click **Open in Visual Studio Code** next to a file.
2. **In VS Code** the conflicting part is highlighted, with the two versions one after the other:
   ```
   <<<<<<< HEAD (Current Change)
   <h1>Welcome to the sandbox</h1>
   =======
   <h1>Hello, designers</h1>
   >>>>>>> main (Incoming Change)
   ```
   - **Current Change** is the version on the branch you're on.
   - **Incoming Change** is the version being merged in.
3. **Choose a version** with the links above the conflict:
   - **Accept Current Change:** keep yours
   - **Accept Incoming Change:** keep theirs
   - **Accept Both Changes:** keep both, one after the other
   - **Compare Changes:** view them side by side

   You can also edit the text by hand. Just make sure to remove all the `<<<<<<<`, `=======` and `>>>>>>>` marker lines.
   For bigger conflicts, click **Resolve in Merge Editor** (bottom right) for a three-panel view: yours, theirs, and the result.
4. **Save the file.** Repeat for every conflict in every listed file.
5. **Back in GitHub Desktop** the files are marked as resolved. Click **Continue merge** (or **Commit merge**), then push.

**Tips**
- Not sure which version is right? Ask the person who made the other change before choosing.
- If the conflict is in someone else's folder, let them resolve it.
- Want to start over? In GitHub Desktop click **Abort merge**. Nothing is lost, you're back where you were before the merge.
- Conflicts are rarer when you keep branches short-lived and pull `main` often.
