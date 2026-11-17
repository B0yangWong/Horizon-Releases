# Security Reports / 安全问题反馈

Please do not disclose real task lists, calendar details, backup or export files, credentials, or personal information in a public issue.

For a suspected vulnerability, use GitHub's private vulnerability reporting option in this repository's Security tab if it is available. If it is not available, open a minimal public issue requesting a private reporting channel without posting the exploit or sensitive data. Ordinary bugs can be reported with invented data through the issue template.

Include the app version, macOS version, a minimal reproduction using invented goals and tasks, and the potential impact. There is no guaranteed response time or security certification for this preview.

## How the App Is Built

- Hardened runtime, **without** the App Sandbox since 0.4.0: the optional AI secretary starts the Claude Code or Codex command-line tool the user installed, which a sandboxed app cannot do. Entitlements: calendars, Apple Events (to read the selected mail or browser page for quick capture, with macOS asking per app), and audio input (voice capture). No debugger entitlement in the public build.
- Only Apple system frameworks; no third-party code in the app. The AI tools are separate programs the user installs; Horizon runs them with their own tools, MCP servers, and saved sessions turned off, and marks task content and attachments as data, not instructions, in its prompts. Like any AI model, they can still be misled by content you give them; the secretary only suggests, and changes nothing without a click (except filing quick captures when that option is on).
- The `horizon-mcp` helper inside the app talks to Horizon over a Unix socket in Horizon's own folder with permissions limited to the current user. It is only reachable by tools the user registered it with.
- In-app updates are installed only if the archive matches an Ed25519 signature from the developer's private key, has the same bundle identifier and a higher version, and passes `codesign --verify`.
- Ad-hoc signed, with no Developer ID or Apple notarization. So that macOS keeps calendar permission across updates, the signature's designated requirement names the bundle identifier `app.horizon.mac` instead of one specific build. The trade-off: another ad-hoc-signed app that uses the same identifier could be treated as Horizon by macOS privacy settings. Install only from this repository's Releases.

Published SHA-256 checksums help detect changed downloads but do not authenticate a publisher or replace Developer ID signing. Do not disable system-wide security protections.

安全问题请优先使用仓库 Security 页的私密报告入口。如果该入口不可用，只在公开 Issue 中请求建立私密渠道，不公开漏洞细节、真实任务、日历内容、备份或导出文件、密钥或其他个人信息。复现材料使用虚构数据。本预览版没有承诺响应时限或安全认证。

从 0.4.0 起，应用启用加固运行时但**不再使用 App Sandbox**，因为可选的 AI 秘书需要启动用户自己安装的 Claude Code 或 Codex。权限只有日历、Apple 事件（随手记读取选中邮件或网页，系统会按 app 询问）和麦克风（语音随手记）；公开版本不含调试权限，应用本身只使用 Apple 系统框架。AI 工具是用户自行安装的独立程序，Horizon 调用时会关闭它们自带的工具、MCP 服务器和会话保存，并在提示里把任务内容和附件标为资料而非指令；但 AI 仍可能被内容误导，所以秘书只提建议，不点就不改（开启时的随手记归档除外）。`horizon-mcp` 小助手通过 Horizon 目录里仅限当前用户的本地套接字通信。应用内更新只有在 Ed25519 签名与开发者私钥一致、标识相同、版本更高且代码签名有效时才会安装。应用为临时本地签名，没有开发者身份签名或公证；为了让更新后保留日历权限，签名要求只认应用标识 `app.horizon.mac`，代价是同样使用这个标识的其他临时签名应用可能被系统当作 Horizon。请只从本仓库的 Releases 下载。
