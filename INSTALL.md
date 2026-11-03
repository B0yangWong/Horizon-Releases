# Install Horizon / 安装 Horizon

## Compatibility

- Download: `Horizon-0.3.0-macOS-universal.zip`.
- Includes native `arm64` and `x86_64` executables for Apple silicon and Intel Macs.
- Both executable slices have a macOS 15.0 minimum deployment target. This is a build target, not a claim of testing every supported OS.
- Checked on the development Apple silicon Mac. Intel hardware, older macOS, and a separate clean Mac have not been tested.
- The app is self-contained. No Xcode, app account, network server, or package-manager installation is needed.
- This preview is ad-hoc signed with hardened runtime and the App Sandbox; it has no Developer ID identity or Apple notarization.

## Install and First Launch

1. Download the app ZIP from [v0.3.0](https://github.com/B0yangWong/Horizon-Releases/releases/tag/v0.3.0). The “Source code” assets are documentation archives, not app installers.
2. Extract and move `Horizon.app` into Applications. Do not run it from inside the archive.
3. Open the app. If macOS cannot verify the developer, only proceed if you trust this release. After the first attempt, follow [Apple's manual instructions](https://support.apple.com/en-us/102445) under System Settings → Privacy & Security → Open Anyway, if available. Managed Macs may forbid this. Do not disable Gatekeeper globally or use a script to remove download quarantine.
4. A warning that the app is damaged or will harm your computer is a reason to stop and report the problem, not an instruction to bypass it.
5. Horizon asks once whether it may send notifications; they are used only for reminders. You can change this later in System Settings → Notifications → Horizon, or turn reminders off in Horizon's Settings → Reminders.
6. Add a task to My Day or create a goal. The interface follows your Mac's language (English or Simplified Chinese). To use a different language for Horizon only, choose System Settings → General → Language & Region → Applications.

## Apple Calendar (Optional)

Choose **Connect** in My Day, the Calendar view, Planned, or Settings → Calendar, and allow full calendar access. Horizon then shows events from the calendars you select and writes scheduled tasks, tasks with a due date (as all-day events), and timed habits to a calendar named “Horizon” (created on first use in your default calendar account). You can pick another writable calendar, or stop adding due dates, in Settings → Calendar.

You can turn access off at any time in System Settings → Privacy & Security → Calendars. From 0.2.0 on, macOS keeps the permission when you update Horizon. Updating from 0.1.0 asks once more.

## Quick Capture and Menu Bar

Press `Control + Option + N` in any app to open the quick-capture bar; change or turn off the shortcut in Settings → Quick Capture. If another app already uses the combination, Settings says so. The shortcut is registered with the standard macOS hot-key service and does not need Accessibility or Input Monitoring permission. Horizon also places a checkmark icon in the menu bar; you can hide it in the same settings tab.

The app does not install a background agent or start at login, and it does not request Accessibility, Input Monitoring, or Screen Recording access.

## Check the Download

Download `SHA256SUMS.txt` from the same release. In Terminal, change to the download folder and run:

```sh
shasum -a 256 Horizon-0.3.0-macOS-universal.zip
```

Compare the result with the ZIP's entry in `SHA256SUMS.txt`. This detects disagreement with the published file; it is not a digital signature, security audit, or Apple approval.

## Updates, Backups, and Existing Data

Quit Horizon normally, then replace the app in Applications. Your data stays in `~/Library/Containers/app.horizon.mac/`; do not delete that folder when updating. Data from 0.1.0 and 0.2.0 opens in 0.3.0 without changes.

Horizon keeps one automatic backup file, replaced as you work (Settings → Backup), by default inside that same folder. Choose a folder on another disk if you want the backup to survive losing this one, and use **Export…** to keep a copy from a particular day. Time Machine also covers the container.

## Uninstall

Quit the app and move `Horizon.app` to the Trash. Removing the app does not remove its data or backup. To remove local records too, delete `~/Library/Containers/app.horizon.mac/` and any backup folder or exported files you chose yourself. If you connected Apple Calendar, the “Horizon” calendar and its events remain in the Calendar app until you delete them there.

## 中文安装要点

下载带有 `macOS-universal.zip` 的应用压缩包，解压后拖入“应用程序”。安装包包含 Apple 芯片和 Intel 架构，最低构建目标为 macOS 15，但 Intel 真机、旧系统和另一台全新 Mac 尚未实测。

本版没有 Apple 开发者身份签名和公证，首次启动可能被拦截。确认信任下载后，仅按 [Apple 官方说明](https://support.apple.com/zh-cn/102445)手动允许；不要关闭系统安全检查、运行移除隔离标记的脚本，或绕过“将损害电脑”“已损坏”提示。

首次打开会询问一次通知权限，只用于提醒，之后可在“系统设置 → 通知”或 Horizon 的“设置 → 提醒”里修改。

苹果日历是可选功能：点“连接”并允许完整访问后，会显示所选日历的日程，并把排了时间的任务、有截止日期的任务（全天日程）和定时习惯写入“Horizon”日历。从 0.2.0 起，更新后系统会保留日历权限；从 0.1.0 升级时会再询问一次。

快速记录默认快捷键为 ⌃⌥N，可在“设置 → 快速记录”中修改或关闭；它使用 macOS 标准的全局快捷键服务，不需要“辅助功能”或“输入监控”权限。菜单栏图标也可以在同一页隐藏。

更新时正常退出后替换应用即可，资料保存在 `~/Library/Containers/app.horizon.mac/`，不要删除；0.1.0 和 0.2.0 的资料可直接在 0.3.0 中打开。自动备份只保留一个文件并随时覆盖，默认也在这个目录里；可以把备份位置改到另一块磁盘，或用“导出…”保存某一天的副本。卸载应用不会删除资料和备份；需要时手动删除上述目录和你自选的备份位置，并在“日历”应用中删除“Horizon”日历。
