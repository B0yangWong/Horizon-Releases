# Validation Scope / 验证范围

This preview has been checked on the development Apple silicon Mac running macOS 27.2. A successful build is not a claim that every supported Mac or first-download security flow has been tested.

## Public-Packaging Checks (0.4.1)

- Optimized Universal build with native `arm64` and `x86_64` slices and a macOS 15.0 minimum target. The bundle contains the app, the small `horizon-mcp` helper, the icon, the asset catalog, and English/Chinese strings; it links only Apple system frameworks.
- Ad-hoc signature and hardened runtime verified. Entitlements are limited to calendars, Apple Events, and audio input; no App Sandbox (see [Security](SECURITY.md)) and no debugger entitlement. The signing requirement is the same identifier as 0.2.0–0.3.0, so calendar permission carries over. The ZIP was extracted again and its signature verified.
- Pattern scans of the app bundle (all strings in every file) and of the public files found no local home paths, account names, email addresses, or text from the developer's own tasks, goals, lists, or secretary memories. Public images were checked for metadata. These checks reduce accidental disclosure; they are not an independent security audit.
- Screenshots come from the actual 0.4.x release builds (and, for some views, 0.3.0) with invented, in-memory data and Apple Calendar turned off. The two secretary chat screenshots are real answers from Claude Code (Sonnet) to that invented data, in English and in Chinese, and confirm that it answers in the interface language.
- The release provides a SHA-256 checksum and a signed update feed.

## Automated Tests

195 unit tests pass. Beyond the areas from earlier versions (habits and streaks, goal progress, My Day, calendar layout and sync, “gone quiet” and suggestions, lists, repeats, reminders, date recognition, backups, search, undo, countdown, sidebar drops), they cover:

- the secretary's exact command lines for Claude Code and Codex (tools, MCP servers, and saved sessions off), JSON answers and their validation, what each request includes, memories and their limits, and the alert and proactive-message limits (how often, gaps, quiet hours);
- the secretary answering in the interface language;
- the secretary staying **off** for new installs, staying on for someone who already used it, and refusing to send anything while off;
- quick-capture filing, message retention, learning from ratings, working-rule limits;
- update signatures (a forged one is rejected) and version comparison;
- Review statistics, My Day's calendar section, chat cards, shortcut tap/hold sharing, voice permission requests not crashing, and keyboard navigation.

## Hands-On Checks

In a separate copy of the app with its own identifier and data folder (so the developer's real data was never touched), using invented data:

- **In-app update, end to end:** an “old” copy found a new version on a local test server, downloaded it, verified the signature, replaced itself, and reopened as the new version. A version with a forged signature was refused, the app kept running unchanged, and the sidebar said why.
- **Secretary off by default:** a fresh install shows the explanation and the Turn On button, and makes no requests.
- My Day with the calendar section, Review for a week and a month, and the English and Chinese interfaces.

On the development Mac with the developer's own data and Claude Code: chat, task briefs, proactive messages, quick-capture filing, bringing along a selection, chat pictures, the calendar context, the quick-capture shortcut opening and closing the panel, and the 0.3.0 → 0.4.0 data move out of the sandbox.

## Remaining Limits

- Intel hardware, older macOS versions, and first installation on a separate clean Mac have not been tested.
- Voice capture with real speech was not tried after the last fix; the permission path is unit-tested. Hover labels on the Review chart were not checked with a real mouse.
- Codex was checked less than Claude Code. AI answers depend on the model and can be wrong; the secretary was tested for behaviour (limits, opt-in, filing), not for the quality of every answer.
- Reading the selection works only in apps that expose it to Accessibility or respond to ⌘C; new Outlook does not expose mail to AppleScript, so selecting the text is the way there.
- Notification delivery depends on macOS permission and Focus settings. Sync against every calendar provider (iCloud, Exchange, Google, local) was not tested.
- No iCloud sync between Macs, iPhone app, or Apple Reminders integration. Data is not independently encrypted. Force quitting can lose the most recent change.

## 中文摘要

0.4.1 在开发用 Apple 芯片 Mac（macOS 27.2）上检查：通用构建（含 `horizon-mcp` 小助手），临时签名与加固运行时有效，权限只有日历、Apple 事件和麦克风，不使用沙盒、不含调试权限，签名要求与此前相同，日历权限会保留；解压后签名有效。对应用包所有文件的字符串和公开文档做了扫描，没有发现本机路径、账户名、邮箱，也没有开发者自己的任务、目标、清单或秘书记忆内容；截图来自发布版本和内存中的虚构数据，日历和秘书均关闭。195 个单元测试全部通过，新增覆盖秘书按界面语言回答、秘书的命令行参数、请求内容、记忆、主动消息限制、**新安装默认关闭且关闭时不发送任何内容**、随手记归档、消息保留、更新签名（伪造签名会被拒绝）、回顾统计、快捷键短按/长按和键盘操作等。在独立测试副本中实测了完整的应用内更新（下载、验签、替换、重新打开），以及伪造签名被拒绝并在侧栏说明原因；还实测了新安装时秘书默认关闭。开发者本机用真实资料和 Claude Code 实测了聊天、读任务、主动消息、随手记归档、带上选中内容和从 0.3.0 沙盒迁移资料。尚未实测：Intel 真机、旧系统、全新 Mac 首次安装、真实语音输入、回顾图表的真实鼠标悬停；Codex 检查得比 Claude Code 少；AI 回答的质量取决于模型，可能出错。
