# Git Tags

## What are Git Tags?

Tags are used to mark specific points in Git history, usually for **releases or versions**.

Think of tags like bookmarks in your project history.

---

## Why Tags are Important

* Mark release versions (v1.0, v2.0)
* Track stable code points
* Easy rollback reference
* Used in CI/CD pipelines
* Better project versioning

---

## Types of Tags

### 1. Lightweight Tag

Just a pointer to a commit.

```bash id="l1t2a3"
git tag v1.0
```

---

### 2. Annotated Tag (Recommended)

Stores extra information like:

* Tagger name
* Date
* Message

```bash id="a1n2t3"
git tag -a v1.0 -m "First stable release"
```

---

## Viewing Tags

```bash id="v1t2g3"
git tag
```

Output:

```text id="t1a2g3"
v1.0
v1.1
v2.0
```

---

## Show Tag Details

```bash id="s1h2o3"
git show v1.0
```

---

## Tagging a Specific Commit

```bash id="t1c2m3"
git tag v1.0 abc1234
```

Where:

* `abc1234` = commit hash

---

## Pushing Tags to GitHub

### Push a single tag:

```bash id="p1u2s3"
git push origin v1.0
```

---

### Push all tags:

```bash id="p4u5s6"
git push origin --tags
```

---

## Deleting Tags

### Delete local tag:

```bash id="d1l2t3"
git tag -d v1.0
```

---

### Delete remote tag:

```bash id="d4r5t6"
git push origin --delete v1.0
```

---

## Tag Workflow Example

### Step 1: Commit changes

```bash id="c1o2m3"
git add .
git commit -m "Prepare release"
```

---

### Step 2: Create tag

```bash id="t1a2g3b"
git tag -a v1.0 -m "Release version 1.0"
```

---

### Step 3: Push code and tag

```bash id="p1u2s3b"
git push origin main
git push origin v1.0
```

---

## Semantic Versioning (Important)

Tags usually follow this format:

```text id="v1v2v3"
MAJOR.MINOR.PATCH
```

### Examples:

* v1.0.0 → First release
* v1.1.0 → New feature added
* v1.1.1 → Bug fix

---

## Git Tags vs Branches

| Feature            | Tags            | Branches           |
| ------------------ | --------------- | ------------------ |
| Mutable            | No              | Yes                |
| Purpose            | Release marking | Active development |
| History changes    | No              | Yes                |
| Moves with commits | No              | Yes                |

---

## Checking Out Tags

You can view a tag:

```bash id="c1h2e3"
git checkout v1.0
```

⚠️ This puts you in "detached HEAD" state.

To work safely:

```bash id="c4b5r6"
git switch -c fix-from-v1.0
```

---

## Common Use in DevOps

Tags are widely used in:

* CI/CD pipelines
* Docker image versioning
* Production deployments
* Release automation

Example:

```text id="d1e2p3"
v1.0 → production release
v1.1 → staging release
```

---

## Viewing Tags with Commit History

```bash id="g1r2a3"
git log --oneline --decorate
```

---

## Common Mistakes

* Forgetting to push tags to remote
* Using tags instead of branches for development
* Not using annotated tags for releases
* Overwriting existing tags accidentally

---

## Best Practices

* Always use annotated tags for releases
* Follow semantic versioning
* Push tags with releases
* Keep tags meaningful and consistent
* Use tags in CI/CD pipelines

---

## Summary Commands

```bash id="s1u2m3"
git tag
git tag -a v1.0 -m "message"
git tag -d v1.0
git push origin v1.0
git push origin --tags
git show v1.0
```

---

## What Next?

Next topic:

👉 **Git-Internals.md** (how Git actually works under the hood: blobs, trees, commits)

