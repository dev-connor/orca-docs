---
title: Chat UI (native chat)
source: https://www.onorca.dev/docs/agents/native-chat
---

## Overview

An experimental view layered on supported agent terminal sessions that provides a structured transcript and composer interface. The terminal remains the primary interface, while Chat UI offers an alternative view for the same PTY. It supports transcript decoding for "Claude, Codex, Grok, and OMP" agents.

## Enable

1. Access Settings → Experimental → Chat UI
2. Activate the Chat UI toggle
3. Optionally configure Default view as Chat UI for new supported agent tabs (or keep Terminal for TUI-first experience)
4. Toggle between Chat UI and terminal views from the agent pane once enabled

## Composer

The message input interface includes:

- Message sending and turn cancellation capabilities
- File and image attachment support (when host permits)
- Draft retention across disconnect/reconnect cycles
- Slash command access via `/` character with agent-aware skill discovery
- Model and options pills for adjusting settings like thought level and mode
- Agent-specific features: Claude model selection from installed CLI, Codex direct model selection, and Grok model/reasoning effort controls
- Pre-launch draft options that become disabled during active sessions

## Questions from the Agent

Claude's structured permission cards (like AskUserQuestion) render directly in the transcript for inline responses via the composer, including sessions on paired Remote Orca Servers.

## Availability

Chat UI is available on desktop for local and remote agent sessions. The mobile companion utilizes similar chat-style transcript patterns for paired sessions.

**Note:** The feature remains experimental with ongoing refinements to transcript fidelity and terminal parity.
