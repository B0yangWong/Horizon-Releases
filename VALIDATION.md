# Validation Scope / 验证范围

This preview has been checked on the development Apple silicon Mac running macOS 27.2. A successful build is not a claim that every supported Mac or first-download security flow has been tested.

## Public-Packaging Checks (0.1.0)

- Optimized Universal build with native `arm64` and `x86_64` slices. Both executable slices have a macOS 15.0 minimum target. The bundle contains only the executable, icon, asset catalog, and English/Chinese string files; it links only Apple system frameworks.
- Local ad-hoc signature, hardened runtime, and the App Sandbox with the calendar entitlement were checked. The ZIP was extracted again, the extracted app's signature verified, and its files compared byte-for-byte with the built app. There is no Developer ID identity or notarization; local Gatekeeper assessment rejects this unnotarized preview, so a clean download may be blocked.
- The extracted app opened with an isolated, in-memory library. The first-download Gatekeeper flow on a separate Mac was not exercised.
- 42 automated unit tests pass, covering habit schedules and streaks (including weekly targets), goal progress roll-up, My Day membership, overlapping calendar blocks, daylight-saving days in the calendar grid, calendar title round-trips, habit repeat rules, “gone quiet” thresholds, suggestion ranking (including never suggesting tasks touched in the last 3 days), and list reordering.
- Two-way Apple Calendar sync was exercised during development against a real calendar: creating an event from a scheduled task, renaming and moving it in Calendar and seeing Horizon update, marking the task complete and seeing the ✓ title, and deleting the event in Calendar and seeing the task unscheduled. The test event was removed afterwards.
- English and Chinese interfaces, My Day, goals, the goals overview, the calendar, habits, the due-date menu and month picker, the habit editor, and the floating task panel on narrow windows were inspected using synthetic data. Public screenshots come from the actual 0.1.0 build with invented, in-memory data and Apple Calendar turned off.
- Pattern scans checked the app bundle and public files for local home paths, account names, and email addresses. Public images were checked for camera or location metadata. These checks reduce accidental disclosure; they are not an independent security audit.
- The release provides a SHA-256 checksum; it checks file agreement, not publisher identity or safety.

## Remaining Limits

- Intel hardware, older macOS versions, and first installation on a separate clean Mac have not been tested. The build target and included architecture are not substitutes for those tests.
- Drag-and-drop interactions (dragging tasks onto the calendar and reordering lists) were built and reviewed but not covered by automated checks.
- Recurring habit events written to Apple Calendar were checked in unit tests for their repeat rules; their sync against every calendar provider (iCloud, Exchange, Google, local) was not tested.
- Because the app is ad-hoc signed, macOS ties calendar permission to each build; an update may ask for access again.
- There is no export, backup, iCloud sync between Macs, iPhone app, notification alerts, Apple Reminders integration, or automatic updater.
- Data is not independently encrypted, and there is no app-level backup. Force quitting can lose the most recent change.
