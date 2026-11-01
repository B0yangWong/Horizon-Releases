# Validation Scope / 验证范围

This preview has been checked on the development Apple silicon Mac running macOS 27.2. A successful build is not a claim that every supported Mac or first-download security flow has been tested.

## Public-Packaging Checks (0.2.0)

- Optimized Universal build with native `arm64` and `x86_64` slices. Both executable slices have a macOS 15.0 minimum target. The bundle contains only the executable, icon, asset catalog, and English/Chinese string files; it links only Apple system frameworks.
- Local ad-hoc signature, hardened runtime, and the App Sandbox were checked. Entitlements are limited to calendars, user-selected files, and app-scoped bookmarks; the debugger entitlement (`get-task-allow`) is not present. The ZIP was extracted again, the extracted app's signature verified, and its files compared byte-for-byte with the built app. There is no Developer ID identity or notarization, so a clean download may be blocked.
- Public screenshots come from the actual 0.2.0 release build with invented, in-memory data and Apple Calendar turned off.
- Pattern scans checked the app bundle and public files for local home paths, account names, and email addresses. Public images were checked for metadata. These checks reduce accidental disclosure; they are not an independent security audit.
- The release provides a SHA-256 checksum; it checks file agreement, not publisher identity or safety.

## Automated Tests

90 unit tests pass. Beyond the 0.1.0 areas (habit schedules and streaks, goal progress, My Day membership, calendar layout including daylight-saving days, sync title round-trips, “gone quiet” and suggestions, list reordering), they cover:

- repeat rules (month ends, weekdays, every-N-weeks on chosen days, a daylight-saving day), creating the next occurrence once, and taking it back on uncheck;
- which reminders are scheduled (lead times, due mornings, habits on unchecked scheduled days, weekly targets, the 60-notification cap, a task's own reminder replacing the automatic one);
- Chinese and English date, time, length, importance, and goal recognition, including phrases that must stay in the title (“每周三”, “一周一次”, “1号线”, “decide”);
- backup round trips (every field, relationships, and steps), rejecting files that aren't Horizon backups;
- calendar import (dates and times, all-day events, skipping duplicates, declined and holiday events, following moves and renames), all-day due-date events, and holiday-calendar detection;
- the month grid across a daylight-saving change, sidebar order storage, text-size steps, and today-only removal of My Day events.

## Hands-On Checks

On the development Mac, using invented data and, separately, the developer's own calendar: month view and calendar list, Import from Calendar and its follow-up behavior, all-day due-date events appearing in Apple Calendar, calendar permission persisting across a rebuild, the quick-capture bar while Horizon is in the background, the menu bar window, smart-add chips, the Remind me and Repeat menus, completing and unchecking repeating tasks, the single backup file and Back Up Now, text size, sidebar reordering, removing a holiday from My Day, and the English and Chinese interfaces.

## Remaining Limits

- Intel hardware, older macOS versions, and first installation on a separate clean Mac have not been tested. The build target and included architecture are not substitutes for those tests.
- Notification delivery depends on macOS notification permission and Focus settings; scheduling is unit-tested, but banners were not tested across macOS versions.
- Sync of all-day and recurring events against every calendar provider (iCloud, Exchange, Google, local) was not tested.
- Holiday calendars are recognized by type or by name (for example “Holidays”, “节假日”); unusually named holiday calendars may still be imported.
- Drag-and-drop is not covered by automated checks.
- The automatic backup keeps a single file. iCloud sync between Macs, an iPhone app, Apple Reminders integration, and an automatic updater are not included. Data is not independently encrypted. Force quitting can lose the most recent change.

## 中文摘要

0.2.0 在开发用 Apple 芯片 Mac（macOS 27.2）上检查：通用构建、临时签名、沙盒与加固运行时、权限仅限日历/用户选择的文件/书签（公开版本不含调试权限），解压后签名有效且与构建逐字节一致；截图来自 0.2.0 发布版本和内存中的虚构数据。90 个单元测试全部通过，覆盖重复规则、提醒安排、中英文日期识别、备份往返、日历导入与节假日识别等。Intel 真机、旧系统、全新 Mac 首次安装、各日历服务商的同步和不同系统版本上的通知展示尚未实测；节假日日历按类型和名称识别，名称特殊的可能仍会被导入；自动备份只有一个文件，资料不单独加密。
