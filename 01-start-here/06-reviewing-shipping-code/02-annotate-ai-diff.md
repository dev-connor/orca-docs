---
title: Annotate AI Diff
source: https://www.onorca.dev/docs/review/annotate-ai-diff
---

Annotate AI Diff serves as Orca's inline code review system for agent-generated changes. This feature allows reviewers to attach comments directly to specific diff lines and submit them collectively to the agent for revision, eliminating the need to manually track line numbers or switch contexts.

## Leave a comment

The commenting process involves three straightforward steps:

1. Position your cursor over any diff line to reveal a **+** symbol in the gutter
2. Click the symbol (or press `c`)
3. Enter your feedback using markdown formatting, then press `Cmd-Enter` to save or `Esc` to cancel

Comments remain anchored to their specific lines and track correctly even when the diff undergoes modifications.

## Send the batch

Upon completing your review, select **Send to agent** at the diff's top. The system composes a single prompt containing all your line-anchored comments and displays a **Send notes to** menu listing available agents for that worktree. You can select an existing agent or initiate a new one from this menu.

The keyboard shortcut remains unassigned by default to prevent conflicts. You can configure it under Settings → Shortcuts to trigger the send menu from the keyboard.

## Why batch?

Submitting comments individually causes agents to revise inconsistently. Batching maintains feedback coherence through unified thinking and a single revision pass, significantly improving outcomes.

## Reply, resolve, re-review

Comments persist after agent revisions, enabling verification of corrections. Use the **Resolve** button to collapse threads. Any unresolved comments become part of the subsequent batch when sending again.
