# Step 7: Merge conflicts

**Goal:** Cause a merge conflict on purpose, then resolve it. Conflicts are normal. Git is simply asking you a question it can't answer by itself.

---

## What is a conflict?

If **both branches change the same part of the same file differently**, Git can't decide which change to keep.

- A **merge conflict** arises.
- It **must be resolved manually**.

🍕 **Pizza version:**

> Mom got **Mozzarella** cheese.
> Dad got **Cheddar** cheese.
> Only **1** cheese needed.
> Manual resolution required.

Last step, everyone touched a **different** file, so Git combined them automatically. Now two people change the **same line**.

---

## How a conflict looks

Two branches both changed `color`:

| Branch | Content |
|---|---|
| `main` | `color = "blue"` |
| `feature` | `color = "red"` |

Git stops and writes **conflict markers** into the file:

```text
<<<<<<< main
color = "blue"
=======
color = "red"
>>>>>>> feature
```

| Marker | Meaning |
|---|---|
| `<<<<<<< main` | **Start.** Everything below is from the branch you're **trying to get into** (the one you're on) |
| `=======` | **Divider** between the two versions |
| `>>>>>>> feature` | **End.** Everything above the divider and below `=======` is from the branch you're **trying to merge from** |

(VS Code may show `HEAD` instead of the branch name; `HEAD` means "the branch you're on".)

## How to resolve

1. **Manually edit** and keep the code you want.
2. **Remove all** the `<<<<<<<`, `=======` and `>>>>>>>` lines.
3. **Stage and commit.**

---

## Hands-on in `pizza-station`

You'll use `app/cheese.md`, which currently says `Cheese: mozzarella` on `main` (from Step 4). If yours doesn't, set it to that and commit.

### 1. Mom's cheese

1. On `main`, create a branch **`cheese-mom`**.
2. Edit `app/cheese.md` to say exactly: `Cheese: Mozzarella (Mom)`
3. Stage and commit: `Mom picks mozzarella`.
4. Switch back to **`main`**.

### 2. Dad's cheese, from the same starting point

1. Create a branch **`cheese-dad`** from `main`.
2. Edit **the same line** of `app/cheese.md` to say: `Cheese: Cheddar (Dad)`
3. Stage and commit: `Dad picks cheddar`.
4. Switch back to **`main`**.

### 3. Merge the first one: no problem

On `main`: **`Git: Merge Branch...`** → `cheese-mom`. It fast-forwards, because `main` hasn't changed.

### 4. Merge the second one: boom 💥

On `main`: **`Git: Merge Branch...`** → `cheese-dad`.

VS Code reports *Merge conflict in app/cheese.md* and the merge **stops**. This is what we wanted.

> **Terminal version:**
> ```bash
> git switch main
> git merge cheese-mom
> git merge cheese-dad      # CONFLICT
> ```

### 5. Find the conflict

In **Source Control** there's now a **Merge Changes** group with `app/cheese.md` in it. Click the file. You'll see:

```text
<<<<<<< HEAD
Cheese: Mozzarella (Mom)
=======
Cheese: Cheddar (Dad)
>>>>>>> cheese-dad
```

Above the conflict VS Code shows clickable choices:

| Choice | Result |
|---|---|
| **Accept Current Change** | Keep what's on **your branch** (Mom's) |
| **Accept Incoming Change** | Keep what's being **merged in** (Dad's) |
| **Accept Both Changes** | Keep both lines |
| **Compare Changes** | Side-by-side view |

> **Prefer a visual tool?** Click **Resolve in Merge Editor** at the bottom right. It shows *Incoming*, *Current* and *Result* panes. Tick what you want and click **Complete Merge**.

### 6. Decide

Only one cheese fits on this pizza. Make a decision. Either click **Accept Current Change** or **Accept Incoming Change**, or edit the file by hand until it reads exactly:

```text
Cheese: Mozzarella and Cheddar blend (Mom and Dad)
```

Whatever you choose, make sure **no marker lines** remain. Search the file for `<<<<` to be sure.

### 7. Finish the merge

1. Save the file.
2. In Source Control, click **+** next to `app/cheese.md` under **Merge Changes** to stage it. That's you telling Git *"resolved"*.
3. The commit box is pre-filled with `Merge branch 'cheese-dad'`. Click **✓ Commit**.

> **Terminal version:**
> ```bash
> git add app/cheese.md
> git commit
> ```

Check the Graph: your merge commit has two parents, just like Step 6. The conflict is history.

---

## Bailing out

Started a merge and want to leave? **Command Palette → `Git: Abort Merge`** (terminal: `git merge --abort`). Your branch goes back to exactly how it was before the merge.

---

## Avoiding conflicts in real life

- **Pull often**, so you start from the latest code.
- **Keep branches short-lived.** The longer a branch lives, the further `main` drifts from it.
- **Make small changes.** Fewer lines changed means fewer collisions.
- **Talk to teammates** before two people edit the same file.

---

## ✅ Checkpoint

- [ ] I know what `<<<<<<<`, `=======` and `>>>>>>>` mean
- [ ] I caused a conflict and resolved it in VS Code
- [ ] No marker lines are left in `app/cheese.md`
- [ ] I can explain **Current** vs **Incoming**

Next: [Step 8: .gitignore](08-gitignore.md)
