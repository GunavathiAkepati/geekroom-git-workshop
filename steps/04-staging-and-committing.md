# Step 4: Staging and committing

**Goal:** Put toppings on the pizza base (**stage**), then bake it (**commit**).

---

## The staging area

- A **temporary space** to hold your modified files *before* you permanently add them to the repository.
- Code in the staging area can be **pulled back** to rewrite or edit.
- Or it can be **exported to the repo** and stored definitively.
- To change something you've staged: go back to the working directory, edit the unstaged file, and stage it again when you're done.

🍕 **Pizza version:** staging is **putting toppings onto the dough at the counter**. Nothing is baked yet. You can still take a topping off and put it back in its tray to think again.

## Committing

- **Permanently saves** your staged changes to the repository's history.
- It's a **snapshot** of your project at a specific point in time.
- It keeps a **log** describing what changed and why.
- ⚠️ **Only staged changes can be committed.**
- Every commit gets a **commit hash**, a unique identifier (its name).

🍕 **Pizza version:** committing is **finally baking the pizza and permanently adding it to your history.**

The flow is always: **edit → stage → commit.**

```
 working directory  ──git add──►  staging area  ──git commit──►  local repository
   (trays)                         (pizza base)                     (baked pizzas)
```

---

## Hands-on in `pizza-station`

### 1. Stage one file

1. Open **Source Control** (**Ctrl+Shift+G**).
2. Under **Changes**, hover over `docs/sauce.md` and click the **+** (**Stage Changes**).
3. It moves to **Staged Changes**. The other files stay in **Changes**.

> **Terminal version:** `git add docs/sauce.md`

### 2. Take it back off (unstage)

1. Hover over `docs/sauce.md` under **Staged Changes** and click the **−** (**Unstage Changes**).
2. It goes back to **Changes**. Putting toppings back in the tray, nothing lost.

> **Terminal version:** `git restore --staged docs/sauce.md`

### 3. Stage and bake the first pizza

1. Stage **everything** this time: click the **+** next to the **Changes** heading (or `git add .`).
2. Type a message in the box above the Commit button: `Add sauce, veggies and cheese trays`
3. Click **✓ Commit**.

> **Terminal version:**
> ```bash
> git add .
> git commit -m "Add sauce, veggies and cheese trays"
> ```

Source Control is now empty: everything has been baked. 🎉

### 4. Prove that only staged changes get committed

1. Open `data/veggies.md` and change it to `Veggies: mushrooms`. Save.
2. Open `app/cheese.md` and change it to `Cheese: mozzarella`. Save.
3. Stage **only** `data/veggies.md` (click its **+**).
4. Commit with the message `Add mushrooms`.
5. Look at Source Control: `app/cheese.md` is **still sitting under Changes**, uncommitted. Only what was on the base got baked.
6. Now stage and commit it too: `Add mozzarella`.

You now have three commits.

---

## What makes a good commit message?

Say **what changed**, in one short plain sentence.

| ✅ Good | ❌ Not good |
|---|---|
| `Add mushrooms` | `stuff` |
| `Fix wrong cheese in cheese.md` | `asdf` |

---

## ✅ Checkpoint

- [ ] I staged a single file and then unstaged it
- [ ] I made three commits in `pizza-station`
- [ ] I saw an edited-but-unstaged file get left out of a commit
- [ ] I can say why staging exists (the pizza base) in one sentence

Next: [Step 5: Logs and reverting](05-logs-and-reverting.md)
