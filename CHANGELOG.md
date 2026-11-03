# Changelog

## 0.3.0 — Lists, search, undo, and a deadline countdown

- Lists: your own lists (for example “Groceries” or “Homework”) under the smart lists, with a name, color, and icon, drag to reorder, and “@list” when adding a task. A task can be in a list and linked to a goal. Lists are part of backups; older backups still restore.
- Search (⌘F): task titles, notes, and steps (completed tasks included), goal, habit, and list names, and Apple Calendar events, grouped, with the matching words marked. An event opens in the month calendar and is pointed out for two seconds.
- Undo (⌘Z): deleting tasks, goals, lists, and habits, completing, My Day, importance, due date, time, repeat, reminder, goal and list changes, calendar moves, and habit check-ins. Deleting shows an “Undo” bar for a few seconds.
- Quick add recognizes repeats: “每天”, “每周一三五”, “每两周”, “隔周”, “工作日”, “每月15号”, “每晚9点”, “every mon and thu”, “every other week”, “monthly”, and more. “周末” and “this weekend” mean the coming Saturday.
- My Day countdown: the next few important due dates, goal deadlines, and exam- or deadline-like calendar events within 30 days, with the days left. Right-click to hide one.
- Drag any task onto My Day, Important, Planned, a list, or a goal in the sidebar.
- Due-date menus have “This weekend” (Saturday).
- Calendar: scroll over the month to turn the page; a month cell that is short of room shows the event's name, shortened, rather than only its time.
- Back and Forward between lists (⌘[ / ⌘]), a sidebar that slides over narrow windows, a larger toolbar and search field, smoother resizing, and a bigger, bolder “Today” due label. Overdue stays red.

中文：新增自定义清单（名称、颜色、图标、拖动排序，添加任务时用“@清单名”放入；清单会一起备份，旧备份仍可恢复）、⌘F 搜索（任务标题、备注、步骤、目标、习惯、清单和苹果日历日程，结果分组并标出匹配文字，点日程会在月视图中高亮两秒）、⌘Z 撤销（删除、完成、日期、重复、提醒、目标、清单、日历拖动和习惯打卡等，删除后显示几秒“撤销”条）、快速添加识别重复说法（“每周一三五”“隔周”“工作日”“every mon and thu”等）和“周末”、“我的一天”顶部的截止倒计时、把任务拖到左侧栏的列表或目标、截止日期菜单的“这周末”、月视图滚动翻页且格子里优先显示事件名称，以及栏目间返回/前进、窄窗口覆盖式侧栏、更大的工具栏和搜索框、更顺滑的窗口缩放、加大加粗的“今天”截止标签。

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
