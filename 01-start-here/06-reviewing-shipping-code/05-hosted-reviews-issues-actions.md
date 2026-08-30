---
title: Hosted reviews, issues & Actions
source: https://www.onorca.dev/docs/review/github
---

Orca integrates code review as a primary worktree feature, linking repositories to pull requests or merge requests while surfacing review status inline and enabling issue triage without leaving the application.

## Connecting a provider

Users can configure their repository provider through Settings → Integrations. GitHub offers the most comprehensive Actions and issue support. GitLab merge requests and issues utilize the same worktree review workflow. Bitbucket Cloud enables in-app connection via email/API token or access token, with credential verification before saving. The system checks Azure DevOps and Gitea pull requests for remote conflicts during worktree creation.

## Reviews

Key review features include:

- Opening hosted reviews from the Source Control panel after pushing, with confirmation of base branch, title, description, and draft state
- Sidebar display of linked reviews with status indicators (open, merged, or closed)
- One-click browser navigation to review pages across multiple platforms
- GitHub checks, reviews, and comments appearing inline in PR tabs
- GitLab pipeline support including bridge and child pipeline job traces
- Reaction pickers for GitHub PR comments matching eight emoji options
- Newest-first sorting for grouped comment sections

**Auto-merge capability:** For GitHub PRs, users can enable automatic merging once requirements pass. The method follows repository defaults (squash, merge commit, or rebase). When merge queues are enabled, the control switches to "Merge when ready."

**Stacked pull requests:** Creating a GitHub PR with an existing open PR as base offers stack creation options, displaying parent PR previews. Stack-aware merge enables merging through multiple dependent PRs atomically.

## Issues

The issue drawer enables browsing, filtering, and editing GitHub and GitLab issues within Orca. Creating worktrees from issues pre-fills task names and maintains issue linkage.

## Actions

Failed GitHub Actions checks display as red indicators on worktrees, with inline access to job logs.

## Tasks

A full GitHub Projects view appears under the Tasks sidebar entry, supporting project card browsing and worktree creation.
