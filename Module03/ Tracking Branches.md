# Git Tracking Branches Notes

## 1. Tracking Branch Overview

- **Definition:** A tracking branch is a local reference that represents a remote branch.

- **Naming Convention:** Named locally as `<remote>/<branch>` (e.g., `origin/master`).

- **Role as Intermediary:** Acts as a local cached link between the local branch and the remote repository.

- **Decoupled Architecture:** Updating local branches (e.g., via `git commit`) or remote repositories does not update tracking branches automatically.

- **Network Updates:** Tracking branches only update during network operations (`git clone`, `git fetch`, `git pull`, `git push`).

---

## 2. Viewing & Managing Tracking Branches

### Viewing Branches

- **Local Branches Only:** Running `git branch` displays only local branch names.

- **All Branches:** Running `git branch --all` (or `git branch -a`) displays both local branches and tracking branches.

### Default Remote Tracking Branch (`origin/HEAD`)

- **Symbolic Reference:** `remotes/origin/HEAD` points to the default tracking branch on the remote repository.

- **Shortcut:** Allows using `origin` in place of the full tracking branch name (e.g., `git log origin` instead of `git log origin/master`).

- **Changing Default Tracking Branch Locally:**

```bash
git remote set-head origin <branch-name>

```

_Example:_ `git remote set-head origin develop` sets the default remote branch reference to `origin/develop`.

- **Changing Default Branch Remote Side (Bitbucket):**
  Navigate to **Settings** > **Main branch** to set the default branch for all users who clone the repository.

---

## 3. Status and Commit History

### Branch Status (`git status`)

- `git status` displays whether your local branch is up to date, ahead, or behind its corresponding tracking branch.

- **Cached Information:** Status reflects state as of the last network operation (`git fetch` or `git pull`). Local commits make the branch report as "ahead by $N$ commits" until pushed.

### Combined Commit Log

- Run `git log --all` to view the commit graph and compare positions of local and remote tracking branch references.
