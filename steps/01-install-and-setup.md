# Step 1: Install and set up

**Goal:** Have **Git** and **Visual Studio Code** installed, tell Git who you are, and connect VS Code to GitHub.

- **Git** tracks your changes.
- **VS Code** is the editor you'll drive Git from.

Jump to your system: [Windows](#windows) · [macOS](#macos). Already installed? Go to [Verify](#verify-your-install).

---

## Windows

### A. VS Code

1. Go to <https://code.visualstudio.com/download> and download the **Windows** installer.
2. Run it. On **Select Additional Tasks**, tick:
   - ✅ **Add "Open with Code" action to Windows Explorer file context menu**
   - ✅ **Add "Open with Code" action to Windows Explorer directory context menu**
   - ✅ **Add to PATH**
3. Click **Install**, then **Finish**.

### B. Git

1. Go to <https://git-scm.com/downloads>, click **Windows**, and download **64-bit Git for Windows Setup**.
2. Run it and click **Next** through the pages. Only change these:

   | Installer page | Choose |
   |---|---|
   | Choosing the default editor used by Git | **Use Visual Studio Code as Git's default editor** |
   | Adjusting the name of the initial branch | **Override the default branch name** → `main` |
   | Adjusting your PATH environment | **Git from the command line and also from 3rd-party software** |
   | Everything else | Leave the defaults |

3. Click **Install**, then **Finish**.

> **Shortcut:** in PowerShell run `winget install --id Git.Git -e` and `winget install --id Microsoft.VisualStudioCode -e`.

---

## macOS

### A. VS Code

1. Go to <https://code.visualstudio.com/download> and download **Mac Universal**.
2. Open the `.zip` and drag **Visual Studio Code** into **Applications**.
3. Open it from Applications. If macOS asks whether you're sure, click **Open**.

### B. Git

macOS often has Git already. Check first:

1. Open **Terminal** (**Cmd+Space**, type `Terminal`, press Enter).
2. Run:
   ```bash
   git --version
   ```
3. - A version number such as `git version 2.39.5` means you're done.
   - If a popup asks you to install **command line developer tools**, click **Install**, wait for it to finish, then run `git --version` again.

> **Alternative:** with Homebrew, run `brew install git`.

---

## Verify your install

Open VS Code, then open its terminal: **Terminal → New Terminal** (or **Ctrl+\`**).

```bash
git --version
```

You should see something like `git version 2.5x.x`. The exact number doesn't matter.

> **Windows:** if it says `git` is not recognized, close **all** VS Code windows and reopen it. The PATH is only picked up on a fresh start.

---

## Tell Git who you are

Every commit you make is stamped with your name and email. Set them once. In the VS Code terminal, replace the quoted text with your own:

```bash
git config --global user.name "your-name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

Check it:

```bash
git config --global --list
```

**Which email?** Use the one on your GitHub account so your commits link to your profile. If you'd rather keep it private, GitHub provides a private address: **GitHub → Settings → Emails → Keep my email addresses private**, then use the `...@users.noreply.github.com` address shown there.

> Remember this repo is public. Commits you make here show this name and email.

---

## Sign in to GitHub from VS Code

1. Click the **Accounts** icon (person silhouette) at the bottom of the left sidebar.
2. Choose **Sign in with GitHub**.
3. Your browser opens. Log in and click **Authorize**. If asked to open VS Code, click **Open**.
4. The Accounts icon now shows your username.

## Add the GitHub Pull Requests extension

1. Open **Extensions** (**Ctrl+Shift+X** / **Cmd+Shift+X**).
2. Search **GitHub Pull Requests** and install the one by **GitHub**.
3. A GitHub (cat) icon appears in the sidebar. You'll use it in Step 11.

---

## ✅ Checkpoint

- [ ] `git --version` prints a version in the VS Code terminal
- [ ] `git config --global --list` shows my name and email
- [ ] The Accounts icon shows my GitHub username
- [ ] The GitHub Pull Requests extension is installed

Next: [Step 2: The pizza analogy](02-the-pizza-analogy.md)
