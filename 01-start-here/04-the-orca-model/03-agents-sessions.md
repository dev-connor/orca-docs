---
title: Agents & sessions
source: https://www.onorca.dev/docs/model/agents-sessions
---

## Overview

An agent session comprises a single CLI agent running in one terminal within a worktree. Orca monitors the lifecycle to maintain visibility into which sessions are active versus dormant without requiring manual tab inspection.

![Inline agent status on every worktree card — yellow while working, green when done](/whats-new/posters/agent-statuses.jpg)

## State Indicators

Agent tabs and worktree rows display consistent status symbols:

- **Spinner** — currently processing
- **Amber question mark** — awaiting user action (approval or input)
- **Emerald check** (dashboard) or **emerald dot** (sidebar) — completed or quietly active
- **Red dot** — obstructed, halted, or errored
- **Gray dot** — inactive
- **No indicator** — standard shell without recognized agent CLI

Status derives from terminal OSC title sequences and agent hooks emitted by Claude Code, Codex, and comparable tools.

## Agent Dashboard

Enabling **Settings → Experimental → Agent Dashboard** adds a kanban board in the sidebar displaying agents across worktrees.

### Board Columns

- **Needs You** — pending user permission or response
- **Working** — currently executing
- **Done** — completed sessions available for review
- **Idle** — quiet agents inactive for approximately 30 minutes (hidden by default)

Cards include host badges for SSH and Remote Orca Server workspaces. Local setups omit the badge.

### Display Options

Display as an in-window board or in a separate pop-out window.

### Search and Filtering

The toolbar offers searching by worktree, project, or agent name, plus filtering by Project, Workspace status, and PR/MR status.

### Card Details

Cards present the agent icon, session name, preview message, project icon, worktree name, and age. "Needs You" cards display amber tinting; "Done" cards show green.

## Launch Defaults

Orca initiates every supported agent with full-autonomy permission flags enabled—Claude receives `--dangerously-skip-permissions`, Codex gets `--dangerously-bypass-approvals-and-sandbox`, and similar equivalents apply to others. The worktree functions as the sandbox environment.

To customize launch parameters, navigate to **Settings → Agents**, expand the target agent, and modify **launch arguments**. A **Reset** option restores original settings.

## Restart Chip

Upon agent termination, a **Restart** chip displays on the tab, enabling one-click rehydration with the same working directory and agent configuration.

## Session Lifecycle

1. **Launch** — select an agent; Orca initiates the CLI
2. **Work** — OSC titles reflect state changes; terminal output displays with search and theming
3. **Idle** — Orca recognizes the transition and sends an agent-finished notification
4. **Exit** — process concludes; Restart chip becomes available
