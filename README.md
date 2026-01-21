# TCU Crew App Updates
update channel for distribution of TCU Crew App. An app for TCU Studios.

# DOWNLOAD LATEST VERSION 
## https://github.com/dwaipayanray95/tcu-crew-updates/releases 

# Changelog

## Unreleased (v0.1.9)
- TBD

## v0.1.82
- Build: bumped app version to v0.1.82.
- Updates: AW sidecar is stopped before OTA installs to avoid file locks.
- Installer: NSIS preinstall now closes TCU Crew and ActivityWatch processes.
- UI: version pill now always reflects the build version.

## v0.1.71
- Build: bumped app version to v0.1.71 and enabled updater artifacts for signed releases.
- Updates: settings now supports manual update checks with clearer messaging.
- Settings: added "Submit bug report" workflow that prepares logs and opens a draft email.
- Fix: AW sidecar bundle path glob corrected for Windows builds.
- Fix: background AW child processes now terminate on app exit.
- Fix: AW sidecar now launches without opening extra console windows on Windows.

## v0.1.6
- Integrate and Implement AW

## v0.1.5
- Major updates all over the place
- Now the entire app is dark and has a brand new UI
- Implement and tweak Liquid Carbon Design System (Mostly will call it TCU Glass Later)

## v0.1.4
- Improved calendar UI & Logic
- Leave Requests with Approvals Feature added

## v0.1.3-testing
- Auth: release OAuth uses in-app auth window with implicit flow for Tauri.
- Auth: deep-link handling via single-instance + custom scheme `tcu-crew://auth/callback`.
- Auth: automatic app restart after token restore to complete login.
- Build: binary renamed to `tcu-crew.exe` and identifier set to `com.tcu.tcucrew`.
- Build: NSIS-only bundle with per-machine install + installer icon.
- Logging: tauri-plugin-log enabled with log files in app log dir.
- UI: login-only view when signed out; main dashboard appears after sign-in.
- App: close guard blocks exit while checked in.

## v0.1.2
- Google-only login via Supabase Auth, with Tauri deep-link OAuth handling and session restore/restart flow.
- Attendance check-in/out with IST timestamps, shift duration calculation, and today’s hours summary.
- Local SQLite storage with sync queue + cloud sync status indicator.
- Admin dashboard: team summary, per-employee filter, monthly stats, attendance table, and live status/hours in summary rows.
- Monthly calendar view with present/absent markers and working-days stats.
- Announcements feed with unread badge, read receipts, realtime channel + polling, and clear/first-login cutoffs.
- In-app notifications/dialogs for check-in/out and announcements.
- Close guard prevents exiting while checked in.
- Autostart on launch (Tauri plugin) and window focus on auth callback.
- Tauri desktop bundle config (NSIS, custom icon, per-machine install).
- App logging to file via tauri-plugin-log.
- Version pill shown in UI (wired to app version).


## v0.1.1
- UI: aligned main row panels to a fixed height with scrollable lists.
- Updates: announcement dialog widened and scrolls long text.
- Updates: persistent "Clear" behavior stored in localStorage.
- Updates: new users only see announcements created after their first login.
- Updates: unread badge remains while "Clear" hides existing announcements.
- Fix: improved announcement card layout and truncation.
- Auth: Google OAuth in Tauri webview.
- App rename: "TCU Crew Command Center" branding and window title.
- Supabase: direct attendance writes/reads with RLS policies.
- Attendance: check-in/out buttons with disable/enable rules.
- Attendance: IST timestamps and day/shift duration calculation.
- Attendance: days-present count and monthly calendar view.
- UI: simplified login screen, removed offline-first copy.
- Admin: dashboard added with team summary and per-employee table.
- Admin: month filter and working-days stats.
- Updates: announcements feed + read receipts + realtime + polling.
- Notifications: in-app dialog for check-in/out and announcements.
- Config: app window width set to 1280.
- Assets: app icon set generated from SVG.

## v0.1.0
- Project docs and schema drafts created.
- Supabase project created and configured.
- Rust toolchain installed.
- Tauri app scaffolded at apps/desktop (vanilla-ts template).
- Initial desktop UI wired to local SQLite attendance (offline-first).
- Supabase client wiring placeholders added.
