# Step 9: Local vs remote

**Goal:** Take your pizza from the **prep station** (your computer) to the **dining table** (GitHub), and learn how the two stay in sync.

---

## Two repositories

| | What it is | Where |
|---|---|---|
| **Local repository** | A copy of the project on **your own computer**, managed by Git | Your laptop |
| **Remote repository** | A **shared** version of the project hosted by GitHub (or another Git server) | GitHub's servers |

```
Git     → tool for local file tracking
GitHub  → interface for sharing repos
```

🍕 **Pizza version:** the prep station is **local**; the **dining table** is **remote**.

**Your local repo has:**

```
Working directory → Staging area → Local Git history (.git folder)
```

**Your remote repo has:**

```
Remote Git history (on GitHub's servers)
```

---

## Connecting them

Creating the link:

```bash
git remote add origin https://github.com/<your-username>/<repo>.git
```

- It means: *"The remote repository named **origin** lives at this URL."*
- **`origin`** is the **default name** for the first remote repo.

After that you can:

| Action | Direction | What it does |
|---|---|---|
| **Push** | local → remote | Sends your commits to GitHub |
| **Pull** | remote → local | **Fetch + merge**: downloads new commits and merges them into your branch |
| **Fetch** | remote → local | Downloads new commits but **doesn't merge** them (your files don't change) |

```bash
git push -u origin main      # uploads your local commits to the shared remote repo
git pull origin main         # downloads and merges changes your collaborator pushed
git fetch                    # downloads, but doesn't merge
```

### The complete Git flow

```
WORKING DIRECTORY
       │  git add
       ▼
  STAGING AREA
       │  git commit
       ▼
LOCAL REPOSITORY  ◄──── git pull origin main ────┐
       │                                         │
       └──── git push origin main ──────────►  GITHUB
```

- **When you push**, Git sends **only the new commits** that aren't already on the remote.
- **When you pull**, Git gets **only the new commits** from the remote.

---

## Hands-on: publish `pizza-station`

### Easy way (VS Code)

1. Open `pizza-station` in VS Code.
2. In Source Control, click **Publish Branch**.
3. Choose **Publish to GitHub private repository** (it's your practice repo; no need for it to be public).
4. Leave all files ticked. `oven.log` and `secrets.env` won't be offered, because you ignored them in Step 8. 🎉
5. Click **Open on GitHub** when it finishes.

### Manual way (what VS Code just did for you)

If you'd rather do it by hand, or want to see the steps:

1. On github.com click **+ → New repository**, name it `pizza-station`, choose **Private**, and leave **README, .gitignore and license unticked**. The remote has to start **empty**.
2. Copy the HTTPS URL, then in the VS Code terminal:
   ```bash
   git remote add origin https://github.com/<your-username>/pizza-station.git
   git push -u origin main
   ```

Check the link:

```bash
git remote -v
```

```
origin  https://github.com/<your-username>/pizza-station.git (fetch)
origin  https://github.com/<your-username>/pizza-station.git (push)
```

Open the repo on GitHub: `README.md`, `docs/`, `data/`, `app/`, `toppings/` and `.gitignore` are all there, and **`secrets.env` is not**.

---

## `main` vs `origin/main`

Your computer holds **two different things** with similar names:

| Name | What it is |
|---|---|
| `main` | **Your** local branch. You change it |
| `origin/main` | Your computer's **last known copy** of GitHub's `main`. It only updates when you talk to GitHub (fetch, pull or push) |

So your computer can be **out of date** without knowing. GitHub doesn't tell it when something changes. That's why **fetch** exists.

## Hands-on: let GitHub get ahead

1. On github.com, open `data/veggies.md` in your `pizza-station`, click the **pencil**, change it to `Veggies: mushrooms, spinach` and **Commit changes** directly to `main`.
2. Go back to VS Code. Your file **hasn't changed**. Your computer doesn't know yet.
3. Command Palette → **`Git: Fetch`**. In the status bar you'll see **↓1** (one commit behind). Your file **still** hasn't changed; fetch only updated `origin/main`.
4. See what's waiting:
   ```bash
   git log HEAD..origin/main --oneline
   git diff HEAD origin/main
   ```
5. Now **pull** (**Sync Changes**, or **`Git: Pull`**). The spinach arrives. ↓1 disappears.
6. Make a local commit but don't push: the status bar shows **↑1** (one commit ahead). Click **Sync Changes** to push it.

| Status bar | Meaning | Do this |
|---|---|---|
| `↑2` | You have 2 commits GitHub doesn't | **Push** |
| `↓3` | GitHub has 3 commits you don't | **Pull** |
| `↓3 ↑2` | Both sides have new commits | Pull (merge), then push. Conflicts may appear here |

> **Sync Changes** in VS Code = pull, then push.

**A push gets rejected** when you're behind: GitHub won't let you overwrite commits you haven't seen. Fetch, pull, then push again.

---

## ✅ Checkpoint

- [ ] `pizza-station` exists on GitHub and `secrets.env` is **not** in it
- [ ] `git remote -v` shows `origin`
- [ ] I saw **↓1** after a fetch and **↑1** after a local commit
- [ ] I can explain the difference between **fetch** and **pull**
- [ ] I can explain the difference between `main` and `origin/main`

Practice done! Now the real thing.

Next: [Step 10: Fork and clone](10-fork-and-clone.md)
