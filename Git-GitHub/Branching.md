# Git Branching

## What is a Branch?

A branch in Git is an independent line of development. It allows you to work on features, fixes, or experiments without affecting the main codebase.

By default, Git creates a branch called:

```text id="b0r1ch"
main
```

---

## Why Branching is Important

* Work on features separately
* Avoid breaking main code
* Enable parallel development
* Safe experimentation
* Better team collaboration

---

## How Git Stores Branches

A branch is just a pointer to a commit.

```text id="c1d2e3"
main → commit A → commit B → commit C
```

When you create a new branch, Git creates another pointer:

```text id="f4g5h6"
main → commit C
feature → commit C
```

---

## Creating a Branch

```bash id="i7j8k9"
git branch feature-login
```

---

## Viewing Branches

```bash id="l1m2n3"
git branch
```

Current branch is marked with `*`

---

## Switching Branches

### Old way:

```bash id="o4p5q6"
git checkout feature-login
```

### Modern way:

```bash id="r7s8t9"
git switch feature-login
```

---

## Creating + Switching at Once

```bash id="u1v2w3"
git checkout -b feature-login
```

or

```bash id="x4y5z6"
git switch -c feature-login
```

---

## Deleting a Branch

### Safe delete:

```bash id="a7b8c9"
git branch -d feature-login
```

### Force delete:

```bash id="d1e2f3"
git branch -D feature-login
```

---

## Renaming a Branch

```bash id="g4h5i6"
git branch -m new-branch-name
```

---

## Branch Workflow Example

### Step 1: Start from main

```bash id="j7k8l9"
git switch main
```

### Step 2: Create feature branch

```bash id="m1n2o3"
git switch -c feature-login
```

### Step 3: Work and commit

```bash id="p4q5r6"
git add .
git commit -m "Add login page"
```

### Step 4: Switch back to main

```bash id="s7t8u9"
git switch main
```

---

## Difference Between Branch and Commit

| Concept | Meaning            |
| ------- | ------------------ |
| Commit  | Snapshot of code   |
| Branch  | Pointer to commits |

---

## HEAD in Git

HEAD points to the current branch or commit.

```text id="v1w2x3"
HEAD → main → latest commit
```

When switching branches, HEAD moves.

---

## Merging Branches (Preview)

To combine changes:

```bash id="y4z5a6"
git merge feature-login
```

---

## Types of Branching Strategies

### 1. Feature Branching

Each feature has its own branch.

### 2. Hotfix Branching

Used for urgent production fixes.

### 3. Release Branching

Used for preparing production releases.

---

## Example Real Workflow

```bash id="b7c8d9"
main
 ├── feature/login
 ├── feature/payment
 └── hotfix/security-patch
```

---

## Common Mistakes

* Working directly on `main`
* Forgetting to switch branches
* Not pulling latest `main` before creating branch
* Long-lived feature branches

---

## Best Practices

* Always branch from updated `main`
* Keep branches small and focused
* Merge frequently
* Delete merged branches
* Use meaningful branch names

Examples:

```text id="e1f2g3"
feature/user-auth
bugfix/login-error
hotfix/security-fix
```

---

## Summary Commands

```bash id="h4i5j6"
git branch
git switch branch-name
git switch -c new-branch
git checkout -b new-branch
git branch -d branch-name
git branch -m new-name
```

---

## What Next?

Next topic:

👉 **Git-Merging.md** (how branches combine + conflict resolution)

