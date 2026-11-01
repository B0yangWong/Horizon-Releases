# Privacy / 隐私说明

Horizon works locally. It has no app account, advertising, analytics upload, cloud sync service, or automatic update check, and it does not make network requests of its own. GitHub hosts downloads and public feedback; the app does not send your data to GitHub.

## Local Records

Horizon runs in the macOS App Sandbox. Its data lives in `~/Library/Containers/app.horizon.mac/`:

- The app database (under `Data/Library/Application Support/`) stores goals, short-term goals, tasks, steps, notes, due dates, scheduled times, habits, check-ins, and activity timestamps used for “gone quiet” hints and suggestions.
- App preferences (under `Data/Library/Preferences/`) store settings such as the completion sound, the “gone quiet” threshold, suggestion choices, which calendars to show, the calendar to write to, and small interface states.

These records are not independently encrypted by Horizon. macOS FileVault, Time Machine, and disk permissions are separate from the app.

## Apple Calendar

Calendar access is optional and requested only when you choose Connect. With access:

- Horizon reads events (title, time, location, notes, and calendar name) from the calendars you choose to show, to display them in My Day and the Calendar view. Events are read on demand; they are not copied into Horizon's database.
- Horizon writes scheduled tasks and timed habits as events in a calendar named “Horizon” (or another calendar you pick). An event contains the task or habit title, its time, a repeat rule for habits, and an internal `horizon://` link that lets Horizon find it again. Task notes and steps are not written to Calendar.
- If you move, rename, or delete those events in Apple Calendar, Horizon updates the matching task or habit.

If the target calendar belongs to iCloud or another online account, that provider stores and syncs it like any of your calendars. You can revoke access in System Settings → Privacy & Security → Calendars.

## Removal

Uninstalling the app does not remove its data. To remove local records, quit the app and delete `~/Library/Containers/app.horizon.mac/`. Consider whether Time Machine or another backup still retains copies. Events Horizon created stay in the Calendar app until you delete the “Horizon” calendar or those events there.

## Public Feedback

GitHub issues and attachments can be public. Use invented tasks and goals, and redact usernames, paths, names, email addresses, calendar details, and confidential material from screenshots. See [Security](SECURITY.md) for vulnerability reporting.

## 中文摘要

应用把目标、任务、习惯、打卡记录和设置保存在本机沙盒目录 `~/Library/Containers/app.horizon.mac/`，不自动上传到 GitHub，没有账户、广告、统计上传、云同步服务或自动更新检查，应用本身不发起网络请求；资料不单独加密。

苹果日历为可选功能：允许后，Horizon 按需读取你选择显示的日历日程用于展示（不复制进数据库），并把排程任务和定时习惯写入“Horizon”日历（只含标题、时间、习惯的重复规则和内部链接，不含备注和步骤）。若该日历属于 iCloud 等在线账户，会由对应服务商同步。可在“系统设置 → 隐私与安全性 → 日历”中随时撤销权限。

卸载应用不会删除资料；需要时手动删除上述目录，并在“日历”应用中删除“Horizon”日历。公开反馈请使用虚构内容，不要上传含个人信息的截图。
