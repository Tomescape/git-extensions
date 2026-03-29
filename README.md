# git-extensions

A collection of custom git commands.

## Installation

Copy the scripts you want to a directory that is included in your `$PATH` (e.g. `/usr/local/bin` or `~/bin`), then make them executable:

```bash
cp git-squash /usr/local/bin/
chmod +x /usr/local/bin/git-squash
```

To install all extensions at once:

```bash
cp git-* /usr/local/bin/
chmod +x /usr/local/bin/git-*
```

Once installed, git will automatically discover any executable named `git-<command>` on your PATH and expose it as `git <command>`.

---

## Commands

### git squash

Squash the last N non-merge commits into a single commit.

Merge commits within the range are included in the squash but are not counted toward N.

**Usage**

```
git squash <count> <message>
```

| Argument  | Description                                      |
|-----------|--------------------------------------------------|
| `count`   | Number of non-merge commits to squash (integer ≥ 1) |
| `message` | Commit message for the resulting squashed commit |

**Examples**

```bash
# Squash the last 3 non-merge commits
git squash 3 "feat: add user authentication"

# Squash 10 commits of work-in-progress into one clean commit
git squash 10 "refactor: consolidate payment module rewrite"
```

**Notes**

- The working tree must be clean (no uncommitted changes) before running.
- Squashing past the root commit is not allowed.
