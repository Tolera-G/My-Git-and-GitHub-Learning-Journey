
# Lesson 47: Understanding Merge Conflicts in Git

## 1. Introduction

A merge conflict occurs when Git cannot automatically
combine changes from different branches.

This commonly happens when two developers modify the
same line of a file differently.

Git identifies the conflict but leaves the decision
to the developer.

## 2. Learning Objectives

By the end of this lesson, you should be able to:

- Explain what a merge conflict is.
- Identify common causes of merge conflicts.
- Understand Git conflict markers.
- Recognize unresolved conflicts.
- Create a merge conflict through practical exercises.

## 3. Why Merge Conflicts Happen

Common causes include:

1. Same line modified differently in two branches.
2. A file deleted in one branch but modified in another.
3. Overlapping changes in the same section of a file.
4. The same file renamed differently across branches.

## 4. Understanding Conflict Markers

When Git detects a conflict, it inserts special
markers into the affected file.

Example:

<<<<<<< HEAD
Git is a powerful version control system.
=======
Git helps developers collaborate.
>>>>>>> feature-update

Explanation:

- `<<<<<<< HEAD`: Starts the current branch's changes.
- `=======`: Separates the two conflicting versions.
- `>>>>>>> feature-update`: Ends the incoming changes.

These markers help developers identify the conflicting
content and decide how to resolve it.

## 5. Practical Exercise: Creating a Merge Conflict

### Step 1: Create an initial file

```bash
echo "Git makes version control easier." > conflict.txt
git add conflict.txt
git commit -m "Add initial conflict practice file"
```

### Step 2: Create a feature branch

```bash
git switch -c feature-update
```

### Step 3: Modify the file on the feature branch

```bash
echo "Git helps developers collaborate." > conflict.txt
git add conflict.txt
git commit -m "Update Git description in feature branch"
```

### Step 4: Return to the main branch

```bash
git switch main
```

### Step 5: Modify the same line differently

```bash
echo "Git tracks changes in software projects." > conflict.txt
git add conflict.txt
git commit -m "Update Git description in main branch"
```

### Step 6: Attempt to merge

```bash
git merge feature-update
```

Git should identify a content conflict because both
branches modified the same line differently.

### Step 7: Inspect the conflict

```bash
git status
git diff
```

Open `conflict.txt` to examine the conflict markers.

**Note:** Do not resolve the conflict during this lesson.
Resolution is covered in Lesson 48.

## 6. Important Git Commands

| Command | Purpose |
|---|---|
| `git switch branch-name` | Switch branches |
| `git switch -c branch-name` | Create and switch to a branch |
| `git merge branch-name` | Merge another branch |
| `git status` | Inspect repository state |
| `git diff` | Inspect file changes |

## 7. Common Mistakes to Avoid

- Assuming merge conflicts mean the repository is broken.
- Deleting conflict markers without understanding them.
- Forgetting to inspect the conflicting changes.
- Committing unresolved conflict markers.
- Practicing conflict resolution on important production branches.

## 8. Key Takeaways

- Merge conflicts are normal in collaborative development.
- Git detects conflicting changes but does not decide
  which version should be kept.
- Conflict markers identify the competing changes.
- Developers must review and resolve conflicts.
- Understanding conflicts is essential when working
  with multiple branches and contributors.

## 9. Practice Challenge

Create a merge conflict between two branches by
modifying the same line differently.

Then answer:

1. Why did Git report a merge conflict?
2. What does `<<<<<<< HEAD` represent?
3. What is the purpose of `git status` during a conflict?
4. Why should unresolved conflicts not be committed?

## 10. Next Lesson

**Lesson 48: Resolving Merge Conflicts in VS Code**

In the next lesson, we will learn how to inspect,
resolve, stage, and complete a merge after a conflict.
