---
title: Scheduled automations
source: https://www.onorca.dev/docs/cli/automations
---

Orca automations enable recurring tasks to run on a schedule via the CLI, automating triage, review, and maintenance work without manual intervention.

## Create a safe first automation

Begin with the `--disabled` flag to refine your prompt and target before activation:

```
orca automations create \
  --name "Weekday triage" \
  --trigger weekdays \
  --time 09:00 \
  --prompt "Triage new issues and summarize blockers" \
  --provider codex \
  --repo my-repo \
  --disabled \
  --json
```

The `--trigger` parameter accepts presets like `hourly`, `daily`, `weekdays`, and `weekly`, as well as cron expressions or RRULE strings. Add `--timezone <tz>` to follow a specific IANA timezone.

## Choose where runs happen

Specify `--repo <selector>` for repository-based work or `--workspace <selector>` for runs inside existing Orca worktrees:

```
orca automations create \
  --name "Nightly status" \
  --trigger "0 18 * * 1-5" \
  --prompt "Summarize today's changes" \
  --provider claude \
  --workspace active \
  --disabled
```

Without these flags, Orca resolves the enclosing worktree from your current shell directory.

## Precheck before a run

Skip execution when a preliminary shell check fails (non-zero exit logs a skipped run):

```
orca automations create \
  --name "PR review" \
  --trigger hourly \
  --precheck "gh pr list --json number -q .[0].number" \
  --prompt "Review requested PRs" \
  --provider codex \
  --repo my-repo \
  --disabled \
  --json
```

## Project host / setup targets

Run automations on specific project host setups beyond basic repository or workspace targeting:

```
orca automations create \
  --name "Remote triage" \
  --trigger daily \
  --time 09:00 \
  --prompt "Triage open issues" \
  --provider claude \
  --project <projectId> \
  --host <hostId> \
  --disabled \
  --json
```

Use `--project-host-setup <id>` for existing setup identifiers. Optionally pass `--source-context '<json>'` to pin task and provider data, or `null` to clear.

## Manage automations across hosts

The desktop **Automations** page consolidates schedules from your computer and connected Orca hosts in a single interface. The **Host** column indicates storage location; filter by host using **Filters → Host** to display one or multiple hosts.

When creating automations in the desktop UI, **Create on** selects the destination host before project selection. Connected hosts requiring server updates remain visible but disabled with an **Update server** notification.

## Missed-run grace

```
orca automations edit <automationId> --missed-run-grace-minutes 30 --json
```

## Reuse an existing automation session

For automations targeting existing worktrees, add `--reuse-session` to continue in the previous live automation terminal rather than starting fresh:

```
orca automations create \
  --name "Inbox digest" \
  --trigger hourly \
  --prompt "Summarize unread mail" \
  --provider codex \
  --workspace active \
  --reuse-session \
  --disabled
```

Switch back to fresh terminals per run using `orca automations edit <automationId> --fresh-session --json`.

## Review and enable

List and inspect automations before activation:

```
orca automations list --json
orca automations show <automationId> --json
orca automations edit <automationId> --enabled --json
```

The desktop automations list includes search functionality filtered by name, project, or prompt. External automations on SSH hosts remain manageable even when disconnected.

Use **Filters** to narrow results by **Host**, **Enabled** or **Paused** state, last-run outcome, or specific **Agents**. The table displays host, result, and relative timing. Sort by **Name** (alphabetically) or **Last run** (newest first).

Navigation shortcuts: type in the search field and use **ArrowUp** or **ArrowDown** to move through matching rows. Use `edit` to modify name, prompt, provider, target, schedule, or enabled state. Use `remove` to delete an automation and its history.

## Run on demand

Manually trigger automations to validate prompts and targets before scheduled execution:

```
orca automations run <automationId> --json
orca automations runs --id <automationId> --json
```

If a run fails before opening a workspace, select **Rerun** in Orca to queue a fresh manual attempt.

## Next steps

- Explore the [Orca CLI overview](/docs/cli/overview) for additional worktree, terminal, and browser commands
- Review [Skills registry & MCP](/docs/cli/skills) to enable agent access to these CLI functions
