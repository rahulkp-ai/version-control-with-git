# Git Merge Conflicts & Resolution Notes

## 1. What is a Merge Conflict?

- **Automatic Merging:** Git automatically combines branch changes into a single merge commit when work is done on separate files or different parts (hunks) of the same file.
- **Conflict Trigger:** A merge conflict occurs only when multiple branches make conflicting changes to the **exact same hunk** of the same file.
- **Human Intervention:** When a conflict occurs, Git cannot automatically decide which changes to keep. A developer must manually intervene to resolve it.

---

## 2. When Conflicts Do & Do Not Occur

| Scenario            | Example                                                                     | Outcome                                        |
| :------------------ | :-------------------------------------------------------------------------- | :--------------------------------------------- |
| **Different Files** | Branch A edits `fileA.txt`; Branch B creates `fileB.txt`.                   | **No Conflict** (Clean automatic merge)        |
| **Different Hunks** | Branch A edits top of `fileA.txt`; Branch B edits bottom of `fileA.txt`.    | **No Conflict** (Clean automatic merge)        |
| **Same Hunk**       | Branch A edits Line 2 of `fileA.txt`; Branch B edits Line 2 of `fileA.txt`. | **Merge Conflict** (Requires human resolution) |

---

## 3. Best Practices to Prevent Conflicts

- **Frequent Merging:** Avoid long-lived feature branches. Perform small, frequent merges to prevent cumulative merge issues.
- **Decoupled Architecture:** Keep codebase modules separated so developers rarely edit the same hunks simultaneously.

---

## 4. The 3 Commits Involved in a Conflict

1. **Ours / Mine:** The commit at the tip of your current checked-out branch (e.g., `master`).
2. **Theirs:** The commit at the tip of the incoming branch being merged.
3. **Merge Base:** The common ancestor commit where both branches diverged.

---

## 5. Anatomy of Conflict Markers

When a merge conflict happens, Git flags the file in your working tree and adds inline markup:

```text
<<<<<<< HEAD
feature 3       <-- "Ours" (Changes on current checked-out branch)
=======
feature 2       <-- "Theirs" (Changes from incoming branch)
>>>>>>> feature2
```

- Lines outside the markers are cleanly merged by Git automatically.
- Text between `<<<<<<<` and `=======` represents your current branch (`HEAD`).
- Text between `=======` and `>>>>>>>` represents the incoming branch.

---

## 6. Step-by-Step Resolution Workflow

1. **Checkout Base Branch:**

```bash
git checkout master

```

2. **Attempt Merge:**

```bash
git merge feature2

```

3. **Check Conflicted Files:**

```bash
git status

```

_(Optional: Run `git merge --abort` if you need to cancel the merge attempt)._ 4. **Edit the File:**
Open the file in a text editor or GUI merge tool. Remove conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) and adjust the code to its final intended state. 5. **Stage Resolved File:**

```bash
git add fileA.txt

```

6. **Finalize Commit:**

```bash
git commit

```

7. **Clean Up Branch (Optional):**

```bash
git branch -d feature2

```
