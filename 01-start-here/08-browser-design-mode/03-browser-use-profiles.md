---
title: Browser-use profiles
source: https://www.onorca.dev/docs/browser/profiles
---

Browser-use profiles enable running the Orca browser with a specific identity — such as a logged-in user, particular cookies, or custom user-agent settings. This functionality proves valuable when agents need to authenticate, reproduce session-specific bugs, or simulate multiple users.

## Create a profile

1. Navigate to Settings → Browser → Profiles
2. Select **Add profile** and assign it a name
3. Optionally configure it with cookies, user-agent, and viewport dimensions
4. For sites rejecting Orca's default Chrome user-agent (particularly some Google authentication flows), establish a profile using the **native Electron user agent** instead of spoofing. Standard profiles continue using a modified Chrome UA for improved Cloudflare compatibility

Alternatively, generate a no-spoof profile via CLI: `orca tab profile create --no-ua-spoof`

## Cookie import and Google sign-in

Import cookies from Chrome, Edge, or cookie files into a profile through Settings or the browser toolbar. Orca updates cookies exclusively for imported domains, preserving existing authentication for other sites within the same profile. Google cookies receive special handling — import dialogs display **Google logins aren't imported** with instructions to **Sign in to Google directly in Orca.** Following an import that excluded Google cookies, a warning identifies the host; open a browser in Orca on that host using the same profile to complete Google authentication.

When a site requests a discoverable passkey from a USB security key with multiple accounts, Orca presents an account picker rather than silently failing. Users can select the desired account or cancel.

## Use a profile

Select a profile from the browser toolbar. All tabs within that pane use the selected profile until switched. Agent-initiated browser operations automatically adopt the active profile.

## Isolation

Each profile maintains separate storage — cookies, local storage, and cache remain isolated from other profiles without cross-contamination.
