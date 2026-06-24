# Git Rebase

## What is Rebase?

Rebase is a Git operation that moves or “replays” commits from one branch onto another.

Instead of creating a merge commit, rebase creates a **linear history**.

---

## Why Rebase is Used

* Cleaner project history
* No extra merge commits
* Easier to read commit logs
* Better for professional workflows

---

## Merge vs Rebase (Core Idea)

### Merge

```text id="m1e2r3"
A --- B --- C (main)
      \     
       D --- E (feature)

After merge:
A --- B --- C --- M (merge commit)
              \ 
               D --- E
```

---

### Rebase

```text id="r1e2b3"
A --- B --- C (main)
              \
               D --- E (feature)

After rebase:
A --- B --- C --- D' --- E'
```

👉 Commits are rewritten on top of main

---

## Basic Rebase Command

```bash id="b1a2s3"
git rebase main
```

Run this while inside feature branch.

---

## Step-by-Step Rebase Workflow

### Step 1: Switch to feature branch

```bash id="s1w2b3"
git switch feature-login
```

---

### Step 2: Rebase onto main

```bash id="r4b5s6"
git rebase main
```

---

### Step 3: Switch back to main

```bash id="m7a8i9"
git switch main
```

---

### Step 4: Merge (fast-forward)

```bash id="m1e2r3b"
git merge feature-login
```

---

## What is Interactive Rebase?

Interactive rebase lets you edit commits.

```bash id="i1r2b3"
git rebase -i HEAD~3
```

---

## Interactive Rebase Options

When you run:

```text id="o1p2t3"
pick   abc123 Add login
pick   def456 Fix bug
pick   ghi789 Update UI
```

You can:

| Command | Meaning                 |
| ------- | ----------------------- |
| pick    | keep commit             |
| reword  | edit message            |
| squash  | combine commits         |
| fixup   | combine without message |
| drop    | remove commit           |

---

## Squashing Commits Example

Before:

```text id="s1q2u3"
commit A - Add login
commit B - Fix typo
commit C - Fix UI
```

After squash:

```text id="s4q5u6"
commit A - Add login feature (clean single commit)
```

---

## Handling Rebase Conflicts

If conflict occurs:

```text id="c1o2n3"
<<<<<<< HEAD
main code
=======
feature code
>>>>>>> feature-login
```

---

### Fix it manually, then:

```bash id="r1e2s3b"
git add .
git rebase --continue
```

---

### Abort rebase:

```bash id="a1b2o3"
git rebase --abort
```

---

## Golden Rule of Rebase

⚠️ Never rebase commits that are already pushed to shared repositories.

Why:

* It rewrites history
* Breaks other developers' repos

---

## Safe Rebase Usage

Good cases:

* Local feature branches
* Before merging into main
* Cleaning commit history

Bad cases:

* Shared branches
* Public repositories with collaborators

---

## Rebase vs Merge Decision

| Situation            | Use    |
| -------------------- | ------ |
| Clean history needed | Rebase |
| Team collaboration   | Merge  |
| Public branch        | Merge  |
| Local feature branch | Rebase |

---

## Example Real Workflow

```bash id="w1o2r3b"
git switch feature-login
git fetch origin
git rebase origin/main
git switch main
git merge feature-login
git push origin main
```

---

## Common Mistakes

* Rebasing shared branches
* Not resolving conflicts properly
* Losing commits due to drop
* Confusing rebase with merge

---

## Best Practices

* Rebase locally only
* Keep commits small
* Use interactive rebase to clean history
* Always test after rebase

---

## Summary Commands

```bash id="s1u2m3"
git rebase main
git rebase -i HEAD~n
git rebase --continue
git rebase --abort
```

---

## What Next?

Next topic:

👉 **Git-Stashing.md** (temporary saving changes without committing)

