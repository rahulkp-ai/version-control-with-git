# Git Core Locations & Managed Content

## 1. Primary Git Locations

### Working Tree (Working Directory)

- **Definition**: The filesystem directory on your local machine containing the files and directories of a checked-out commit.
- **Purpose**: Where you actively view, create, edit, and delete files to prepare changes for the next commit.
- **Key Mechanism**: Checking out a commit populates the working tree with that commit's specific files.

### Staging Area (Index)

- **Definition**: An intermediate preview area that tracks changes staged for the upcoming snapshot.
- **Purpose**: Allows crafting granular, meaningful commits by selectively adding specific files/changes.
- **Key Command**: Files are placed here using `git add`.

### Local Repository

- **Definition**: The full local database storing the complete commit history, branches, tags, and metadata for the project.
- **Purpose**: Provides offline access to review past states, create branches, or undo changes without network dependencies.

### Remote Repository

- **Definition**: A repository hosted on a remote server, cloud platform (e.g., GitHub, GitLab), or central network location.
- **Purpose**: Serves as the central source of truth for team collaboration and integration.
- **Synchronization**: Kept in sync with local repositories via `git push` and `git pull`.

---

## 2. Directory Structure On Disk

$$\text{Project Directory} = \text{Working Tree} + \text{Hidden } \mathtt{.git/}\text{ Directory}$$

- **Project Directory**: The root folder containing your project on your computer.
- **`.git/` Hidden Directory**: Contains the internal tracking metadata, including the **Staging Area** and **Local Repository**.
- **Critical Note**: Deleting the root project directory removes the `.git/` folder, which permanently deletes the local repository, commit history, and staged changes.

---

## 3. Core Git Architecture Summary

| Location                       | Stored Content               | Primary Purpose                              | Key Associated Operations           |
| ------------------------------ | ---------------------------- | -------------------------------------------- | ----------------------------------- |
| **Working Tree**               | Raw editable files           | Active workspace for modifying project files | Standard editor, `git checkout`     |
| **Staging Area (Index)**       | List of proposed changes     | Pre-commit snapshot staging                  | `git add`                           |
| **Local Repository (`.git/`)** | Complete commit history      | Offline version control database             | `git commit`                        |
| **Remote Repository**          | Official centralized history | Multi-developer collaboration                | `git push`, `git pull`, `git fetch` |
