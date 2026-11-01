# Install Horizon / 安装 Horizon

## Compatibility

- Download: `Horizon-0.1.0-macOS-universal.zip`.
- Includes native `arm64` and `x86_64` executables for Apple silicon and Intel Macs.
- Both executable slices have a macOS 15.0 minimum deployment target. This is a build target, not a claim of testing every supported OS.
- Checked on the development Apple silicon Mac. Intel hardware, older macOS, and a separate clean Mac have not been tested.
- The app is self-contained. No Xcode, app account, network server, or package-manager installation is needed.
- This preview is ad-hoc signed with hardened runtime and the App Sandbox; it has no Developer ID identity or Apple notarization.

## Install and First Launch

1. Download the app ZIP from [v0.1.0](https://github.com/B0yangWong/Horizon-Releases/releases/tag/v0.1.0). The “Source code” assets are documentation archives, not app installers.
2. Extract and move `Horizon.app` into Applications. Do not run it from inside the archive.
3. Open the app. If macOS cannot verify the developer, only proceed if you trust this release. After the first attempt, follow [Apple's manual instructions](https://support.apple.com/en-us/102445) under System Settings → Privacy & Security → Open Anyway, if available. Managed Macs may forbid this. Do not disable Gatekeeper globally or use a script to remove download quarantine.
4. A warning that the app is damaged or will harm your computer is a reason to stop and report the problem, not an instruction to bypass it.
5. Add a task to My Day or create a goal. The interface follows your Mac's language (English or Simplified Chinese). To use a different language for Horizon only, choose System Settings → General → Language & Region → Applications.

## Apple Calendar (Optional)

Choose **Connect** in My Day, the Calendar view, or Settings → Calendar, and allow full calendar access. Horizon then shows events from the calendars you select and writes scheduled tasks and timed habits to a calendar named “Horizon” (created on first use in your default calendar account). You can pick another writable calendar in Settings → Calendar.

You can turn access off at any time in System Settings → Privacy & Security → Calendars. Because this preview is ad-hoc signed, macOS may ask for calendar access again after you install a new version.

The app does not install a background agent, start at login, or request Accessibility or Screen Recording access.

## Check the Download

Download `SHA256SUMS.txt` from the same release. In Terminal, change to the download folder and run:

```sh
shasum -a 256 Horizon-0.1.0-macOS-universal.zip
```

Compare the result with the ZIP's entry in `SHA256SUMS.txt`. This detects disagreement with the published file; it is not a digital signature, security audit, or Apple approval.

## Updates and Existing Data

Quit Horizon normally, then replace the app in Applications. Your data stays in `~/Library/Containers/app.horizon.mac/`; do not delete that folder when updating. 0.1.0 has no export or backup feature of its own, so keep Time Machine or another backup if your plans matter to you.

## Uninstall

Quit the app and move `Horizon.app` to the Trash. Removing the app does not remove its data. To remove local records too, delete `~/Library/Containers/app.horizon.mac/`. If you connected Apple Calendar, the “Horizon” calendar and its events remain in the Calendar app until you delete them there.

## 中文安装要点

下载带有 `macOS-universal.zip` 的应用压缩包，解压后拖入“应用程序”。安装包包含 Apple 芯片和 Intel 架构，最低构建目标为 macOS 15，但 Intel 真机、旧系统和另一台全新 Mac 尚未实测。

本版没有 Apple 开发者身份签名和公证，首次启动可能被拦截。确认信任下载后，仅按 [Apple 官方说明](https://support.apple.com/zh-cn/102445)手动允许；不要关闭系统安全检查、运行移除隔离标记的脚本，或绕过“将损害电脑”“已损坏”提示。

苹果日历是可选功能：点“连接”并允许完整访问后，会显示所选日历的日程，并把排程任务和定时习惯写入“Horizon”日历。安装新版本后，系统可能会再次询问日历权限。

更新时正常退出后替换应用即可，资料保存在 `~/Library/Containers/app.horizon.mac/`，不要删除。0.1.0 没有自带备份，请依靠时间机器等备份。卸载应用不会删除资料；需要时手动删除上述目录，并在“日历”应用中删除“Horizon”日历。
