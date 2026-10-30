# Cheat sheet

Everything can be done with buttons in VS Code. Terminal commands are shown so you learn both.

## The loop 🍕

```
edit files → stage (add toppings) → commit (bake) → push (serve to the table)
```

## Contributing to someone else's repo

```
fork → clone your fork → add upstream → branch → edit → commit → push → pull request → sync fork
```

## Actions

| I want to... | In VS Code | Terminal |
|---|---|---|
| Open Command Palette | **Ctrl+Shift+P** / **Cmd+Shift+P** | |
| Open Source Control | **Ctrl+Shift+G** | |
| Open terminal | **Ctrl+\`** | |
| Make a folder | Explorer → New Folder | `mkdir <name>` |
| Start a repo | Source Control → **Initialize Repository** | `git init` |
| Clone a repo | Palette → `Git: Clone` | `git clone <url>` |
| See what changed | Source Control → **Changes** | `git status` |
| Stage a file | **+** next to the file | `git add <file>` |
| Stage everything | **+** next to **Changes** | `git add .` |
| Unstage a file | **−** next to the file | `git restore --staged <file>` |
| Commit | Type a message → **✓ Commit** | `git commit -m "msg"` |
| See history | Source Control → **Graph** | `git log --oneline` |
| Revert a commit (new commit) | Terminal | `git revert <hash>` |
| Undo last commit (unpushed only) | **⋯ → Commit → Undo Last Commit** | `git reset --soft HEAD~1` |
| Create a branch | Click branch name → **+ Create new branch...** | `git switch -c <name>` |
| Switch branch | Click branch name → pick one | `git switch <name>` |
| Merge a branch into the current one | Palette → `Git: Merge Branch...` | `git merge <branch>` |
| Abort a merge | Palette → `Git: Abort Merge` | `git merge --abort` |
| Delete a branch | Palette → `Git: Delete Branch...` | `git branch -d <name>` |
| Connect to a remote | **Publish Branch** | `git remote add origin <url>` |
| List remotes | | `git remote -v` |
| Add the original repo as `upstream` | | `git remote add upstream <url>` |
| Push a new branch | **Publish Branch** | `git push -u origin <name>` |
| Push later commits | **Sync Changes** | `git push` |
| Download without merging | Palette → `Git: Fetch` | `git fetch` |
| Download and merge | **Sync Changes** or `Git: Pull` | `git pull` |
| Stop tracking a file | | `git rm --cached <file>` |

## Merge markers

```text
<<<<<<< HEAD              ← start: the branch you're on ("Current")
your lines
=======                   ← divider
their lines
>>>>>>> other-branch      ← end: the branch you're merging in ("Incoming")
```

Fix = keep what you want → delete all three marker lines → save → stage → commit.

## Golden rules

1. Never work directly on `main`. Always make a branch.
2. Pull/fetch before you start something new.
3. Commit small, with a message that says what changed.
4. One topic per pull request.
5. Never commit passwords or API keys. Put them in `.gitignore`.
6. A conflict is not an error. It's Git asking you to decide.
