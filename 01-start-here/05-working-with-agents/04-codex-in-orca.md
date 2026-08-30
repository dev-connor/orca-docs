---
title: Codex in Orca
source: https://www.onorca.dev/docs/agents/codex
---

Codex is OpenAI's agentic CLI that integrates deeply with Orca, preserving account identity across usage, hot-swap, and restart operations.

## Setup

1. Install Codex following OpenAI's documentation
2. Log in from any terminal
3. Orca reads `~/.codex` for accounts and credentials

## Launching

Select **Codex** from the agent combobox. Orca launches the tool with the worktree as the current working directory and routes authentication through the currently selected account.

## Account Hot-Swap

Multiple Codex accounts can be maintained to extend rate limits. Orca's switcher changes the active account without requiring re-login or configuration modifications. (See separate documentation on hot-swapping accounts.)

## System Default vs Extra Accounts

The **System default** option uses your actual `~/.codex` login. Additional accounts managed by Orca receive isolated home directories under Orca's account data, keeping credentials and rollouts separate. New launches follow the active account; existing sessions retain their original home until restarted.

## Nested Task Subagents

When Codex creates Task subagents, Orca displays them as child rows under the parent in the agent list and dashboard. Expand the chevron to view children; clicking a child focuses the parent terminal.

## Continue in New Session

From an agent terminal's header or menu, choose **Continue in New Session…**. This starts a fresh session and injects a bounded handoff prompt from prior transcript or context, leaving the original session unchanged.

## Restart Chip

When Codex exits, the restart chip relaunches it with the same account. To restart with a different account, use the switcher first.

## Usage & Rate Limits

Orca displays local Codex usage state for the active account in the status bar.

## Codex on Windows (WSL)

On Windows, run Codex from host or WSL. WSL-hosted accounts receive isolated home directories within the distro, mapped back as paths for auth, with launches and rate-limit fetches routed through the selected distro.
