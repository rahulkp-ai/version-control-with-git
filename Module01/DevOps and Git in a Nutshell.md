# DevOps and Git: Fundamental Principles

## 1. DevOps & Continuous Improvement

- **DevOps**: Modern software development practices focused on continuous improvement.
- **Small Batch Sizes**: Continuously planning, building, and releasing small incremental changes rather than large batches (Waterfall approach).
- **Benefits of Small Changes**:
- Faster feedback loops.
- Easier bug fixes and feature additions.
- Smoother, low-risk deployment iterations.

---

## 2. Managing Versions with Commits

- **Commit**: A snapshot of the entire project at a specific point in time, forming the project history.
- **Efficiency**:
- Git does **not** store redundant copies of unchanged files.
- Each unique file is stored only once.
- _Example_: If a project has 50 files (Commit A) and a bug fix alters 1 file (Commit B), Git only stores 1 new file, bringing the total unique stored files to 51.

- **Reversibility**: Project history allows reverting to older snapshots or introducing new commits that undo unwanted changes.

---

## 3. Isolated Development with Branches

- **Branch**: An independent line of development.
- **Default Branch**: Named `master` (or `main`).
- **Parallel Workflows**:
- Allows active production code to remain stable on the main branch while developers work on feature branches (e.g., `featureX`, `bugY`).
- Changes on isolated branches do not affect or clutter the main branch until explicitly combined.

---

## 4. Integration and Quality via Pull Requests & Merges

- **Pull Request (PR)**: A formal proposal to merge changes from a feature branch into a target branch (e.g., `master`).
- **Quality Assurance in PRs**:
- **Peer Review**: Team members discuss, review, and approve code changes.
- **Automated Testing**: CI pipelines must pass tests before merging to prevent regressions in production.

- **Merge**: Integrates approved and tested code from a feature branch back into the main line of development.
