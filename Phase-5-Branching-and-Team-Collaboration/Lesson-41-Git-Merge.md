# Lesson 41: Git Merge — Combining Changes from Different Branches

## 1. Learning Objectives

- Understand Git merging.
- Merge one branch into another.
- Understand fast-forward merges.
- Understand three-way merges.
- Recognize merge conflicts.
- Verify successful merges.

## 2. What Is Git Merge?

Git merge combines changes from different branches into the currently checked-out branch.

Example:

```bash
git switch main
git merge feature-login
```

This integrates changes from `feature-login` into `main`.

## 3. Types of Merging

### Fast-Forward Merge

Occurs when the destination branch has not developed new commits since the feature branch was created.

Git moves the destination branch pointer forward without creating a new merge commit.

### Three-Way Merge

Occurs when both branches have developed independently.

Git uses:
- Common ancestor commit.
- Latest destination branch commit.
- Latest incoming branch commit.

Git creates a merge commit connecting both histories.

## 4. Basic Merge Workflow

```bash
git branch
git switch main
git merge feature-login
```

## 5. Merge Conflicts

A merge conflict occurs when Git cannot automatically reconcile changes from different branches.

Conflict markers:

```text
<<<<<<< HEAD
Current branch changes
=======
Incoming branch changes
>>>>>>> feature-login
```

Resolution:

1. Open the affected file.
2. Choose or combine the changes.
3. Remove conflict markers.
4. Save the file.
5. Stage the resolved file.
6. Complete the merge.

```bash
git add filename
git commit
```

## 6. Useful Commands

| Command | Description |
|---|---|
| `git merge branch-name` | Merge another branch |
| `git merge --abort` | Abort an unfinished merge |
| `git status` | Check repository status |
| `git log --oneline --graph --all` | Visualize commit history |
| `git show --stat` | Inspect commit changes |

## 7. Practical Exercise

1. Switch to `main`.
2. Create `feature/first-merge`.
3. Create `first-merge.txt`.
4. Add and commit the file.
5. Switch back to `main`.
6. Merge the feature branch.
7. Verify that the file exists in `main`.
8. Inspect the commit history.

## 8. Key Takeaways

- Git merge combines changes from different branches.
- The currently checked-out branch receives the changes.
- Fast-forward merges move a branch pointer forward.
- Three-way merges create a merge commit.
- Merge conflicts require manual resolution.
- Always inspect your repository status after merging.

**Lesson Status:** Complete after practical exercise.