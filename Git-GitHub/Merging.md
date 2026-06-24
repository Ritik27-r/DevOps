# Git Merging

## What is Merging?

Merging is the process of combining changes from one branch into another branch.

Most commonly:

* feature branch → main branch

---

## Why Merging is Important

* Combines completed features
* Integrates team work
* Keeps main branch updated
* Enables collaboration

---

## Basic Merge Concept

Example:

```text id="m1a2r3"
main:    A --- B --- C
feature:         D --- E
```

After merge:

```text id="m4e5r6"
main:    A --- B --- C --- D --- E
```

---

## Types of Merges

### 1. Fast-Forward Merge

Happens when main has no new commits.

```text id="f1a2s3"
main → A → B → C
feature (ahead of main)
```

After merge:

```text id="f4a5s6"
main → A → B → C → D → E
```

No merge commit is created.

---

### 2. Three-Way Merge

Used when both branches have new commits.

```text id="t1w2m3"
      D --- E (feature)
     /
A --- B --- C (main)
```

Git creates a **merge commit**.

---

## How to Merge Branches

### Step 1: Switch to target branch

Usually `main`:

```bash id="s1t2u3"
git switch main
```

---

### Step 2: Merge feature branch

```bash id="m4r5g6"
git merge feature-login
```

---

## Merge Commit Example

```text id="c7o8m9"
Merge branch 'feature-login' into main
```

---

## Checking Merge History

```bash id="h1i2s3"
git log --oneline --graph --all
```

This shows branch structure visually.

---

## Merge Conflicts

A conflict happens when Git cannot automatically combine changes.

Example:

Both branches modify same line:

```text id="c1o2n3"
main:    Hello World
feature: Hello Git
```

Git will stop and ask you to resolve it.

---

## Conflict Markers

```text id="c4o5n6"
<<<<<<< HEAD
Hello World
=======
Hello Git
>>>>>>> feature-login
```

---

## Resolving Conflicts

### Step 1: Edit file manually

Keep correct version:

```text id="r1e2s3"
Hello Git
```

---

### Step 2: Mark resolved

```bash id="a1d2d3"
git add file.txt
```

---

### Step 3: Complete merge

```bash id="c4m5t6"
git commit
```

---

## Abort a Merge

If something goes wrong:

```bash id="b7a8c9"
git merge --abort
```

---

## Viewing Merge Status

```bash id="s9t8a7"
git status
```

---

## Merge vs Rebase (Important)

| Feature      | Merge        | Rebase         |
| ------------ | ------------ | -------------- |
| History      | Preserved    | Rewritten      |
| Commit style | Merge commit | Linear history |
| Complexity   | Easy         | Advanced       |

---

## Example Merge Workflow

```bash id="w1o2r3"
git switch main
git pull origin main
git merge feature-login
git push origin main
```

---

## Common Mistakes

* Merging without pulling latest main
* Ignoring conflict resolution
* Pushing broken merges
* Not testing after merge

---

## Best Practices

* Always pull before merging
* Keep branches small
* Resolve conflicts carefully
* Test after merge
* Delete merged branches

---

## Deleting Branch After Merge

```bash id="d1e2l3"
git branch -d feature-login
```

---

## Summary Commands

```bash id="s4u5m6"
git merge branch-name
git status
git add .
git commit
git merge --abort
```

---

## What Next?

Next topic:

👉 **Git-Rebase.md** (clean history + advanced workflow)

