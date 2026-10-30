# Step 12: A conflict in a real pull request

**Goal:** Everyone orders cheese at the same time. Resolve the resulting conflict on a real pull request.

In Step 7 you caused a conflict yourself. Here you'll meet it the way it usually happens in real life: **someone else's change landed first.**

🍕 **Pizza version:** the restaurant has **one** order sheet, and everybody writes their cheese order on the **same line**. The first order goes in cleanly. Everyone after that finds the line already taken.

---

## The file

[`exercises/cheese-order.md`](../exercises/cheese-order.md) has one line everyone changes:

```text
Cheese: ???
```

## 1. Start fresh from the latest `main`

Do this **before** creating your branch, or you'll be starting from an old copy.

1. On your fork's page, click **Sync fork → Update branch**.
2. In VS Code switch to `main` and **Sync Changes**.

   (Terminal: `git switch main && git pull upstream main`)
3. Create a branch:
   ```
   cheese-<your-username>
   ```

## 2. Make your order

1. Open `exercises/cheese-order.md`.
2. **Replace the whole `Cheese: ???` line** with your own order, including your username:
   ```text
   Cheese: Mozzarella (octocat)
   ```
3. Save, stage, commit (`Add octocat's cheese order`), **Publish Branch**.

## 3. Open the pull request

Open a PR into `Sw4ppleneel/geekroom-git-workshop:main`, exactly like Step 11.

What happens next depends on whether someone else got there first:

- **GitHub says "Able to merge":** you were first. A maintainer merges it. You're done, and you've seen the happy path.
- **GitHub says "This branch has conflicts that must be resolved":** someone else's order is already on that line. **This is the exercise.** 👇

---

## 4. Resolve the conflict

Resolve it on your machine, in VS Code. Your PR is simply a view of your branch on your fork, so fixing the branch fixes the PR.

### a. Fetch the original repo's latest `main`

Make sure you're on **your** `cheese-<your-username>` branch (bottom-left), then:

```bash
git fetch upstream
```

(Or Command Palette → `Git: Fetch From All Remotes`.)

### b. Merge `upstream/main` into your branch

Command Palette → **`Git: Merge Branch...`** → choose **`upstream/main`**.

> **Terminal version:** `git merge upstream/main`

VS Code reports *Merge conflict in exercises/cheese-order.md*. Expected! 🎯

### c. Look at the markers

Open the file from **Source Control → Merge Changes**:

```text
<<<<<<< HEAD
Cheese: Mozzarella (octocat)
=======
Cheese: Cheddar (hubot)
>>>>>>> upstream/main
```

| Part | Whose it is |
|---|---|
| Between `<<<<<<< HEAD` and `=======` | **Yours** (Current Change) |
| Between `=======` and `>>>>>>> upstream/main` | **What's already on the original repo's `main`** (Incoming Change) |

### d. Decide what to keep

This is a shared order sheet, so everyone's order belongs on it. **Keep both lines.** Click **Accept Both Changes**, or edit by hand so the file looks like this, with **all three marker lines removed**:

```text
Cheese: Cheddar (hubot)
Cheese: Mozzarella (octocat)
```

> ⚠️ Don't delete someone else's order. "Accept Current Change" would throw away the other person's line. Always read both sides before you choose.

### e. Mark it resolved and commit

1. Save the file.
2. In Source Control, click **+** next to the file to stage it.
3. The message is pre-filled (`Merge remote-tracking branch 'upstream/main' into cheese-octocat`). Click **✓ Commit**.

### f. Push

Click **Sync Changes** (or `git push`). It goes to your fork's `cheese-<your-username>` branch.

### g. Check the PR

Reload your pull request on GitHub. The conflict warning is gone, and **Files changed** shows your line added. A maintainer can now merge it.

If another order lands before yours does, GitHub may say conflicts again. That's normal: repeat from step **a** (fetch → merge `upstream/main` → resolve → commit → push).

---

## Why did this happen?

Git merges by comparing **lines**. When two people change the **same line**, Git can't tell whose version should win, so it hands the decision to you. It's not an error. It's the tool being honest about what it can't know.

Everything you did here is how real teams work:

```
fetch upstream → merge it into your branch → resolve → commit → push → PR updates
```

---

## ✅ Self-check

- [ ] I opened a PR that changed `exercises/cheese-order.md`
- [ ] If it conflicted, I merged `upstream/main` into my branch and resolved it in VS Code
- [ ] No `<<<<<<<`, `=======` or `>>>>>>>` lines are left in the file
- [ ] My PR shows no conflicts

---

## 🎉 You've finished!

You went from "what is Git?" to a merged pull request on a public project. Pizza-wise:

**init** the prep station → **stage** toppings on the base → **commit** (bake) → read the **log** → **branch** your own mini pizza → **merge** into the family pizza → argue about **cheese** (conflicts) → **push** it to the dining table → **fork** the restaurant's recipe → serve with a **pull request**.

**Where to go next**

- Look for beginner-friendly issues on projects you use (search GitHub for the label `good first issue`).
- Use `pizza-station` as a sandbox. Break it, fix it, repeat.
- Keep the [cheat sheet](../reference/cheatsheet.md) handy.
