---
title: Orchestration
source: https://www.onorca.dev/docs/cli/orchestration
---

## Overview

Orchestration coordinates multiple agents through a structured system combining Runs (namespace + coordinator inbox), Tasks, Dispatches, supervised workers, messages, and decision gates. This layer is recommended when ownership, completion tracking, or directed acyclic graphs (DAGs) are needed.

## Core Model

The system operates on these key concepts:

- **Run** — persistent namespace and inbox that never schedules workers directly
- **Task** — work item with spec, dependencies, and status tracking (pending, ready, dispatched, completed, failed, blocked)
- **Dispatch** — single task attempt on a terminal with lifecycle authority
- **Message** — inbox communications including status updates, completions, and questions
- **Decision gate** — coordinator-owned question blocking task progression

## Preferred Supervised Loop

Create a Run and task, then start a worker:

```
orca orchestration run-create --objective "Split checkout QA and summarize blockers" --json
orca orchestration task-create --spec "Audit billing settings for mobile layout" --task-title "Billing audit" --json
orca orchestration worker-start --task <taskId> --worktree current --agent codex --json
```

Workers report completion with outcome status, task ID, and dispatch ID together.

## Messaging & Group Addresses

Group addresses enable directed communication: `@all`, `@idle`, `@claude`, `@codex`, and agent-specific targets. The check command retrieves messages FIFO from the oldest unacknowledged delivery.

## Decision Gates

Explicit gates block tasks until coordinator resolution:

```
orca orchestration gate-create --task <taskId> --question "Merge change?" --options '["yes","no"]' --json
orca orchestration gate-resolve --id <gateId> --resolution "yes" --json
```

## Recovery & State Management

Inspect dispatch state, read worker output, and reset orchestration state when intentionally abandoning it. Task IDs are clickable links focusing assigned terminals.
