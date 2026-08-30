---
title: Quick Open & Jump Palette
source: https://www.onorca.dev/docs/model/quick-open
---

Orca provides keyboard-first navigation tools to streamline movement across multiple worktrees and tabs.

## Quick Open (Cmd-P)

This feature enables file searching within the current worktree. Users type a filename fragment, and Orca ranks results by recency and match quality, opening selected files in new editor tabs. The interface prioritizes filenames in results, abbreviating parent directories when space is limited. Notably, "gitignored files are included in results — they're surfaced as a second pass after tracked matches," allowing frequently-accessed build outputs and configuration files to remain discoverable without cluttering primary results.

## New-tab Omnibox (+)

The tab strip's plus icon provides unified search across open tabs, files, URLs, and agents. File results follow the same filename-forward layout as Quick Open. The system intelligently prefers jumping to already-open editor buffers rather than duplicating files. Users can perform web searches by typing naturally, with multi-word phrases promoting search results. Prefixing queries with `?` bypasses file and tab matching for immediate searching.

## Worktree Jump Palette (Cmd-J)

This comprehensive navigation tool searches across all worktrees and tabs simultaneously. The search accepts repository or worktree name fragments, automatically including non-archived worktrees regardless of sidebar visibility. Users can press Tab to access host and project filtering menus, which display as removable chips.

Results encompass recent agent sessions and terminals, recent worktrees, projects, all worktrees organized by repository, PR/MR metadata matches, and open tabs. When queries match both tabs and worktrees, "the palette interleaves a short preview of each section so neither primary list is buried." Users can press Shift-Enter to open worktrees in new splits, and when no existing worktree matches, create one using the typed text as its name.
