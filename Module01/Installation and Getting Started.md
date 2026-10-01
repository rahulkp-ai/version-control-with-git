# Installing & Getting Started with Git (CLI)

## 1. Verifying & Installing Git

- **Check Installation**: Open your terminal (CLI) and run:

```bash
git --version

```

- **Install**: If no version is returned, download and install Git from [git-scm.com](https://git-scm.com/).

---

## 2. Git Command Syntax

A standard Git command follows this structure:

$$\text{git} + \text{command} + [\text{flags}] + [\text{arguments}]$$

- **Base Command**: Begins with `git` followed by the action (e.g., `git status`).
- **Flags / Options / Switches**: Modify command behavior.
- _Short flag_: Starts with a single dash (e.g., `git status -s`).
- _Long flag_: Starts with double dashes (e.g., `git status --short`).

- **Arguments**: Targets for the command, such as specific file paths (e.g., `git add file.txt`).

---

## 3. Accessing Git Documentation & Help Syntax

### Help Commands

- **In-depth Manual**: `git help <command>` or `git <command> --help` (opens detailed documentation).
- **Overall Help**: `git help` or running `git` alone.
- **Concise Options Summary**: `git <command> -h` (e.g., `git init -h`).

### Documentation Notation Conventions

## 4. Git Configuration (`git config`)

g
| Symbol / Format | Meaning | Example |
| --- | --- | --- |
| `-` / `--` | Flag, option, or switch indicator | `-p` or `--patch` |
| `|`co | Logical **OR** (choose one option) | `-p | --patch` |
| `[...]` | Optional parameters | `[<pathspec>]` |
| `<...>` | Required placeholder (replace with actual value) | `<command>` |
| `[<...>]` | Optional placeholder | `[<file>]` |
| `(...)` | Grouping for disambiguation or mandatory choice | `(-p | --patch)` |
| `--` | Standalone delimiter separating options from paths | `git checkout -- <file>` |
| `...` | Indicates multiple occurrences allowed | `<path>...` |

### Configuration Scopes & Precedence

1. **Local** (`--local` or omitted): Applies only to the current repository. _(Highest precedence)_
2. **Global** (`--global`): Applies to all repositories for the current OS user.
3. **System** (`--system`): Applies to all repositories across all users on the machine. _(Lowest precedence)_

### Essential Configuration Commands

- **Set User Identity**:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

```

- **Set Default Text Editor**:

```bash
git config --global core.editor "nano"

```

- **Read Configuration Values**:

```bash
git config user.name
git config user.email
git config core.editor

```
