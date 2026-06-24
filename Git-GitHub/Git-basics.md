# Git Basics

## What is Git?

Git is a **distributed version control system** used to track changes in source code during software development. It allows multiple developers to work together without overwriting each other’s work.

Git was created by **Linus Torvalds** in 2005 for Linux kernel development.

---

## Why Git is Important

* Tracks changes in code
* Helps collaborate with teams
* Allows rollback to previous versions
* Supports branching and merging
* Works offline (distributed system)

---

## Git vs GitHub

| Git                  | GitHub                   |
| -------------------- | ------------------------ |
| Version control tool | Cloud hosting platform   |
| Runs locally         | Runs on the web          |
| No internet needed   | Requires internet        |
| Command-line tool    | Web UI + Git integration |

---

## Git Architecture

Git has 3 main areas:

### 1. Working Directory

Your actual project files.

### 2. Staging Area (Index)

A temporary area where changes are prepared before commit.

### 3. Repository (.git)

Stores all committed history.

```text id="g1a8xq"
Working Directory → Staging Area → Local Repository
```

---

## Basic Git Workflow

```text id="w0k9ld"
Edit Files → git add → git commit → git push
```

---

## Installing Git

### Linux (Debian/Ubuntu)

```bash id="u1k2lm"
sudo apt update
sudo apt install git
```

### Verify installation

```bash id="v9k3pl"
git --version
```

---

## First Time Setup

Set your identity:

```bash id="a1b2c3"
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Check config:

```bash id="d4e5f6"
git config --list
```

---

## Creating a Repository

### Initialize a new repo

```bash id="g7h8i9"
git init
```

This creates a hidden `.git` folder.

---

## Cloning a Repository

Copy an existing repo:

```bash id="j1k2l3"
git clone https://github.com/user/repo.git
```

---

## Checking Status

```bash id="m4n5o6"
git status
```

Shows:

* Modified files
* Staged files
* Untracked files

---

## Staging Changes

Add files to staging area:

```bash id="p7q8r9"
git add file.txt
```

Add everything:

```bash id="s1t2u3"
git add .
```

---

## Committing Changes

Save snapshot of staged changes:

```bash id="v4w5x6"
git commit -m "Initial commit"
```

Good commit messages should be:

* Clear
* Short
* Descriptive

Example:

```bash id="y7z8a9"
git commit -m "Add login feature"
```

---

## Viewing History

```bash id="b1c2d3"
git log
```

Compact view:

```bash id="e4f5g6"
git log --oneline
```

Graph view:

```bash id="h7i8j9"
git log --graph --oneline --all
```

---

## Pushing to Remote

Send changes to GitHub:

```bash id="k1l2m3"
git push origin main
```

---

## Pulling Changes

Get latest updates:

```bash id="n4o5p6"
git pull origin main
```

---

## Git Help Commands

```bash id="q7r8s9"
git help
git help commit
```

---

## Common Beginner Mistakes

* Forgetting to `git add` before commit
* Wrong commit messages
* Pushing without pulling latest changes
* Working directly on main branch

---

## Summary Workflow

```bash id="t1u2v3"
git init
git add .
git commit -m "message"
git push origin main
```

---

## What Next?

Next topics to learn:

* Branching and workflows
* Merging conflicts
* Rebase strategy
* GitHub Pull Requests

