# Git's Graph Model & Directed Acyclic Graphs (DAGs)

---

## 1. What is a Graph?

A **graph** is a discrete structure used to model relationships between connected entities.

- **Nodes (Vertices):** Represent individual entities or objects.
- **Edges (Lines):** Represent connections or relationships between nodes.

$$\text{Graph } G = (V, E) \quad \text{where } V \text{ is a set of vertices (nodes) and } E \text{ is a set of edges.}$$

**Common Examples:**

- Family trees (ancestor/descendant relationships)
- File systems (directories and files)
- Social networks (user connections)
- Git commit history

---

## 2. Directed Acyclic Graph (DAG) Essentials

Git represents project history using a specific category of graph called a **Directed Acyclic Graph (DAG)**.

### Key Components

1. **Directed Graph:**

- Edges have a defined orientation (represented visually as arrows).
- Edge direction depends strictly on how the relationship between two nodes is defined.
- _Example:_ In a generational model containing nodes $[\text{Grandparent}] \to [\text{Parent}] \to [\text{Child}]$:
- Pointing toward _child_ yields forward orientation ($\to$).
- Pointing toward _parent/ancestor_ yields reverse orientation ($\leftarrow$).

2. **Acyclic Property:**

- Contains **no closed loops or cycles** (non-circular).
- It is impossible to traverse the graph along directed edges and return to the starting node.

$$\text{Path } P = (v_0, v_1, \dots, v_k) \implies v_0 \neq v_k \quad \forall P \in \text{DAG}$$

| Graph Type  | Properties                                                     | Path Traversal Example                          |
| ----------- | -------------------------------------------------------------- | ----------------------------------------------- |
| **Acyclic** | No circular paths exist. Traversal is strictly unidirectional. | $C \to B \to A$ (cannot return to $C$)          |
| **Cyclic**  | Contains at least one path where start node equals end node.   | $A \to B \to C \to A$ (infinite loop potential) |

---

## 3. Git's Internal Graph Structure

Git structures a repository's full commit history as a DAG:

- **Nodes = Commits:** Each node represents an immutable snapshot of the repository state.
- **Edges = Parent References:** Directed arrows point strictly from a **child commit to its parent commit(s)** (pointing backward in time toward ancestors).

### Branching and Merging Mechanics

```
  (Commit B)
   ^       \
  /         v
(Commit A)  (Commit D)
  \         ^
   v       /
  (Commit C)

```

1. **Branching (Divergence):**

- Occurs when a single commit has **more than one child commit**.
- In the diagram above, **Commit A** has two children (**Commit B** and **Commit C**).

2. **Merging (Convergence):**

- Occurs when a single commit has **more than one parent commit**.
- **Commit D** is a merge commit referencing both **Commit B** and **Commit C** as direct parents.

---

## 4. Visualizing Git Graphs

### Graphical Clients (e.g., Sourcetree)

- Renders commits chronologically, typically with the **most recent commit at the top**.
- Explicit arrowheads are omitted; directionality is **implied by vertical position** (top commits point down to older parent commits).

### Command Line Interface (CLI)

View the commit graph directly in your terminal using formatted `git log` flags:

```bash
git log --graph --oneline --all

```

- **CLI vs. GUI:** Terminal tools provide fast, native access to graph topology, while graphical clients assist in visualizing dense, highly concurrent branching structures.

---

## Key Takeaways

- Git uses a **Directed Acyclic Graph (DAG)** to track repository history without risk of infinite history loops.
- **Nodes** are commits; **Edges** point backward from child commits to parent commits.
- **Branches** represent nodes with multiple children; **Merges** represent nodes with multiple parents.
