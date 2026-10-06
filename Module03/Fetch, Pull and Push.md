# Git Network Commands: Fetch, Pull, and Push

## Overview of Network Commands

Most Git commands interact strictly with the local repository. Network commands communicate directly with a remote repository (e.g., GitHub, Bitbucket).

- **`git clone`**: Copies a remote repository to create a local repository.
- **`git fetch`**: Retrieves the latest objects and references from the remote repository.
- **`git pull`**: Combines `git fetch` and `git merge` in a single command.
- **`git push`**: Sends local commits and references to the remote repository.

---

## 1. `git fetch`

Retrieves new objects and references from the remote repository and updates tracking branches (e.g., `origin/master`).

- **Key Concept**: Downloads changes **without** merging them into your local working branch.
- **Default Behavior**: Targets the default remote (usually `origin`) if no argument is provided.

### Workflow & Behavior

1. Running `git fetch` updates tracking branches to reflect the state of the remote repository.
2. Local branch labels (e.g., `master`) remain unaffected and do not move.
3. Running `git status` after a fetch reveals if your local branch is behind the tracking branch.

```bash
git fetch
git status
# Output indicates whether local branch is behind and if a fast-forward merge is possible
```

---

## 2. `git pull`

Executes two operations under the hood:

$$\text{git pull} = \text{git fetch} + \text{git merge FETCH\_HEAD}$$

_(Where `FETCH_HEAD` refers to the tip of the tracking branch)._

### Merge Strategies & Flags

- **`--ff` (Default)**: Performs a fast-forward merge if possible; otherwise creates a merge commit.
- **`--no-ff`**: Always creates a merge commit, even if a fast-forward is possible.
- **`--ff-only`**: Accepts only fast-forward merges. Aborts if a merge commit would be required.
- **`--rebase`**: Reapplies local commits on top of fetched upstream commits instead of merging.

### Pull Scenarios

1. **Fast-Forward Merge**:

- Occurs when no new local commits exist on your current branch.
- Git simply moves the local branch pointer forward to match the tracking branch tip.

2. **Merge Commit**:

- Occurs when both the local and remote branches have diverged with independent commits.
- Git creates a new merge commit combining both histories. Tracking branch remains at the remote tip.

### Uncommitted Changes Safety Mechanism

- If `git pull` affects files you have modified locally without committing:
- **Abort**: Git stops the merge to protect local changes from being overwritten.
- **Resolution**: You must either `git commit` or `git stash` local changes before pulling again.

- Uncommitted files that are **not** modified on the remote are left untouched by `git pull`.

---

## 3. `git push`

Sends local commits to the remote repository and updates remote references.

```bash
git push -u <remote_name> <branch_name>
# Example: git push -u origin master

```

- **`-u` / `--set-upstream**`: Links the current local branch to the specified remote tracking branch. Future pushes and pulls on this branch can omit repository/branch arguments.

### Golden Rule for Pushing

- **Always Fetch/Pull Before Pushing**:
- If the remote repository contains commits that you do not have locally, `git push` will be rejected.
- **Resolution**: Fetch or pull remote changes, resolve any conflicts locally, and then push.
