---
title: Troubleshooting GitHub errors
source: https://www.onorca.dev/docs/github-errors
---

## Overview

Orca communicates with GitHub through the **GitHub CLI (`gh`)** installed on your machine or remote host. When PR status, checks, issues, or Tasks fail to refresh, the root cause is typically GitHub authentication, permissions, or API rate limits—not a defect in Orca's PR panel itself.

## Quick Triage Reference

| Error Message | Likely Cause | Initial Solution |
|---|---|---|
| "GitHub is rate-limiting requests" / "rate limit exceeded (core)" | REST API quota exhausted | Wait for reset; reduce concurrent `gh` usage; review Settings → Git → GitHub API Budget |
| "GitHub authentication is unavailable" / `gh auth` prompts | `gh` not authenticated or token expired | Run `gh auth status`, then `gh auth login` |
| "GitHub did not allow access" / HTTP 403 (not rate limit) | Insufficient token scopes or repo access denied | Re-authenticate with `repo` scope; confirm browser access to the PR |
| "repository is unavailable" / HTTP 404 | Incorrect remote, private repo without access, or renamed repo | Verify `git remote -v` and test browser access |
| "GitHub is unreachable" / timeouts | Network, proxy, VPN, or GitHub service issue | Check [githubstatus.com](https://www.githubstatus.com/); test without VPN |
| "GitHub CLI is unavailable" | `gh` missing from PATH | Install `gh` and fully restart Orca |

## Rate Limits (Most Common Issue)

GitHub allocates a shared hourly budget per authenticated user. This quota is consumed by all tools on that account: Orca, terminal `gh` commands, AI agents invoking `gh`, CI scripts, browser extensions, and other applications.

### Primary Rate-Limit Buckets

- **REST (core)**: Covers most PR/issue queries and API calls; typical limit is 5,000 per hour
- **GraphQL**: Used for Projects/Tasks and advanced PR queries; typical limit is 5,000 points per hour
- **Search**: Powers search-driven lists; typical limit is 30 per minute

When exhausted, GitHub returns HTTP 403. Orca preserves the last known PR status and temporarily stops spawning new `gh` calls to prevent cascading failures.

### Why Settings May Appear Healthy During a Rate Limit

The GitHub API Budget reading in Settings uses a special probe endpoint that is exempt from rate-limit accounting. This probe can report remaining quota while actual REST calls for the same user already return zero availability. Trust the live error on the PR panel above the Settings numbers when they disagree.

### Verifying Rate Limits from Terminal

```bash
# Probe (exempt from accounting; may appear healthier than reality)
gh api rate_limit --jq '.resources | {core, graphql, search}'

# Real REST call (what PR refresh depends on)
gh api user -i 2>&1 | head -40
```

If the second command returns 403 with `API rate limit exceeded` and `X-Ratelimit-Remaining: 0`, the account is blocked until the `X-Ratelimit-Reset` timestamp.

### Typical Causes of Quota Exhaustion

- Multiple Orca windows or development builds refreshing PRs simultaneously
- Agents automating `gh` for bulk operations (assigning PRs/issues, polling checks)
- Heavy Tasks with multi-repository queries during active PR panel refreshes
- Other applications using the same GitHub token

### Recovery Steps

1. Wait for the hourly reset indicated in the error or `X-Ratelimit-Reset` value
2. Close extra Orca instances and pause automation scripts
3. Avoid manual refresh attempts while limited; Orca already backs off automatically
4. In scripts, prefer batched GraphQL operations over looping REST calls on personal accounts
5. After reset, if issues persist, verify authentication (see next section)

## Authentication Problems

Orca inherits the authentication configuration of `gh` on your host.

### Checking Authentication Status

```bash
gh auth status -h github.com
gh api user --jq '{login, id}'
```

Healthy output shows you're logged in, your token is valid, and `gh api user` returns your GitHub login.

### Common Authentication Issues

**Environment variable tokens (`GITHUB_TOKEN` or `GH_TOKEN`)**
If these are set in shell profiles, they override keyring credentials and can cause confusion if stale or incorrect. Clear them and re-authenticate:

```bash
unset GITHUB_TOKEN GH_TOKEN
gh auth logout -h github.com
gh auth login -h github.com
```

**Expired or revoked tokens**
Run `gh auth login` or `gh auth refresh` and restart Orca to use the new credentials.

**Organization SAML SSO requirements**
Private org repositories may require SSO authorization on the token. Complete the SSO flow in GitHub's token settings, then retry.

**Remote and SSH worktrees**
Authentication is host-specific. Logging in on your laptop does not authenticate `gh` on a remote machine. SSH to the remote host and run `gh auth login` there separately.

## Permission and Repository Errors

| Error | Meaning |
|---|---|
| HTTP 403 (without rate-limit message) | Token lacks required scopes or you lack access to the resource |
| HTTP 404 / "could not resolve to a Repository" | Repository is missing, renamed, or not visible to this token |
| "resource not accessible by integration" | Your token type cannot perform the requested action |

### Resolution

- Confirm the PR or repository opens in a browser while logged in as the same user shown by `gh api user`
- Re-authenticate using classic token scopes including `repo`, and add `read:org` or `project` if needed for those features
- For GitHub Enterprise instances, authenticate `gh` to that specific hostname using `gh auth login --hostname …`

## Network and GitHub Outages

Errors mentioning timeouts, "could not resolve host", or general unreachability indicate connectivity problems:

- Check [GitHub Status](https://www.githubstatus.com/)
- Attempt without VPN or corporate proxy
- For remote hosts, verify outbound HTTPS connectivity to `api.github.com` is available

## GitHub CLI Installation

If Orca reports the GitHub CLI is unavailable:

1. Install [`gh`](https://cli.github.com/) using your system's package manager
2. Verify `which gh` returns a path in a normal terminal
3. Fully quit and reopen Orca so the updated PATH takes effect
4. On Windows, ensure `gh` is installed for the same environment Orca uses (WSL or native)

## How Orca Handles GitHub Failures

- **Rate limits and outages**: PR and Checks panels display the last known status with a banner notification instead of clearing the interface
- **Authentication or permission failures**: Clear empty-state messages prompt you to fix login or access issues
- **Circuit breaker**: After a primary rate-limit 403, Orca briefly prevents new `gh` spawns for that rate-limit bucket to maintain responsiveness and avoid deeper failure cascades

## Checking GitHub API Budget in Orca

Open **Settings → Git** to view **GitHub API Budget**:

- Displays remaining counts for REST, Search, and GraphQL from GitHub's probe endpoint
- Refresh after waiting out a rate limit
- On remote Orca servers, check the remote advanced budget view for the server's own GitHub identity (local Settings only reflects the desktop client)

## Troubleshooting Steps for Unresolved Issues

1. Reproduce the issue in a terminal using `gh pr view` or `gh api user` from the same machine and user account Orca is using
2. Collect logs via **Help → Open Logs**
3. File an issue with the classified error text (without secrets), redacted `gh auth status` output, and confirmation of whether terminal `gh` fails identically

**Report to:**
- [GitHub Issues](https://github.com/stablyai/orca/issues)
- [Discord](https://discord.gg/fzjDKHxv8Q)

## Related Documentation

- Hosted reviews, issues & Actions — GitHub-dependent PR and Checks features
- Settings reference — Integrations and Git configuration
- Usage & rate-limit tracking — AI provider limits (Claude/Codex), distinct from GitHub API
- Troubleshooting & FAQ — General Orca troubleshooting
