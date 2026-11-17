# Privacy / 隐私说明

Horizon works locally. It has no Horizon account, advertising, analytics, or cloud sync service. GitHub hosts downloads and public feedback; the app does not send your tasks or other data to GitHub.

Horizon itself makes only two kinds of network request, both to GitHub: a once-a-day check for a new version (Settings → General → “Check for updates automatically”, which you can turn off), and downloading an update when you choose to install it. Like any web request, these show GitHub your IP address and that a copy of Horizon is checking; they carry no tasks or personal content.

Everything else that can leave your Mac goes through features you turn on yourself, described below: the AI secretary, Apple Calendar, and voice capture.

## Local Records

Since 0.4.0, Horizon runs outside the macOS App Sandbox (the secretary needs to start the Claude Code or Codex tool you installed). Its files are:

- `~/Library/Application Support/Horizon/default.store` (with `-wal` and `-shm` files): goals, lists, tasks, steps, notes, due dates, scheduled times, reminders, repeat rules, categories, habits, check-ins, activity timestamps, the secretary's chat messages, memories, and working rules.
- `~/Library/Application Support/Horizon/Materials/`: files and pictures you attach to task notes or paste into the chat.
- `~/Library/Application Support/Horizon/Backups/` (or a folder you choose): the automatic backup file, plus the first backup of each of the last 7 days. Backups are readable JSON with all of the above except attached files (pasted text is included); restoring keeps one extra copy named “before restore”.
- `~/Library/Preferences/app.horizon.mac.plist`: settings, including the “About me” text and term dates you give the secretary.
- `~/Library/Application Support/Horizon/tools.sock`: a local connection point used only if you add Horizon to your own Claude Code or Codex (see below). Only your macOS user account can open it.

Chat messages are deleted after 90 days (180 if you rated them; a cleared conversation after a week). Attachments of tasks completed more than a month ago are cleaned up.

Neither the database nor backups or exports are encrypted by Horizon. An exported or backup file contains all your goals and tasks in readable form: keep it somewhere private, and never attach it to public issues. macOS FileVault, Time Machine, and disk permissions are separate from the app.

**Coming from 0.3.0 or earlier:** on first launch, 0.4.0 copies the database, backups, and settings out of the old sandbox folder `~/Library/Containers/app.horizon.mac/` and leaves that folder unchanged. Once you've checked everything is there, you can delete the old folder yourself.

## AI Secretary (Optional, Off by Default)

Horizon includes no AI service, API keys, or AI account. The secretary works only after you turn it on (in the chat panel or Settings → Secretary), and only through a command-line tool you installed and signed in to yourself: **Claude Code** (sends to Anthropic, using your Claude plan) or **Codex** (sends to OpenAI, using your ChatGPT plan). Their terms and privacy policies, and your settings with them, govern that data. Horizon never sees your sign-in or password.

While it's on, each request contains what that job needs:

- the tasks concerned, with their notes, steps, postponements, attached text (read on your Mac from PDFs, images, and pages), and pictures when you send them;
- other open tasks that are related or due soon, one line each, and your lists, goals, categories, and habits with recent check-ins;
- your Apple Calendar events, if Calendar is connected: all calendars, including hidden ones, from a year back to two years ahead (titles and times; the next 14 days also with locations and short notes);
- the “About me” text and term dates you entered, the secretary's memories, its working rules, and recent chat messages;
- for quick capture, what you typed and anything you chose to bring along (see below).

Requests are made when you ask something, when you open a task brief, and on its own within the limits you set (a morning brief, a weekly look at what keeps slipping, occasional check-ins, and every three days a look back at your thumbs up and down). Horizon runs the tool with its built-in tools, plug-ins (MCP servers), and saved sessions turned off, in an empty folder. Turning the secretary off stops all requests; what was already sent stays under the provider's policies.

**Using Horizon from Claude Code or Codex (optional):** Settings → Secretary → “Add to Claude Code / Add to Codex” registers a small helper (`horizon-mcp`, inside the app) with your own tool. When *you* then use that tool, it can list, search, read, create, and update your tasks, read your profile, and leave notes, through `tools.sock`. Changes it makes can be undone in Horizon. Remove it from your tool's MCP settings to stop.

## Quick Capture and Bringing Content Along

The quick-capture and voice shortcuts are registered with the standard macOS hot-key service; Horizon is told only when those combinations are pressed and does not see other keystrokes.

If “Bring along what's selected in the app you're in” is on (Settings → Quick Capture), pressing the shortcut reads, from the app in front:

- the selected text, using Accessibility permission (asked once; without it, nothing is read). Where an app doesn't expose its selection, Horizon presses ⌘C for you and puts your clipboard back afterwards; text marked as concealed (such as passwords from password managers) is ignored;
- in Mail or Microsoft Outlook, the selected message's subject, sender, and text; in Safari, Chrome, and similar browsers, the page title and address. These use Automation permission, which macOS asks for per app.

What's brought along is shown in the panel, can be removed, and is only saved, or sent to the secretary, when you press Return. Turn the option off and nothing is read. **Services → Send to Horizon** and pasting into the panel work without any permission.

## Voice Capture

Voice capture uses the microphone only while you're using it (holding or toggling the shortcut, or clicking the microphone). Speech is turned into text with Apple's speech recognition. When your language supports on-device recognition, Horizon requires it, so audio stays on the Mac; otherwise Apple's speech service processes it under Apple's terms. Nothing is recorded or kept; only the resulting text becomes a task. Permissions can be withdrawn in System Settings → Privacy & Security → Microphone and Speech Recognition.

## Notifications

Reminders and secretary messages can appear as local notifications showing a title and short text. Depending on your notification settings, macOS may show them on the lock screen or in Notification Center. Nothing goes through a push service.

## Apple Calendar

Calendar access is optional and requested only when you choose Connect. With access:

- Horizon reads events (title, time, location, notes, and calendar name) to show them in My Day, the countdown, the Calendar view, and search, and, if the secretary is on, to include them in its requests as described above. Events are read on demand; they are not copied into Horizon's database unless you import them.
- **Import from Calendar** copies chosen events into Horizon as tasks; they keep following their event, and Horizon never changes your own calendars.
- Horizon writes scheduled tasks, tasks with a due date, and timed habits as events in a calendar named “Horizon” (or another you pick): the title, time or day, a repeat rule for habits, and an internal `horizon://` link. Notes and steps are not written to Calendar.
- If you move, rename, or delete those events in Apple Calendar, Horizon updates the matching task or habit.

If the target calendar belongs to iCloud or another online account, that provider stores and syncs it like any of your calendars. You can revoke access in System Settings → Privacy & Security → Calendars.

## Updates

The update check downloads a small file (`latest.json`) from this repository's latest release. An update is installed only if its archive matches a signature made with the developer's private key, it is Horizon with a higher version number, and its code signature verifies. The app is then replaced in place and reopened; your data folder is not touched.

## Removal

Uninstalling the app does not remove its data. To remove local records, quit Horizon and delete `~/Library/Application Support/Horizon/` and `~/Library/Preferences/app.horizon.mac.plist`, the old `~/Library/Containers/app.horizon.mac/` if you used 0.3.0 or earlier, plus any backup folder or exported files you chose. If you added Horizon to Claude Code or Codex, remove it there too. Consider whether Time Machine or another backup still has copies. Events Horizon created stay in the Calendar app until you delete the “Horizon” calendar.

## Public Feedback

GitHub issues and attachments can be public. Use invented tasks and goals, and redact usernames, paths, names, email addresses, calendar details, chat transcripts, and confidential material from screenshots. Never attach a backup or export file. See [Security](SECURITY.md) for vulnerability reporting.

## 中文摘要

Horizon 在本机工作，没有 Horizon 账户、广告、统计上传或云同步。Horizon 自己只向 GitHub 发两种请求：每天检查一次新版本（“设置 → 通用 → 自动检查更新”，可关闭），以及在你选择安装时下载更新；这些请求不包含任务或个人内容，但和任何网络请求一样，GitHub 能看到你的 IP 地址。其他可能离开 Mac 的内容，都来自你自己打开的功能：AI 秘书、苹果日历和语音随手记。

**本机资料：**从 0.4.0 起，Horizon 不再运行在 App 沙盒中（秘书需要启动你安装的 Claude Code 或 Codex）。资料库、秘书的聊天和记忆在 `~/Library/Application Support/Horizon/default.store`，附件在同目录的 `Materials/`，备份在 `Backups/`（或你选的位置，保留一个自动备份文件和最近 7 天每天一份），设置（包括给秘书的“关于我”）在 `~/Library/Preferences/app.horizon.mac.plist`。聊天消息 90 天后删除（点过赞或踩的 180 天，清空的对话一周后删除）。资料库、备份和导出文件都不单独加密，请妥善保管，不要附在公开 Issue 里。从 0.3.0 升级时，0.4.0 首次启动会把资料从旧沙盒目录 `~/Library/Containers/app.horizon.mac/` 复制出来，原目录保持不变，确认无误后可自行删除。

**AI 秘书（可选，默认关闭）：**Horizon 不带 AI 服务、API 密钥或 AI 账户。只有你自己打开秘书后它才工作，而且只通过你自己安装并登录的命令行工具：Claude Code（发给 Anthropic，用你的 Claude 订阅）或 Codex（发给 OpenAI，用你的 ChatGPT 订阅），数据适用对方的条款和隐私政策；Horizon 接触不到你的登录信息。打开期间，每次请求包含这项工作需要的内容：相关任务及其备注、步骤、附件文字和你发的图片；其他相关或快到期的任务（每条一行）；清单、目标、类别和习惯；已连接时的苹果日历日程（全部日历，含隐藏的，过去一年到未来两年）；“关于我”、学期日期、秘书的记忆和工作守则、最近的聊天；随手记时你输入和选择带上的内容。请求发生在你提问、让秘书看任务时，以及它在你设的范围内主动工作时（早间简报、每周回看拖延事项、偶尔的提醒、每三天根据你的反馈回顾一次）。Horizon 调用工具时关闭其自带工具、插件和会话保存。关闭秘书即停止发送；已发送的内容按服务商的政策处理。可选的“添加到 Claude Code / Codex”会把应用内的 `horizon-mcp` 小助手登记到你自己的工具里，之后你在那边使用时，它可以通过只有你的用户账户能打开的 `tools.sock` 查看、创建和修改任务，改动可在 Horizon 中撤销。

**随手记与带上内容：**快捷键使用 macOS 标准全局快捷键服务，只在按下这组按键时收到通知。开启“带上当前 App 里选中的内容”后，按快捷键时会读取前台 app 选中的文字（需要“辅助功能”权限；读不到时会代按 ⌘C 并在之后恢复剪贴板，标为隐藏的内容如密码会被忽略），以及 Mail 或 Outlook 中选中邮件的主题、发件人和正文、浏览器当前页面的标题和地址（需要系统按 app 询问的“自动化”权限）。带上的内容会显示在面板里，可以移除，只有按回车才会保存或交给秘书。关闭该选项就不会读取。“服务 → 发送到 Horizon”和直接粘贴不需要任何权限。

**语音随手记：**只在你使用时打开麦克风，用 Apple 的语音识别转成文字。你的语言支持本机识别时 Horizon 会强制本机识别，音频不离开 Mac；否则由 Apple 的语音服务按其条款处理。不录音、不保存音频，只保留识别出的文字。

**通知与苹果日历：**提醒和秘书消息以本机通知显示，不经过推送服务。日历为可选功能：允许后按需读取日程，用于显示、倒计时、搜索，以及在秘书打开时随请求发送；“从日历导入”只读跟随，不改你自己的日历；排了时间的任务、有截止日期的任务和定时习惯会写入“Horizon”日历（不含备注和步骤）。可随时在“系统设置 → 隐私与安全性”中撤销日历、麦克风、语音识别、辅助功能和自动化权限。

**更新：**只有当安装包与开发者私钥的签名一致、确实是更高版本的 Horizon、且代码签名有效时才会安装，资料目录不受影响。

**卸载：**卸载应用不会删除资料；需要时手动删除上述目录、设置文件、旧版沙盒目录和自选的备份位置，在 Claude Code 或 Codex 里移除 Horizon，并在“日历”应用中删除“Horizon”日历。公开反馈请使用虚构内容，不要上传含个人信息的截图、聊天记录或备份文件。
