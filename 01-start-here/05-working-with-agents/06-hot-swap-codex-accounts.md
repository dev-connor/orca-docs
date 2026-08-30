---
title: Hot-swap Codex accounts
source: https://www.onorca.dev/docs/agents/codex-hot-swap
---

Orca enables users to quickly switch between multiple Codex accounts without requiring re-authentication or manual configuration changes. This functionality also applies to Claude Code accounts.

## Add accounts

To set up multiple accounts:

1. Log into each Codex account from a terminal at least once to store authentication data in `~/.codex`
2. Navigate to Settings → Agents → Codex Accounts
3. Orca displays all detected accounts alongside their usage statistics and token limits
4. Assign descriptive names to each account (e.g., "personal", "work")

## Swap accounts

Simply click the Codex indicator in the status bar to access the account switcher. Select your desired account; subsequently launched Codex sessions will use it. Existing active sessions retain their original account until restarted.

## System default

The **System default** option represents your primary host Codex login stored in `~/.codex`. Managed accounts operate in isolated environments without modifying the system login. Choose this option when you want launches to align with terminal-based `codex` commands outside Orca.

## Configuration synchronization

For managed accounts, Orca syncs settings from your primary `~/.codex/config.toml` into the active runtime environment. If this source file is unavailable, empty, or unreadable, a warning appears. The system preserves the most recently synchronized settings until the source file becomes accessible.

## Key behaviors

- Account switching happens instantly without re-authentication
- Running Codex processes maintain their current account until restarted
- Status bar usage data reflects the actively selected account
- System restarts preserve the active account at restart time

## Claude Code accounts

The Claude account switcher operates identically, using `~/.claude` as its data directory.
