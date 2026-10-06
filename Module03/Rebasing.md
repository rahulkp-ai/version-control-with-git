# Git Rebasing

## Overview & Golden Rule

Rebasing moves a sequence of commits to a new base commit (or new parent). It changes the ancestor chain of your commits, resulting in a cleaner, linear commit history.

> ⚠️ **Golden Rule of Rebasing**: **Never rewrite public history.**
> Only rebase local branches or private feature branches that have not been shared with or pushed to others. Changing commit history on shared branches causes severe sync issues for collaborators.

---

## How Rebasing Works Under the Hood

When you rebase a branch onto another (e.g., rebasing `featureX` onto `master`):

1. **Calculating Diffs (Patches)**: Git identifies the changes made in each commit of the feature branch relative to its original base.
   $$\text{Diff}_{AB} = \text{Commit}_B - \text{Commit}_A$$
2. **Reapplying Commits**: Git moves the base of the feature branch to the tip of the upstream branch (`master`) and applies those diffs one by one on top of it.
3. **New Commit Hashes**: Because the parent commit ID changed, each reapplied commit gets a brand-new commit hash ($B \rightarrow B'$, $C \rightarrow C'$).

---

## Pros & Cons of Rebasing

| Pros                                                                                                          | Cons                                                                                                              |
| :------------------------------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------- |
| **Clean, linear history**: Eliminates redundant merge commits.                                                | **Rewriting history**: Dangerous if used on shared branches.                                                      |
| **Up-to-date testing**: Incorporates upstream updates (bug fixes, features) into your current branch context. | **Merge conflicts**: Reapplying commits sequentially can lead to multiple conflict resolution steps.              |
| **Easier future merges**: Pre-resolves conflicts before pulling into the main branch.                         | **Loss of chronological history**: Does not preserve the exact timeline of when commits were originally authored. |

---

## Executing a Rebase

### Standard Commands

There are two syntax options to initiate a rebase:

```bash
# Option 1: Two-step workflow
git checkout featureX
git rebase master

# Option 2: Single-step workflow
git rebase master featureX
```

---

## Handling Merge Conflicts During Rebase

Because rebasing reapplies commits individually, conflicts may occur during the replay process.

### Workflow to Resolve Conflicts

1. **Start Rebase:** Initiate the rebase onto upstream branch.
   Run `git rebase master` while on your feature branch. Git will pause when a conflict is detected.

2. **Identify Conflicts:**
   Run `git status` to locate unmerged files containing conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).

3. **Resolve and Stage:**
   Edit the affected files to resolve conflicts, then stage them:

```bash
git add fileA.txt

```

4. **Continue Rebase:** Do NOT use git commit.
   Resume the rebase process with:

```bash
git rebase --continue

```

### Aborting a Rebase

If you run into issues or want to undo the rebase during a conflict:

```bash
git rebase --abort

```

_This safely restores your branch back to its pre-rebase state._

---

## Comparison: Merge vs. Rebase Conflict Resolution

| Step              | Standard Merge Flow (`git merge`)         | Rebase Flow (`git rebase`)                            |
| ----------------- | ----------------------------------------- | ----------------------------------------------------- |
| **Target Branch** | Checkout `master`, merge `featureX`       | Checkout `featureX`, rebase onto `master`             |
| **Fixing Files**  | Resolve markers, then `git add fileA.txt` | Resolve markers, then `git add fileA.txt`             |
| **Final Command** | `git commit` (creates a merge commit)     | `git rebase --continue` (reapplies remaining commits) |
| **Result Graph**  | Non-linear graph with a merge commit      | Linear graph with no extra merge commit               |
