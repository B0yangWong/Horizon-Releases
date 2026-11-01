# Security Reports / 安全问题反馈

Please do not disclose real task lists, calendar details, backup or export files, credentials, or personal information in a public issue.

For a suspected vulnerability, use GitHub's private vulnerability reporting option in this repository's Security tab if it is available. If it is not available, open a minimal public issue requesting a private reporting channel without posting the exploit or sensitive data. Ordinary bugs can be reported with invented data through the issue template.

Include the app version, macOS version, a minimal reproduction using invented goals and tasks, and the potential impact. There is no guaranteed response time or security certification for this preview.

## How the App Is Built

- App Sandbox with hardened runtime. Entitlements: calendars, read/write access only to files and folders you pick in an Open or Save panel (export, import, backup folder), and app-scoped bookmarks to remember a chosen backup folder. No network, camera, microphone, contacts, or location entitlements, and no debugger entitlement in the public build.
- Only Apple system frameworks; no third-party code.
- Ad-hoc signed, with no Developer ID or Apple notarization. So that macOS keeps calendar permission across updates, the signature's designated requirement names the bundle identifier `app.horizon.mac` instead of one specific build. The trade-off: another ad-hoc-signed app that uses the same identifier could be treated as Horizon by macOS privacy settings. Install only from this repository's Releases.

Published SHA-256 checksums help detect changed downloads but do not authenticate a publisher or replace Developer ID signing. Do not disable system-wide security protections.

安全问题请优先使用仓库 Security 页的私密报告入口。如果该入口不可用，只在公开 Issue 中请求建立私密渠道，不公开漏洞细节、真实任务、日历内容、备份或导出文件、密钥或其他个人信息。复现材料使用虚构数据。本预览版没有承诺响应时限或安全认证。

应用运行在 App Sandbox 中并启用加固运行时，只申请日历、你在打开/保存面板中选择的文件（导出、导入、备份位置）以及记住备份位置所需的权限；没有网络、相机、麦克风、通讯录、位置权限，公开版本也不含调试权限，只使用 Apple 系统框架。应用为临时本地签名，没有开发者身份签名或公证；为了让更新后保留日历权限，签名要求只认应用标识 `app.horizon.mac`，代价是同样使用这个标识的其他临时签名应用可能被系统当作 Horizon。请只从本仓库的 Releases 下载。
