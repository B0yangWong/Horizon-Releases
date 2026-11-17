# Install Horizon / 安装 Horizon

## Compatibility

- Download: `Horizon-0.4.1-macOS-universal.zip`.
- Includes native `arm64` and `x86_64` executables for Apple silicon and Intel Macs.
- Both executable slices have a macOS 15.0 minimum deployment target. This is a build target, not a claim of testing every supported OS.
- Checked on the development Apple silicon Mac. Intel hardware, older macOS, and a separate clean Mac have not been tested.
- Free for personal, non-commercial use only; see [Usage Terms](USAGE.md).
- The app is self-contained. No Xcode or Horizon account is needed. The optional AI secretary needs Claude Code or Codex, which you install and sign in to yourself (see below).
- This preview is ad-hoc signed with hardened runtime; it has no Developer ID identity or Apple notarization. Since 0.4.0 it does not use the App Sandbox, so that the secretary can start your Claude Code or Codex.

## Install and First Launch

1. Download the app ZIP from [the latest release](https://github.com/B0yangWong/Horizon-Releases/releases/latest). The “Source code” assets are documentation archives, not app installers.
2. Extract and move `Horizon.app` into Applications. Do not run it from inside the archive or from Downloads: in-app updates need a folder Horizon can write to.
3. Open the app. If macOS cannot verify the developer, only proceed if you trust this release. After the first attempt, follow [Apple's manual instructions](https://support.apple.com/en-us/102445) under System Settings → Privacy & Security → Open Anyway, if available. Managed Macs may forbid this. Do not disable Gatekeeper globally or use a script to remove download quarantine.
4. A warning that the app is damaged or will harm your computer is a reason to stop and report the problem, not an instruction to bypass it.
5. Horizon asks once whether it may send notifications, for reminders and (if you turn it on) secretary messages. You can change this in System Settings → Notifications → Horizon.
6. The interface follows your Mac's language (English or Simplified Chinese); choose another in Settings → General → Language, then reopen.

## Updating

**From 0.3.0 or earlier:** quit Horizon, replace the app in Applications, and open it. On first launch, 0.4.0 copies your data and settings out of the old sandbox folder (`~/Library/Containers/app.horizon.mac/`) into `~/Library/Application Support/Horizon/` and leaves the old folder unchanged as a fallback. Calendar permission carries over. Because the app now runs outside the sandbox, macOS may ask about some permissions again the first time they're used.

**From 0.4.0 on:** Horizon checks for a new version once a day (Settings → General → “Check for updates automatically”). When one is available, click **Update to …** at the bottom of the sidebar, or **Install … and Reopen** in Settings → General. Horizon downloads it, checks its signature and version, replaces itself, and reopens. Your data is not touched. You can always update by hand instead: quit, replace the app, open.

## Apple Calendar (Optional)

Choose **Connect** in My Day, the Calendar view, Planned, or Settings → Calendar, and allow full calendar access. Horizon then shows events from the calendars you select and writes scheduled tasks, tasks with a due date (as all-day events), and timed habits to a calendar named “Horizon”. You can pick another writable calendar, or stop adding due dates, in Settings → Calendar. Turn access off at any time in System Settings → Privacy & Security → Calendars.

## Quick Capture, Voice, and the Menu Bar

- `Control + Option + N` opens the quick-capture bar in any app; `Control + Option + V` starts voice capture. Change either in Settings → Quick Capture, and choose **Tap** or **Hold** for each. Two shortcuts may use the same keys if one is Tap and the other Hold.
- **Voice capture** asks for Microphone and Speech Recognition permission the first time.
- **Bring along what's selected** (on by default, switchable in Settings → Quick Capture): to read the selected text in other apps, Horizon needs Accessibility permission. Settings → Quick Capture → “Allow…” opens the request; you can grant it in System Settings → Privacy & Security → Accessibility. Reading the selected mail in Mail or Outlook, or the page in a browser, makes macOS ask for Automation permission for that app. Without these permissions, quick capture still works; you can paste, or use **Services → Send to Horizon**.
- Horizon places a checkmark icon in the menu bar; hide it in Settings → Quick Capture.

## AI Secretary (Optional)

The secretary is off until you turn it on. It needs one of these on your Mac, installed and signed in by you:

1. **Claude Code**, with a Claude plan that includes it. In Terminal: `brew install --cask claude-code`, then `claude auth login`. See [github.com/anthropics/claude-code](https://github.com/anthropics/claude-code) for other ways to install.
2. **Codex**, with a ChatGPT plan that includes it. In Terminal: `brew install --cask codex`, then `codex login`. See [github.com/openai/codex](https://github.com/openai/codex).

Then open Settings → Secretary, turn on **Use the AI secretary**, pick the tool and a model, and click **Test**. The status rows show whether each tool is installed and signed in; **Check Again** picks up a sign-in made after Horizon opened. Read [Privacy](PRIVACY.md) for what is sent to Anthropic or OpenAI.

Optional settings on the same page: About me and term dates, how often it may write (never to up to 6 a day), quiet hours, tone, the morning brief, notifications for its messages, and **Open Horizon at login**, so it can write to you without you opening the app first.

## Check the Download

Download `SHA256SUMS.txt` from the same release. In Terminal, change to the download folder and run:

```sh
shasum -a 256 Horizon-0.4.1-macOS-universal.zip
```

Compare the result with the ZIP's entry in `SHA256SUMS.txt`. This detects disagreement with the published file; it is not a security audit or Apple approval. In-app updates are additionally checked against the developer's signing key.

## Backups and Existing Data

Horizon keeps an automatic backup file, replaced as you work, plus the first backup of each of the last 7 days (Settings → Backup), by default in `~/Library/Application Support/Horizon/Backups/`. Choose a folder on another disk if you want the backup to survive losing this one, and use **Export…** to keep a copy from a particular day. Files attached to tasks are not inside backups; they stay in the `Materials` folder. Time Machine covers both.

## Uninstall

Quit the app and move `Horizon.app` to the Trash. Removing the app does not remove its data. To remove local records too, delete `~/Library/Application Support/Horizon/`, `~/Library/Preferences/app.horizon.mac.plist`, the old `~/Library/Containers/app.horizon.mac/` if it exists, and any backup folder or exported files you chose. Turn off **Open Horizon at login** first if you enabled it, and remove Horizon from Claude Code or Codex if you added it there. The “Horizon” calendar and its events remain in the Calendar app until you delete them there.

## 中文安装要点

从[最新版本页](https://github.com/B0yangWong/Horizon-Releases/releases/latest)下载带有 `macOS-universal.zip` 的应用压缩包（仅限个人、非商业使用，见[使用条款](USAGE.md)），解压后拖入“应用程序”（不要在压缩包或“下载”文件夹里直接运行，应用内更新需要可写的位置）。安装包包含 Apple 芯片和 Intel 架构，最低构建目标为 macOS 15，但 Intel 真机、旧系统和另一台全新 Mac 尚未实测。

本版没有 Apple 开发者身份签名和公证，首次启动可能被拦截。确认信任下载后，仅按 [Apple 官方说明](https://support.apple.com/zh-cn/102445)手动允许；不要关闭系统安全检查、运行移除隔离标记的脚本，或绕过“将损害电脑”“已损坏”提示。从 0.4.0 起应用不再使用 App 沙盒，以便秘书能启动你安装的 Claude Code 或 Codex。

首次打开会询问一次通知权限（用于提醒，以及开启后秘书的消息）。界面默认跟随系统语言，可在“设置 → 通用 → 语言”里改为中文或英文，重新打开后生效。

**升级：**从 0.3.0 或更早版本升级时，退出后替换应用再打开即可；0.4.0 首次启动会把资料和设置从旧沙盒目录 `~/Library/Containers/app.horizon.mac/` 复制到 `~/Library/Application Support/Horizon/`，旧目录保持不变，日历权限会保留，个别权限可能在首次用到时再询问一次。从 0.4.0 起，Horizon 每天检查一次新版本（可在“设置 → 通用”关闭），点左侧栏底部的“更新到 …”或设置里的“安装 … 并重新打开”即可自动更新；它会先核对签名和版本，资料不受影响。也可以继续手动替换。

**日历（可选）：**点“连接”并允许完整访问后，会显示所选日历的日程，并把排了时间的任务、有截止日期的任务（全天日程）和定时习惯写入“Horizon”日历。

**随手记与语音：**默认 ⌃⌥N 随手记、⌃⌥V 语音，可在“设置 → 快速记录”中修改，并为每个快捷键选择“短按”或“长按”；一个短按、一个长按时可以用同一组按键。语音第一次使用时会询问麦克风和语音识别权限。“带上当前 App 里选中的内容”需要“辅助功能”权限（设置里点“允许…”），读取 Mail/Outlook 邮件或浏览器页面时系统会按 app 询问“自动化”权限；不给这些权限也能正常随手记，可以直接粘贴或使用“服务 → 发送到 Horizon”。

**AI 秘书（可选）：**默认关闭。需要你自己安装并登录其一：Claude Code（需包含它的 Claude 订阅；终端运行 `brew install --cask claude-code` 后 `claude auth login`），或 Codex（需包含它的 ChatGPT 订阅；`brew install --cask codex` 后 `codex login`）。然后在“设置 → 秘书”打开“使用 AI 秘书”，选择工具和模型并点“测试”。发送哪些内容请看[隐私说明](PRIVACY.md)。同一页还可以设置“关于我”、学期、主动发消息的频率、免打扰时段、语气、早间简报和“登录时打开 Horizon”。

**备份：**一个随时覆盖的自动备份文件，加上最近 7 天每天一份，默认在 `~/Library/Application Support/Horizon/Backups/`；任务附件不在备份里，保存在 `Materials` 文件夹。可以把备份位置改到另一块磁盘，或用“导出…”保存某一天的副本。

**卸载：**卸载应用不会删除资料；需要时删除上面提到的资料目录、设置文件、旧沙盒目录和自选的备份位置，先关闭“登录时打开 Horizon”，并在 Claude Code 或 Codex 中移除 Horizon；“Horizon”日历需在“日历”应用中自行删除。
