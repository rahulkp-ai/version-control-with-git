### 1. Merging Overview

- **Purpose:** Merging integrates commits from a topic branch (e.g., `featureX`) into a longer-running base branch (e.g., `master` or `main`).
- **Branch Membership:** Commits made on a topic branch become part of the base branch once merged. Individual commits can belong to multiple branches simultaneously.
- **4 Main Merge Types:** Fast-Forward Merge, Merge Commit, Squash Merge, and Rebase _(the transcript focuses on the first two)_.

---

### 2. Fast-Forward Merges (`--ff`)

- **Mechanism:** Moves the base branch pointer forward to the tip of the feature branch without creating a new commit.
- **Prerequisite:** Allowed **only** if no new commits were added to the base branch since the feature branch diverged.
- **Outcome:** Produces a strictly **linear commit history**.

1. **Check out base branch:**
   Switch to your destination branch using `git checkout master`.

2. **Merge feature branch:**
   Execute `git merge featureX`. Git defaults to a fast-forward merge if possible.

3. **Clean up branch pointer (Optional):**
   Delete the feature branch tag using `git branch -d featureX`.

---

### 3. Merge Commits (Three-Way / Non-Fast-Forward)

- **Mechanism:** Creates a new **Merge Commit** ($M$) combining the tips of both branches.
- **Multiple Parents:** A merge commit always has two parent commits (the previous tip of the base branch and the tip of the feature branch).
- **Automatic Creation:** Triggered automatically when the base branch has diverged (new commits exist on the base branch).
- **Forced Merge Commits (`--no-ff`):** Using `git merge --no-ff featureX` forces Git to build a merge commit even if a fast-forward merge is possible. This preserves explicit visual context of feature work in the log graph.

---

## Merge Strategy Comparison

| Feature                   | Fast-Forward (`--ff`) | Standard Merge Commit     | Forced Merge Commit (`--no-ff`)       |
| ------------------------- | --------------------- | ------------------------- | ------------------------------------- |
| **Base Branch Diverged?** | No                    | Yes                       | No                                    |
| **Creates New Commit?**   | No                    | Yes (2 parents)           | Yes (2 parents)                       |
| **History Structure**     | Linear                | Non-linear                | Non-linear                            |
| **Use Case**              | Simple, quick updates | Integrating parallel work | Preserving feature history explicitly |

---
