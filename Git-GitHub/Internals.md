# Git Internals

## What are Git Internals?

Git internals explain how Git actually stores and manages data behind the scenes.

Instead of storing files normally, Git uses a **content-addressed object database**.

---

## Why Git Internals Matter

* Understand how Git really works
* Debug complex issues
* Prepare for DevOps interviews
* Improve Git confidence
* Avoid “magical” usage

---

## The `.git` Directory

Every Git repository has a hidden folder:

```text id="g1i2t3"
.git/
```

This contains everything Git needs.

Important parts:

```text id="g4i5t6"
.git/
├── objects/
├── refs/
├── HEAD
├── config
```

---

## Core Git Objects

Git stores everything as 4 main object types:

### 1. Blob (File Data)

A blob stores **file content only** (no filename).

Example:

```text id="b1l2o3"
Hello World
```

---

### 2. Tree (Directory Structure)

A tree represents folders and file names.

Example:

```text id="t1r2e3"
project/
 ├── app.py
 └── readme.md
```

---

### 3. Commit (Snapshot)

A commit points to:

* Tree (project structure)
* Parent commit
* Author info
* Message

Example:

```text id="c1o2m3"
Commit → Tree → Blobs
```

---

### 4. Tag (Pointer to commit)

A tag points to a specific commit (usually a release).

---

## Git Object Flow

```text id="f1l2o3w"
File → Blob → Tree → Commit → Branch
```

---

## How Git Stores Data

Git uses **SHA-1 hashes** to identify objects.

Example:

```text id="h1a2s3h"
e4f3c2a91b...
```

Each object is stored by its hash.

---

## Inspecting Git Objects

### View object type

```bash id="o1b2j3"
git cat-file -t <hash>
```

---

### View object content

```bash id="o4b5j6"
git cat-file -p <hash>
```

---

## HEAD in Git

HEAD points to the current branch or commit.

```text id="h1e2a3d"
HEAD → main → latest commit
```

---

## Branch Internals

A branch is just a file storing a commit hash.

Example:

```text id="b1r2a3n4"
refs/heads/main → e4f3c2a
```

---

## Commit Structure

A commit contains:

```text id="c1s2t3"
tree:    abc123
parent:  def456
author:  user
message: "commit message"
```

---

## How Git Tracks Changes

Git does NOT store differences like traditional systems.

Instead:

* Stores full snapshots (efficiently via compression)
* Reuses unchanged objects

---

## Staging Area Internals

The staging area is stored in:

```text id="i1n2d3e4"
.git/index
```

It tracks:

* Files added via `git add`
* Changes ready for commit

---

## Garbage Collection

Git automatically cleans unused objects:

```bash id="g1c2l3n"
git gc
```

---

## Reflog (Hidden History)

Git keeps history of HEAD movements:

```bash id="r1e2f3l4"
git reflog
```

This can recover lost commits.

---

## Recover Lost Commits

If you accidentally delete something:

```bash id="r4e5c6o"
git reflog
git checkout <commit>
```

---

## Packed Objects

To save space, Git compresses objects:

```text id="p1a2c3k"
.git/objects/pack/
```

---

## Git Storage Efficiency

Git is efficient because:

* Deduplicates files
* Compresses objects
* Reuses unchanged blobs
* Stores only snapshots logically

---

## Real Example Flow

### Step 1: Create file

```text id="f1i2l3"
app.py
```

### Step 2: Add to Git

```bash id="a1d2d3"
git add app.py
```

### Step 3: Create blob

```text id="b1l2o3b"
Blob(hash)
```

### Step 4: Create tree

```text id="t1r2e3e"
Tree → app.py → blob
```

### Step 5: Commit

```text id="c1o2m3m"
Commit → tree
```

---

## Common Misconceptions

* Git stores file differences ❌
* Git stores snapshots ✔
* Branch is a folder ❌
* Branch is a pointer ✔
* Commit changes files directly ❌
* Commit creates new object graph ✔

---

## Why This Matters in DevOps

Understanding internals helps with:

* Debugging CI/CD failures
* Fixing corrupted repos
* Advanced Git operations
* Interview questions
* Performance optimization

---

## Summary

Git is:

* A key-value object store
* Based on SHA hashes
* Built on blobs, trees, commits, tags
* Efficient due to compression and reuse

---
