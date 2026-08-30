---
title: Diff viewer
source: https://www.onorca.dev/docs/review/diff-viewer
---

Orca includes a specialized diff viewer built for reviewing AI-generated code with comprehensive tooling. Every worktree has a built-in diff against its start-from ref.

## Features

The viewer provides:

- **Combined diff** spanning all staged, unstaged, and untracked files
- **Line numbers** on both sides, which users can toggle on/off
- **Image diffs** with side-by-side, swipe, and onion-skin comparison modes for binary images
- **HTML preview** — in combined views, existing HTML sections display an "Open Preview to the Side" option for viewing working-tree HTML in a side browser split
- **Merge-conflict UI** offering three-way views and inline resolution options
- **Staging by hunk or line** — visual equivalent to `git add -p`

## Scoping

The default view shows changes relative to the worktree's start-from reference. Users can modify this to compare against any commit, branch, or base reference using the diff toolbar.

## Word Wrap

Long lines wrap without horizontal scrolling when enabled. The setting defaults to off and can be toggled via the actions menu or configured globally in Settings.

## File Tree

Combined diffs display a collapsible file tree alongside hunks. The tree width is resizable and persists across sessions.

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| j / k | Navigate to next/previous changed file |
| n / p | Navigate to next/previous hunk |
| F7 / Shift+F7 | Next/previous change in active editor |
| s | Stage current hunk |
| c | Start a comment |
