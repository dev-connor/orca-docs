---
title: Usage & rate-limit tracking
source: https://www.onorca.dev/docs/agents/usage-tracking
---

Orca monitors local usage data for Claude Code, Codex, Gemini, OpenCode, Kimi Code, and MiniMax, displaying this information in the status bar to help users track their proximity to rate limits before agent operations are interrupted.

## What's shown

- Active account's current usage relative to its plan
- Reset timing for various rate-limit windows (5-hour, daily, weekly, and Claude Fable weekly where available)
- Warning indicator when usage exceeds 80% of any limit

## How it works

The system reads usage information stored locally by each agent on disk (in directories like `~/.claude` and `~/.codex`). "No API calls, no extra auth" are required. The displayed usage reflects the agent's own record-keeping rather than real-time data, updating only when the agent writes new information.

## Multi-account accounting

"The status bar always reflects the _active_ account." Users can view other configured accounts and their respective usage through the account switcher.

## Usage roster

Clicking the usage indicator opens a popover listing all tracked providers with their plan, reset timing, and per-window usage bars. The list prioritizes providers with the tightest limits first.

**View options:**

- Detailed view with full bars, labels, and percentages
- Compact view showing only the tightest window per provider

Users can configure appearance settings to display "% used" or "% remaining." Unavailable accounts display status messages like "not signed in" or "Usage unavailable."

### Mobile

The companion app's Accounts screen provides the same usage information and account switching. When Codex earns rate-limit reset credits, users can redeem them from this interface.

## Estimated cost (Stats)

Some statistics may display estimated costs for recognized model families. Rows marked "inferred pricing" rely on Orca's pricing table rather than provider billing data; "Prefer the provider console for authoritative spend."
