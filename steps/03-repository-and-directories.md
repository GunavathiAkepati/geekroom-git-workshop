# Step 3: Repository and directories

**Goal:** Create your own **pizza prep station**: a brand-new repository with three trays (directories).

From here to Step 9 you work in a practice repo called **`pizza-station`**. It's separate from this workshop repo and it's yours to break.

---

## What is a repository?

- The **main folder** for your project.
- Holds the relevant **folders (directories) and files**.
- It's just an ordinary directory that has been **initialised**, i.e. converted into a special kind of directory called a **repo**.
- It's **tracked by Git**.

Creating one takes two ideas:

| Command | What it does |
|---|---|
| `mkdir <folder-name>` | Creates a folder (directory) |
| `git init` | Turns your directory into a repository |

Under the hood, `git init` adds a hidden folder called **`.git`** where Git keeps your whole history. You never edit it by hand.

## What is a directory?

- A **folder inside your repository**.
- It can contain other directories or files.
- The directory with the files you're actively working on is called the **working directory**.

In pizza terms, the repository is the prep station and each directory is a **tray**:

```
pizza-station/          ← repository (prep station)
├── docs/               ← sauce tray
├── data/               ← veggie tray
└── app/                ← cheese tray
```

---

## 1. Make the folder and open it

1. Choose a place that is **not** already inside another Git repo, for example `Documents`.
2. In VS Code: **File → Open Folder...** (macOS: **File → Open...**), click **New Folder**, name it **`pizza-station`**, and open it.
3. Click **Yes, I trust the authors** if asked.

> **Terminal version:**
> ```bash
> mkdir pizza-station
> cd pizza-station
> code .
> ```

## 2. Initialise it

1. Open **Source Control** (**Ctrl+Shift+G**; on macOS also use the **Control** key).
2. You'll see *"The folder currently open doesn't have a Git repository"*. Click **Initialize Repository**.

   > **Terminal version:** `git init`
3. The bottom-left corner of VS Code now shows **`main`**. That's your current branch.

**You've just created a repository.** (If the bottom-left says `master`, see [troubleshooting](../reference/troubleshooting.md#my-branch-is-called-master-instead-of-main).)

## 3. Add the trays and some files

Git tracks **files**, not empty folders. A tray with nothing in it doesn't exist as far as Git is concerned. So put one file in each.

In the Explorer, create these (right-click → **New Folder** / **New File**):

| Path | Contents |
|---|---|
| `README.md` | `# Pizza Station` |
| `docs/sauce.md` | `Sauce: tomato` |
| `data/veggies.md` | `Veggies: none yet` |
| `app/cheese.md` | `Cheese: ???` |

Save each file (**Ctrl+S** / **Cmd+S**).

Now look at Source Control: the files show up under **Changes** with a green **U** (untracked). Git has noticed them but isn't tracking them yet. That's Step 4.

> **See the hidden `.git` folder (optional):** on Windows, File Explorer → **View → Show → Hidden items**. On macOS, in Finder press **Cmd+Shift+.** (full stop).

---

## ✅ Self-check

- [ ] The bottom-left of VS Code shows `main`
- [ ] My folder has `docs/`, `data/` and `app/`, each with a file
- [ ] Source Control lists my files as **U** (untracked)
- [ ] I can explain `mkdir` vs `git init`

Next: [Step 4: Staging and committing](04-staging-and-committing.md)
