---
title: Supported agents
source: https://www.onorca.dev/docs/agents/supported
---

Orca provides built-in integration with numerous CLI-based coding agents, all launchable with a single click through the agent picker.

## Permissions Default

The platform pre-fills permission-bypass flags for each supported CLI agent to streamline workflows. As explained in the documentation, "worktrees are disposable: an agent running in its own checkout can experiment without you re-confirming every shell command, and you can still cherry-pick or discard the diff before merging."

Users can toggle between **Yolo** and **Manual** launch modes via Settings → Agents → Agent Permissions. Custom configurations remain untouched when global permission settings change.

## Supported Agents

The platform ships with pre-configured access to 40+ agents, including:

- **Deep integration**: Claude Code, Codex, Cursor CLI (usage tracking, hot-swap capabilities)
- **Auto-setup agents**: GitHub Copilot CLI, Grok, OpenCode, Gemini, Aider, Continue, Devin, and many others
- **Feature-rich support**: Various agents offer hooks, status indicators, session history, and usage/rate-limit tracking

Notable integrations include Prime Agent, OMP, Pi, and regional options like Kimi, Qwen Code, and Trae.
