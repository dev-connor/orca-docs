---
title: Agent Session History
source: https://www.onorca.dev/docs/agents/session-history
---

## Overview

Browse and resume past Claude, Codex, Cursor, Gemini, and other agent sessions from Orca's right sidebar. The system scans on-disk session transcripts that agent CLIs generate and displays them in the **Agent Session History** panel. Users can select a past session, click **Resume**, and Orca executes the agent's resume command in a fresh terminal with the same working directory and session ID.

## Open the Panel

Access the right sidebar and navigate to the **Agents** tab. The panel header displays a count (e.g., "12 shown · 47 recent") and includes a search box for filtering by session title, working directory, branch, model, or conversation preview text.

## Scope

A toggle at the panel top determines which sessions display:

- **Workspace** — sessions from the current workspace or worktree
- **Project** — sessions associated with the active Orca project
- **All** — every session found across all agents on the machine

Remote workspaces can browse local history, but resume actions only function from local workspaces.

## View Options

The view-options menu controls:

- **Agents** — enable or disable individual CLIs (Claude, Codex, Hermes, Pi, OMP, Prime Agent, Cursor, Gemini, and others)
- **Sort** — by "Last updated" or "Created"
- **Group** — by "Project," "Folder," or "Agent"
- **Hide empty sessions** — exclude sessions with no recorded messages

## Resume a Session

Clicking a session row displays its details, including working directory, branch, model, message count, and conversation turns. Available actions include:

- **Resume** — opens a new terminal and runs the agent's resume command
- **Copy resume command** — copies the shell command for external terminal use
- **Copy session ID** / **Copy log path** — for scripting or bug reports
- **Open log** / **Reveal log** — view the transcript in Orca or the OS file manager
- **Open cwd** — open the session's working directory as a workspace

## Transcript Sources

Orca reads from each agent's session store (Codex's `~/.codex/sessions`, Claude's `~/.claude` history, Cursor's session log, etc.). No additional configuration is required; transcripts appear automatically after the next scan.
