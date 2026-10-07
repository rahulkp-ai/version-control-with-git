# Git Pull Requests Overview

## 1. What is a Pull Request (PR)?

A pull request is a feature provided by Git hosting platforms (such as GitHub and Bitbucket) that facilitates team communication, code reviews, and feedback prior to integrating changes.

- **Primary Goal:** Merge a feature branch into a target/longer-running branch.
- **Key Benefits:**
  - Enables team discussion around branch work.
  - Sends automatic notifications to team members.
  - Acts as a structured **code review** tool with comment and approval mechanisms.

---

## 2. Repository Configurations

- **Single Remote Repository:** Requesting to merge a branch into another branch within the same repository.
- **Two Remote Repositories (Forking Model):** Requesting to merge a branch from a **forked repository** into an **upstream repository**.
  - Used when a contributor lacks direct write access to the upstream repository.

---

## 3. When to Open a Pull Request

A pull request can be created at **any point** after branch creation:

1. **Immediately upon branch creation:** To start early team discussion on planned work.
2. **In progress:** To ask for assistance or feedback when stuck on an implementation.
3. **When work is complete:** To request formal code review and final merging.

---

## 4. Single Repository Workflow

### Step A: Preparation (Local CLI)

1. **Create and switch to a new feature branch:**

   ```bash
   git checkout -b featureX
   ```

2. **Make changes, stage, and commit:**

```bash
touch fileA.txt
git add fileA.txt
git commit -m "Add fileA.txt"

```

3. **Push to the remote repository and set upstream tracking:**

```bash
git push --set-upstream origin featureX

```

> **Tip:** Git host CLI output usually includes a direct URL to create a PR in your browser.

---

### Step B: Opening the Pull Request

1. Log into your Git host (e.g., Bitbucket/GitHub) and navigate to the repository.
2. Click **Pull Requests** $\rightarrow$ **Create a Pull Request**.
3. Fill out the PR form:

- **Title**
- **Description** (details of changes)
- **Reviewers** (assign team members)

4. Submit the PR.

---

### Step C: Reviewing and Managing a Pull Request

Reviewers inspect the PR context (code diffs, commits, and comments):

- **Approve:** Adds your vote to the approval count. Teams often require a minimum number of approvals before merging.
- **Decline / Reject:** Closes the PR without merging. _(Cannot be undone)_.
- **Edit:** Updates PR details. _(Note: Pushing new commits to the branch automatically updates the PR—editing is not required)._
- **Comment:** Provide feedback or request changes directly on specific lines or threads.

---

### Step D: Merging and Clean-up

Once approved, the branch is ready to be merged into the target branch.

#### Merge Strategies:

1. **Merge Commit:** Preserves all individual commits and creates a dedicated merge commit.
2. **Squash Merge:** Combines all commits on the branch into a single, linear commit on the target branch.
3. **Local Merge:** Merge the branch on your local client as usual and push to the remote server. The PR will close automatically.

#### Post-Merge Branch Cleanup:

Delete the remote branch label once merging is complete:

```bash
git push origin -d featureX

```

---

## 5. Key Takeaways

- **Ultimate Goal:** Merge a branch into a project line.
- **Collaboration:** Facilitates team feedback, review, and approval.
- **Flexibility:** Can be opened at any stage of branch development.
- **Automatic Updates:** New commits pushed to the branch automatically update the open PR.
- **Execution:** Merges can be performed on the host UI or via your local Git client.
