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

