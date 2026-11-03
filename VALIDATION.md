# Validation Scope / 验证范围

This preview has been checked on the development Apple silicon Mac running macOS 27.2. A successful build is not a claim that every supported Mac or first-download security flow has been tested.

## Public-Packaging Checks (0.3.0)

- Optimized Universal build with native `arm64` and `x86_64` slices. Both executable slices have a macOS 15.0 minimum target. The bundle contains only the executable, icon, asset catalog, and English/Chinese string files; it links only Apple system frameworks.
- Local ad-hoc signature, hardened runtime, and the App Sandbox were checked. Entitlements are limited to calendars, user-selected files, and app-scoped bookmarks; the debugger entitlement (`get-task-allow`) is not present. The signing requirement is unchanged from 0.2.0, so calendar permission carries over. The ZIP was extracted again, the extracted app's signature verified, and its files compared byte-for-byte with the built app. There is no Developer ID identity or notarization, so a clean download may be blocked.
- Public screenshots come from the actual 0.3.0 release build with invented, in-memory data and Apple Calendar turned off. The mouse pointer was painted out of a few of them; nothing else was edited.
- Pattern scans checked the app bundle and public files for local home paths, account names, and email addresses. Public images were checked for metadata. These checks reduce accidental disclosure; they are not an independent security audit.
- The release provides a SHA-256 checksum; it checks file agreement, not publisher identity or safety.

## Automated Tests

114 unit tests pass. Beyond the 0.1.0 and 0.2.0 areas (habit schedules and streaks, goal progress, My Day membership, calendar layout, sync round-trips, “gone quiet” and suggestions, list reordering, repeat rules, reminders, Chinese and English date and time recognition, backups, calendar import), they cover:

- “@list” recognition (including “@5pm” staying a time), list backups, and restoring backups made before lists existed;
- search matching (every word, case, accents, full-width letters) and calendar-event results (coming ones first, then past ones);
- undo that is really saved: a deleted task coming back with its steps, goal, and list; undoing changes and redoing them; undoing a repeating task's completion taking back its next occurrence; deleted goals and lists linking their tasks, habits, and sub-goals again; habit check-ins;
- repeat recognition in quick add (“每周一三五”, “每两周”, “隔周”, “每隔一天”, “工作日”, “每月15号”, “每晚9点”, “every mon and thu”, “every other week”, “monthly”), counts that are not weekdays (“每周三次”), and “周末 / this weekend”;
- the countdown (which events count, the 30-day window, hiding, duplicates, the limit) and dropping a task on sidebar lists, goals, My Day, Important, and Planned, including undo.

## Hands-On Checks

On the development Mac, using invented data and, separately, the developer's own calendar: creating, editing, and choosing lists; “@list” and repeat phrases when adding; search with marked matches; deleting a task and bringing it back with the Undo bar; “This weekend” in the due-date menu; the countdown, including opening a calendar event from it in the month view with the event pointed out; scrolling the month view; event names in narrow month cells; the larger toolbar; and the English and Chinese interfaces.

## Remaining Limits

- Intel hardware, older macOS versions, and first installation on a separate clean Mac have not been tested. The build target and included architecture are not substitutes for those tests.
- Notification delivery depends on macOS notification permission and Focus settings; scheduling is unit-tested, but banners were not tested across macOS versions.
- Sync of all-day and recurring events against every calendar provider (iCloud, Exchange, Google, local) was not tested.
- Holiday calendars are recognized by type or by name (for example “Holidays”, “节假日”); unusually named holiday calendars may still be imported.
- Drag gestures (onto the calendar or the sidebar) are not covered by automated checks; what happens on drop is. Undo from the Edit menu was checked through unit tests and the Undo bar, not by pressing ⌘Z by hand on another Mac.
- The automatic backup keeps a single file. iCloud sync between Macs, an iPhone app, Apple Reminders integration, and an automatic updater are not included. Data is not independently encrypted. Force quitting can lose the most recent change.

## 中文摘要

0.3.0 在开发用 Apple 芯片 Mac（macOS 27.2）上检查：通用构建、临时签名、沙盒与加固运行时、权限仅限日历/用户选择的文件/书签（公开版本不含调试权限），签名要求与 0.2.0 相同，日历权限会保留；解压后签名有效且与构建逐字节一致；截图来自 0.3.0 发布版本和内存中的虚构数据，只抹去了个别截图里的鼠标指针。114 个单元测试全部通过，新增覆盖“@清单”识别、清单备份、搜索匹配与日历日程排序、确实写入保存的撤销（删除后恢复步骤、目标和清单，重复任务的完成撤销等）、快速添加的重复说法和“周末”、倒计时选取以及拖到左侧栏。Intel 真机、旧系统、全新 Mac 首次安装、各日历服务商的同步和不同系统版本上的通知展示尚未实测；拖动手势本身没有自动化测试；节假日日历按类型和名称识别，名称特殊的可能仍会被导入；自动备份只有一个文件，资料不单独加密。
