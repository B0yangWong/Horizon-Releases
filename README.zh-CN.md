<h1 align="center">Horizon</h1>

<p align="center"><img src="images/app-icon.png" width="96" alt="蓝色黑洞与发光对勾图标"></p>

<p align="center"><strong>把长期目标、每日任务和习惯放进一个安静的 Mac 计划工具。</strong></p>

<p align="center">把大目标拆成小步骤，对照苹果日历安排今天，让习惯坚持下去。</p>

<p align="center">
  <a href="https://github.com/B0yangWong/Horizon-Releases/releases/download/v0.1.0/Horizon-0.1.0-macOS-universal.zip">下载 Mac 版</a> |
  <a href="INSTALL.md">安装说明</a> |
  <a href="PRIVACY.md">隐私说明</a> |
  <a href="README.md">English</a>
</p>

---

Horizon 是一款原生 macOS 计划应用。设定长期目标，可以在下面再放短期目标，也可以不放；任务和习惯都能关联到目标。“我的一天”把今天的任务、日历日程和有固定时间的习惯合成一个列表。没有截止日期的任务也不会被遗忘：一段时间没动的事项会被温和地标出来。无需注册账户或配置云端服务。

本仓库只提供应用下载、使用文档和虚构示例截图，**不公开应用源码**。请下载 Releases 中的应用 ZIP；GitHub 自动生成的“Source code”压缩包只是本仓库的文档，不是安装包。

**0.1.0 预览版：最低构建目标为 macOS 15，通用安装包包含 Apple 芯片与 Intel 架构。** 已在开发用 Apple 芯片 Mac 上检查；Intel 真机、较旧的 macOS 和另一台全新 Mac 的首次安装尚未实测。应用采用临时本地签名，没有 Apple 开发者身份签名或公证，首次打开可能被系统拦截，详见[安装说明](INSTALL.md)。

## 主要功能

| 功能 | 使用方式 |
| --- | --- |
| 我的一天 | 选出今天要做的事。今天到期、今天排了时间的任务、苹果日历日程和有固定时间的习惯按时间排在一个列表里，每天自动重新开始。 |
| 目标 | 建立长期目标，可以在下面放短期目标；截止日期可有可无。进度根据任务和短期目标自动汇总。 |
| 目标总览 | 查看所有目标和进度，新建目标；已达成和已归档的目标也在这里，归档的可以恢复。 |
| 任务 | 添加步骤、备注、截止日期（今天、明天、下周或在日历上选择）、重要标记，并关联到任意目标。 |
| 习惯 | 每天、每周固定几天或每周几次。在最近 7 天的打卡格里打卡，查看连续天数；也可以给习惯设定固定时间。 |
| 日历 | 日视图和周视图，显示苹果日历日程。把待排程的任务拖到时间格上为它预留时间，或双击空白处直接新建。 |
| 苹果日历双向同步 | 排了时间的任务和有固定时间的习惯会写入名为“Horizon”的日历；在苹果日历里移动、改名或删除，Horizon 会同步更新；完成的任务标题前会加 ✓。可选功能。 |
| 不让事情溜走 | 没有截止日期的任务和一段时间（默认 14 天）没有进展的目标会得到“久未推进”提示；每天“我的一天”会推荐几个至少 3 天没动过的任务。 |
| 细节 | 对勾描线动画、轻柔的完成音效、清空“我的一天”或达成目标时的彩带、拖动排序，并支持“减弱动态效果”。 |
| 中英文界面 | 界面跟随 Mac 系统语言，支持英文和简体中文。 |

## 界面预览

以下是 0.1.0 实际构建版本的截图，使用内存中的虚构目标、任务和习惯，并关闭了苹果日历，不含任何个人资料。全新安装不包含这些示例内容。

<p align="center"><img src="images/my-day-zh.jpg" width="900" alt="中文界面的“我的一天”"></p>

<p align="center"><img src="images/goal-en.jpg" width="900" alt="短期目标页面：习惯、任务和进度环"></p>

<details>
<summary>目标总览、日历和习惯</summary>

<p align="center"><img src="images/goals-en.jpg" width="900" alt="目标总览"></p>

<p align="center"><img src="images/calendar-en.jpg" width="900" alt="周日历与待排程任务"></p>

<p align="center"><img src="images/habits-en.jpg" width="900" alt="习惯打卡与连续天数"></p>

</details>

## 安装与打开

1. 从 [0.1.0 版本](https://github.com/B0yangWong/Horizon-Releases/releases/tag/v0.1.0)下载 [Horizon-0.1.0-macOS-universal.zip](https://github.com/B0yangWong/Horizon-Releases/releases/download/v0.1.0/Horizon-0.1.0-macOS-universal.zip)。
2. 解压后把 `Horizon.app` 拖入“应用程序”。不需要 Xcode 或其他运行环境。
3. 打开应用。如果系统提示无法验证开发者，请确认你信任这个下载，然后仅按 [Apple 官方说明](https://support.apple.com/zh-cn/102445)手动允许。如果提示“将损害电脑”或“已损坏”，请停止并反馈。不要关闭系统安全检查，也不要运行移除隔离标记的命令。
4. 在“我的一天”添加任务，或新建第一个目标。想在 Horizon 里看到日历，点“我的一天”或日历页里的“连接”，并允许完整的日历访问权限；也可以跳过。

发布页附带 `SHA256SUMS.txt`，用于核对下载文件是否完整；它不能证明发布者身份，也不代表 Apple 认可。详见[安装说明](INSTALL.md)。

## 常用快捷键

| 操作 | 快捷键 |
| --- | --- |
| 跳到当前列表的“添加任务” | `Command + N` |
| 新建目标 | `Command + Shift + N` |
| 我的一天、重要、目标、计划内、全部任务、日历、习惯 | `Command + 1` … `Command + 7` |
| 完成选中的任务 | `Command + D` |
| 把选中的任务加入或移出“我的一天” | `Command + T` |
| 标记选中的任务为重要 | `Command + I` |
| 删除选中的任务 | `Command + Delete` |
| 关闭任务面板 | `Escape` |
| 设置 | `Command + 逗号` |

点任务打开详情面板；窗口较窄时面板会浮在列表上方。右键任务、目标和习惯有更多操作，双击习惯可以编辑。

## 资料保存在你的 Mac 上

目标、任务和习惯保存在应用的沙盒目录 `~/Library/Containers/app.horizon.mac/` 中，应用不会上传到本仓库。没有账户、广告、统计上传、云同步服务或自动更新检查。

苹果日历访问是可选的。允许后，Horizon 会读取你选择显示的日历中的日程，并把排了时间的任务和有固定时间的习惯写入“Horizon”日历。如果这个日历位于 iCloud 或其他在线账户，会由 Apple 或该服务商像其他日历一样同步。详见[隐私说明](PRIVACY.md)。

更新需要手动进行：退出应用后替换即可，资料保留在原目录。0.1.0 没有自带导出或备份功能，可依靠时间机器等 Mac 备份。

## 当前限制与反馈

Horizon 是本机使用的预览版，不包含 iPhone 应用、多台 Mac 之间的 iCloud 同步、通知提醒、苹果“提醒事项”集成、导入导出或协作。“每周几次”的习惯没有固定日子，不会写入苹果日历。由于采用临时本地签名，安装更新后系统可能会再次请求日历权限。已检查与未检查的范围见[验证范围](VALIDATION.md)。

[问题反馈和功能建议](https://github.com/B0yangWong/Horizon-Releases/issues/new/choose)请写明应用版本、macOS 版本，并用虚构内容描述复现步骤。Issue 是公开的，请不要附上真实的任务清单、日历内容或含有个人信息的截图。报告安全问题前请先阅读[安全说明](SECURITY.md)。

应用可免费下载并在自己的 Mac 上运行。本仓库不授予应用或图标的开源许可，详见[使用范围](USAGE.md)和[更新记录](CHANGELOG.md)。
