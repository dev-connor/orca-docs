---
title: Install
source: https://www.onorca.dev/docs/install
---

## Download

Orca is available as a desktop application for multiple platforms. Users can email themselves a download link or access direct links:

- **macOS:** Apple Silicon and Intel versions available
- **Windows:** Installer executable provided
- **Linux:** AppImage and .deb formats available
- Older versions accessible via GitHub Releases

### Homebrew Installation (macOS)

Orca can be installed using Homebrew with the command:

```
brew install --cask stablyai/orca/orca
```

Updates via Homebrew track the stable channel. For release candidate builds, use GitHub Releases or the in-app update flow.

## First Launch

Upon initial startup, Orca will:

- Request access to your home directory for repository management
- Offer to import settings from `~/.claude`, `~/.codex`, and Ghostty if available
- Display an empty landing screen for adding your first repository

## Updates

By default, Orca automatically updates on the stable channel. Release candidate builds with new features ship frequently, often daily.

To access RC builds, use modifier key combinations when clicking "Check for Updates":

- **Shift+click:** Latest RC prerelease
- **Cmd+click** (macOS) / **Ctrl+click** (Windows/Linux): Latest perf-tagged prerelease
- **Option+click** (macOS only): Validated local macOS build

Downgrading to previous versions is supported through GitHub Releases without affecting worktree data.

## Platform-Specific Notes

**macOS:** Applications are signed and notarized; initial launch confirmation is normal.

**Windows:** Default shell selection (PowerShell or CMD) available in Settings → Terminal.

**Linux:** Both AppImage and .deb builds offered with additional details on Releases page.
