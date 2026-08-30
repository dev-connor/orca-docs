---
title: How to use GLM-5.2 in Orca ADE
source: https://www.onorca.dev/docs/agents/glm-agent
---

## Overview

GLM-5.2 integrates with Orca through existing agent harnesses. Users configure the model in Claude Code, OpenCode, Cline, Kilo Code, Roo Code, Droid, OpenClaw, or similar CLI agents, then launch from Orca's picker. The platform provides isolated worktrees, terminal panes, browser access, code review workflows, and session management.

## Prerequisites

An active Z.ai CodePlan subscription with GLM Coding Plan access is required. OpenAI-compatible harnesses also need a Z.ai API key. Orca does not include or resell GLM access. Configuration details follow Z.ai's latest model guide.

## Configuration Instructions

**Claude Code**: Modify `~/.claude/settings.json` to override model settings:
- Set `ANTHROPIC_DEFAULT_SONNET_MODEL` and `ANTHROPIC_DEFAULT_OPUS_MODEL` to `glm-5.2[1m]`
- Maintain `CLAUDE_CODE_AUTO_COMPACT_WINDOW` at `1000000`
- Run `/status` to verify the active model

**OpenAI-Compatible Harnesses**: Configure provider settings with base URL `https://api.z.ai/api/coding/paas/v4`, add Z.ai API key, set custom model to `glm-5.2`, and configure context window to `1000000`.

**OpenClaw**: Manually add GLM-5.2 to `~/.openclaw/openclaw.json` with specified parameters, then restart the gateway using `openclaw gateway restart`.

## Key Principle

Configure GLM-5.2 in the agent's provider/model settings, then allow Orca to launch that harness within the appropriate worktree.
