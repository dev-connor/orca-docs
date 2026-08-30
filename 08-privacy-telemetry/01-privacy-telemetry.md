---
title: Privacy & Telemetry
source: https://www.onorca.dev/docs/telemetry
---

## Summary

Orca collects anonymous product-usage data identified by a random local ID with no personal information attached. The platform explicitly avoids transmitting file contents, prompts, agent output, terminal data, repository names, branch information, URLs, paths, or commit messages. Users can disable telemetry by setting `DO_NOT_TRACK=1` or `ORCA_TELEMETRY_DISABLED=1`.

## What we collect

Telemetry events include basic build and platform metadata: version, operating system type, CPU architecture, OS release information, and release channel. Orca tracks lifecycle events (app launches), repository and workspace creation methods, agent initialization with agent type from a predefined list, and coarse error categories without exposing raw error messages. Settings changes from a whitelisted subset are recorded, along with telemetry opt-in/opt-out status.

## What we never send

The documentation specifies that "No file paths, repo names, branch names, URLs, commit messages, or current working directory" are transmitted. Additionally, no agent prompts, responses, terminal contents, raw error messages, stack frames, user account information, IP addresses, precise geolocation data, or vendor-side user profiles are sent.

## How to opt out

Users have three methods to disable telemetry: toggling the setting within Settings → Privacy, setting the `DO_NOT_TRACK=1` environment variable, or using `ORCA_TELEMETRY_DISABLED=1`.

## Where the data goes

PostHog Cloud in the United States region handles data storage with retention following PostHog's default plan settings. Access remains restricted to a limited number of Orca maintainers.
