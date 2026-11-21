# Lesson 43: Writing Effective Pull Request Descriptions & Comparing Changes

## 1. Learning Objectives

By the end of this lesson, you should be able to:

- Understand the purpose of Pull Request (PR) descriptions.
- Write clear and professional PR descriptions.
- Compare changes between two Git branches.
- Identify files modified between branches.
- Review changes before merging.

## 2. What Is a Pull Request Description?

A Pull Request description explains the changes proposed in a branch before they are merged into another branch.

It helps reviewers understand:
- What was changed?
- Why was it changed?
- How can the changes be tested?
- What should reviewers pay attention to?

A good PR description improves communication and makes code reviews more effective.

## 3. Anatomy of a Professional Pull Request

A professional PR description generally contains four sections:

### Summary
Briefly explains what the Pull Request introduces.

### Motivation
Explains why the changes were necessary.

### Changes
Lists the important modifications.

### Testing
Explains how the changes were tested or how reviewers can verify them.

### Example

```markdown
## Summary
Added a login page to the application.

## Motivation
Users need a way to access their accounts.

## Changes
- Created the login form.
- Added email and password fields.
- Implemented basic form validation.
- Improved page layout.

## Testing
- Tested form submission.
- Verified required fields.
- Checked desktop and mobile layouts.
```

## 4. Comparing Changes Between Branches

Git allows developers to compare branches to understand the differences between their contents.

For example:

- `main`: The original project branch.
- `feature/add-login-page`: A branch containing new functionality.

Comparing these branches helps developers review proposed changes before merging.

## 5. Important Git Comparison Commands

### Compare two branches

```bash
git diff main feature/add-login-page
```

Displays the actual code differences between the branches.

### Display changed filenames

```bash
git diff --name-only main feature/add-login-page
```

Displays only the filenames that have changed.

### Display a summary of changes

```bash
git diff --stat main feature/add-login-page
```

Displays a summary showing the number of insertions and deletions per file.

## 6. Understanding What Happens Behind the Scenes

Git compares the content of two branches and calculates their differences.

When comparing branches, Git uses their commit histories to determine the relevant changes.

GitHub uses branch comparisons when displaying Pull Request changes.

A Pull Request normally compares a source branch against a target branch.

For example:

- Source: `feature/add-login-page`
- Target: `main`

The comparison shows the changes proposed for integration into `main`.

## 7. Common Mistakes

| Mistake | Better Practice |
|---|---|
| Writing unclear descriptions | Explain changes specifically |
| Ignoring the motivation | Explain why changes are needed |
| Forgetting testing details | Include testing instructions |
| Comparing incorrect branches | Verify source and target branches |
| Writing excessively long descriptions | Use organized sections |

## 8. Practical Exercise

Practice in your Git learning repository.

### Step 1: Create a new branch

```bash
git switch -c feature/pr-description-practice
```

### Step 2: Create a practice directory

```bash
mkdir 05-Branching-and-Collaboration
cd 05-Branching-and-Collaboration
```

### Step 3: Create a Markdown file

Create `pr-example.md` and add:

```markdown
# Pull Request Practice

## Feature
Practice writing professional Pull Request descriptions.

## Purpose
Help developers communicate their changes effectively.
```

### Step 4: Commit the changes

```bash
git add .
git commit -m "Add pull request description practice"
```

### Step 5: Compare branches

```bash
git diff main feature/pr-description-practice
```

### Step 6: Display changed filenames

```bash
git diff --name-only main feature/pr-description-practice
```

### Step 7: Display change statistics

```bash
git diff --stat main feature/pr-description-practice
```

## 9. Key Takeaways

- A Pull Request description communicates the purpose and details of proposed changes.
- Good descriptions make code reviews easier.
- `git diff` displays differences between branches.
- `git diff --name-only` displays changed filenames.
- `git diff --stat` summarizes changes.
- Reviewing changes before merging helps prevent mistakes.

## 10. Lesson Completion

Before completing this lesson, ensure that you can:

- [ ] Explain the purpose of a Pull Request description.
- [ ] Identify the four major sections of a PR description.
- [ ] Compare two branches using `git diff`.
- [ ] Display changed filenames.
- [ ] Display change statistics.
- [ ] Complete the practical exercise.

**Next Lesson:** Working with Pull Request Reviews and Feedback.