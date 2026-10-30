# Step 2: The pizza analogy

**Goal:** Learn the map. Every Git idea in this workshop is a part of baking and serving a pizza. Come back to this page whenever a word feels abstract.

---

## Build the pizza, one piece at a time

| Pizza world | Git world |
|---|---|
| **Pizza prep station** | Your **repository** (repo) |
| Each **tray** (sauce, veggie, cheese) | A **directory** (folder) in your repo |
| Sauce tray | `docs/` |
| Veggie tray | `data/` |
| Cheese tray | `app/` |
| **Pizza base** on the counter | The **staging area** |
| **Toppings** | **Files** |
| **Baking** the pizza | **Committing** a file to your repo |
| **Kitchen order ticket** (every pizza baked, and when) | The **log** (history) |
| **Unnecessary items** (flour bags, the box) | **`.gitignore`** |
| **Individual mini pizzas**, each person tops their own | **Branches** |
| Everyone's toppings go onto the **communal family pizza** | **Merging** branches |
| Baking the merged pizza | A **merge commit** |
| Mom and Dad both want a different cheese, but only one fits | A **merge conflict** |
| Fixing a pizza baked long ago (you can't un-bake it, so you bake a corrected one) | **Reverting** a commit |
| **Dining table** | The **remote repository** (GitHub) |

---

## The same thing as a picture

```
        PREP STATION (your computer)                    DINING TABLE (GitHub)
┌───────────────────────────────────────────┐        ┌──────────────────────┐
│  trays          pizza base       oven     │        │                      │
│  (working   →   (staging    →   (local    │ push → │   remote repository  │
│  directory)      area)           history) │ ← pull │       (origin)       │
└───────────────────────────────────────────┘        └──────────────────────┘
   edit files      git add          git commit
```

Read it left to right:

1. You **edit** files in your trays (the **working directory**).
2. You put the toppings you want onto the base (**stage** them with `git add`).
3. You **bake** them (`git commit`) and the pizza goes into your history.
4. You carry the pizza to the dining table (`git push`) so everyone else can have some.
5. When someone else puts a pizza on the table, you bring it back to your station (`git pull`).

---

## How you'll use it

You'll meet each row of the table in order:

- Steps 3 to 5 cover the **prep station, trays, base, toppings, baking, order ticket**.
- Steps 6 and 7 cover the **mini pizzas, the communal pizza, and arguments over cheese**.
- Step 8 covers **leaving things off the table**.
- Steps 9 to 12 cover the **dining table**, and how to share your pizza with a whole restaurant of strangers.

---

## ✅ Checkpoint

- [ ] I can say what a **repository**, a **commit** and a **branch** are in pizza terms
- [ ] I know the staging area is the **pizza base** where toppings wait before baking

Next: [Step 3: Repository and directories](03-repository-and-directories.md)
