---
title: Linear items drawer
source: https://www.onorca.dev/docs/review/linear
---

Linear integration allows users to browse, create, update, and link Linear issues to worktrees alongside hosted review providers in the task drawer.

## Setup

Three configuration steps are required:

1. Access Settings → Integrations → Linear
2. Add a personal API token from Linear → Settings → API
3. Select desired teams for visibility

## Using Linear

Key features include:

- **Combined view**: GitHub and Linear issues appear together in the task drawer
- **Workspace mode**: "Has Workspace" filter shows only issues already linked to local worktrees or folder workspaces
- **Worktree creation**: Launching from a Linear issue opens the interactive workspace composer with pre-filled naming and automatic issue ID attachment. When available, Linear's suggested branch name is used rather than a title slug
- **Issue linking**: Edit worktree details to link or change issues via the Issue field with Linear chip, replacing previous provider links if needed
- **Issue updates**: Open detail views to modify status, assignee, priority, labels, and estimates using Linear's own priority icons
- **Rich context**: Agents receive inline images and media from issue descriptions, comments, and sub-issues in their prompt context
- **Draft preservation**: Form text persists if dialogs are dismissed accidentally during the same session
- **Pagination**: Long lists include a Load more action
- **Layout persistence**: List vs board views, grouping, ordering, columns, and filters persist across restarts per Linear workspace
- **Source memory**: Orca recalls the last-used task source per repository

Status synchronization to "In Progress" when creating worktrees is optional per team.

## Agents and CLI

Agents can read and write Linear through `orca linear` commands and the `orca-linear` skill, supporting MCP-compatible operations like `save-issue`, `list-issues`, and relation management, plus context flags such as `--activity` and `--full`.
