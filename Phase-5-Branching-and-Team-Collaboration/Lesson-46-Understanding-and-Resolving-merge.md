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

