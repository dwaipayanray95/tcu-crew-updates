# TCU Crew Command Center

**TCU Crew Command Center** is the all-in-one desktop app for **TCU Studios** built to keep the whole crew aligned and eventually our one stop solution for everything. 🕶️

## INSTALLATION GUIDE
- Windows users download and install the latest .exe file from the link below or from the releases page. If the smart screen filter pops-up by pass it. I have made the app so of course it safe 👍 😎
- Mac users download and install the latest .dmg from the link below or from the releases page. 🍎
- No need to download future versions post installation as the app auto updates. 😎
#

DOWNLOAD LATEST VERSION - https://github.com/dwaipayanray95/tcu-crew-updates/releases 
#
## What it does

- **Google Sign-In** – quick, familiar access  
- **Daily Check-In / Check-Out** – track attendance with ease  
- **Announcements** – stay updated with studio-wide notes and updates  
- **More features to come in soon / Will update a submit feature request page too
- Lots of features and changes. Complete changelog below.

# Check out the changelog for an entire feature list #

## Still a WIP

## If the app feels stuck

Sometimes the app may appear frozen or not respond as expected. A refresh usually fixes it.. I am just a vibe coder

1. **Right-click anywhere inside the app**
2. Select **Refresh**
3. The **login screen will reload**
4. **Wait a few seconds** before clicking **Log in** or anything else. The app will load.
5. The app is thoroughly tested
6. Contact me for beta tests :')

### About “Supabase is not configured”

During refresh, you may briefly see:

> “Supabase is not configured”

That message should clear on its own—**please wait until it disappears** before continuing.  
(I am improving this behavior in a future update.)

---

**TCU Studios • TCU Crew Command Center**



# Changelog

## v0.2.0
- Wohoo! Got it work for Mac OS! 
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

## v0.1.83
- Wohoo! We have an app for Mac as well!
- Overall Major UI changes
- Major UI Overhaul again - Refined Liquid Carbon Design System
- Major changes ahead
- Weather is broken for Mac

## v0.1.82
- Build: bumped app version to v0.1.82.
- Installer: NSIS preinstall now closes TCU Crew and AW processes.
- UI: version pill now always reflects the build version.

## v0.1.71
- Build: bumped app version to v0.1.71 and enabled updater artifacts for signed releases.
- Updates: settings now supports manual update checks with clearer messaging.
- Settings: added "Submit bug report" workflow that prepares logs and opens a draft email

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
