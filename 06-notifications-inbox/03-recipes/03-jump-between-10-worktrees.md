---
title: Jump between 10 worktrees
source: https://www.onorca.dev/docs/recipes/jump-worktrees
---

Managing numerous worktrees requires strategic tools. Orca provides the Jump Palette, Restart chip, and agent state indicators specifically designed for handling this scale of work.

## Steps

1. Press `Cmd-J` to open the jump palette and enter a task name fragment. Use Enter to jump or Shift-Enter to open in a split view. The Tab key filters results by host or project when dealing with extensive lists.

2. Review the sidebar to identify active agents (marked with green dots). Prioritize worktrees showing yellow indicators, as these require immediate attention.

3. Each worktree includes a Restart chip that relaunches exited agents—particularly useful for resuming work after system sleep.

4. Leverage the persistent notification bell to process the "agent finished" queue. Clicking notifications automatically navigates you to the relevant worktree.

## Hygiene

Regularly remove merged worktrees to maintain optimal performance. Since deletion is streamlined in Orca—removing both the worktree and branch simultaneously—accumulated merged worktrees unnecessarily degrade jump palette responsiveness.
