# Lesson 40: Renaming and Deleting Branches in Git

## Learning Objectives

By the end of this lesson, you should understand how to rename and delete local and remote branches.

## 1. Renaming Local Branches

Rename the current branch:

```bash
git branch -m new-name
```

Rename another branch:

```bash
git branch -m old-name new-name
```

## 2. Deleting Local Branches

Safely delete a merged branch:

```bash
git branch -d branch-name
```

Force-delete a branch:

```bash
git branch -D branch-name
```

## 3. Renaming Remote Branches

Git does not automatically rename remote branches when local branches are renamed.

To rename a remote branch:

```bash
git branch -m old-name new-name
git push -u origin new-name
git push origin --delete old-name
```

## 4. Deleting Remote Branches

```bash
git push origin --delete branch-name
```

## 5. Useful Commands

| Command | Description |
|---|---|
| `git branch` | List local branches |
| `git branch -a` | List all branches |
| `git branch -m` | Rename a branch |
| `git branch -d` | Safely delete a local branch |
| `git branch -D` | Force-delete a local branch |
| `git fetch --prune` | Remove stale remote-tracking references |

## Key Takeaways

- Local and remote branches are managed separately.
- Always switch away from a branch before deleting it.
- Prefer safe deletion with `-d`.
- Use force deletion only when you understand the consequences.
- Renaming a local branch does not automatically rename its remote counterpart.

## Practical Exercise

1. Create a branch named `practice-rename`.
2. Rename it to `practice-branch-renamed`.
3. Verify the new name.
4. Switch to `main`.
5. Delete the practice branch.
6. Verify that it no longer exists.

**Lesson Status:** Completed after practical exercise.