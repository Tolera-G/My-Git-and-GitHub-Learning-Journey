# Lesson 47: Resolving Merge Conflicts During Rebasing

## 1. Learning Objectives

By the end of this lesson, you should be able to:

- Explain how Git rebase works.
- Understand why conflicts happen during rebasing.
- Identify conflicts during a rebase.
- Understand conflict markers during rebasing.
- Resolve conflicts manually.
- Continue, skip, or abort a rebase.

## 2. What Is Git Rebase?

Git rebase moves or replays commits from one branch onto another branch.

For example:

```text
Before:

      C  feature
     /
A---B        main
```

After rebasing feature onto main:

```text
A---B---C'  feature
```

The original commit C is recreated as C' with a new commit identity.

Command:

```bash
git rebase main
```

## 3. Why Do Conflicts Happen During Rebasing?

Conflicts happen when Git cannot automatically apply a commit during the rebase process.

Example:

- Developer A changes a line in the main branch.
- Developer B changes the same line in a feature branch.
- Developer B attempts to rebase onto main.

Git cannot automatically determine the correct final content.

Therefore, it pauses the rebase and asks the developer to resolve the conflict.

## 4. Understanding Conflict Markers During Rebase

Example:

```text
<<<<<<< HEAD
Welcome to our updated Git community!
=======
Welcome to our software engineering community!
>>>>>>> abc1234 (Update announcement)
```

During a rebase:

- `HEAD` represents the updated base branch at the current replay point.
- The incoming commit represents the feature commit being replayed.
- `=======` separates the competing versions.

The labels differ in meaning from what developers often expect during a normal merge.

## 5. Resolving Rebase Conflicts

Follow these steps:

1. Start the rebase.
2. Identify conflicted files.
3. Open the affected files.
4. Examine the competing changes.
5. Choose the correct final content.
6. Remove conflict markers.
7. Save the files.
8. Stage resolved files.
9. Continue the rebase.
10. Repeat if additional conflicts appear.

## 6. Important Git Rebase Commands

### Start a rebase

```bash
git rebase main
```

Replays the current branch's commits onto main.

### Check repository status

```bash
git status
```

Identifies unresolved conflicts and the current rebase state.

### Inspect differences

```bash
git diff
```

Displays unresolved differences.

### Stage resolved files

```bash
git add filename
```

Marks the manually resolved content as staged.

### Continue the rebase

```bash
git rebase --continue
```

Continues replaying commits after resolving conflicts.

### Skip the current commit

```bash
git rebase --skip
```

Skips the commit currently being replayed. This omits its changes from the resulting history.

### Abort the rebase

```bash
git rebase --abort
```
