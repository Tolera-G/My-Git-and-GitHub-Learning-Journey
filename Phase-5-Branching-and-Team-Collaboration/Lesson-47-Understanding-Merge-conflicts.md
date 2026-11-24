
# Lesson 47: Understanding Merge Conflicts

## Learning Objectives
- Understand merge conflicts.
- Identify common causes of conflicts.
- Recognize Git conflict markers.
- Create a merge conflict using two branches.

## 1. What Is a Merge Conflict?
A merge conflict occurs when Git cannot automatically
combine changes from different branches.

## 2. Common Causes
- Two branches modify the same line differently.
- One branch deletes a file while another modifies it.
- Different overlapping changes are introduced.

## 3. Git Conflict Markers
- <<<<<<< HEAD: Beginning of current branch changes.
- =======: Separates conflicting versions.
- >>>>>>> branch: End of incoming branch changes.

## 4. Practical Exercise
1. Create a file on main.
2. Create a feature branch.
3. Modify the same line in both branches.
4. Commit both changes.
5. Merge the feature branch into main.
6. Inspect the conflict using git status and git diff.

## 5. Important Commands

```bash
git status
git diff
git merge feature-update
```

## 6. Key Takeaway
Merge conflicts are a normal part of collaborative
development. Git identifies conflicting changes and
allows developers to decide how to combine them.

## 7. Next Lesson
Lesson 48: Resolving Merge Conflicts in VS Code.
