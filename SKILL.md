---
name: free-space-max-safe-cleanup
description: "Safely reclaim disk space from caches, logs, temp files, stale builds, and unused dependencies while protecting system bootability, app launch files, recent chats, and uncertain personal data."
---

# FreeSpace Max — Safe Disk Cleanup

Use this skill when the user asks to deeply clean Windows disks, maximize free space, remove caches or stale development artifacts, or identify files that can be deleted safely.

## Operating policy

- Maximize reclaimed space while avoiding anything that could prevent Windows or an installed application from launching.
- Scan every local disk unless the user narrows the scope. Desktop contents are protected and must never be changed automatically.
- Treat files that appear to be personal documents, photos, videos, archives, project source, databases, backups, or exports as uncertain. Put them in a review list rather than deleting them.
- User directories such as Downloads, Documents, Pictures, Videos, and Music may be scanned, but personal-looking files are review-only. Do not infer that an old file is disposable solely from age.
- Keep chat messages and attachments from the most recent 7 days. Older cache, downloaded media, thumbnails, and temporary chat files may be candidates; databases that cannot be safely filtered by date are review-only.
- Keep application logs from the most recent 1 day when the format allows it. Older logs, crash dumps, diagnostic traces, installer leftovers, update packages, shader caches, browser cache, GPU cache, and temporary files are low-risk candidates.
- Development artifacts such as `node_modules`, `.venv`, `venv`, `dist`, `build`, `.next`, package-manager caches, unused SDK downloads, and stale virtual environments may be candidates, including across projects. Protect active project source and lockfiles.
- Old application versions and duplicate installers may be candidates after checking that a newer version exists and the path is not the active install.
- System cleanup may include Recycle Bin, Windows update leftovers, error reports, old restore points, hibernation data, and other system caches. Treat pagefile configuration and files required for boot or recovery as high-risk and ask before changing them.
- Browser cleanup should remove cache-like data only. Preserve cookies, saved logins, bookmarks, history, profiles, and extensions unless the user explicitly asks otherwise.
- The user has no default archive drive. Ask for a destination before moving anything. If no destination is supplied, leave movable uncertain files in place and list them.

## Required workflow

1. Inspect disk free space, mounted drives, permissions, running processes, and the paths that will be considered. Do not delete during discovery.
2. Rank directories and files, emphasizing items at least 1 GB, and classify each candidate as low-risk, review-required, protected, or locked.
3. Present a concise dry-run summary before high-risk changes. Low-risk cleanup can proceed automatically under the user's standing policy; ask about review-required items and destination paths for moves.
4. Close only applications that hold files needed for an approved cleanup. If a process cannot be closed safely, skip its locked files and continue.
5. Delete only exact, verified paths. Never use a broad wildcard or recursively delete a user profile, project root, Windows root, or application root. Preserve the desktop and protected files.
6. Re-scan the affected paths and report reclaimed space, deleted items, skipped/locked paths, and items awaiting review. Keep the report concise and do not create a persistent history unless requested.

## Confirmation rules

Ask before deleting anything that could contain personal data, an active project, a chat database, a current application installation, a backup, a restore point the user may need, or a system file whose role is uncertain. Also ask before moving files when no destination path is known. Do not ask again for the user's standing low-risk policy, but obtain fresh confirmation for a specific destructive high-risk action.

## Safety checks

- Verify the resolved absolute path stays within the intended target directory before recursive deletion.
- Check file ownership, attributes, reparse points, and junctions; skip links and avoid double counting.
- Use actual file sizes and disclose when logical size may differ from physical allocation because of compression, sparse files, or hard links.
- Never expose secrets found in config files, tokens, credentials, or chat databases in the report.

