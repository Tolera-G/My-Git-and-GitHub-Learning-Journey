# Lesson 48: Understanding Detached HEAD State in Git

**Phase:** 5 — Branching & Collaboration  
**Level:** Intermediate

## 1. Learning Objectives

By the end of this lesson, you should be able to:

- Explain the purpose of `HEAD` in Git.
- Understand Detached HEAD state.
- Recognize when Git enters Detached HEAD.
- Create a branch to preserve work.
- Return to a normal branch safely.

## 2. What Is HEAD?

`HEAD` is Git's reference to your current position in the repository.

Normally, HEAD points to the current branch, and the branch points to the latest commit.

Example:

```text
HEAD → main → Commit C3
```

When you create a new commit on `main`, the branch moves forward and HEAD follows it.

## 3. What Is Detached HEAD?

Detached HEAD occurs when HEAD points directly to a commit instead of pointing to a branch.

Example:

```bash
git switch --detach a1b2c3d
```

The repository enters Detached HEAD state.

Conceptually:

```text
HEAD → Commit C2

main → Commit C3
```

The `main` branch remains at C3, while HEAD is viewing C2.

Detached HEAD is not an error. It allows you to inspect and work from a specific historical commit.

## 4. Why Use Detached HEAD?

Detached HEAD is useful when you want to:

- Inspect an older version of your project.
- Test how an application worked in the past.
- Investigate a bug introduced by a later commit.
- Compare historical versions without moving your current branch.

To inspect your commit history:

```bash
git log --oneline
```

To switch to a specific commit:

```bash
git switch --detach COMMIT_HASH
```

Replace `COMMIT_HASH` with an actual commit hash.

## 5. The Risk of Committing in Detached HEAD

Git allows you to create commits while in Detached HEAD state.

However, these commits are not automatically attached to a branch.

If you switch away without creating a branch to preserve them, they may become difficult to locate.

### How to preserve your work

While still in Detached HEAD, execute:

```bash
git switch -c save-my-work
```

This creates a new branch at your current commit and attaches HEAD to that branch.

You can then continue working normally.

## 6. Returning to a Branch

To return to your main branch:

```bash
git switch main
```

Use the appropriate branch name if your repository uses a different name.

## 7. Important Git Commands

| Command | Purpose |
|---|---|
| `git status` | Checks whether HEAD is detached |
| `git log --oneline --decorate` | Displays commits and references |
| `git switch --detach HASH` | Enters Detached HEAD |
| `git switch -c branch-name` | Creates a branch from the current position |
| `git switch main` | Switches to the main branch |
| `git reflog` | Shows recent movements of HEAD |

## 8. Practical Exercise

1. Open your Git learning repository.
2. Check the working tree using `git status`.
3. Record your current branch using `git branch --show-current`.
4. Inspect your history using `git log --oneline --decorate -5`.
5. Select a commit hash.
6. Enter Detached HEAD using `git switch --detach HASH`.
7. Confirm the state using `git status`.
8. Create a branch using `git switch -c detached-head-practice`.
9. Confirm the new branch using `git branch`.
10. Return to your original branch.

## 9. Important Takeaways

- HEAD identifies your current position in Git.
- Normally, HEAD points to a branch.
- In Detached HEAD, HEAD points directly to a commit.
- Detached HEAD is not an error.
- Commits created in Detached HEAD are not automatically attached to a branch.
- Use `git switch -c branch-name` to preserve your work.

**Golden Rule:** If you create something valuable while in Detached HEAD, create a branch before switching away.