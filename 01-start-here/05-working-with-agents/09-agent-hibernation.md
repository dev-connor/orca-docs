---
title: Agent hibernation
source: https://www.onorca.dev/docs/agents/hibernation
---

Agent hibernation enables Orca to pause idle background agent terminals and automatically resume them when you reopen a worktree. This feature helps manage memory when maintaining dozens of active worktrees.

## Overview

The system "lets Orca quietly stop those terminals once they've been done and untouched long enough, then resume the same session the next time you open the worktree." This is currently an experimental feature, disabled by default and accessible under **Settings → Experimental → Agent hibernation**.

## Hibernation Criteria

Terminals only pause when all conditions are met:

- Agent is in a completed state, not awaiting input
- Terminal isn't in an active or foreground-rendering worktree
- No keystrokes received since completion
- Agent supports resumable sessions (Claude, Codex, Gemini, Antigravity, OpenCode, Pi, MiMo Code, Droid, Grok, Devin, or OMP)
- Idle duration exceeds the configured threshold
- No mobile session is controlling the terminal
- No unresolved orchestration dispatch remains
- No active subagent roster attached to the pane

## Configuration

The idle window setting determines pause timing, with options ranging from 1 minute to 24 hours (default: 30 minutes). "The clock starts from the agent's last `done` update; any keystroke, new output, or returning to the agent's terminal tab resets it."

## Resumption Process

Upon reopening a hibernated worktree, "Orca relaunches the agent CLI with the same resume flags it would use from Agent Session History." The conversation, working directory, and provider session continue seamlessly.

## Limitations

Non-resumable terminals (Cursor CLI, Hermes, Copilot, Trae) remain active and don't hibernate.
