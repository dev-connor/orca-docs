---
title: Commit & push from Orca
source: https://www.onorca.dev/docs/review/commit-push
---

## Commit

Users can stage changes by hunk or file from the diff viewer, then compose a commit message in the bottom panel. The interface offers a "Generate with AI" option to have Orca draft messages from staged changes. Committing uses keyboard shortcuts (Cmd-Enter on macOS, Ctrl-Enter on Windows/Linux).

Repository pre-commit hooks execute normally. When hooks fail, Orca displays the output inline. Failed commits trigger a "Fix with AI" option that starts the default agent with hook output, the attempted message, and staged files—focused solely on repair without attempting to bypass hooks or force commits.

## Push

The Push action sends the worktree's branch to `origin`, automatically setting upstream on first push. Orca prevents silent force-pushes when branches lag behind.

For rewritten history scenarios, "Force push with lease" appears as an explicit, separate action showing the commit count and upstream branch name. This uses `--force-with-lease` to prevent accidentally overwriting others' commits if the local view of the remote is stale.

## Open a Hosted Review

After pushing, users confirm the base branch, title, description, and draft state before creating pull or merge requests. GitHub supports stacking PRs above existing ones. The "Generate pull request details with AI" option drafts fields from branch diffs and commits, aiming for brief problem/solution summaries with appropriate issue linking (`Fixes` vs `Refs`).

## Per-repo AI Action Recipes

Source Control AI actions use customizable recipes selecting agents, CLI arguments, and prompts. Templates support variables like `{basePrompt}`, `{branch}`, `{stagedFiles}`, and `{linkedIssue}`. Repository-specific overrides are tracked separately from global defaults.

## Amend

Amending requires explicit selection via "Commit → Amend." Orca requires confirmation before amending already-pushed commits.

## Source Control Panel

The sidebar panel enables staging, discarding files, and executing Commit, Push, Pull, or Sync actions. The branch context row displays current branch stacked above the compare base, with a compact chip showing total lines added/removed. The primary button adapts based on state, progressing from "Stage Files" to "Commit" to "Push/Pull/Sync."

Conflicted states surface "Resolve with AI" alongside "Review conflicts," plus "Abort merge" or "Abort rebase" options.

## Next Steps

- Hosted reviews, issues & Actions
- Annotate AI Diff
