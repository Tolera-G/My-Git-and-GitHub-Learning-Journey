# Lesson 44: Working with Pull Request Reviews and Feedback

## 1. Learning Objectives

By the end of this lesson, you should be able to:

- Explain the purpose of Pull Request reviews.
- Understand GitHub review decisions.
- Understand how reviewers provide feedback.
- Respond to requested changes.
- Update an existing Pull Request with new commits.

## 2. What Is a Pull Request Review?

A Pull Request review is a process in which developers examine proposed code changes before they are merged into another branch.

The purpose is to:

- Identify programming errors.
- Improve code quality.
- Maintain coding standards.
- Improve readability and maintainability.
- Share knowledge between developers.

## 3. Types of Pull Request Reviews

GitHub provides three main review decisions:

### Approve
The reviewer accepts the proposed changes.

### Comment
The reviewer provides feedback without explicitly approving or requesting changes.

### Request Changes
The reviewer identifies problems that should be addressed before the Pull Request is approved.

## 4. Understanding Review Comments

Reviewers can comment on specific lines of code.

For example:

```javascript
function calculateTotal(price, quantity) {
    return price * quantity;
}
```

A reviewer might ask:

"What happens if quantity is negative?"

The developer can improve the function:

```javascript
function calculateTotal(price, quantity) {
    if (quantity < 0) {
        throw new Error("Quantity cannot be negative");
    }

    return price * quantity;
}
```

Review comments help developers identify problems and improve their implementations.

## 5. Responding to Requested Changes

When a reviewer requests changes:

1. Read and understand the feedback.
2. Identify the affected code.
3. Make the necessary corrections.
4. Test the updated code.
5. Stage and commit the corrections.
6. Push the new commits to the same branch.

Example:

```bash
git add .
git commit -m "Fix requested review changes"
git push
```

The existing Pull Request automatically reflects the new commits.

## 6. Git Commands Used During Reviews

| Command | Description |
|---|---|
| `git status` | Checks working-tree status |
| `git diff` | Displays unstaged changes |
| `git diff --staged` | Displays staged changes |
| `git log --oneline` | Displays commit history |
| `git add .` | Stages changes |
| `git commit -m "message"` | Creates a commit |
| `git push` | Pushes commits to the remote branch |

## 7. Pull Request Review Workflow

1. Developer creates a feature branch.
2. Developer implements changes.
3. Developer commits and pushes changes.
4. Developer opens a Pull Request.
5. Reviewer examines the changes.
6. Reviewer provides feedback.
7. Developer makes corrections.
8. Developer pushes updated commits.
9. Reviewer checks the corrections.
10. Pull Request is approved and merged.

## 8. Practical Exercise

### Step 1: Switch branches

```bash
git switch feature/pr-description-practice
```

### Step 2: Create review-practice.js

```javascript
function calculateTotal(price, quantity) {
    return price * quantity;
}

console.log(calculateTotal(100, 2));
```

### Step 3: Commit and push

```bash
git add .
git commit -m "Add calculation function for review practice"
git push
```

### Step 4: Simulate reviewer feedback

Modify the function to validate quantity:

```javascript
function calculateTotal(price, quantity) {
    if (quantity < 0) {
        throw new Error("Quantity cannot be negative");
    }

    return price * quantity;
}

console.log(calculateTotal(100, 2));
```

### Step 5: Commit the correction

```bash
git add .
git commit -m "Validate quantity in calculation function"
git push
```

## 9. Key Takeaways

- Pull Request reviews improve software quality.
- GitHub provides Approve, Comment, and Request Changes decisions.
- Review comments help developers identify improvements.
- New commits can update an existing Pull Request.
- Developers should understand and test requested corrections before pushing them.

## 10. Lesson Completion Checklist

- [ ] Understand Pull Request reviews.
- [ ] Identify the three review decisions.
- [ ] Understand review comments.
- [ ] Simulate reviewer feedback.
- [ ] Make corrections and push new commits.

**Next Lesson:** Merging Pull Requests and Understanding Merge Strategies.