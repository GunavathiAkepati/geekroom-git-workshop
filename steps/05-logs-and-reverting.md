# Step 5: Logs and reverting

**Goal:** Read your history, then fix a mistake without erasing it.

---

## Logs

Git keeps a **history** (the log) of every commit. Each entry includes:

| Part | What it is |
|---|---|
| **Commit ID (SHA)** | A unique 40-character hash that identifies the commit |
| **Author** | Name and email of the person who made the commit (the ones you set in Step 1) |
| **Date & time** | When the commit was made |
| **Commit message** | The description it was saved with |

🍕 **Pizza version:** pulling up the **kitchen order ticket**. It contains every pizza baked, and when.

### Look at yours

**In VS Code:** open Source Control and expand the **Graph** section (or open **Timeline** in the Explorer for a single file). Each dot is a commit. Click one to see what changed.

**In the terminal:**

```bash
git log
git log --oneline
```

`--oneline` shows a short hash plus the message, which is easier to read:

```
c4e91a2 Add mozzarella
7b03d58 Add mushrooms
1f2a6e9 Add sauce, veggies and cheese trays
```

You'll see the short hash is just the first few characters of the long one. You can use the short version wherever Git wants a commit name.

---

## Reverting

**Reverting** reverses the changes introduced by a commit and **saves that reversal as a new commit** (with its own new hash).

🍕 **Pizza version:** a pizza baked long ago had the wrong topping. You **can't un-bake it**, so you **bake a corrected one**. The history still shows both, and nothing is rewritten.

### Make a mistake on purpose

1. Open `data/veggies.md` and change it to `Veggies: mushrooms, pineapple`. Save.
2. Stage it and commit with the message `Add pineapple`. 🍍

Everyone agrees this was a mistake.

### Revert it

In the terminal, using the hash from `git log --oneline`:

```bash
git revert <hash-of-the-pineapple-commit>
```

Your editor opens with a message like `Revert "Add pineapple"`. Save and close that tab to accept it.

Now look at the log or the Graph: the pineapple commit is still there, **plus** a new revert commit on top, and `data/veggies.md` is back to `Veggies: mushrooms`.

> In recent VS Code versions you can also right-click a commit in the **Graph** and look for a revert option. If you don't see it, use the terminal command above. That always works.

---

## "Undo Last Commit" is a different thing

In Source Control, the **⋯** menu → **Commit** → **Undo Last Commit** takes your last commit **back out of the history** and puts its changes back in the staging area, as if you'd never baked it.

| | **Revert** | **Undo Last Commit** |
|---|---|---|
| What happens | Adds a **new** commit that reverses an old one | **Removes** the last commit from history; its changes return to staged |
| History | Preserved | Rewritten |
| Safe after you've shared (pushed) it? | ✅ Yes | ❌ No, only use before pushing |
| Pizza | Bake a corrected pizza | Pizza is still on the counter; put it back on the dough |

Rule of thumb: **if other people might already have the commit, revert. If it's only on your machine, undo is fine.**

### Try it

1. Make a small edit (`Cheese: mozzarella and basil`), stage it, and commit `Add basil`.
2. Use **⋯ → Commit → Undo Last Commit**.
3. Notice the commit is gone from the Graph and the change is back under **Staged Changes**.
4. Commit it again with a better message: `Add basil to cheese`.

---

## 🚩 Checkpoint 3: First commit

**5 min in VS Code. Use a new practice folder.**

1. **Initialize** a repository.
2. Create **`menu.txt`** with your favourite topping.
3. **Stage** it and **commit**: `Add pizza menu`
4. **Find the commit** in the history.

**Show a partner the message and the commit hash.**

> ⚠️ "New practice folder" means a **separate** one, for example `pizza-menu`. Don't create it inside `pizza-station`, or you'll nest one repository inside another.

Need a reminder?

| Task | Where |
|---|---|
| Initialize | [Step 3](03-repository-and-directories.md#2-initialise-it) |
| Stage and commit | [Step 4](04-staging-and-committing.md) |
| Find the commit | Source Control → **Graph**, or `git log --oneline` (above) |

---

## ✅ Self-check

- [ ] I can find a commit's hash, author, date and message in the Graph or `git log`
- [ ] I reverted the pineapple commit and the original commit is still in my history
- [ ] I can explain when to use **revert** and when **Undo Last Commit** is OK

Next: [Step 6: Branches and merging](06-branches-and-merging.md)
