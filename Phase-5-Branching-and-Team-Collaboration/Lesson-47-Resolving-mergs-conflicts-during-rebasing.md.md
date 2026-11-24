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

Cancels the ongoing rebase and attempts to restore the original branch state.

## 7. Merge Conflicts vs Rebase Conflicts

| Merge | Rebase |
|---|---|
| Combines branch histories | Replays commits |
| Uses `git merge` | Uses `git rebase` |
| Resolve conflicts and stage files | Resolve conflicts and stage files |
| Complete using `git commit` | Continue using `git rebase --continue` |
| Can create a merge commit | Recreates commits with new identities |

## 8. Practical Exercise

### Step 1: Create a base branch

```bash
git switch main
git switch -c rebase-practice-main
```

Create `rebase-message.txt`:

```text
Welcome to our Git learning community!
```

Commit:

```bash
git add rebase-message.txt
git commit -m "Add original rebase practice message"
```

### Step 2: Create a feature branch

```bash
git switch -c rebase-practice-feature
```

Change the file:

```text
Welcome to our software engineering community!
```

Commit:

```bash
git add rebase-message.txt
git commit -m "Update message from feature branch"
```

### Step 3: Update the base branch

```bash
git switch rebase-practice-main
```

Change the same file:

```text
Welcome to our updated Git community!
```

Commit:

```bash
git add rebase-message.txt
git commit -m "Update message from main branch"
```

### Step 4: Start the rebase

```bash
git switch rebase-practice-feature
git rebase rebase-practice-main
```

Git should report a conflict.

### Step 5: Inspect the conflict

```bash
git status
```

Open the affected file and examine the competing versions.

### Step 6: Resolve the conflict

Choose the final content:

```text
Welcome to our updated Git and software engineering community!
```

Remove conflict markers and save.

### Step 7: Stage the resolved file

```bash
git add rebase-message.txt
```

### Step 8: Continue the rebase

```bash
git rebase --continue
```

### Step 9: Inspect the commit history

```bash
git log --oneline --graph --all
```

Observe how the feature commit has been replayed onto the updated base branch.

## 9. Key Takeaways

- Rebase replays commits onto another branch.
- Conflicts occur when Git cannot automatically apply a commit.
- Rebase can encounter multiple conflicts during the same operation.
- `git rebase --continue` resumes the operation.
- `git rebase --skip` omits the current commit.
- `git rebase --abort` cancels the operation.
- Rebasing changes commit identities.
- Avoid rebasing shared branches without coordinating with teammates.

## 10. Lesson Completion Checklist

- [ ] Understand Git rebase.
- [ ] Explain why rebase conflicts happen.
- [ ] Identify conflict markers.
- [ ] Create a rebase conflict.
- [ ] Resolve the conflict manually.
- [ ] Continue the rebase.
- [ ] Inspect the final commit history.

**Next Lesson:** Understanding Detached HEAD State in Git.