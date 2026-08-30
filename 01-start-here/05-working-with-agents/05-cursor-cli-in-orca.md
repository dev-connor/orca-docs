---
title: Cursor CLI in Orca
source: https://www.onorca.dev/docs/agents/cursor-cli
---

Cursor CLI serves as Cursor's command-line agent, which Orca integrates with "first-class support — launch from the combobox, full OSC state detection, and restart chip on exit."

## Setup

The setup process involves three straightforward steps:

1. Install Cursor CLI according to Cursor's documentation
2. Complete an initial login
3. Orca automatically detects the CLI when it's available on the system PATH

## Launching

Users can select **Cursor** from the combobox to initiate the CLI, which runs "scoped to the worktree." The Cursor terminal user interface generates state events necessary for displaying agent status indicators.

## Model Selection

"Model selection is driven by Cursor's own settings. Orca doesn't override it — configure inside the CLI." This approach allows users to manage their model preferences directly through Cursor's native configuration rather than through Orca's interface.
