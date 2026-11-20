# Lesson 39: Switching Branches in Git

## 1. Introduction

Switching branches means moving from one Git branch to another without creating a new branch.

It allows developers to work on different features or versions of a project independently.

## 2. Important Commands

| Command | Purpose |
|---|---|
| `git branch` | Lists local branches |
| `git switch main` | Switches to main |
| `git switch feature-login` | Switches to feature-login |
| `git switch -c new-branch` | Creates and switches to a new branch |
| `git checkout main` | Older alternative for switching branches |

## 3. How It Works

When switching branches, Git updates the working directory to reflect the selected branch's committed state.

Git may prevent switching when uncommitted changes would be overwritten.

## 4. Practical Example

```bash
git branch
git switch -c practice-branch
git branch
git switch main
git switch practice-branch
```

## 5. Key Takeaways

- A branch provides an independent line of development.
- `git switch` moves between branches.
- `git switch -c` creates and switches to a branch.
- Git protects uncommitted work from being accidentally overwritten.

## 6. Practice Questions

1. Which command switches to the main branch?
2. What is the difference between `git switch main` and `git switch -c main`?
3. What happens when you switch branches?
4. Why might Git prevent you from switching branches?