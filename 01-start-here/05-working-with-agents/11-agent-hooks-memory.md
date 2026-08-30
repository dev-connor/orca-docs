---
title: Agent hooks & memory
source: https://www.onorca.dev/docs/agents/hooks-memory
---

Orca integrates with existing agent hook and memory conventions from Claude Code and Codex. The system reads these configurations, respects them, and provides IDE-level UI support where applicable.

## Per-repo hooks

Orca accesses each repository's `.claude/` and `.codex/` configuration directories. Any hooks already configured will execute automatically when Orca launches an agent within that repository's worktree.

## Worktree setup hooks

Users can configure commands to run automatically following worktree creation—such as `pnpm install`, `direnv allow`, or custom scripts for restoring `.env` files. These are managed through Settings → Repository → Hooks.

## Memory files

The agent-owned memory files (`CLAUDE.md` for Claude and `AGENTS.md` for Codex, located at repo root or nested directories) remain untouched by Orca. They appear in the file explorer as standard files, allowing inline editing.

## Agent status hooks

"Settings → Agents → Agent status hooks controls the Orca-managed hooks that report working / waiting / done into the UI." Disabling this setting removes managed hooks and prevents reinstallation; re-enabling restores functionality without requiring an app restart. CLI commands available: `orca agent hooks status|on|off --json`.

## Surviving a restart

Hook endpoints are persisted to disk and re-sourced on each invocation, enabling long-running agent sessions to maintain connection to the live Orca server following application restarts. The Orca CLI provides a worktree status field that agents can update independently via worktree checkpoints.
