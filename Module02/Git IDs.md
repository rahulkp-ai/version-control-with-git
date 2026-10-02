# Git Objects, SHA-1 Hashes & Plumbing Commands

---

## 1. The Internal Git Object Store

Git manages repository history using an internal key-value database located in `.git/objects`. Every entity stored in this database falls into one of four primary object types:

| Object Type                      | Function & Payload Structure                                                                                                                         | User Visibility        |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| **Commit**                       | Plain-text manifest containing committer/author metadata, timestamps, commit message, pointer(s) to parent commit(s), and root tree SHA-1 reference. | **Porcelain (Direct)** |
| **Annotated Tag**                | Reference object pointing explicitly to a specific commit, containing tagger metadata, timestamp, and GPG signature/message.                         | **Porcelain (Direct)** |
| **Tree**                         | Represents directory state. Contains directory entries, mode permissions, filenames, and pointers to child trees or blobs.                           | Internal (Plumbing)    |
| **Blob** _(Binary Large Object)_ | Uncompressed/zlib-compressed file data payload, stripped of metadata (e.g., filename, paths, permissions).                                           | Internal (Plumbing)    |

$$\text{Commit Object} \longrightarrow \text{Root Tree Object} \longrightarrow \{\text{Sub-tree Objects}, \text{Blob Objects}\}$$

---

## 2. Git Identifiers (Git IDs / SHA-1)

A **Git ID** (also called _Object ID_, _hash_, _checksum_, or _SHA-1_) serves as both the unique identifier and address of an object within the object store.

- **Length & Base:** 40-character hexadecimal string representing a 160-bit cryptographically derived hash value.
- **Deterministic Computation:** Hash values are generated directly from object payload data combined with its type header and byte size.

$$\text{Git ID} = \text{SHA-1}\left(\text{type} + \text{" "} + \text{bytesize} + \text{"\0"} + \text{content}\right)$$

### Key Properties

1. **Deterministic Unique Mapping:** Identical contents, headers, and metadata strictly map to the exact same 40-character hexadecimal string.
2. **Avalanche Effect:** A minimal variation in the raw input payload (e.g., adding a single trailing space) forces a drastic, non-linear transformation in the resulting SHA-1 hash.

```
Input: "hi"           --> Hash: 45b9...
Input: "hi " (space)  --> Hash: 0b5d...

```

---

## 3. Low-Level Plumbing: `git hash-object`

Git commands are categorized into user-facing **Porcelain** commands (`git log`, `git commit`) and low-level **Plumbing** commands (`git hash-object`, `git cat-file`).

`git hash-object` computes the SHA-1 key for a given input file stream or payload directly:

```bash
# Write content to a file
echo "hi" > fileA.txt

# Calculate the SHA-1 hash of the file payload without writing to object store
git hash-object fileA.txt
# Output: 45b9...

# Modifying payload triggers avalanche effect
echo "hi " > fileA.txt
git hash-object fileA.txt
# Output: 0b5d...

```

---

## 4. Shortening Git Identifiers & Disambiguation

Because 40-character hex strings present high cognitive friction, Git allows abbreviated prefixes in CLI parameters and display options.

- **Standard Default Prefix:** **7 characters** (e.g., `git log --oneline`).
- **Minimum Threshold:** Requires **at least 4 characters** when passing IDs to Git commands (`git show <hash>`).
- **Disambiguation:** If a 4-character prefix matches more than one object in `.git/objects`, Git throws an ambiguity error, requiring additional characters until the prefix uniquely identifies a single object.

```bash
# View shortened 7-character commit IDs
git log --oneline

# Inspect object contents using a 4-character prefix
git show 45b9

```

---

## Key Takeaways

- Git encapsulates state using **4 core objects**: Commits, Tags, Trees, and Blobs.
- **Git IDs** are 40-character hexadecimal SHA-1 values derived directly from object type, size, and content.
- The **avalanche effect** guarantees that micro-changes produce distinct object IDs.
- **`git hash-object`** is a low-level plumbing command that calculates raw object hashes.
- Object IDs can be abbreviated to as few as **4 characters** provided the prefix remains unique across the object store.
