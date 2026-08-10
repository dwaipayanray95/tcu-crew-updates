## v3.20.7 - 2026-08-10

### New
* **Chat Content Search:** Universal search now includes chat message content.
* **Cross-Device Chat Sync & Backups:** Added chat history syncing over LAN and Google Drive, unified manual and automatic backup triggers, and added an app-close safety net that backs up data before quitting.
* **File Sharing Capabilities:** Introduced drag-and-drop multi-file attachments and a new visual file-offer dialog.
* **Attendance & Leave Features:** Added a "clocked-in-since" status indicator and a custom DD/MM/YYYY date range input for leave and WFH request dialogs.

### Improved
* **Chat & File Transfers:** Made P2P chat bubble text selectable with high-contrast highlights, labeled transfer speeds with explicit upload/download directions, and automatically brought the app to the foreground on incoming file offers.
* **UI & Indicators:** Added LAN/relay status coloring to the Team Online card, adjusted the Comms sidebar indicator layout, and refined leave-type dropdown styling.

### Fixed
* **App Close & Shutdown:** Forced immediate process exit on window close to eliminate shutdown hangs on Windows, and ensured activity-tracking data syncs during the app-close backup window.
* **Database Migration:** Renamed the local database file to `tcu_crew.db` with automatic legacy data migration.
* **Chat Sync & History:** Resolved duplicate chat history entries, false "delivered" statuses, data loss during background syncs, and file-offer handshake retries on transient connection failures.
* **Authentication & Settings:** Fixed force-sign-out issues on Android by dropping expired Google scopes, and repaired update-checker feedback in settings.
* **Integrations & Aggregation:** Deduped monthly shift totals by calendar day and resolved missing email addresses for ClickUp task watchers using team profiles.

<details><summary>Full commit list</summary>

- fix(settings): repair update-checker feedback + per-platform release tags (0463a75)
- feat(search): wire chat message content into universal search (0c5b613)
- fix(comms): sync activity-tracking data during app-close backup window (dddcb58)
- fix(db): rename local database file to tcu_crew.db with legacy migration (73d36ed)
- [feat(comms): app-close safety net now hides-and-backs-up before quitting] (2daaec7)
- [feat(comms): unify settings and chat backup triggers and manual backup button] (64c241e)
- fix(comms): correct history dupes, false-delivered status, and sync data loss (64b0c93)
- feat(comms): app-close safety, two-tier Drive backup, foreground sync fix (3159eb8)
- fix(comms): correct history dupes, false-delivered status, and sync data loss (792e983)
- feat(comms): cross-device chat history sync (LAN + Drive backup) (762fdb8)
- fix(comms): retry file-offer handshake on transient connection failure (2761f6d)
- fix(comms): match app dialog design language for incoming file offers (e52bf5a)
- feat(comms): visual file-offer dialog + drag-and-drop multi-file attachments (1914902)
- fix(comms): foreground app on incoming LAN file offer (2ef10ad)
- fix(comms): label transfer speed with upload/download direction (7e49c9c)
- chore: remove dead Google Chat/Tasks code, rename google_chat_service.dart to google_directory_service.dart, dedupe docs (6a3f22b)
- feat: add clocked-in-since status and consolidate attendance/presence math into shared calculations (f10b35f)
- feat: replace built-in date range picker with a custom cursor-aware DD/MM/YYYY input for the leave/WFH dialog (fb5be80)
- fix: give leave-type dropdown items explicit theme styling and default date range to "Select range" placeholder (9750133)
- feat: add date range picker to leave/WFH request dialog on desktop and mobile (9acde2c)
- fix: force process exit after window close instead of waiting for background timers/sockets to drain (fixes slow close on Windows) (01aed45)
- fix: use high-contrast, bubble-aware selection highlight for chat text instead of the theme's low-opacity default (a38f3df)
- make LAN P2P chat bubble text selectable (was only fixed on the unused Google Chat bubble path) (364b605)
- add LAN/relay presence coloring to Team Online card and move Comms sidebar indicator to the right (1ec2895)
- fix: dedupe monthly shift totals by calendar day and log silent consolidation-purge failures (277d4f4)
- fix: [resolve watcher emails via team members when ClickUp's watcher objects omit email] (6ca4a37)
- fix: stop force-signing users out on Android by dropping stale Google Chat scopes and no longer treating expired-token responses as scope failures (b23eb62)

</details>

## v3.17.8 - 2026-08-05

### New
* **Full-Screen Clock-In Gate:** Added a full-screen gate interface active until clocking in, featuring a pinned sign-out avatar and editable, randomized attributed quotes.
* **Universal Search Bar:** Introduced a universal search bar across the application.
* **Private Personal Task Manager:** Replaced the Google Tasks integration with a built-in, private personal task manager.
* **Chat Cloud Relay & Presence:** Added a Supabase cloud-relay fallback for sending chat messages off-LAN, alongside three-state presence indicators (LAN, relay, offline) in the Comms roster and chat headers.
* **macOS DMG Installer Styling:** Updated and styled the macOS DMG installer package.

### Improved
* **ClickUp Sync & Live Updates:** Enhanced ClickUp synchronization to handle partial failures gracefully and added webhook-driven live updates.
* **Crew Profile Dialog:** Reworked and updated the crew profile dialog and views.
* **Task Management UI:** Streamlined personal task controls by replacing text buttons with calendar and task completion icons, and improved task card icon alignments.
* **Elapsed Time Formatting:** Formatted elapsed shift hours as `XXh YYm` instead of the ambiguous `HH:MM`.

### Fixed
* **Dashboard & Overlay Graphics:** Resolved lingering clock-in button and avatar overlays when leaving the dashboard tab, and corrected layout lines on the Clock-In Gate.
* **Shift & Attendance Data:** Fixed attendance data corruption, centralized stats calculations, cleared stale clock-out states after break re-clock-ins, and ensured local shift caches are purged after dispute/consolidation updates.
* **Search & Task Sync:** Fixed search and task synchronization bugs.

<details><summary>Full commit list</summary>

- fix: clear stale clock-in button/avatar overlay rect when leaving dashboard tab (fddaa79)
- feat: correct search/task-sync bugs, rework crew profile dialog (85e5a5d)
- major functionality changes and fixes to universal search bar (6c17545)
- feat: universal search bar (46cd8ea)
- fix: task card icon aligments (23d78dd)
- remove clear completed text and replace with icon for personal tasks (c00a8f3)
- replace Set/Change text button with edit calendar icon (9b91db4)
- feat: replace Google Tasks with private Personal Task Manager (42b75a5)
- feat: add attributed quotes to Clock-In Gate rotation (dc1169e)
- feat: style the macOS DMG installer with create-dmg (c945355)
- feat: pin a sign-out-only avatar on the Clock-In Gate (662b7eb)
- fix: wrap Clock-In Gate content in Material to fix debug yellow underline (efd950c)
- feat: add editable, randomized quotes to the Clock-In Gate (77d0286)
- feat: add full-screen Clock-In Gate shown until the user clocks in (8de17f9)
- fix: format elapsed hours as "XXh YYm" instead of ambiguous "HH:MM" (a19b263)
- fix: don't show a stale clock-out when re-clocked-in after a break (a618404)
- fix: [purge stale local shift cache after dispute/consolidation corrections] (faa0b1f)
- fix: [correct attendance data corruption and centralize stats calculation] (84f9519)
- fix: [make ClickUp sync resilient to partial failures and add webhook-driven live updates] (1407911)
- [Add LAN/relay/offline presence status to chat detail header, drop raw IP] (a6a6fbd)
- [Add three-state LAN/relay/offline presence dots to Comms roster] (6391110)
- feat(chat): [Add Supabase cloud-relay fallback for off-LAN chat messages] (3d53f96)
- [Try multiple current Gemini models for release notes with fallback logging] (c76b085)

</details>

## v3.12.23 - 2026-08-04

- [Auto-close Android list-selector bottom sheet after picking a list] (baaa07f)
- [Make Team Online widget refresh live via Realtime instead of a stale one-shot fetch] (3d47986)
- fix: [release-notes generation using a shut-down Gemini model] (aaa2b9b)
- fix: [Use Flutter's reassembleApplication() for theme/accent refresh instead of manual Element walk] (b03d390)
- fix: [theme/accent refresh destroying navigation state] (1f9e11d)
- [Add ability to dismiss finished file transfers from the chat footer] (492017d)
- [Fix unreadable "NO DUE DATE" label in dark mode ClickUp task cards] (2e346bb)
- [Add responsive Appearance picker to Android Settings, collapsed behind a clickable row] (20ca50e)
- [Fix ClickUp tasks flashing then vanishing on dashboard cold start (Android)] (3afde45)
- [Move Settings off Android bottom nav into AppBar shortcut, relocate Sign Out, and replace chat status text with dots] (e94301c)
- [Fix Activity tab not scrolling to latest comment on first open] (ab782d3)
- [Show real profile pictures in Team Online widget] (f6c1c90)
- [Fix ClickUp comment image and YouTube link previews (embed attempt reverted)] (21fe2d7)
- [Open a zoomable viewer with download on ClickUp comment image tap] (15274f2)
- feat: [Render ClickUp comment image attachments via task-level attachment cross-reference] (6a2a239)
- fix: [MCP Danger Zone delete button never enabling and deploy its Edge Function] (c733852)
- [Fix MCP delete-user action popping the wrong navigator route] (9c2580b)
- feat: [Show live throughput on active P2P transfers] (b860135)
- feat: [Replace LAN chat's peer-connection debug panel with profile, tasks, and shared files] (69e2b85)
- chore: [Rename google_comms_* files/classes to comms_* now that Google Chat is gone] (c508196)
- [Sort roster alphabetically, add tap-to-chat, drop Google Chat UI] (c1bac8c)

<details><summary>Full commit list</summary>

- [Auto-close Android list-selector bottom sheet after picking a list] (baaa07f)
- [Make Team Online widget refresh live via Realtime instead of a stale one-shot fetch] (3d47986)
- fix: [release-notes generation using a shut-down Gemini model] (aaa2b9b)
- fix: [Use Flutter's reassembleApplication() for theme/accent refresh instead of manual Element walk] (b03d390)
- fix: [theme/accent refresh destroying navigation state] (1f9e11d)
- [Add ability to dismiss finished file transfers from the chat footer] (492017d)
- [Fix unreadable "NO DUE DATE" label in dark mode ClickUp task cards] (2e346bb)
- [Add responsive Appearance picker to Android Settings, collapsed behind a clickable row] (20ca50e)
- [Fix ClickUp tasks flashing then vanishing on dashboard cold start (Android)] (3afde45)
- [Move Settings off Android bottom nav into AppBar shortcut, relocate Sign Out, and replace chat status text with dots] (e94301c)
- [Fix Activity tab not scrolling to latest comment on first open] (ab782d3)
- [Show real profile pictures in Team Online widget] (f6c1c90)
- [Fix ClickUp comment image and YouTube link previews (embed attempt reverted)] (21fe2d7)
- [Open a zoomable viewer with download on ClickUp comment image tap] (15274f2)
- feat: [Render ClickUp comment image attachments via task-level attachment cross-reference] (6a2a239)
- fix: [MCP Danger Zone delete button never enabling and deploy its Edge Function] (c733852)
- [Fix MCP delete-user action popping the wrong navigator route] (9c2580b)
- feat: [Show live throughput on active P2P transfers] (b860135)
- feat: [Replace LAN chat's peer-connection debug panel with profile, tasks, and shared files] (69e2b85)
- chore: [Rename google_comms_* files/classes to comms_* now that Google Chat is gone] (c508196)
- [Sort roster alphabetically, add tap-to-chat, drop Google Chat UI] (c1bac8c)

</details>

## v3.10.15 - 2026-07-31

- [`Notify ClickUp task watchers and @mentions, not just assignees`] (8f07107)
- [Add periodic 6-hour update check for desktop platforms] (6235b08)
- [Show clock-in status immediately, add subtasks section and hide-done filter to ClickUp tasks] (5edf466)
- [Parallelize ClickUp cache reads on startup to cut Android cold-start delay] (edf6e6c)
- [Sync ClickUp tasks on Android app resume and lock app to portrait orientation] (3f8705a)
- [Add mobile task detail tabs, fix layout bugs, remove custom fields, and clean up profile/back navigation] (6a5b0f4)
- feat: new app icon for android (c8107a2)
- feat: LAN File Transfer (d6f9f4a)
- [Add bottom padding to clear floating nav pill, reorganize dashboard clock-in card, and show friendly Google Tasks network errors] (69c7fdd)
- [Add tabbed My Tasks widget to Android dashboard, fix Google auth sign-out race and token exchange bug] (038274f)
- [Add REQUEST_INSTALL_PACKAGES permission to fix silent APK install failure] (7c583c3)
- [Redesign Android login screen, add Google sign-in timeout, and fix nav pill back/chat-hide behavior] (32c385d)
- [Add focus-aware retry to startup update check instead of single silent attempt] (ac62430)

<details><summary>Full commit list</summary>

- [`Notify ClickUp task watchers and @mentions, not just assignees`] (8f07107)
- [Add periodic 6-hour update check for desktop platforms] (6235b08)
- [Show clock-in status immediately, add subtasks section and hide-done filter to ClickUp tasks] (5edf466)
- [Parallelize ClickUp cache reads on startup to cut Android cold-start delay] (edf6e6c)
- [Sync ClickUp tasks on Android app resume and lock app to portrait orientation] (3f8705a)
- [Add mobile task detail tabs, fix layout bugs, remove custom fields, and clean up profile/back navigation] (6a5b0f4)
- feat: new app icon for android (c8107a2)
- feat: LAN File Transfer (d6f9f4a)
- [Add bottom padding to clear floating nav pill, reorganize dashboard clock-in card, and show friendly Google Tasks network errors] (69c7fdd)
- [Add tabbed My Tasks widget to Android dashboard, fix Google auth sign-out race and token exchange bug] (038274f)
- [Add REQUEST_INSTALL_PACKAGES permission to fix silent APK install failure] (7c583c3)
- [Redesign Android login screen, add Google sign-in timeout, and fix nav pill back/chat-hide behavior] (32c385d)
- [Add focus-aware retry to startup update check instead of single silent attempt] (ac62430)

</details>

## v3.8.20 - 2026-07-29

- [Sign Android release APKs and publish them via the GitHub release pipeline] (ad88912)
- fix(mobile ui): [double headers, notification overflow, appbar seam, stat card sizing] (bc97424)
- [Redesign Android bottom nav as a floating glass pill with droplet-morph animation] (a40fe52)
- [Foreground desktop app and open chat on new LAN message] (d6c1598)
- fix: [LAN self-message fan-out to all online devices] (3a2d8b3)
- fix: [chat auto-scroll to latest message and integrate context-mode for the project] (ea7bc47)
- fix: [LAN self-messaging, cross-device delivery, and employee_id corruption bug] (fd6e849)
- fix: [LAN P2P self-messaging, Android back button, cleartext networking, and match mobile dashboard/calendar styling to desktop] (165095a)
- [Add Android support with LAN P2P multi-device messaging, retheme mobile screens to match desktop, and refresh docs] (55dcabf)
- style: [Redesign MCP editor into themed sub-cards with danger zone last, add table row-count storage overview] (bf0737c)
- [Add per-employee notification clear with confirmation, make MCP editor a full-screen dialog, fix clock-in notification timezone] (09d2fea)
- fix: [approveDispute failing when a day has multiple raw shift rowsleft] (1ed5560)

<details><summary>Full commit list</summary>

- [Sign Android release APKs and publish them via the GitHub release pipeline] (ad88912)
- fix(mobile ui): [double headers, notification overflow, appbar seam, stat card sizing] (bc97424)
- [Redesign Android bottom nav as a floating glass pill with droplet-morph animation] (a40fe52)
- [Foreground desktop app and open chat on new LAN message] (d6c1598)
- fix: [LAN self-message fan-out to all online devices] (3a2d8b3)
- fix: [chat auto-scroll to latest message and integrate context-mode for the project] (ea7bc47)
- fix: [LAN self-messaging, cross-device delivery, and employee_id corruption bug] (fd6e849)
- fix: [LAN P2P self-messaging, Android back button, cleartext networking, and match mobile dashboard/calendar styling to desktop] (165095a)
- [Add Android support with LAN P2P multi-device messaging, retheme mobile screens to match desktop, and refresh docs] (55dcabf)
- style: [Redesign MCP editor into themed sub-cards with danger zone last, add table row-count storage overview] (bf0737c)
- [Add per-employee notification clear with confirmation, make MCP editor a full-screen dialog, fix clock-in notification timezone] (09d2fea)
- fix: [approveDispute failing when a day has multiple raw shift rowsleft] (1ed5560)

</details>

## v3.6.1 - 2026-07-23

- [Add persistent warning dialog before entering the MCP tab] (50ad7f1)
- feat: [Add Master Control Panel: attendance export, employee edit, fleet controls, data cleanup, and destructive admin tools] (d32cbe1)
- style: [Restyle admin approval buttons and group App Sessions by app with detail view] (b5e00aa)
- [Add dispute_locked flag to prevent nightly consolidation from overwriting approved disputes] (0dcdc1f)
- fix: [Punctuality stat not refreshing after dispute approval] (2d098ff)
- add google OAuth reauth guard, google task fixes, calendar hover details, clickup webhook staleness guard (465b781)
- now hovering over calendar dates showcases the daily stats for that particular day (b7b393e)
- add notificaiton reminder for task and add ability to set date and time for tasks (31ef550)
- add richer task/creation and editing (78c835e)
- chore: auto sign out user if google scopes missing (3a764e0)
- feat: integrate google tasks (53edeb7)
- fix: changelog url (7693ec1)
- remove real-time audit toast system (aeddbc9)
- add attendance calendar overhaul, dispute pipeline fixes and daily shift consolidation (7e94599)

<details><summary>Full commit list</summary>

- [Add persistent warning dialog before entering the MCP tab] (50ad7f1)
- feat: [Add Master Control Panel: attendance export, employee edit, fleet controls, data cleanup, and destructive admin tools] (d32cbe1)
- style: [Restyle admin approval buttons and group App Sessions by app with detail view] (b5e00aa)
- [Add dispute_locked flag to prevent nightly consolidation from overwriting approved disputes] (0dcdc1f)
- fix: [Punctuality stat not refreshing after dispute approval] (2d098ff)
- add google OAuth reauth guard, google task fixes, calendar hover details, clickup webhook staleness guard (465b781)
- now hovering over calendar dates showcases the daily stats for that particular day (b7b393e)
- add notificaiton reminder for task and add ability to set date and time for tasks (31ef550)
- add richer task/creation and editing (78c835e)
- chore: auto sign out user if google scopes missing (3a764e0)
- feat: integrate google tasks (53edeb7)
- fix: changelog url (7693ec1)
- remove real-time audit toast system (aeddbc9)
- add attendance calendar overhaul, dispute pipeline fixes and daily shift consolidation (7e94599)

</details>

## v3.3.38 - 2026-07-23

- rework the calendar to handle leaves and disputes properly (05fcbdb)
- perf: explicitly use impeller renderer on mac os (4466aaa)
- fix: auto start on macos (77fb453)
- feat: now able to attach files to click up comments and shows assigned comments from clickup (fd9b080)
- fix: notifications for users if they made changes on clickup (e45689e)
- fix: notification sound on macos (5e9a171)
- optimise clickup taska layout (eda123c)
- feat: added reliable clickup notifications via webhook (f7a1985)
- rearrange the notification UI a bit (7494934)

<details><summary>Full commit list</summary>

- rework the calendar to handle leaves and disputes properly (05fcbdb)
- perf: explicitly use impeller renderer on mac os (4466aaa)
- fix: auto start on macos (77fb453)
- feat: now able to attach files to click up comments and shows assigned comments from clickup (fd9b080)
- fix: notifications for users if they made changes on clickup (e45689e)
- fix: notification sound on macos (5e9a171)
- optimise clickup taska layout (eda123c)
- feat: added reliable clickup notifications via webhook (f7a1985)
- rearrange the notification UI a bit (7494934)

</details>

## v3.3.38 - 2026-07-23

- rework the calendar to handle leaves and disputes properly (05fcbdb)
- perf: explicitly use impeller renderer on mac os (4466aaa)
- fix: auto start on macos (77fb453)
- feat: now able to attach files to click up comments and shows assigned comments from clickup (fd9b080)
- fix: notifications for users if they made changes on clickup (e45689e)
- fix: notification sound on macos (5e9a171)
- optimise clickup taska layout (eda123c)
- feat: added reliable clickup notifications via webhook (f7a1985)
- rearrange the notification UI a bit (7494934)

<details><summary>Full commit list</summary>

- rework the calendar to handle leaves and disputes properly (05fcbdb)
- perf: explicitly use impeller renderer on mac os (4466aaa)
- fix: auto start on macos (77fb453)
- feat: now able to attach files to click up comments and shows assigned comments from clickup (fd9b080)
- fix: notifications for users if they made changes on clickup (e45689e)
- fix: notification sound on macos (5e9a171)
- optimise clickup taska layout (eda123c)
- feat: added reliable clickup notifications via webhook (f7a1985)
- rearrange the notification UI a bit (7494934)

</details>

## v3.3.20 - 2026-07-22

- feat: added notification support (a57d574)
- fix logic and layout change in admin panel (1/2) and update build scripts (ac983aa)
- refactor: split DatabaseService god-class into domain repos (d711ed0)
- refactor: splitoversized files and clean up lint debt (296a59d)
- make changes to admin panel and fix security stuff (c14bb6e)
- style(clickup): rework the UI for clickup and tasks (b19deab)
- feat: show live sync/backup status in dashboard header (5855f61)
- perf: lower ClickUp sync poll interval from 30s to 15s (921b6dc)
- feat: add attachment upload UI for ClickUp tasks (9beb1bf)
- security: prevent non-admin users from self-escalating via profiles.role (36b7a29)

<details><summary>Full commit list</summary>

- feat: added notification support (a57d574)
- fix logic and layout change in admin panel (1/2) and update build scripts (ac983aa)
- refactor: split DatabaseService god-class into domain repos (d711ed0)
- refactor: splitoversized files and clean up lint debt (296a59d)
- make changes to admin panel and fix security stuff (c14bb6e)
- style(clickup): rework the UI for clickup and tasks (b19deab)
- feat: show live sync/backup status in dashboard header (5855f61)
- perf: lower ClickUp sync poll interval from 30s to 15s (921b6dc)
- feat: add attachment upload UI for ClickUp tasks (9beb1bf)
- security: prevent non-admin users from self-escalating via profiles.role (36b7a29)

</details>

## v3.1.41 - 2026-07-20

- fix: app not drawing due to db migration (423a01d)
- fix: make column-add migrations tolerate already-existing columns (c793468)
- chore: bump version to 3.1.40 (43795dc)
- fix: don't let notification-permission init block app startup (d83e055)
- ci: drop Android from tag-triggered release pipeline (aa1a783)
- fix: remove unused _showTotalHoursDialog to unblock CI analyze gate (247cbad)
- Huge amount of changes overall, theme, clickup, security etc. (44e7dd6)
- ci: automate changelog on release, rotate Google client ID, fix RLS script (a4ef526)
- fix: fix login via new sdk (a77afcf)
- ci: add signed/checked release pipeline, fix CI-blocking gaps (b54397a)
- security: remediate audit findings — secrets, RLS, updater integrity, P2P auth (8ad2235)
- ci: Add GitHub Actions workflow for on-demand release builds (Android arm64-v8a APK, macOS DMG, Windows Inno Setup EXE) (0bc3155)
- clickup list persistence over users (f077daf)
- feat: Add force global update trigger and first launch markdown release notes dialog (967bd04)
- add afk and a few fixes on macos (526f973)
- add scroll feature to aw (59d6e2b)
- docs(context-mode): update GEMINI.md, agents.md, contexts.md for v2.98 feature set (7c46514)
- rework aw interface (a5fae83)
- added support for release notes on new installs (7657236)
- Add backup to google drive feature (2af62af)

<details><summary>Full commit list</summary>

- fix: app not drawing due to db migration (423a01d)
- fix: make column-add migrations tolerate already-existing columns (c793468)
- chore: bump version to 3.1.40 (43795dc)
- fix: don't let notification-permission init block app startup (d83e055)
- ci: drop Android from tag-triggered release pipeline (aa1a783)
- fix: remove unused _showTotalHoursDialog to unblock CI analyze gate (247cbad)
- Huge amount of changes overall, theme, clickup, security etc. (44e7dd6)
- ci: automate changelog on release, rotate Google client ID, fix RLS script (a4ef526)
- fix: fix login via new sdk (a77afcf)
- ci: add signed/checked release pipeline, fix CI-blocking gaps (b54397a)
- security: remediate audit findings — secrets, RLS, updater integrity, P2P auth (8ad2235)
- ci: Add GitHub Actions workflow for on-demand release builds (Android arm64-v8a APK, macOS DMG, Windows Inno Setup EXE) (0bc3155)
- clickup list persistence over users (f077daf)
- feat: Add force global update trigger and first launch markdown release notes dialog (967bd04)
- add afk and a few fixes on macos (526f973)
- add scroll feature to aw (59d6e2b)
- docs(context-mode): update GEMINI.md, agents.md, contexts.md for v2.98 feature set (7c46514)
- rework aw interface (a5fae83)
- added support for release notes on new installs (7657236)
- Add backup to google drive feature (2af62af)

</details>

## v3.1.40 - 2026-07-20

- chore: bump version to 3.1.40 (43795dc)
- fix: don't let notification-permission init block app startup (d83e055)
- ci: drop Android from tag-triggered release pipeline (aa1a783)
- fix: remove unused _showTotalHoursDialog to unblock CI analyze gate (247cbad)
- Huge amount of changes overall, theme, clickup, security etc. (44e7dd6)
- ci: automate changelog on release, rotate Google client ID, fix RLS script (a4ef526)
- fix: fix login via new sdk (a77afcf)
- ci: add signed/checked release pipeline, fix CI-blocking gaps (b54397a)
- security: remediate audit findings — secrets, RLS, updater integrity, P2P auth (8ad2235)
- ci: Add GitHub Actions workflow for on-demand release builds (Android arm64-v8a APK, macOS DMG, Windows Inno Setup EXE) (0bc3155)
- clickup list persistence over users (f077daf)
- feat: Add force global update trigger and first launch markdown release notes dialog (967bd04)
- add afk and a few fixes on macos (526f973)
- add scroll feature to aw (59d6e2b)
- docs(context-mode): update GEMINI.md, agents.md, contexts.md for v2.98 feature set (7c46514)
- rework aw interface (a5fae83)
- added support for release notes on new installs (7657236)
- Add backup to google drive feature (2af62af)
- Chat fixes, more glassy & android build fixes (164e214)
- fix incoming notification & unknown user naming issue in spaces (6ea558c)

<details><summary>Full commit list</summary>

- chore: bump version to 3.1.40 (43795dc)
- fix: don't let notification-permission init block app startup (d83e055)
- ci: drop Android from tag-triggered release pipeline (aa1a783)
- fix: remove unused _showTotalHoursDialog to unblock CI analyze gate (247cbad)
- Huge amount of changes overall, theme, clickup, security etc. (44e7dd6)
- ci: automate changelog on release, rotate Google client ID, fix RLS script (a4ef526)
- fix: fix login via new sdk (a77afcf)
- ci: add signed/checked release pipeline, fix CI-blocking gaps (b54397a)
- security: remediate audit findings — secrets, RLS, updater integrity, P2P auth (8ad2235)
- ci: Add GitHub Actions workflow for on-demand release builds (Android arm64-v8a APK, macOS DMG, Windows Inno Setup EXE) (0bc3155)
- clickup list persistence over users (f077daf)
- feat: Add force global update trigger and first launch markdown release notes dialog (967bd04)
- add afk and a few fixes on macos (526f973)
- add scroll feature to aw (59d6e2b)
- docs(context-mode): update GEMINI.md, agents.md, contexts.md for v2.98 feature set (7c46514)
- rework aw interface (a5fae83)
- added support for release notes on new installs (7657236)
- Add backup to google drive feature (2af62af)
- Chat fixes, more glassy & android build fixes (164e214)
- fix incoming notification & unknown user naming issue in spaces (6ea558c)

</details>

## v3.1.39 - 2026-07-20

- ci: drop Android from tag-triggered release pipeline (aa1a783)
- fix: remove unused _showTotalHoursDialog to unblock CI analyze gate (247cbad)
- Huge amount of changes overall, theme, clickup, security etc. (44e7dd6)
- ci: automate changelog on release, rotate Google client ID, fix RLS script (a4ef526)
- fix: fix login via new sdk (a77afcf)
- ci: add signed/checked release pipeline, fix CI-blocking gaps (b54397a)
- security: remediate audit findings — secrets, RLS, updater integrity, P2P auth (8ad2235)
- ci: Add GitHub Actions workflow for on-demand release builds (Android arm64-v8a APK, macOS DMG, Windows Inno Setup EXE) (0bc3155)
- clickup list persistence over users (f077daf)
- feat: Add force global update trigger and first launch markdown release notes dialog (967bd04)
- add afk and a few fixes on macos (526f973)
- add scroll feature to aw (59d6e2b)
- docs(context-mode): update GEMINI.md, agents.md, contexts.md for v2.98 feature set (7c46514)
- rework aw interface (a5fae83)
- added support for release notes on new installs (7657236)
- Add backup to google drive feature (2af62af)
- Chat fixes, more glassy & android build fixes (164e214)
- fix incoming notification & unknown user naming issue in spaces (6ea558c)
- add notification service for Google Chat messages (5faa040)
- fix login into android app (6b5b72f)

<details><summary>Full commit list</summary>

- ci: drop Android from tag-triggered release pipeline (aa1a783)
- fix: remove unused _showTotalHoursDialog to unblock CI analyze gate (247cbad)
- Huge amount of changes overall, theme, clickup, security etc. (44e7dd6)
- ci: automate changelog on release, rotate Google client ID, fix RLS script (a4ef526)
- fix: fix login via new sdk (a77afcf)
- ci: add signed/checked release pipeline, fix CI-blocking gaps (b54397a)
- security: remediate audit findings — secrets, RLS, updater integrity, P2P auth (8ad2235)
- ci: Add GitHub Actions workflow for on-demand release builds (Android arm64-v8a APK, macOS DMG, Windows Inno Setup EXE) (0bc3155)
- clickup list persistence over users (f077daf)
- feat: Add force global update trigger and first launch markdown release notes dialog (967bd04)
- add afk and a few fixes on macos (526f973)
- add scroll feature to aw (59d6e2b)
- docs(context-mode): update GEMINI.md, agents.md, contexts.md for v2.98 feature set (7c46514)
- rework aw interface (a5fae83)
- added support for release notes on new installs (7657236)
- Add backup to google drive feature (2af62af)
- Chat fixes, more glassy & android build fixes (164e214)
- fix incoming notification & unknown user naming issue in spaces (6ea558c)
- add notification service for Google Chat messages (5faa040)
- fix login into android app (6b5b72f)

## v0.3.6 — Chat & File Transfer Overhaul
- Chat System — Ground-Up Rewrite
- Replaced the monolithic chat system with a clean, modular architecture across 11 focused modules
- LAN-first delivery: messages and files route over the local network when peers are on the same Wi-Fi/LAN, falling back to Supabase only when off-network
- IPMessenger-style file transfers: fast direct HTTP transfers over LAN with no cloud relay
- Parallel uploads: up to 4 files transfer simultaneously during folder sends
- Resume on failure: interrupted transfers pick up from where they left off using byte-range tracking
- Real-time transfer speed & ETA: 2-second sliding window speed meter shows live MB/s and time remaining
- Hard stall timeout: transfers that stall for 30 seconds are automatically aborted and flagged
- Accept / Decline UI for incoming file transfers with progress bar, speed display, and open-folder button on completion
- LAN peers shown with green "LAN" badge and sorted to top of the user list
- Typing indicators, unread message badges, and per-thread message history

### Reliability & Performance
- Fixed file write corruption on resume — switched from File::create (truncates) to OpenOptions with seek, preserving already-received bytes
- Increased upload read buffer from 64 KB → 256 KB for better throughput
- Progress events now fire every 150 ms (was 200 ms) for smoother UI updates
- Added /transfer/state endpoint for querying per-file resume offsets before each upload

### Supabase Free Tier — Usage Reduction
- Reduced Realtime message volume by ~75% by slowing down polling intervals:
- Presence pulse: 8 s → 30 s
- Presence repair: 20 s → 60 s
- Signal repair: 10 s → 30 s
- Directory refresh: 30 s → 2 min
- Activity sync: 15 s → 60 s
- Online probe: 30 s → 2 min
- Announcements poll: 30 s → 5 min

### Weather & Location
- Fixed broken geolocation service chain — replaced rate-limited and auth-blocked services
- Added ip-api.com as primary IP geolocation source (reliable, no API key required)
- Added ipinfo.io as secondary fallback for both coordinates and city name
- Replaced geocode.maps.co (now requires paid API key) with Nominatim / OpenStreetMap for reverse geocoding
- Reverse geocode chain now: Nominatim → BigDataCloud → Open-Meteo (all free, no keys)
## 
### v0.3.5
- Chat reliability: added automatic signaling channel self-repair to recover from stale "Waiting for signaling channel" state after inactivity.
- Chat presence: improved LAN-first presence handling to reduce LAN/Supabase source flipping when apps are backgrounded.
- Transfers: reverted to WebRTC-only transfer path (removed hybrid local HTTP path from runtime transfer flow).
- Transfers: added and tuned transfer stall watchdog logic for both outgoing and incoming pipelines.
- Transfers: improved WebRTC transfer throughput profile (adaptive flow control, 2 MB chunk default/max, and 24 MB/64 MB channel buffer thresholds).
- Transfers: improved progress/speed reporting stability and consistency between sender/receiver views.
- Transfers UX: completed incoming transfer messages are clickable to open destination folder; destination path is persisted for access after app restart.
- Chat UI: removed diagnostics panel and message delete control from chat bubble actions.
- Chat UI: reduced chat typography scale and redesigned composer layout for denser history view (compact send button + split icon-only file/folder attach controls).
- Chat UI: added active user avatar in chat header with a visual separator above message log.
- Build/Version: version updated globally to 0.3.5 in desktop and Tauri metadata
##
### v0.3.0
- UI: refreshed modal/notification close icon styling.
- Chat: LAN-first messaging matured with stronger connection handling, clearer connection state labels, and color-coded status (LAN direct/relay/connecting).
- Chat: crew panel now shows Online + All crew (including offline users) with avatars, unread badges, and tighter stacked cards.
- Chat: profiles show name + first clock-in time on cards.
- Chat: realtime updates while the modal is open with auto-scroll to latest.
- Chat: message reactions (👍🔥😂), read receipts, edit/delete, and typing indicator.
- Chat: improved file transfer UX (inline history, proper Sent/Received labels, dynamic progress).
- Chat: per-platform notification handling and ability to foreground chat on new messages.
- Stability: reduced freezes during clock in/out and multi-chat focus handling.
- Platform: geolocation plugin enabled and reverse-geocode refresh behavior improved. Windows is still a little buggy and needs to manually fetch location.
- Packaging: build and dependency fixes, Windows build attempts, TCU-AW renamed in resources, app version bumped to v0.2.2 along the way.
##
### v0.2.0 PUBLIC BETA RELEASE | Wohoo! Got it to work for Mac OS!
- UI: custom glass titlebar with Minimize/Power Off controls and sticky header behavior.
- UI: Liquid Carbon refinements (background gradient, scrollbars, softer hover lighting, darker manage-day popover).
- UI: clock widget now compact with time-of-day visuals driven by local sunrise/sunset.
- UI: weather + city line added to the clock widget, with location-use prompt.
- UI: user attendance analytics panel with weekly/monthly breakdown modal.
- Settings: 12/24-hour clock toggle.
- Settings: in-app changelog viewer.
- Tray: quick tray menu actions for dashboard/admin/settings/manage leaves/clock in/out + quit; focus main window on tray actions.
- Admin: new sub-tabs (Quick Access/Employee/Leave Approvals) with employee snapshot + attendance insights panel.
- Admin: attendance insights include monthly range controls and metrics (days present/absent, avg clock-in, avg hours, totals, late count).
- Notifications: leave request/approval updates now notify both user and admin (realtime + polling fallback).
- Auth: macOS OAuth uses system browser with deep-link return support.
- Attendance: auto-checkout on next launch using heartbeat timestamp after force-quit/shutdown.
- Attendance: weekly totals and clock-in averages for user/admin views.
- Updates: macOS updater artifacts supported (app tarball + signature).
- macOS: location permission prompt + IP-based geolocation fallbacks for weather.
- macOS: app icon padded to better fill the dock mask.
##
### v0.1.83 Wohoo! We have an app for Mac as well!
- Overall Major UI changes
- Major UI Overhaul again - Refined Liquid Carbon Design System
- Major changes ahead
- Weather is broken for Mac
##
### v0.1.82
- Installer: NSIS preinstall now closes TCU Crew and AW processes.
- UI: version pill now always reflects the build version.
##
### v0.1.71
- Build: bumped app version to v0.1.71 and enabled updater artifacts for signed releases.
- Updates: settings now supports manual update checks with clearer messaging.
- Settings: added "Submit bug report" workflow that prepares logs and opens a draft email (broken)
##
### v0.1.5
- Major updates all over the place
- Now the entire app is dark and has a brand new UI
- Implement and tweak Liquid Carbon Design System (Mostly will call it TCU Glass Later)
##
### v0.1.4
- Improved calendar UI & Logic
- Leave Requests with Approvals Feature added
##
### v0.1.3-testing
- Auth: release OAuth uses in-app auth window with implicit flow for Tauri.
- Auth: deep-link handling via single-instance + custom scheme tcu-crew://auth/callback.
- Auth: automatic app restart after token restore to complete login.
- Build: binary renamed to tcu-crew.exe and identifier set to com.tcu.tcucrew.
- Build: NSIS-only bundle with per-machine install + installer icon.
- Logging: tauri-plugin-log enabled with log files in app log dir.
- UI: login-only view when signed out; main dashboard appears after sign-in.
- App: close guard blocks exit while checked in.
##
### v0.1.2
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
##
### v0.1.1
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
##
### v0.1.0
- Project docs and schema drafts created.
- Supabase project created and configured.
- Rust toolchain installed.
- Tauri app scaffolded at apps/desktop (vanilla-ts template).
- Initial desktop UI wired to local SQLite attendance (offline-first).
- Supabase client wiring placeholders added.

</details>

