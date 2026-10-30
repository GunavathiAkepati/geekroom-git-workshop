# Git & GitHub Workshop: Let's Bake a Pizza 🍕

Welcome! This repository **is** the workshop. Follow it from top to bottom and you'll go from "what is Git?" to sending your own **pull request** to a real, public project, which is exactly how open source works.

Everything is done from **VS Code** (with the terminal commands shown next to the buttons, so you learn both).

> **The idea:** Git is easier to understand when you stop thinking about code and start thinking about pizza. A repository is a prep station, a commit is baking, a branch is a mini pizza each family member tops their own way, and a merge conflict is Mom and Dad both putting cheese on the same pizza. Keep that picture in your head and the rest follows.

---

## What you'll learn

- What **Git** and **GitHub** are, and why every project uses them
- How to install and set up Git and VS Code (Windows and macOS)
- **Repositories**, **directories**, the **staging area** and **commits**
- Reading the **log** and **reverting** a mistake
- **Branches**, **merging**, and how to resolve a **merge conflict**
- **`.gitignore`**
- **Local vs remote** repositories: `push`, `pull`, `fetch`
- **Forking** and **cloning** someone else's project
- Opening your first **pull request**

---

## How to use this repo

1. Do the steps **in order**. Each one is a file in [`steps/`](steps/).
2. Steps 3 to 9 happen in a **practice repo called `pizza-station`** that you create yourself. It's yours, so you can't break anything here.
3. Steps 10 to 12 happen **in this repo**, through a fork and a pull request.
4. Every step ends with a ✅ **Self-check**: a short list to confirm you're good before moving on.
5. Three steps also have a 🚩 **Checkpoint**: a short timed activity to do with a partner (see [Checkpoints](#checkpoints)).
6. Stuck? Try [`reference/troubleshooting.md`](reference/troubleshooting.md). Need a word explained? See [`reference/glossary.md`](reference/glossary.md).

---

## The workshop

| # | Step | Pizza version | What you do |
|---|------|---------------|-------------|
| 0 | [Start here](steps/00-start-here.md) | The restaurant | What Git and GitHub are, make an account |
| 1 | [Install and set up](steps/01-install-and-setup.md) | Buying the kitchen equipment | Git + VS Code on Windows or macOS, set your name and email |
| 2 | [The pizza analogy](steps/02-the-pizza-analogy.md) | The whole menu | The map you'll use for everything else |
| 3 | [Repository and directories](steps/03-repository-and-directories.md) | Setting up the prep station and trays | `git init`, create folders and files |
| 4 | [Staging and committing](steps/04-staging-and-committing.md) | Toppings onto the base, then baking | Stage, commit |
| 5 | [Logs and reverting](steps/05-logs-and-reverting.md) | The kitchen order ticket | Read history, fix a bad commit |
| 6 | [Branches and merging](steps/06-branches-and-merging.md) | Mini pizzas for each family member | Branch, merge, fast-forward vs three-way |
| 7 | [Merge conflicts](steps/07-merge-conflicts.md) | Mom's Mozzarella vs Dad's Cheddar | Cause and resolve a conflict |
| 8 | [.gitignore](steps/08-gitignore.md) | Leaving the flour bags off the table | Keep files out of Git |
| 9 | [Local vs remote](steps/09-local-vs-remote.md) | Prep station vs dining table | `remote`, `push`, `pull`, `fetch` |
| 10 | [Fork and clone](steps/10-fork-and-clone.md) | Copying a restaurant's recipe | Get a copy of this repo |
| 11 | [Your first pull request](steps/11-your-first-pull-request.md) | Serving your pizza to the table | Add yourself to `participants/` |
| 12 | [A conflict in a real PR](steps/12-conflict-in-a-real-pr.md) | Everyone orders at once | Resolve a conflict on a real pull request |

---

## Checkpoints

Short timed activities. Do them with a partner and show each other your result.

| 🚩 | Where | Time | The task |
|---|---|---|---|
| [Checkpoint 3: First commit](steps/05-logs-and-reverting.md#-checkpoint-3-first-commit) | End of Step 5 | 5 min, solo + show a partner | New folder → init → `menu.txt` → commit → find the hash |
| [Checkpoint 4: Merge conflict](steps/07-merge-conflicts.md#-checkpoint-4-merge-conflict) | End of Step 7 | 3 min, pairs | Resolve `"blue"` vs `"red"` to one line; what must be removed? |
| [Checkpoint 5: Remote sync](steps/09-local-vs-remote.md#-checkpoint-5-remote-sync) | End of Step 9 | 3 min, pairs | Pick push / fetch / pull for three jobs; why doesn't a commit update GitHub? |

---

## Repository map

```
.
├── README.md                  <- you are here
├── CONTRIBUTING.md            <- the rules for pull requests to this repo
├── steps/                     <- the workshop, step by step (start with 00)
├── participants/              <- Step 11: you add your own file here
├── exercises/
│   └── cheese-order.md        <- Step 12: everyone edits this file
├── reference/
│   ├── cheatsheet.md
│   ├── glossary.md
│   └── troubleshooting.md
└── .github/
    └── PULL_REQUEST_TEMPLATE.md
```

---

## ⚠️ This repository is public

Anything you put in a pull request here is visible to **everyone**, forever, including your GitHub username and anything you write in your file. Don't include phone numbers, home addresses, passwords or anything else you wouldn't put on a poster.

Ready? Start with [Step 0](steps/00-start-here.md).
