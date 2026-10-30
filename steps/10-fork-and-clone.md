# Step 10: Fork and clone

**Goal:** Get your own copy of *this* repository so you can change it safely and propose your changes back.

---

## The big question

**What is open source?** Software whose code is public, so anyone can read it, use it, and propose improvements.

**How do you contribute to it?** You can't just edit someone else's project. You'd be changing their code. Instead you **fork** it, **clone** your fork, change it, and ask the owners to take your change with a **pull request**.

🍕 **Pizza version:** you're a customer at someone else's restaurant. You can't walk into their kitchen and change their pizza. You **copy the recipe to your own kitchen**, make your version, and **suggest it** to the restaurant.

---

## Fork a repo

- A **fork** is a **personal copy of someone else's repository** on a remote server (GitHub).
- It lets you **experiment freely** without affecting the original project.

## Clone a repo

- A **clone** is a **local copy of a remote repository**.
- When you clone, you download **all the project files and the entire commit history** to your own machine.

```
original repo (upstream)  ── fork ──►  your fork on GitHub (origin)  ── clone ──►  your computer
  Sw4ppleneel/geekroom-git-workshop       <you>/geekroom-git-workshop                 local folder
```

> **Fork** copies a repo from one GitHub account to another. **Clone** copies a repo from GitHub to your computer. You need **both** to contribute to someone else's project.

---

## 1. Fork this repository

1. Open <https://github.com/Sw4ppleneel/geekroom-git-workshop>.
2. Click **Fork** (top right).
3. Leave the name as it is, and make sure **Copy the `main` branch only** is ticked.
4. Click **Create fork**.

You land on `https://github.com/<your-username>/geekroom-git-workshop`. That's **your** copy. Notice the line under the title: *forked from Sw4ppleneel/geekroom-git-workshop*.

## 2. Clone your fork

1. On **your fork's** page, click the green **Code** button and copy the **HTTPS** URL:
   ```
   https://github.com/<your-username>/geekroom-git-workshop.git
   ```
   ⚠️ Make sure your **own username** is in there, not `Sw4ppleneel`. That's the most common mistake.
2. In VS Code open the Command Palette and run **`Git: Clone`**.
3. Paste the URL, press Enter, and choose a folder to put it in (not inside `pizza-station`!).
4. Click **Open** when VS Code offers, and **Yes, I trust the authors**.

> **Terminal version:**
> ```bash
> git clone https://github.com/<your-username>/geekroom-git-workshop.git
> cd geekroom-git-workshop
> code .
> ```

Bottom-left says `main`. Open `README.md`; it's this page's repo, on your machine.

## 3. Add `upstream`

Right now your clone knows one remote, `origin`, which is **your fork**. Add the **original** repo as a second remote called **`upstream`**, so you can pull in other people's changes later:

```bash
git remote add upstream https://github.com/Sw4ppleneel/geekroom-git-workshop.git
git remote -v
```

```
origin    https://github.com/<your-username>/geekroom-git-workshop.git (fetch)
origin    https://github.com/<your-username>/geekroom-git-workshop.git (push)
upstream  https://github.com/Sw4ppleneel/geekroom-git-workshop.git (fetch)
upstream  https://github.com/Sw4ppleneel/geekroom-git-workshop.git (push)
```

| Remote | Points to | Used for |
|---|---|---|
| `origin` | **Your fork** | You **push** here |
| `upstream` | **The original repo** | You **fetch/pull** here to stay up to date |

You can't push to `upstream`, and you shouldn't need to. Changes get there through a pull request.

---

## ✅ Self-check

- [ ] I have a fork at `github.com/<my-username>/geekroom-git-workshop`
- [ ] The repo is cloned on my machine and VS Code shows `main`
- [ ] `git remote -v` shows **both** `origin` (my fork) and `upstream` (the original)
- [ ] I can explain fork vs clone

Next: [Step 11: Your first pull request](11-your-first-pull-request.md)
