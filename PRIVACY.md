# Privacy / 隐私说明

Horizon works locally. It has no app account, advertising, analytics upload, cloud sync service, or automatic update check, and it does not make network requests of its own. GitHub hosts downloads and public feedback; the app does not send your data to GitHub.

## Local Records

Horizon runs in the macOS App Sandbox. Its data lives in `~/Library/Containers/app.horizon.mac/`:

- The app database (under `Data/Library/Application Support/`) stores goals, short-term goals, lists, tasks, steps, notes, due dates, scheduled times, reminders, repeat rules, habits, check-ins, and activity timestamps used for “gone quiet” hints and suggestions.
- The automatic backup (`Data/Library/Application Support/Backups/Horizon Backup.json`, or the folder you choose) is a plain JSON copy of all of that, replaced each time. Restoring keeps one extra copy named “before restore”.
- App preferences (under `Data/Library/Preferences/`) store settings such as reminder times, the quick-capture shortcut, text size, sidebar order, which calendars to show, the calendar to write to, and small interface states.

Neither the database nor backups or exports are independently encrypted by Horizon. An exported or backup file contains all your goals and tasks in readable form: keep it somewhere private, and do not attach it to public issues. macOS FileVault, Time Machine, and disk permissions are separate from the app.

If you choose a backup folder elsewhere, Horizon keeps a sandbox bookmark so it can write there again; it only reads and writes its own backup files in that folder.

## Notifications

Reminders are local notifications scheduled on your Mac. They show the task or habit title and its time. Depending on your notification settings, macOS may show them on the lock screen or in Notification Center. Nothing is sent to a push service.

## Quick Capture Shortcut

The global shortcut is registered with the standard macOS hot-key service. Horizon is told only when that exact combination is pressed; it does not see other keystrokes and does not request Accessibility or Input Monitoring access.

## Apple Calendar

Calendar access is optional and requested only when you choose Connect. With access:

- Horizon reads events (title, time, location, notes, and calendar name) from the calendars you choose to show, to display them in My Day, the countdown, the Calendar view, and search results. Searching happens on your Mac. Events are read on demand; they are not copied into Horizon's database unless you import them.
- **Import from Calendar** (in Planned) copies the chosen events into Horizon as tasks: title, date and time, calendar name, and the event's location and notes as the task note. Holiday, birthday, and declined events are skipped. Imported tasks keep following their event; Horizon never writes them back or changes your own calendars.
- Horizon writes scheduled tasks, tasks with a due date, and timed habits as events in a calendar named “Horizon” (or another calendar you pick). An event contains the task or habit title, its time or day, a repeat rule for habits, and an internal `horizon://` link that lets Horizon find it again. Task notes and steps are not written to Calendar.
- If you move, rename, or delete those events in Apple Calendar, Horizon updates the matching task or habit.
- Removing an event from My Day or hiding a calendar changes only what Horizon shows.

If the target calendar belongs to iCloud or another online account, that provider stores and syncs it like any of your calendars. You can revoke access in System Settings → Privacy & Security → Calendars.

## Removal

Uninstalling the app does not remove its data. To remove local records, quit the app and delete `~/Library/Containers/app.horizon.mac/`, plus any backup folder or exported files you chose. Consider whether Time Machine or another backup still retains copies. Events Horizon created stay in the Calendar app until you delete the “Horizon” calendar or those events there.

## Public Feedback

GitHub issues and attachments can be public. Use invented tasks and goals, and redact usernames, paths, names, email addresses, calendar details, and confidential material from screenshots. Never attach a backup or export file. See [Security](SECURITY.md) for vulnerability reporting.

## 中文摘要

应用把目标、清单、任务、提醒、重复规则、习惯、打卡记录和设置保存在本机沙盒目录 `~/Library/Containers/app.horizon.mac/`，不自动上传到 GitHub，没有账户、广告、统计上传、云同步服务或自动更新检查，应用本身不发起网络请求。

自动备份是一个可读的 JSON 文件，每次覆盖，默认也在该目录（可改到自选位置）；恢复时会另存一份“恢复前”。数据库、备份和导出文件都不单独加密，包含你的全部目标和任务，请妥善保管，不要附在公开 Issue 中。

提醒是本机通知，会显示任务或习惯的标题和时间，是否出现在锁屏上取决于你的通知设置，不经过推送服务。快速记录快捷键使用 macOS 标准全局快捷键服务，只在按下这组按键时收到通知，看不到其他按键，不需要“辅助功能”或“输入监控”权限。

苹果日历为可选功能：允许后，Horizon 按需读取你选择显示的日历日程，用于展示、倒计时和搜索（搜索在本机进行）；“从日历导入”会把所选日程复制成任务（标题、时间、日历名，地点和备注写入任务备注），并跳过节假日、生日和已拒绝的日程，之后只读跟随，不会改动你自己的日历。排了时间的任务、有截止日期的任务和定时习惯会写入“Horizon”日历（只含标题、时间或日期、习惯的重复规则和内部链接，不含备注和步骤）。从“我的一天”移除日程或隐藏日历只影响 Horizon 里的显示。可在“系统设置 → 隐私与安全性 → 日历”中随时撤销权限。

卸载应用不会删除资料；需要时手动删除上述目录和自选的备份位置，并在“日历”应用中删除“Horizon”日历。公开反馈请使用虚构内容，不要上传含个人信息的截图或备份文件。
