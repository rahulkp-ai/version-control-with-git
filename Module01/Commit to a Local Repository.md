# Committing to a Local Repository Using the CLI

## 1. Inspecting File States (`git status`)

- **Purpose**: Displays the active branch and the status of files in both the working tree and staging area.
- **File States**:
- **Untracked**: New files in the working directory not yet tracked by Git.
- **Staged**: Files added to the index, ready to be included in the next commit.
- **Modified**: Previously tracked files changed in the working directory but not yet restaged.

- **Short Status (`git status -s`)**:
- `??` (Red): Untracked file in the working tree.
- `A ` (Green): Added/staged file.
- ` M` (Red): Modified file in the working tree (unstaged).
- `AM` (Green `A` + Red `M`): File staged initially, then modified further in the working tree without restaging.

---

## 2. Staging Changes (`git add`)

- **Stage a Single File**:

```bash
git add fileA.txt

```

- **Stage an Entire Directory**:

```bash
git add dirA/

```

_Stages all untracked and modified files within `dirA/`._

- **Stage All Changes in Directory (`git add .`)**:

```bash
git add .

```

> **Caution**: Use `git add .` carefully to avoid accidentally staging untracked files or secret environment files not intended for version control.

---

## 3. Creating Commits (`git commit`)

- **Commit with Inline Message**:

```bash
git commit -m "Initial commit"

```

- **Commit via Default Text Editor**:
  Running `git commit` without the `-m` flag launches your configured editor (e.g., `nano`, `vim`) to write detailed, multi-line commit messages.
- **Commit Behavior**: A commit saves a complete project snapshot. Committed files remain tracked in the repository and future commits unless explicitly removed.

---

## 4. Viewing Commit History (`git log`)

| Command                         | Output Description                                                           |
| ------------------------------- | ---------------------------------------------------------------------------- |
| `git log`                       | Detailed commit history (shows commit hash, author, date, and full message). |
| `git log --oneline`             | Condensed history (one line per commit with abbreviated hash and subject).   |
| `git log -n <number>`           | Limits output to the $N$ most recent commits (e.g., `git log -n 2`).         |
| `git log --oneline -n <number>` | Condensed view of the $N$ most recent commits.                               |
