---
title: Tabs, panes & split layouts
source: https://www.onorca.dev/docs/model/tabs-panes-splits
---

Orca's pane system enables users to monitor multiple agents simultaneously while preserving context. The architecture organizes tabs into tab groups, which then divide into layouts.

## Tabs

Each tab contains a single element—terminal, editor buffer, browser, diff view, or pull request. These tabs exist within a tab group and support the following interactions:

- Reorder tabs vertically within groups via dragging
- Move tabs between groups by dragging across them
- Close all editor file tabs in the active worktree using `Cmd+Option+W` (macOS) or `Ctrl+Alt+W` (Windows/Linux)
- Visual focus indicator via active-tab color bar

### Switching tabs

| Action | macOS | Linux / Windows |
|--------|-------|-----------------|
| Next/previous tab (all types) | `Cmd+Shift+]` / `Cmd+Shift+[` | `Ctrl+Shift+]` / `Ctrl+Shift+[` |
| Next/previous tab (same type) | `Cmd+Option+]` / `Cmd+Option+[` | `Ctrl+Alt+]` / `Ctrl+Alt+[` |
| Previous recent tab | `Ctrl+Tab` | `Ctrl+Tab` |

Users can customize these bindings in Settings → Shortcuts; existing installations preserve customizations in `~/.orca/keybindings.json`.

## Split panes

Dragging tabs to pane edges creates splits:

- **Right edge** creates horizontal left/right division
- **Bottom edge** creates vertical top/bottom division

Splits support nesting, allowing complex layouts combining agent terminals, diff views, browsers, and editors simultaneously. Terminal tabs additionally support internal splitting via the tab menu using "Split terminal right" or "Split terminal down" options.

## Pinned boundaries

Pane boundaries remain stationary; window resizing preserves layout positioning. Boundary positions are maintained per worktree.

## Tab groups across worktrees

Each worktree maintains independent tab layouts. Switching worktrees replaces the entire pane tree, restoring previously arranged tabs in their original positions.
