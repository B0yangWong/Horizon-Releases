# Changelog

## 0.2.0 — Reminders, repeats, quick capture, and backups

- Repeating tasks: daily, weekdays, weekly, monthly, yearly, or custom (every N days/weeks/months/years, weekly on chosen days). Completing one creates the next with its time and reminder; unchecking takes it back.
- Reminders: “Remind me” 10 or 30 minutes before a task starts or at a custom time, plus optional automatic reminders before scheduled tasks, on the morning a task is due, and at habit times. Complete, check in, or snooze from the notification.
- Quick capture: a changeable global shortcut (⌃⌥N by default) opens a slim “Add a task” bar over any app, including full-screen ones; a menu bar window lists today's tasks and habits.
- Smart add in every add field: dates, times, lengths, “!” for important, and “#goal” in English or Chinese, shown as chips before adding.
- Calendar: a month view, a list of calendars grouped by account with Select All / Deselect All, and drag a task onto a day to make it due.
- Apple Calendar: tasks with only a due date are written as all-day events (switchable), and “Import from Calendar” in Planned adds upcoming events as tasks that follow their event. Holiday, birthday, and declined events are not imported.
- My Day: holidays and other all-day events sit above “Add a task”; right-click an event to remove it from today or hide its calendar.
- Backup: one automatic backup file replaced as you work, a copy kept before any restore, a choosable folder, and JSON export and import.
- Comfort: text size from 85% to 150% (⌘+ / ⌘− / ⌘0), drag sidebar lists into your own order, click empty space to close the task panel, completed tasks leave Planned after a moment, and goal deadlines use the month calendar.
- macOS now keeps Horizon's calendar permission across updates. The public build no longer includes the debugger entitlement.

中文：新增重复任务（每天、工作日、每周、每月、每年和自定义）、提醒（开始前 10/30 分钟、自定时间，以及排程任务、到期当天和习惯的自动提醒，可在通知上完成或稍后提醒）、全局快捷键快速记录（默认 ⌃⌥N，可改）和菜单栏窗口、所有添加框的中英文日期时间识别、日历月视图与按账户分组的日历显示开关、截止日期写入苹果日历的全天日程、“从日历导入”到“计划内”、“我的一天”顶部的节假日条（右键可移除或隐藏该日历）、单文件自动备份与 JSON 导出导入、文字大小调整、左侧栏目拖动排序等。更新后系统会保留日历权限；公开版本移除了调试权限。

## 0.1.0 — First public Mac preview

- A standalone Universal app for Apple silicon and Intel, sandboxed, with no third-party libraries.
- My Day: today's tasks, tasks due or scheduled today, Apple Calendar events, and timed habits in one list; it starts fresh every day.
- Long-term and optional short-term goals with optional deadlines, progress roll-up, and a goals overview with achieved and archived goals.
- Tasks with steps, notes, importance, goal links, and a due-date menu (Today, Tomorrow, Next week, or pick a date).
- Habits every day, on certain weekdays, or N times per week, with streaks, a 7-day check-in strip, and an optional set time.
- Day and week calendar with drag to schedule, and two-way sync of scheduled tasks and timed habits with a “Horizon” calendar in Apple Calendar.
- “Gone quiet” hints for undated tasks and quiet goals, plus daily suggestions for tasks untouched for at least 3 days.
- Keyboard shortcuts, completion sound, confetti, drag to reorder, layouts for narrow windows, and English/Chinese interfaces.
- Blue black-hole icon with a glowing checkmark.

This is the first public download of this app. It is not Developer ID signed or notarized. Intel hardware, older macOS versions, and a separate clean-Mac first install remain untested.

中文：首个公开 Mac 预览版，提供独立通用应用下载。包含“我的一天”（任务、日历日程与定时习惯合并显示）、长期/短期目标与进度、目标总览、任务步骤与截止日期菜单、三种频率的习惯与连续天数、日/周日历与拖动排程、苹果日历双向同步、“久未推进”提示与每日推荐、快捷键、小窗口布局和中英文界面。图标为蓝色黑洞与发光对勾。
