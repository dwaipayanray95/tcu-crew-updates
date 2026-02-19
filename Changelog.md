All notable changes to the TCU Crew Command Center app are documented here.

v0.3.5
Chat reliability: added automatic signaling channel self-repair to recover from stale "Waiting for signaling channel" state after inactivity.
Chat presence: improved LAN-first presence handling to reduce LAN/Supabase source flipping when apps are backgrounded.
Transfers: reverted to WebRTC-only transfer path (removed hybrid local HTTP path from runtime transfer flow).
Transfers: added and tuned transfer stall watchdog logic for both outgoing and incoming pipelines.
Transfers: improved WebRTC transfer throughput profile (adaptive flow control, 2 MB chunk default/max, and 24 MB/64 MB channel buffer thresholds).
Transfers: improved progress/speed reporting stability and consistency between sender/receiver views.
Transfers UX: completed incoming transfer messages are clickable to open destination folder; destination path is persisted for access after app restart.
Chat UI: removed diagnostics panel and message delete control from chat bubble actions.
Chat UI: reduced chat typography scale and redesigned composer layout for denser history view (compact send button + split icon-only file/folder attach controls).
Chat UI: added active user avatar in chat header with a visual separator above message log.
Build/Version: version updated globally to 0.3.5 in desktop and Tauri metadata
