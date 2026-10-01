## Git Basics — init, add, commit

**What Git is**

Git is a version control system — it tracks changes to your files over time, so you can save snapshots of your work, go back to any previous snapshot, and work on features without risking your main code. It runs locally on your machine (different from GitHub, which is a hosting service for Git repos online — that's tomorrow's topic).

**Why it matters**

Without Git: "final_v2_FINAL_reallyfinal.zip" folders, no way to undo a mistake beyond Ctrl+Z, no safe way to experiment. Git solves all of this with a structured history of changes.

**Checking installation**

```jsx
windows
https://git-scm.com/install/windows

linux
sudo apt update
sudo apt install git
``````bash
git --version
```

Confirms Git is installed and shows the version.

**One-time setup — identity**

```bash
git config --global user.name "Mohit"
git config --global user.email "mohit@example.com"
```

Every commit gets tagged with this name/email — Git needs to know who's making changes. `--global` means this applies to every repo on your machine, not just one project.

**Initializing a repository**

```bash
git init
```

Run this inside a project folder. It creates a hidden `.git` folder — that's where Git stores all the tracking history. From this point, Git starts watatching this folder for changes.

```bash
mkdir my-project
cd my-project
git init
```

**The three states in Git — core mental model**

A file in a Git project moves through three areas:

```
Working Directory  →  Staging Area  →  Repository (committed)
   (your files)          (git add)         (git commit)
```

- **Working directory** — your actual files, as you're editing them- **Staging area** — a holding zone; files you've marked as "ready to be saved" but haven't saved yet
- **Repository** — the permanent saved snapshot (a commit)

This two-step process (stage, then commit) is what confuses beginners most — but it exists so you can choose exactly *which* changes go into a commit, instead of committing everything blindly.

**Checking status**

```bash
git status
```

The most-used Git command. Shows what's changed, what's staged, what's untracked. Run this constantly — it always tells you what to do next.

**Staging changes — `git add`**

```bash
git add index.html          # stage one specific file
git add .                   # stage everything changed in current folder
git add file1.html file2.css  # stage multiple specific files
```Staging doesn't save anything permanently yet — it just marks files as "include this in the next commit."

**Committing — `git commit`**

```bash
git commit -m "Add homepage structure"
```

This takes everything in the staging area and saves it as a permanent snapshot in the repo's history. The `-m` flag lets you write the commit message inline — every commit needs a message describing what changed.

**A typical daily workflow**

```bash
git status                          # see what changed
git add .                           # stage the changes
git commit -m "Fix navbar styling"  # save the snapshot
```

**Viewing history**```bash
git log
```

Shows all commits — who made them, when, and the message. Each commit has a unique ID (a long hash) that can be used to reference it later.

```bash
git log --oneline
```

Compact version — one line per commit, easier to scan.

**Ignoring files — `.gitignore`**

```
node_modules/
.env
*.log
```

A `.gitignore` file (plain text, in the project root) tells Git which files/folders to never track — things like dependencies, secrets, or generated files that shouldn't be part of version history.

**Common mistakes**- Running `git commit` without `git add` first — nothing staged means nothing to commit
- Vague commit messages like "update" or "fix" — should describe *what* changed
- Forgetting `git init`, then wondering why `git status` says "not a git repository"
- Committing `node_modules` or other huge/generated folders because `.gitignore` wasn't set up first

**Small practice task**

- Create a new folder, run `git init`
- Create an `index.html` file, run `git status` to see it as untracked
- Stage it with `git add`, check `git status` again to see the difference
- Commit it with a clear message
- Make a small change, repeat the add → commit cycle two more times
- Run `git log --oneline` to see the full history so far# day-11
git
