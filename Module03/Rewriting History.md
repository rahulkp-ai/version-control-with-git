## 1. Amending the Most Recent Commit (`git commit --amend`)

Amending allows you to modify the most recent commit. Any modification generates a **new SHA-1 commit hash**, rewriting the commit's history.

- **Fixing a Commit Message:**

```bash
git commit --amend -m "Corrected commit message"

```

- **Adding or Updating Files in the Latest Commit:**

```bash
# 1. Modify or stage your files
git add fileC.txt

# 2. Amend without changing the commit message
git commit --amend --no-edit

```

---

## 2. Interactive Rebase (`git rebase -i`)

Interactive rebase allows you to rewrite, reorder, delete, or combine commits across a branch.

> **Important:** Do not use interactive rebase on commits that have already been pushed and shared with collaborators.

### Starting an Interactive Rebase

Specify a parent commit (or SHA-1) prior to the commits you wish to edit:

```bash
git rebase -i <commit-sha-or-HEAD~N>

```

### Interactive Rebase Commands

When the interactive editor opens, you can change the action keyword before each commit:

| Command      | Short | Description                                                                     |
| ------------ | ----- | ------------------------------------------------------------------------------- |
| **`pick`**   | `p`   | Keep and use the commit as-is.                                                  |
| **`reword`** | `r`   | Use the commit, but edit the commit message.                                    |
| **`edit`**   | `e`   | Pause the rebase at this commit to amend files/content.                         |
| **`squash`** | `s`   | Combine this commit into the previous commit and retain both messages.          |
| **`fixup`**  | `f`   | Combine this commit into the previous commit, discarding this commit's message. |
| **`exec`**   | `x`   | Run a shell command at this point in the rebase sequence.                       |
| **`drop`**   | `d`   | Remove/delete the commit entirely.                                              |

---

## 3. Workflow Examples

### Editing an Older Commit (`edit`)

1. Run `git rebase -i <parent-commit-SHA>`.
2. Change `pick` to `edit` next to the targeted commit and save.
3. Git pauses at that commit in a **detached HEAD** state.
4. Make your file changes or renames:

```bash
git add <modified-files>
git commit --amend

```

5. Resume the rebase:

```bash
git rebase --continue

```

### Deleting vs. Squashing a Commit

- **Deleting (`drop` / `d`):** Completely discards the commit and its changes. Any work introduced in that commit is permanently lost from the working tree.
- **Squashing (`squash` / `s`):** Combines the commit's changes with the preceding commit. **No work is lost.**

---

## 4. Squash Merging (`git merge --squash`)

A squash merge takes all new commits from a feature branch, combines them into a single set of changes, and stages them onto the target branch (e.g., `main`/`master`).

```bash
# 1. Switch to target branch
git checkout master

# 2. Perform squash merge
git merge --squash featureX

# 3. Commit the staged changes
git commit -m "Add featureX functionality"

# 4. Clean up branch
git branch -d featureX

```

- **Result:** Produces a clean, linear history on `master`. Individual feature branch commit histories are condensed into a single commit, and the unreferenced feature commits are eventually garbage-collected by Git.
