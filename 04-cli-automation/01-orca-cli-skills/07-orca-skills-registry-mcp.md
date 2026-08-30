---
title: Orca skills registry & MCP
source: https://www.onorca.dev/docs/cli/skills
---

## Overview

Orca distributes agent skills through a hybrid system where lightweight discovery stubs guide agents to load full documentation. The installation process uses `npx skills add` commands, with guides served dynamically from the running CLI to ensure version consistency.

## Installable Orca Skills

Seven core skills are available for installation:

- **orca-cli**: Manage worktrees, terminals, files, automations, and embedded browsers
- **orchestration**: Coordinate multi-agent runs, tasks, supervised workers, and decision gates
- **computer-use**: Control desktop applications via accessibility trees and UI actions
- **orca-linear**: Read/write Linear tickets through CLI integration
- **orca-emulator**: Control iOS Simulator instances
- **orca-emulator-android**: Manage Android devices via adb
- **orca-per-workspace-env**: Configure per-workspace environment recipes

## Hybrid Stubs and Live Guides

Installed stubs instruct agents to resolve the CLI executable, then load full documentation using `orca skills get <topic>`. The system recommends using `--json` flags for deterministic automation output and discourages agents from inferring undocumented flags.

## Skill Updates

Orca monitors installed skill versions and offers in-app updates. The system can run updates in the background through a status bar indicator. On headless systems (SSH, containers, CI), the CLI wrapper `orca skills update` provides non-interactive alternatives without requiring a running Orca runtime.

## Installing and Removing Skills

The in-app Skills page allows workspace and agent selection before installation. Skill deletion explains removal restrictions, such as bundled or read-only status.

## Sharing Private Skills

Users can publish skill bundles behind unlisted, revocable links requiring an Orca account. Recipients select scope (global, workspace, or SSH host) and can review versions before installation. Links act as credentials and can be revoked at any time.

## Individual Skill Descriptions

Each core skill includes brief documentation on purpose and typical use cases, with references to deeper guides in the documentation.

## Discovery Sources

Orca automatically scans skill directories for Claude, Codex, Agent Skills, and OMP installations without manual configuration.

## Custom Skills

External repositories containing `skills/<name>/SKILL.md` files can be installed via `npx skills add`, enabling internal company-specific integrations.

## MCP Servers

Model Context Protocol endpoints registered in Settings → Integrations → MCP expose external tools within compatible agent CLIs.
