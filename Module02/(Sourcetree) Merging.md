Here is a clear summary and key takeaways from the transcript on **Git Merging**.

---

## 1. Overview of Merging

- **Purpose:** Merging combines the work from independent topic branches (e.g., `featureX`) into a longer-running base branch (e.g., `master` or `main`).
- **Shared Commits:** Commits created on a feature branch become part of the base branch once merged.
- **4 Main Merge Types:** Fast-Forward Merge, Merge Commit, Squash Merge, and Rebase.

---

## 2. Fast-Forward Merges

- **Mechanism:** Moves the base branch pointer forward to the tip of the feature branch. No new commit is generated.
- **Condition:** Only possible when **no new commits** were added to the base branch after the feature branch was created.
- **Result:** Produces a clean, **linear commit history**.

### Step-by-Step Execution (SourceTree & CLI)

1. **Check out the base branch:**
   Switch to your base branch (e.g., `git checkout master` or double-click `master` in SourceTree).

2. **Merge the feature branch:**
   Execute the merge command (`git merge featureX` or select the feature commit in SourceTree and click **OK**).

3. **Delete the feature branch label (Optional):**
   Remove the feature branch tag to maintain a clean workspace (`git branch -d featureX`).

---

## 3. Merge Commits (Three-Way Merges)

- **Mechanism:** Combines the tips of both branches into a brand-new commit called a **Merge Commit** ($M$).
- **Parents:** A merge commit always has **multiple parents** (e.g., the tip of the feature branch and the tip of the base branch).
- **Condition:** Used automatically when the base branch has diverged (new commits exist on the base branch), making a fast-forward merge impossible.
- **Result:** Produces a **non-linear commit history**, clearly showing branch paths.

---

## 4. Forced Merge Commits (No Fast-Forward / `--no-ff`)

- **Purpose:** Forces Git to create a merge commit even if a fast-forward merge is possible.
- **Why Use It:** Helps team workflows retain explicit visual context of where feature work started and merged.
- **SourceTree Setting:** Check the box _“Create a commit even if merge resolved via fast-forward”_.

---

## Summary Comparison

| Merge Type                      | Base Branch Diverged? | Creates New Commit? | History Structure |
| ------------------------------- | --------------------- | ------------------- | ----------------- |
| **Fast-Forward (`--ff`)**       | No                    | No                  | Linear            |
| **Merge Commit**                | Yes                   | Yes (Two Parents)   | Non-linear        |
| **No Fast-Forward (`--no-ff`)** | No                    | Yes (Two Parents)   | Non-linear        |
