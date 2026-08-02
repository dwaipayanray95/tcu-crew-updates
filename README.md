# TCU Crew

**TCU Crew** is the all-in-one workstation app for **TCU Studios** — built to
keep the whole crew aligned across desktop and mobile. 🕶️

This repo is the update channel the app checks against — release notes and
installers for every platform live here. For the changelog, see
[CHANGELOG.md](./CHANGELOG.md).

## Installation guide

- **Windows** — download and install the latest `.exe` from the
  [Releases page](https://github.com/dwaipayanray95/tcu-crew-updates/releases).
  If Windows SmartScreen pops up, click "More info" → "Run anyway" — the app
  is safe, just not yet code-signed for Windows.
- **macOS** — download and install the latest `.dmg` from the
  [Releases page](https://github.com/dwaipayanray95/tcu-crew-updates/releases).
  Since the app isn't notarized, macOS Gatekeeper will refuse to open it the
  first time. Run this once in Terminal after installing to `/Applications`:
  ```bash
  xattr -cr "/Applications/TCU Crew.app"
  ```
- **Android** — download and install the latest `.apk` from the
  [Releases page](https://github.com/dwaipayanray95/tcu-crew-updates/releases).
  You'll need to allow "install from unknown sources" for your browser/file
  manager the first time.
- No need to manually download future versions after the first install —
  every platform checks for and installs updates automatically.

## What it does

- **Google Workspace Sign-In** — one-tap access with your studio account
- **Shift clock-in/out** — attendance tracking with AFK-aware activity
  monitoring (desktop) and a personal calendar of your shift history
- **Chat** — Google Chat integration alongside a direct, offline-first LAN
  chat between your own devices and teammates on the same network (with
  file/folder transfer)
- **Tasks** — full ClickUp integration: view and manage your assigned tasks,
  subtasks, comments, and attachments without leaving the app
- **Notifications** — a unified inbox for task updates, mentions, leave
  approvals, and announcements
- **Admin Master Control Panel** *(admin accounts only)* — crew oversight,
  attendance management, and workspace administration
- **Auto-updates** — every platform silently checks for and installs new
  releases from this repo

## Platforms

macOS, Windows, and Android — built with Flutter from a single codebase, so
every platform stays in step feature-for-feature.

## If the app feels stuck

1. Fully close the app (quit on desktop, swipe away on Android) and reopen it.
2. If it's a desktop app that seems frozen specifically after your computer
   woke from sleep or came back online, give it a few seconds — it's
   reconnecting.
3. Still stuck? Reach out and I'll take a look.

---

**TCU Studios • TCU Crew**
