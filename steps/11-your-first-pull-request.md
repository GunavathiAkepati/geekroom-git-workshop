# Step 11: Your first pull request

**Goal:** Add yourself to the repository's `participants/` folder and propose the change with a **pull request**.

---

## What is a pull request?

A **pull request (PR)** is a proposal that says: *"I made these changes on my branch. Please review them and merge them into `main`."*

- You'll see a prompt to **open a pull request**.
- You **review your changes**, then **create the PR**.
- A **maintainer** (or you, if it's your own repo) can then **merge it** into the `main` branch.

🍕 **Pizza version:** you've made your pizza in your own kitchen. The PR is **serving it to the table** and letting the restaurant decide whether it goes on the menu.

---

## The rules (they're short)

Read [CONTRIBUTING.md](../CONTRIBUTING.md) first. In short:

- Add **one file**: `participants/<your-username>.md`.
- Don't edit anyone else's file.
- Remember it's **public**. No private details.

---

## 1. Create a branch

Never work on `main`. Make a branch for your change:

1. In your clone, click the branch name in the bottom-left → **+ Create new branch...**
2. Name it:
   ```
   add-<your-username>
   ```
   For example: `add-octocat`.

> **Terminal version:** `git switch -c add-octocat`

## 2. Add your file

1. Right-click the **`participants`** folder → **New File**.
2. Name it `<your-username>.md` (exactly your GitHub username, e.g. `octocat.md`).
3. Paste this and fill it in:

   ```markdown
   # Your name or nickname

   - **GitHub username:** your-username
   - **Favourite pizza topping:** ...
   - **Why I'm learning Git:** one sentence
   ```
4. Save.

## 3. Stage and commit

1. Source Control → click **+** next to your new file (**stage**).
2. Message: `Add <your-username> to participants`
3. Click **✓ Commit**.

> **Terminal version:**
> ```bash
> git add participants/octocat.md
> git commit -m "Add octocat to participants"
> ```

## 4. Push to *your fork*

Click **Publish Branch**. VS Code pushes it to `origin`, which is **your fork**.

> **Terminal version:** `git push -u origin add-octocat`

Check it: open your fork on GitHub. The branch dropdown lists `add-<your-username>`, and your file is in `participants/`.

## 5. Open the pull request

### Option A: GitHub banner

1. On your fork's page on github.com, a yellow banner says **Compare & pull request**. Click it.
2. Check the top of the page:

   | | Should say |
   |---|---|
   | **base repository** | `Sw4ppleneel/geekroom-git-workshop` |
   | **base** | `main` |
   | **head repository** | `<your-username>/geekroom-git-workshop` |
   | **compare** | `add-<your-username>` |

   (Your changes flow **from your fork's branch → into the original's `main`**.)
3. The title is pre-filled from your commit. The description box is pre-filled with a short template. Fill it in.
4. Click **Create pull request**.

### Option B: from VS Code

Click the **GitHub (cat) icon** in the sidebar → **Create Pull Request**, and confirm base and compare as above.

> No banner? Go to the **original** repo → **Pull requests** → **New pull request** → **compare across forks**, and set the head repository to your fork and the compare branch to your branch.

---

## 6. Look at your own PR

On the PR page:

- **Conversation:** the discussion, and where merging happens
- **Commits:** the commits in this PR
- **Files changed:** exactly the lines you added (green) and removed (red)

Open **Files changed**. This is what a reviewer sees. It should be **one new file** and nothing else. If other files show up, you changed something you shouldn't have. Fix it on your branch and push again; the PR updates itself.

## 7. Wait for a review

A maintainer will look at your PR, may leave comments, and then **merge** it. If they ask for a change:

1. Make the change on the **same branch** in VS Code.
2. Commit it and **Sync Changes** (push).
3. The PR **updates automatically**. You don't open a new one.

---

## 8. After your PR is merged

Your change is in the original repository's `main`, but **your fork and your clone don't know yet**. Catch up:

1. On your fork's page on github.com click **Sync fork → Update branch**.
2. In VS Code switch to `main` (bottom-left) and **Sync Changes** / **`Git: Pull`**.
3. Open `participants/`: your file is there, along with everyone else who has been merged.

(Or from the terminal: `git switch main && git pull upstream main && git push origin main`.)

You can delete your `add-<your-username>` branch now: **`Git: Delete Branch...`** locally, and the trash can next to it under **Branches** on GitHub.

🎉 **You've contributed to an open source project.**

---

## ✅ Checkpoint

- [ ] My PR is open: base `Sw4ppleneel/geekroom-git-workshop:main`, compare `<me>:add-<me>`
- [ ] **Files changed** shows only `participants/<my-username>.md`
- [ ] After it merged, my local `main` contains my file

Next: [Step 12: A conflict in a real PR](12-conflict-in-a-real-pr.md)
