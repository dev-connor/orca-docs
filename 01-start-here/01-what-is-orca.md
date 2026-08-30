---
title: What is Orca?
source: https://www.onorca.dev/docs
---

## Overview

Orca functions as "a desktop IDE for running multiple AI coding agents side by side." Each task receives its own git worktree, agent terminal, and browser tab, allowing coordination across Claude Code, Codex, Cursor CLI, and similar tools without branch management complications.

## When to Use Orca

- Run three agents simultaneously on the same bug and select the best solution
- Carefully review AI-generated code changes before deployment
- Centralize management of existing Claude Code, Codex, or Cursor CLI subscriptions
- Execute agents on remote infrastructure—via SSH, self-hosted servers, or on-demand VMs—while maintaining IDE functionality

## Intended Audience

Orca targets experienced developers who leverage AI to enhance productivity rather than replace human coding. The platform assumes users review code changes, maintain proper git practices, and value worktree organization. It is not designed for non-technical users seeking no-code automation.

## What Orca Is Not

- **Not a model provider** — it orchestrates existing agent subscriptions
- **Not a git management tool** — worktrees are standard git repositories supporting direct command-line operations
- **Not a managed hosting service** — it runs locally by default; remote execution uses user-controlled infrastructure

## Next Steps

The documentation recommends proceeding to installation instructions, followed by the first three-agent session walkthrough, then exploring remote execution options when ready.
