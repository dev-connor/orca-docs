---
title: Worktree checkpoints
source: https://www.onorca.dev/docs/cli/worktree-checkpoints
---

Every Orca worktree includes a lightweight, free-text **comment field** that displays a status snapshot of the worktree's current activity. Agents can modify this field through the CLI, and it serves as the recommended approach for keeping team members informed without relying on chat.

## The pattern

```
orca worktree set --worktree active --comment "reproduced auth failure; testing credential-chain fix" --json
```

## Card status (optional)

Alongside the free-text comment, update the workspace card status when transitioning between phases:

```
orca worktree set --worktree active \
  --comment "fix implemented; running integration tests" \
  --workspace-status in-progress \
  --json
```

Available statuses include: `todo`, `in-progress`, `in-review`, `completed`, or custom identifiers your workspace defines.

## Good checkpoint moments

- Completed a meaningful implementation segment
- Confirmed or rejected a hypothesis
- Finished a code review
- Encountered a blocker (external dependency, upstream issue, permission restriction)
- Shifting between investigation and solution, or solution and verification phases

## Format

The opening line describes what occurred, where it occurred, and the current status or subsequent action.

```
orca worktree set --worktree active --comment "added debounce to SearchBar onChange (src/components/SearchBar.tsx); ready for review
goal: reduce redundant API calls per #298" --json
```

## Reading before writing

Before updating the comment, retrieve existing content to avoid overwriting user-defined context:

```
orca worktree current --json
```

Retain relevant information, discard outdated details, and integrate your new update.
