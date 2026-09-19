# FreeSpace Max — Safe Disk Cleanup

FreeSpace Max is a Codex skill for reclaiming Windows disk space while protecting bootability, application launch files, recent chats, active projects, and uncertain personal data.

It prioritizes caches, logs, temporary files, stale build artifacts, unused development dependencies, old installers, update leftovers, and other low-risk candidates. It keeps the desktop unchanged, preserves recent chat data, asks before uncertain deletions, and produces a concise cleanup report.

## Highlights

- Scans all local disks and ranks files and directories over 1 GB.
- Cleans low-risk caches, logs, temp files, crash dumps, shader caches, package caches, and stale development artifacts.
- Keeps logs from the last day and chat data from the last seven days when date-aware cleanup is safe.
- Preserves browser logins, cookies, bookmarks, history, extensions, active source code, and personal-looking files.
- Handles locked files by closing approved applications or skipping files that remain in use.
- Requires a destination before moving anything and never silently moves uncertain data.

## Usage

Install this folder as a Codex skill, then ask Codex to clean the disks using the configured safe rules. Review the dry-run summary before approving high-risk candidates.

## License

MIT

