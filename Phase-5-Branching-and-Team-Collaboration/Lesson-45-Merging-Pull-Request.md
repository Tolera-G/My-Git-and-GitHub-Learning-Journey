# Lesson 45: Merging Pull Requests and Understanding Merge Strategies

## 1. Learning Objectives

By the end of this lesson, you should be able to:

- Explain what merging a Pull Request means.
- Understand the three GitHub merge strategies.
- Compare merge commit, squash and merge, and rebase and merge.
- Merge branches using Git commands.
- Delete branches after successful merging.

## 2. What Is Merging?

Merging is the process of integrating changes from one branch into another.

For example:

- `main`: The target branch.
- `feature/login-page`: The source branch.

When the feature is ready and approved, its changes can be integrated into `main`.

## 3. Three GitHub Merge Strategies

### A. Merge Commit

A merge commit combines the changes from two branches and creates a new commit connecting their histories.

Example:

```text
      A---B
     /     \
C---D       M
     \     /
      E---F
```

Advantages:
- Preserves branch history.
- Shows where branches were integrated.
- Maintains individual commits.

### B. Squash and Merge

Squash and merge combines multiple commits from a feature branch into one commit on the target branch.

Example:

Before:

```text
Commit 1: Create login form
Commit 2: Fix login form
Commit 3: Adjust spacing
Commit 4: Fix validation
```

After:

```text
A---B---S
```

Advantages:
- Produces a cleaner history.
- Groups related changes together.
- Avoids many small commits in the target branch.

### C. Rebase and Merge

Rebase and merge replays individual commits from the feature branch onto the target branch.

Example:

Before:

```text
      C---D  feature
     /
A---B        main
```

After:

```text
A---B---C'---D'  main
```

Advantages:
- Produces a linear history.
- Preserves individual changes as separate commits.
- Avoids creating a merge commit.

Rebase creates new commit identities because commits are recreated.

## 4. Comparing Merge Strategies

| Strategy | Merge Commit | Result |
|---|---|---|
| Merge commit | Yes | Preserves branch history |
| Squash and merge | No | Combines changes into one commit |
| Rebase and merge | No | Replays individual commits |

Repository settings and branch protection rules may restrict available strategies.

## 5. Merging Branches Using Git

You can merge branches directly from the terminal.

### Step 1: Switch to the target branch

```bash
git switch main
```

### Step 2: Update the target branch

```bash
git pull origin main
```

### Step 3: Merge the feature branch

```bash
git merge feature/login-page
```

### Step 4: Push the updated branch

```bash
git push origin main
```

These commands integrate the feature branch into the local main branch and publish the resulting changes.

In collaborative projects, follow the team's Pull Request and branch protection policies.

## 6. Deleting Branches After Merging

After a successful merge, you can delete branches that are no longer needed.

### Delete a local branch

```bash
git branch -d feature/login-page
```

### Delete a remote branch

```bash
git push origin --delete feature/login-page
```

GitHub also provides an option to delete the source branch after merging a Pull Request.

Deleting the branch does not normally remove its already-merged changes.

## 7. When Should You Use Each Strategy?

- Merge commit: When preserving the full branch history is important.
- Squash and merge: When you want a concise history with one commit per feature.
- Rebase and merge: When you want a linear history with individual commits preserved.

The appropriate strategy depends on the project's collaboration rules.

## 8. Practical Exercise

### Step 1: Update main

```bash
git switch main
git pull origin main
```

### Step 2: Create a feature branch

```bash
git switch -c feature/merge-pr-practice
```

### Step 3: Create merge-pr-practice.md

```markdown
# Pull Request Merge Practice

## Objective
Understand how Pull Requests are merged.

## Topics
- Merge commit
- Squash and merge
- Rebase and merge
```

### Step 4: Commit and push

```bash
git add .
git commit -m "Add pull request merge practice"
git push -u origin feature/merge-pr-practice
```

### Step 5: Create a Pull Request

On GitHub:

- Base branch: main
- Compare branch: feature/merge-pr-practice

Create the Pull Request.

### Step 6: Merge the Pull Request

Choose Squash and merge if available.

Confirm the merge.

### Step 7: Update local main

```bash
git switch main
git pull origin main
```

### Step 8: Inspect commit history

```bash
git log --oneline --graph --all
```

### Step 9: Delete the local feature branch

```bash
git branch -d feature/merge-pr-practice
```

If the remote branch has not already been deleted:

```bash
git push origin --delete feature/merge-pr-practice
```

## 9. Key Takeaways

- Merging integrates changes from one branch into another.
- GitHub supports three main merge strategies.
- Merge commits preserve branch history.
- Squash and merge combines changes into one commit.
- Rebase and merge produces a linear history.
- Git supports merging directly through the terminal.
- Unnecessary feature branches can be deleted after merging.

## 10. Lesson Completion Checklist

- [ ] Understand merging.
- [ ] Explain the three merge strategies.
- [ ] Compare their differences.
- [ ] Merge a feature branch.
- [ ] Inspect the commit history.
- [ ] Delete the merged feature branch.

**Next Lesson:** Understanding and Resolving Merge Conflicts.