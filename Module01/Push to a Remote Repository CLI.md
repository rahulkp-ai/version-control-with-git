# Pushing Commits to Remote Repositories via CLI

## 1. Starting Workflows: `git clone` vs `git remote add`

| Starting Scenario                  | Command                        | Result                                                                                     |
| ---------------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------ |
| **No local repo exists**           | `git clone <URL> [dir_name]`   | Downloads remote repo, creates local directory, and configures remote alias `origin`.      |
| **Local repo exists with commits** | `git remote add <alias> <URL>` | Links local repository to a remote repository URL using a shortcut alias (e.g., `origin`). |

---

## 2. Cloning Remote Repositories (`git clone`)

- **Default Directory Name**: Extracts folder name directly from the repository URL (e.g., `helloworld.git` $\rightarrow$ `helloworld/`).
- **Custom Directory Name**:

```bash
git clone https://bitbucket.org/user/helloworld.git my_custom_project

```

- **Inspecting Linked Remotes**:

```bash
git remote -v

```

_Outputs fetch and push URLs associated with remote aliases (e.g., `origin`)._

---

## 3. Connecting Existing Repositories (`git remote add`)

If you have a local project directory with existing commits:

1. **Add Remote Endpoint**:

```bash
git remote add origin https://bitbucket.org/user/repoa.git

```

2. **Verify Configuration**:

```bash
git remote -v

```

---

## 4. Pushing Commits to Remote (`git push`)

- **Purpose**: Writes local branch commits to the remote branch, synchronizing their states and creating a remote backup.
- **First Push Syntax**:

```bash
git push -u origin master

```

- `-u` / `--set-upstream`: Establishes a tracking link between the local branch (`master`) and remote branch (`origin/master`).

- **Subsequent Pushes**: Once tracking is configured, simply run:

```bash
git push

```

---

## 5. Summary Workflows

### Option A: Starting from Scratch

```bash
cd repos
git clone https://bitbucket.org/user/repoa.git
cd repoa
echo "# Project Title" > README.md
git add README.md
git commit -m "Initial commit"
git push -u origin master

```

### Option B: Existing Local Repository

```bash
cd repos/existing-project
git remote add origin https://bitbucket.org/user/repoa.git
git push -u origin master

```
