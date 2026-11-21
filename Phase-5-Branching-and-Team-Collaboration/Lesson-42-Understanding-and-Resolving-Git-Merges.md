# Lesson 42: Understanding and Resolving Git Merge Conflicts

## 1. Learning Objectives

- Understand merge conflicts.
- Identify conflict markers.
- Inspect conflicting files.
- Resolve conflicts manually.
- Complete or abort a merge.

## 2. What Is a Merge Conflict?

A merge conflict happens when Git cannot automatically reconcile changes from different branches.

It commonly occurs when two branches modify the same part of a file differently.

## 3. Conflict Markers

```text
<<<<<<< HEAD
Current branch changes
=======
Incoming branch changes
>>>>>>> feature-branch
```

- `<<<<<<< HEAD`: Current branch version.
- `=======`: Separates the conflicting versions.
- `>>>>>>> feature-branch`: Incoming branch version.

## 4. Resolving Merge Conflicts

1. Run `git status` to identify conflicting files.
2. Open the affected files.
3. Choose or combine the changes.
4. Remove conflict markers.
5. Save the files.
6. Stage the resolved files.
7. Complete the merge commit.

```bash
git add filename
git commit
```

## 5. Aborting a Merge

To cancel an unfinished merge:

```bash
git merge --abort
```

## 6. Useful Commands

| Command | Purpose |
|---|---|
| `git status` | Check repository status |
| `git diff` | Inspect changes |
| `git add filename` | Stage resolved files |
| `git commit` | Complete merge |
| `git merge --abort` | Abort merge |
| `git diff --name-only --diff-filter=U` | List unresolved files |

## 7. Practical Exercise

1. Create an original file on `main`.
2. Create `feature-version-one`.
3. Modify and commit the file.
4. Create `feature-version-two` from `main`.
5. Modify the same line differently.
6. Merge version two into version one.
7. Inspect the conflict.
8. Resolve the conflict manually.
9. Stage and commit the resolution.
10. Verify the commit history.

## 8. Key Takeaways

- Git cannot always automatically combine changes.
- Conflict markers identify conflicting sections.
- HEAD identifies the current branch's version.
- Manually resolved files must be staged.
- A merge is completed by committing the resolution.
- `git merge --abort