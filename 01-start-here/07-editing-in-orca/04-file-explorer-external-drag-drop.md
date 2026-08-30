---
title: File explorer & external drag-drop
source: https://www.onorca.dev/docs/editing/file-explorer
---

The file explorer resides on the left side of each worktree, monitoring your on-disk files in real time. Create, rename, delete, and move operations map to filesystem actions, so changes from the agent appear instantly. Directory listings use natural (numeric-aware) sorting — `9`, `99`, `100` instead of lexicographic ordering. This sorting applies to SSH, remote runtime, Source Control tree nodes, folder pickers, and the mobile file tree.

## External drag-drop

- Drop files from Finder/Explorer into the file tree to copy them in.
- Drop an image into a markdown editor to insert it at the cursor.
- Drop files onto an agent terminal to paste their paths at the prompt.
- For SSH worktrees, drag-drop works by uploading the file to the remote host before completing the drop, so the agent sees it as a real on-disk path.

## Git status

Files are colored by git status — untracked, modified, staged, ignored. Right-click for actions: discard, stage, rename, Copy Path, and Copy Relative Path (`Cmd+Option+Shift+C` / `Ctrl+Alt+Shift+C` by default; remappable).

Right-click a single file and choose Copy to place the file itself on the OS clipboard. For SSH worktrees, Orca stages the remote file locally, then writes that staged file reference to the clipboard; remote folders are excluded.

## Download (SSH / remote)

On the desktop app, right-click a remote file → Download, or a remote folder → Download Folder when the connection supports recursive transfer. Orca opens a native save/folder dialog. Not available in the web client. Local worktrees do not show this action.

## Search a folder

Right-click a folder and choose "Find in Folder" to open Search with that folder already scoped. You can also select a folder in the file explorer and press `Cmd-Shift-F` on macOS or `Ctrl-Shift-F` on Windows and Linux.
