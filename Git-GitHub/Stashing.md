# Git Stashing

## What is Stashing?

Stashing is a Git feature that allows you to temporarily save uncommitted changes without making a commit.

It is useful when you need to:

* Switch branches quickly
* Fix urgent bugs
* Pull updates without committing unfinished work

---

## Why Stashing is Useful

* Avoid committing incomplete work
* Quickly switch context
* Keep working directory clean
* Prevent losing changes

---

## Basic Stash Command

```bash id="s1t2a3"
git stash
```

This saves:

* Modified tracked files
* Staged changes

---

## Stash with Message

```bash id="s4t5a6"
git stash save "work in progress login feature"
```

Modern alternative:

```bash id="s7t8a9"
git stash push -m "login feature WIP"
```

---

## View Stashes

```bash id="v1s2t3"
git stash list
```

Example output:

```text id="l1i2s3"
stash@{0}: WIP on main: login feature
stash@{1}: WIP on feature: bug fix
```

---

## Apply Stash

### Apply latest stash (without removing)

```bash id="a1p2s3"
git stash apply
```

---

### Apply specific stash

```bash id="a4p5s6"
git stash apply stash@{1}
```

---

## Pop Stash

Apply and remove from stash list:

```bash id="p1o2p3"
git stash pop
```

---

## Drop Stash

Remove a specific stash:

```bash id="d1r2o3"
git stash drop stash@{0}
```

---

## Clear All Stashes

```bash id="c1l2e3"
git stash clear
```

⚠️ This permanently deletes all stashed changes.

---

## Stash Untracked Files

By default, untracked files are not stashed.

To include them:

```bash id="u1n2t3"
git stash -u
```

---

## Stash All (Including Ignored Files)

```bash id="a7l8l9"
git stash -a
```

---

## Common Workflow Example

### Step 1: Working on feature

```bash id="w1o2r3"
git add .
```

### Step 2: Need to switch branch quickly

```bash id="s1w2i3"
git stash
git switch main
```

### Step 3: Come back later

```bash id="g1e2t3"
git switch feature-branch
git stash pop
```

---

## Viewing Stash Contents

```bash id="s1h2o3"
git stash show
```

Detailed view:

```bash id="s4h5o6"
git stash show -p
```

---

## Applying Stash Without Deleting

Useful for testing:

```bash id="a1p2p3"
git stash apply
```

---

## Real-Life Use Cases

### 1. Urgent Bug Fix

You are working on a feature but production bug appears:

```bash id="b1u2g3"
git stash
git switch main
git pull origin main
```

---

### 2. Switching Context

Move between tasks without losing progress.

---

### 3. Testing Experimental Code

Try changes without committing.

---

## Stash vs Commit

| Feature           | Stash             | Commit             |
| ----------------- | ----------------- | ------------------ |
| Saved in history  | No                | Yes                |
| Visible to others | No                | Yes                |
| Purpose           | Temporary storage | Permanent snapshot |
| Usage             | Quick switching   | Code versioning    |

---

## Common Mistakes

* Forgetting stashed changes exist
* Using stash instead of proper commit
* Losing stash by clearing accidentally
* Overusing stash instead of branches

---

## Best Practices

* Use stash only for temporary work
* Prefer branches for long tasks
* Add messages to stashes
* Regularly clean old stashes
* Check stash list before clearing

---

## Summary Commands

```bash id="s1u2m3"
git stash
git stash push -m "message"
git stash list
git stash apply
git stash pop
git stash drop
git stash clear
git stash show -p
```

---

## What Next?

Next topic:

👉 **Git-Tags.md** (versioning and releases in Git)

