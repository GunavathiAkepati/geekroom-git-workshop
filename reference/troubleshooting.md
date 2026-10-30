# Troubleshooting

Find your problem and try the fix. Still stuck? Ask the person next to you or someone in the room.

---

## `git` is not recognized

**Windows:** `'git' is not recognized as an internal or external command`

1. Close **all** VS Code windows and reopen. The PATH only updates on a fresh start.
2. Still failing? Restart your computer.
3. Still failing? Re-run the Git installer and, on the PATH page, choose **Git from the command line and also from 3rd-party software**.

**macOS:** a popup asks to install command line tools. Click **Install**, wait, and try again.

---

## "Author identity unknown" / "Please tell me who you are"

You skipped the name/email setup. Run, with your own details:

```bash
git config --global user.name "your-name"
git config --global user.email "you@example.com"
```

Then retry the commit.

---

## My branch is called `master` instead of `main`

```bash
git config --global init.defaultBranch main
```

For a repo you already made, rename it: Command Palette → `Git: Rename Branch...` → `main` (terminal: `git branch -M main`).

---

## I ran `git init` inside another repository

If Source Control lists files you didn't expect, you've nested one repo inside another. Delete the inner folder and recreate it somewhere that isn't already a repo.

---

## My new folder doesn't show up in Source Control

Git doesn't track **empty** folders. Put a file in it.

---

## I committed a password / API key

1. Treat it as **compromised**: change or revoke it right away at the service that issued it.
2. Add the file to `.gitignore` and use `git rm --cached <file>` so it stops being tracked.
3. Note that deleting it in a new commit doesn't remove it from history. That's why step 1 matters.

---

## Clone fails or keeps asking for a password

- GitHub doesn't accept account passwords for Git. Use the **browser sign-in** VS Code opens, or sign in with the **Accounts** icon (Step 1).
- Use the **HTTPS** URL, not SSH.
- Make sure the URL has **your own username** in it when you're cloning your fork.

---

## I can't find the Fork button

You must be logged in to GitHub, and you must be on the **original** repo's page (`Sw4ppleneel/geekroom-git-workshop`), not on your own fork. Forking a repo you already forked takes you to your existing fork.

---

## Push is rejected: "Permission denied" / 403

You're probably pushing to the **original** repo instead of **your fork**. Check:

```bash
git remote -v
```

`origin` must point at **your** username. If it points at `Sw4ppleneel`, fix it:

```bash
git remote set-url origin https://github.com/<your-username>/geekroom-git-workshop.git
```

---

## Push is rejected: "non-fast-forward" / "updates were rejected"

The branch on GitHub has commits you don't have yet (you're *behind*). Click **Sync Changes** (pull, then push). If a conflict appears, see [Step 7](../steps/07-merge-conflicts.md).

---

## Push is rejected for my practice repo: "unrelated histories" / "fetch first"

You ticked **Add a README** (or a license, or `.gitignore`) when creating the repo on GitHub, so it already has a commit your local repo lacks. Easiest fix: delete the GitHub repo, create it again **empty**, and push.

---

## `git remote add origin` says "remote origin already exists"

Check with `git remote -v`. To point it at the right URL: `git remote set-url origin <url>`.

---

## I can't switch branches

VS Code says you have uncommitted changes that would be overwritten.

- Commit them (Step 4), **or**
- Palette → `Git: Stash` to set them aside, switch, and `Git: Pop Stash` later.

---

## I committed on `main` by mistake

If you **haven't pushed**:

1. Palette → `Git: Create Branch...` and make a new branch. Your commit comes with you.
2. Your `main` still has the commit. The simplest clean-up is to re-clone into a fresh folder.

If you **have pushed** to your fork's `main`, it's fine. It's your fork. Just make a branch from now on.

---

## I don't see the "Create Pull Request" button

- Is the **GitHub Pull Requests** extension installed and are you signed in? (Step 1)
- Did you **publish** the branch first?
- Fall back: open your fork on github.com and click **Compare & pull request**.

---

## My PR shows lots of files I didn't change

You probably branched from an old `main`, or edited something extra. Check **Files changed**, undo the extra changes on your branch (`Git: Discard Changes` for uncommitted ones), commit and push. The PR updates itself.

---

## The PR says "This branch has conflicts"

Expected in [Step 12](../steps/12-conflict-in-a-real-pr.md). Follow the resolution steps there (fetch `upstream`, merge `upstream/main`, resolve, commit, push).

---

## I resolved the conflict but the file still shows `<<<<<<<`

Delete **all three** marker lines (`<<<<<<<`, `=======`, `>>>>>>>`), save, **stage** the file, then commit. Search the file for `<<<<` to be sure none remain.

---

## I'm stuck in a half-merged state

Palette → `Git: Abort Merge` (terminal: `git merge --abort`). Your branch returns to how it was before the merge. Then try again.

---

## VS Code says I'm up to date but GitHub has newer commits

Your computer only learns about GitHub changes when you fetch. Palette → `Git: Fetch`, then look at the ↓ number in the status bar.

---

## The terminal is PowerShell / zsh / Git Bash. Does it matter?

No. All the `git` commands in this guide work in PowerShell, Command Prompt, Git Bash, zsh and bash.

---

## Nothing works

Re-clone into a **new, empty folder** and carry on from your current step. Anything you've already pushed to GitHub is still there.
