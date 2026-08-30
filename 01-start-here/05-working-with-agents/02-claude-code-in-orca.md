---
title: Claude Code in Orca
source: https://www.onorca.dev/docs/agents/claude-code
---

Claude Code serves as "Anthropic's agentic CLI" that integrates into Orca as a terminal agent with built-in account awareness and session management capabilities.

## Setup

The installation process involves three straightforward steps:

1. Install Claude Code via npm or Anthropic's documentation
2. Complete login from any terminal session
3. Orca automatically detects the `~/.claude` configuration without additional setup

## Launching

When you activate Claude Code from a worktree's terminal, Orca initializes it with that worktree as the working directory. The agent emits OSC title events for status indicators.

## Usage & Rate Limits

Orca monitors your local usage state and displays "current usage plus rate-limit proximity in the status bar," as documented in the usage tracking section.

## Account Hot-Swap

The platform supports managing multiple Claude accounts with single-click switching. Notably, "Switching accounts works even with live Claude sessions running," with built-in safeguards preventing authentication conflicts.

## Subagents and Teams

Background subagents and team members can display as expandable child rows within the worktree agent list and Agent Dashboard, with child selection focusing the lead terminal.

## Hooks & Memory

Claude Code supports per-repository hooks and memory files, surfaced through Orca's agent hooks and memory interface.
