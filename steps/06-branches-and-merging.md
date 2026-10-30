# Step 6: Branches and merging

**Goal:** Let three family members top their own mini pizzas at the same time, then combine them onto the family pizza.

---

## Branches

- A branch is a **duplicated version of your code**, up to the point where you branched.
- Changes you make on the new branch (often called a **feature branch**) are **not communicated** to the `main` branch, the code you branched from, until you merge them.

🍕 **Pizza version:** **individual mini pizzas, each family member tops with their own toppings.** Mom has olives and corn; the kid has ham and onion. Nobody messes with anyone else's pizza.

```
main      A───B
               \
mom             C───D
kid             E───F
sister          G───H
```

## Merging

- **Merging** combines two branches.
- It takes the commits from a **source** branch (e.g. `mom`) and applies them to a **target** branch (e.g. `main`).
- Sometimes it creates a new **merge commit** that ties the two histories together.

🍕 **Pizza version:** the family members **put all their individual toppings onto the communal family pizza.**

The rule for merging: **switch to the branch you want to merge *into*, then merge the other one in.**

```bash
git switch main          # the branch you want to merge INTO
git merge mom            # the branch you want to merge FROM
```

(`git checkout main` does the same as `git switch main` and you'll see it in older tutorials.)

---

## Kinds of merges

### Fast-forward merge

If the branch you're merging **into** has **no new commits** since you branched, Git can simply **move the branch pointer forward**. No merge commit is needed.

```
before:   main: A --- B
                        \
          feature:       C --- D

after:    main: A --- B --- C --- D
```

🍕 *Mom puts olives and corn on the pizza and strolls away. Afterwards the kid comes and adds ham and onion. No conflict; just simple addition.*

### Three-way merge

If **both** branches have new commits, Git finds the **common ancestor** commit and combines the changes from both sides into a new **merge commit** (call it `M`) with **two parents**.

```
before:   main:    A --- B --- C --- D
                           \
          feature:          E --- F

after:    main:    A --- B --- C --- D ------- M
                           \                  /
          feature:          E ----- F --------
```

`M` has two parents:

- **Parent 1** → `D` (the last commit on `main`)
- **Parent 2** → `F` (the last commit on `feature`)

🍕 *Mom, Brother and Sister each topped their own mini pizza. There's no conflict between any of them: all toppings are merged and finally committed together. The **merge commit** is baking the merged pizza made of everyone's toppings.*

---

## Hands-on in `pizza-station`

Make sure you're on `main` with nothing left to commit (bottom-left says `main`, Source Control is empty).

### 1. Create three branches from the same starting point

For each of `mom`, `kid` and `sister`:

1. **Click the branch name** in the bottom-left status bar.
2. Choose **+ Create new branch...**, type the name, press Enter.
3. Create the file for that person (below), stage it, and commit.
4. Switch back to `main` (click the branch name → `main`) **before** creating the next branch.

| Branch | File | Contents | Commit message |
|---|---|---|---|
| `mom` | `toppings/mom.md` | `Mom: olives and corn` | `Add Mom's toppings` |
| `kid` | `toppings/kid.md` | `Kid: ham and onion` | `Add Kid's toppings` |
| `sister` | `toppings/sister.md` | `Sister: basil and chilli` | `Add Sister's toppings` |

> **Terminal version, for one branch:**
> ```bash
> git switch -c mom
> # create toppings/mom.md
> git add toppings/mom.md
> git commit -m "Add Mom's toppings"
> git switch main
> ```

Notice what happens when you switch: **files appear and disappear** as you move between branches. Switch to `main` and `toppings/` isn't there. Switch to `mom` and `toppings/mom.md` is.

### 2. Merge Mom's pizza: a fast-forward

1. Make sure you're on **`main`**.
2. Open the Command Palette (**Ctrl+Shift+P** / **Cmd+Shift+P**), run **`Git: Merge Branch...`**, and choose **`mom`**.

   > **Terminal version:** `git merge mom`
3. Git says *Fast-forward*. `main` has simply moved up to Mom's commit, with **no merge commit**.

Check the **Graph**: it's a straight line.

### 3. Merge the kid's pizza: a three-way merge

`main` has moved on (it now has Mom's commit) since `kid` was created, so a fast-forward is no longer possible.

1. Still on `main`, run **`Git: Merge Branch...`** → **`kid`**.
2. VS Code opens a **commit message** tab: `Merge branch 'kid'`. **Close that tab** (or press **Ctrl+Enter** / **Cmd+Enter**) to accept it.
3. Check the Graph: the lines **split and rejoin**, with a merge commit that has two parents. That's `M`. 🍕

### 4. Merge Sister's pizza

Do the same for **`sister`**. Both merges succeeded **without a conflict**, because each branch touched a **different file**.

Open `toppings/`: all three toppings files are on `main` now. The family pizza is complete.

> Don't want the branches any more? **`Git: Delete Branch...`** → pick `mom`, `kid`, `sister`. Their commits live on in `main`.

---

## ✅ Checkpoint

- [ ] I created three branches and saw files appear and disappear as I switched
- [ ] My first merge was a **fast-forward** (a straight line in the Graph)
- [ ] My next merges created **merge commits** (lines split and rejoin)
- [ ] I can explain why the first was a fast-forward and the others weren't

Next: [Step 7: Merge conflicts](07-merge-conflicts.md)
