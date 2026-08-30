---
title: Jira items drawer
source: https://www.onorca.dev/docs/review/jira
---

Browse, edit, and link Jira Cloud or self-hosted Server/Data Center issues to worktrees alongside GitHub and Linear items.

## Connect a Jira Site

Follow these steps to establish a connection:

1. Open the **Tasks** sidebar and select **Jira** from the source picker
2. Click **Connect Jira** to open the connection dialog
3. Choose your Jira deployment type:

**For Jira Cloud:**
- Provide your Jira Cloud site URL (e.g., `https://example.atlassian.net`)
- Enter your Atlassian email address
- Generate an API token via id.atlassian.com → Security → API tokens

**For Self-Hosted (Server/Data Center):**
- Enter your Jira base URL
- Select authentication method: Personal access token (recommended) or username/password

4. Click **Connect** to verify credentials

You can connect multiple Atlassian sites and use a site picker to view issues across all connected instances.

## Using Jira

The task drawer displays unified GitHub, Linear, and Jira issues. Key capabilities include:

- View full issue details, comments, and metadata in a side drawer
- Edit status (via available transitions), priority, assignee, and custom fields
- Add comments through the drawer's composer
- Create worktrees from issues with pre-filled names and linked associations
- Paste Jira issue URLs or search by text when creating workspaces
- Orca remembers your last-used task source per repository

## Security

Atlassian credentials are encrypted via the OS keychain and stored locally, and only communicate with your configured Jira site. Revoke tokens through Atlassian account settings when discontinuing Orca use.
