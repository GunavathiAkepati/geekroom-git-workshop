# Step 8: .gitignore

**Goal:** Keep files that don't belong in the repository out of it.

🍕 **Pizza version:** *Unnecessary items* are the flour bags, the empty box and the cleaning cloth. They're in the kitchen, but they don't belong on the table.

---

## What `.gitignore` does

- Tells Git **which files and folders to ignore**.
- Git **won't track, stage or commit** them.

### What it's for

- **Temporary files** like logs or cache.
- **Sensitive information** like passwords or API keys, so they're never pushed to GitHub.
- Keeping your repository **clean** by excluding unnecessary files.

> 🔐 This matters even more on a public repo. If you commit a password or API key and push it, **assume it's compromised**. Deleting it afterwards does not remove it from history.

---

## Tracked vs untracked

| Status | Meaning |
|---|---|
| **Tracked** | Committed **at least once** |
| **Untracked** | **Never committed.** Even a *staged* file counts as untracked until you commit it |

### The important catch

- `.gitignore` only stops **new, untracked** files from being staged.
- It does **not** work on files that are **already tracked**. Their changes still show up in `git status`.

---

## Hands-on in `pizza-station`

### 1. Create files that shouldn't be committed

Create these in the root of `pizza-station`:

| File | Contents |
|---|---|
| `oven.log` | `oven preheated at 220C` |
| `secrets.env` | `OVEN_API_KEY=not-a-real-key` |

Source Control lists both as **U**. If you committed them now, they'd be in your history forever.

### 2. Create `.gitignore`

Create a file named exactly **`.gitignore`** (with the leading dot, no `.txt` on the end) in the root, containing:

```text
# temporary files
*.log

# secrets
secrets.env

# macOS junk
.DS_Store
```

Save it. **`oven.log` and `secrets.env` vanish from Source Control.** Git is ignoring them.

| Pattern | Ignores |
|---|---|
| `*.log` | Any file ending in `.log` |
| `secrets.env` | That one file |
| `.DS_Store` | The hidden file macOS creates in folders |
| `node_modules/` | A whole folder (a common one in JavaScript projects) |

### 3. Commit the `.gitignore` itself

Stage and commit `.gitignore` with the message `Add .gitignore`. (You **do** commit this file, so everyone who clones the repo ignores the same things.)

### 4. See the catch with a tracked file

1. Create `notes.log` and commit it **before** it's ignored: temporarily comment out the `*.log` line by putting a `#` in front of it, stage and commit `notes.log` with `Add notes`, then remove the `#` again and save.
2. Now edit `notes.log`. Even though `*.log` is back in `.gitignore`, the change **still shows up** in Source Control, because Git is already tracking it.
3. To make Git forget a tracked file (without deleting it from your disk), run in the terminal:
   ```bash
   git rm --cached notes.log
   ```
4. Commit `Stop tracking notes.log`. From now on it's ignored.

---

## ✅ Self-check

- [ ] `oven.log` and `secrets.env` don't appear in Source Control
- [ ] `.gitignore` itself is committed
- [ ] I can explain tracked vs untracked
- [ ] I know `.gitignore` doesn't affect files Git is already tracking

Next: [Step 9: Local vs remote](09-local-vs-remote.md)
