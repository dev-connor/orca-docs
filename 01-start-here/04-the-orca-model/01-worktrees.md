---
title: Worktrees
source: https://www.onorca.dev/docs/model/worktrees
---

## Overview

Orca operates with worktree-native functionality, giving each task its own on-disk repository copy via `git worktree`. This architecture enables parallel agent work safely, as agents never interfere with each other's files.

## The Model

The system operates on several key principles:

- Each repository maintains a **base ref** (typically `origin/main`)
- Every worktree has its own **start-from ref** that determines what it branches from
- Worktrees possess individual branches, separate file directories, and dedicated agent terminals
- Deletion removes both the directory and branch, with confirmation prompts

## Per-Feature Lifecycle

The workflow follows five stages:

1. **Create** — specify task name, select start-from reference, optionally link to GitHub/Linear/Jira/GitLab
2. **Work** — use agent terminals, editor tabs, browser tabs, and terminal panes within worktree scope
3. **Review** — examine diffs against start-from ref, annotate changes, review attribution
4. **Ship** — commit, push, open pull requests, monitor checks inline
5. **Archive or delete** — single-click removal of worktree and branch

## Background Creation

The Create Worktree dialog closes immediately upon submission. Git operations continue in the background while you continue using Orca. The new worktree appears in the sidebar with a progress indicator, displaying live setup status until checkout completes. You can switch between worktrees, monitor progress, or cancel from the in-tab panel.

## Start-From Picker Options

When creating worktrees, you can branch from:

- The repository's base ref (fastest option)
- Another local branch (useful for stacking work on reviewed PRs)
- A specific commit SHA
- An existing remote branch (Orca fetches and checks it out)

## Shared Directories & Gitignored Files

New worktrees arrive as clean checkouts without dependencies, caches, or local secrets in gitignored paths. Orca addresses this through three methods:

1. **Worktree Shared Paths** — configured per repository in Settings, materializing paths from primary checkout into new worktrees via APFS clone-copy on macOS or symlinks otherwise

2. **`worktree.sharedDirectories` in `orca.yaml`** — repository-checked-in listing of gitignored directories to share via symlink, suitable for large rebuildable trees like `node_modules` or `.cache`. These entries must exist as directories in the primary checkout and be gitignored

3. **`.worktreeinclude` at repo root** — lists gitignored files or directories to copy (not symlink) into each new worktree for independent ownership. Supports comments and blank lines; only literal paths work (no globs or negation)

```yaml
# orca.yaml (repo root)
worktree:
  sharedDirectories:
    - node_modules
    - .cache
```

```
# .worktreeinclude (repo root)
.env
.env.local
.vscode/settings.json
```

## Create Dialog Features

The Create Workspace dialog includes type-ahead comboboxes for **Project** and **Run on**:

- Type to filter; Enter commits the selected row
- **Project** keeps "Add a new project" pinned at bottom
- **Run on** lists ready hosts and recipes, plus hosts needing project setup
- **Agent** selector can set defaults, including Blank Terminal
- Link GitHub PRs, Linear issues, GitLab MRs, or Jira issues from the name field

## Emoji Workspace Names

Type Slack-style shortcodes (`:rocket:`) in the workspace name field to select emoji. This picker activates when double-clicking to rename worktrees or editing worktree details. Orca converts emoji to readable shortcodes for branch names (🚀 becomes `rocket`), and Jump Palette search matches emoji-named workspaces by their shortcode fragments.

## Branch Naming

By default, Orca derives branch names from workspace names or linked work items (GitHub PR, Linear/Jira issue, GitLab MR). Expand the **Advanced** drawer in the Create Worktree dialog to set an explicit branch name. The same drawer lets you designate an active worktree as the **Parent workspace** for nesting in the sidebar (without affecting Git history).

When creating from a Linear issue, Orca uses Linear's own branch name suggestion instead of only slugifying the title.

## Sidebar Layout

The sidebar groups worktrees by **project** by default, with top-level rows representing projects that expand into active worktrees. A dedicated filter input narrows the list without affecting global search.

The filter menu organizes options under **Show** (Hosts and projects) and toggles for:

- **Sleeping** workspaces
- **Except default branch** (only when sleeping is hidden)
- **Default branch** workspaces
- **Automation-created** workspaces
- **CLI-created** workspaces
- **Other-client** workspaces
- **Detached HEAD** workspaces

You can pin worktrees to keep long-running work visible. Right-clicking reveals archive, sleep, and delete actions. Keyboard shortcuts: `Cmd-Shift-Backspace` (macOS) or `Ctrl-Shift-Backspace` (Windows/Linux) initiates deletion; hold `Cmd`/`Ctrl` for multi-selection or `Shift` for contiguous ranges.

When worktrees have nested children, the context menu offers **Sleep with Descendants** and **Delete with Descendants** options.

## Resource Manager Cleanup

Access **Resource Manager → Clean up workspaces** to review and remove workspaces across your setup. The list includes local worktrees, main worktrees, folder workspaces, and disconnected SSH host workspaces, with search, filter, and sort capabilities.

## Preserved Branches

Bulk deletion still removes on-disk folders. If Git refuses to drop a local branch with unmerged commits, Orca preserves those branches and displays a toast with a **Review N Branches** option, allowing selective force-deletion.

## Multi-Repo Project Groups & Folder Workspaces

When importing a parent folder with multiple Git repositories, Orca can group them under a **project group**. Create a **folder workspace** by hovering the project group's header and clicking the **+** action. This binds a feature's task source to one underlying repository while keeping the workspace grouped with siblings.

## Using Plain Git

Every Orca worktree is a genuine Git worktree accessible via terminal. External worktrees created with `git worktree add` stay hidden until shown in Orca. The sidebar displays a **hidden worktrees** card when repositories contain such worktrees.

In **Settings → General → Workspace**, configure global defaults for external-worktree sources. These apply to current and future worktrees on that host. In a project's **Non-Orca worktrees** dialog, override source settings for that specific project.

If you run `git worktree remove` from the CLI, Orca detects and cleans up its own state during the next refresh cycle.
