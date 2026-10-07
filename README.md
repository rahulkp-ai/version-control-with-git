# Version Control with Git

Welcome to the **Version Control with Git** repository. This repository contains structured study notes, tutorials, and practical exercises covering fundamental to advanced Git concepts, branching strategies, remotes, and workflows.

---

## 📂 Repository Structure

```text
version-control-with-git/
├── FeatureConflit.txt
├── FeatureXfile01.txt
├── FeatureXfile02.txt
├── FeatureXfile03.txt
├── Module01/
│   ├── Commit to a Local Repository.md
│   ├── Create a Local Repository.md
│   ├── Create a Remote Repository.md
│   ├── DevOps and Git in a Nutshell.md
│   ├── Git Locations.md
│   ├── Git Overview.md
│   ├── Installation and Getting Started.md
│   └── Push to a Remote Repository CLI.md
├── Module02/
│   ├── (Command Line) Merging.md
│   ├── (Sourcetree) Merging.md
│   ├── Branches.md
│   ├── Git IDs.md
│   ├── Git References.md
│   └── Git's Graph Model.md
├── Module03/
│   ├── Tracking Branches.md
│   ├── Fetch, Pull and Push.md
│   ├── Rebasing.md
│   ├── Resolving Merge Conflicts.md
│   └── Rewriting History.md
└── Module04/
    ├── Git Workflows.md
    └── Pull Requests01.md
```

---

## 📚 Module Summary

### 🛠️ Module 01: Introduction & Basic Operations

Focuses on foundational core concepts of Git, initial system installation, repository setup, and basic local-to-remote pushing mechanisms.

- **DevOps and Git in a Nutshell**: Contextualizing version control within modern DevOps practices.
- **Git Overview & Locations**: Key concepts behind local tracking (Working Directory, Staging Area/Index, Repository).
- **Installation & Repository Setup**: Instructions for creating and configuring local and remote repositories.
- **Basic Workflow**: Committing changes locally and pushing to remote destinations using the CLI.

---

### 🌿 Module 02: Branching & Git Architecture

Explores Git's internal storage mechanisms, graph model, and branching capabilities.

- **Git Architecture**: Understanding Git IDs (SHA-1/SHA-256 hashes), references, and the Directed Acyclic Graph (DAG) model.
- **Branching & Merging**: Creating branches, managing parallel development, and executing merges via the Command Line and Sourcetree GUI.

---

### 🔄 Module 03: Remote Synchronization & History Management

Covers standard remote operations, resolving conflicting changes, and altering project history safely.

- **Remote Management**: Working with tracking branches, executing `fetch`, `pull`, and `push`.
- **Rebasing & Conflict Resolution**: Re-applying commits on top of another base tip and handling merge conflicts manually.
- **History Operations**: Techniques for amending, resetting, and rewriting local history.

---

### 👥 Module 04: Workflows & Collaboration

Examines team coordination strategies and peer code reviews.

- **Pull Requests**: Code review patterns, collaborative approvals, and updating feature branches.
- **Git Workflows**: Comprehensive review of Centralized, Feature Branch, Forking, and GitFlow workflows.

---

## 🧪 Practice & Sample Files

The root directory contains sample files used during hands-on exercises (e.g., simulating merge conflicts and working with feature branches):

- `FeatureConflit.txt`
- `FeatureXfile01.txt`
- `FeatureXfile02.txt`
- `FeatureXfile03.txt`

---

## Getting Started

1. **Clone the repository:**

   ```bash
   git clone <repository-url>
   cd version-control-with-git
   ```

2. **Navigate the modules:**
   Explore each folder in sequence (`Module01` through `Module04`) to read through the detailed markdown notes and guides.
