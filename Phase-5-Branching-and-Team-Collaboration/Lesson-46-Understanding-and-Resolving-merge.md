# Lesson 46: Understanding and Resolving Merge Conflicts

## 1. Learning Objectives

By the end of this lesson, you should be able to:

- Explain what a merge conflict is.
- Identify common causes of merge conflicts.
- Understand Git conflict markers.
- Explain three-way merging.
- Resolve conflicts manually.
- Complete or abort a merge operation.

## 2. What Is a Merge Conflict?

A merge conflict occurs when Git cannot automatically combine changes from different branches.

For example, two developers modify the same line differently.

Original version:

```text
Welcome to our website.
```

Developer A:

```text
Welcome to our new website.
```

Developer B:

```text
Welcome to our amazing website.
```

Git cannot automatically decide which version should be kept.

Therefore, it asks the developer to resolve the conflict.

## 3. Common Causes of Merge Conflicts

| Situation | Explanation |
|---|---|
| Same line modified | Different changes are made to the same line |
| Conflicting changes | Changes overlap and cannot be automatically combined |
| File deleted and modified | One branch deletes a file while another modifies it |
| Conflicting renames | The same file is renamed differently |

Note: Modifying the same file does not automatically cause a conflict. Git can combine independent changes.

## 4. Understanding Conflict Markers

When Git encounters a content conflict, it may insert markers into the affected file.

Example:

```text
<<<<<<< HEAD
Welcome to our new website.
=======
Welcome to our amazing website.
>>>>>>> feature/teammate-update
```

### Meaning of each marker

- `<<<<<<< HEAD`: Beginning of the current branch's version.
- `=======`: Separates the competing versions.
- `>>>>>>> branch-name`: End of the incoming branch's version.

These markers help developers identify the conflicting content.

## 5. Understanding Three-Way Merging

Git uses three versions when performing a typical three-way merge:

1. Base: The common ancestor of both branches.
2. Ours: The version in the current branch.
3. Theirs: The version in the incoming branch.

Git compares these versions to determine how to combine changes.

When changes cannot be reconciled automatically, Git reports a conflict.

## 6. Commands Used to Resolve Conflicts

### Check repository status

```bash
git status
```

Identifies files with unresolved conflicts.

### Inspect differences

```bash
git diff
```

Displays unresolved differences in the working tree.

### Inspect the current branch version

```bash
git diff --ours
```

### Inspect the incoming branch version

```bash
git diff --theirs
```

### Mark a resolved file

```bash
git add filename
```

Stages the manually resolved file.

### Complete the merge

```bash
git commit -m "Resolve merge conflict"
```

Creates the merge commit after conflicts have been resolved.

### Abort an ongoing merge

```bash
git merge --abort
```

Attempts to cancel the merge and restore the pre-merge state.

## 7. Steps for Resolving a Merge Conflict

1. Run `git status` to identify conflicted files.
2. Open the affected files.
3. Examine both competing versions.
4. Decide what the final content should be.
5. Remove all conflict markers.
6. Save the corrected files.
7. Stage the resolved files using `git add`.
8. Check the repository status.
9. Complete the merge using `git commit`.
## 8. Practical Exercise

### Scenario

Two developers independently modify the same announcement.

Developer A:

```text
Welcome to our Git learning community!
```

Developer B:

```text
Welcome to our software engineering community!
```

### Step 1: Create Developer A's branch

```bash
git switch main
git switch -c conflict-practice-a
```

Create `message.txt`:

```text
Welcome to our Git learning community!
```

Commit:

```bash
git add .
git commit -m "Add original community announcement"
```

### Step 2: Create Developer B's branch

```bash
git switch main
git switch -c conflict-practice-b
```

Change `message.txt` to:

```text
Welcome to our software engineering community!
```

Commit:

```bash
git add .
git commit -m "Update community announcement"
```

### Step 3: Create a conflict

```bash
git switch conflict-practice-a
git merge conflict-practice-b
```

Git should report a merge conflict.

### Step 4: Inspect the conflict

```bash
git status
```

Open `message.txt` and inspect the conflict markers.

### Step 5: Resolve the conflict

Choose the final content:

```text
Welcome to our Git and software engineering learning community!
```

Remove all conflict markers.

### Step 6: Stage the resolved file

```bash
git add 05-Branching-and-Collaboration/message.txt
```

### Step 7: Complete the merge

```bash
git commit -m "Resolve community announcement merge conflict"
```

### Step 8: Inspect the history

```bash
git log --oneline --graph --all
```

Observe the merge commit and the two development branches.

## 9. Key Takeaways

- Merge conflicts happen when Git cannot automatically combine competing changes.
- Editing the same file does not always create a conflict.
- Git uses three-way merging.
- Conflict markers identify competing content.
- Developers must manually decide the final content.
- `git add` marks resolved files as staged.
- `git merge --abort` cancels an ongoing merge.
- A successful conflict resolution can be completed with a merge commit.

## 10. Lesson Completion Checklist

- [ ] Understand merge conflicts.
- [ ] Identify common causes.
- [ ] Understand conflict markers.
- [ ] Explain three-way merging.
- [ ] Create a merge conflict.
- [ ] Resolve the conflict manually.
- [ ] Complete the merge.
- [ ] Inspect the commit history.

**Next Lesson:** Understanding Merge Conflicts During Rebasing and How to Resolve Them.
