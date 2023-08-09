---
layout: en
title: 定时任务
nav_order: 2
parent: 发布
grand_parent: 使用指南
---
{: .no_toc .header }

## 什么是定时任务

------
您是否遇到以下问题？
- 每天早上发布服务，使每日更新生效
- 早上上班前，FAQ/流程已接受过直接对话训练

针对上述类似的期刊工作，我们开发了定时任务功能。

- 可选的发布/调试
- 可选的常见问题解答/对话流程
- 任务启用/暂停
- 多个任务同时存在
- 任务在指定日期内生效

支持两种循环模式：
- Cron 表达式
- 固定时间间隔

------

### Cron 表达式

------

cron 表达式是由 6 或 7 个由空格分隔的字段组成的字符串。 字段可以包含任何允许的值，以及该字段允许的特殊字符的各种组合。 字段如下：

| 字段名 | 是否必填 | 填入的值 | 允许的特殊符号 |
| --- | --- | --- | --- |
| Seconds | YES | 0-59 | , - \* / |
| Minutes | YES | 0-59 | , - \* / |
| Hours | YES | 0-23 | , - \* / |
| Day of month | YES | 1-31 | , - \* ? / L W
|
| Month | YES | 1-12 or JAN-DEC | , - \* / |
| Day of week | YES | 1-7 or SUN-SAT | , - \* ? / L # |
| Year | NO | empty, 1970-2099 | , - \* / |

所以 cron 表达式可以像这样简单: \* \* \* \* ? \*

或者更复杂，像这样: 0/5 14,18,3-39,52 \* ? JAN,MAR,SEP MON-FRI 2002-2010

例子
--------

以下是一些完整的示例：

<table><tbody><tr><td>Expression</td><td>Meaning</td></tr><tr><td><tt>0 0 12 * * ?</tt></td><td>Fire at 12pm (noon) every day</td></tr><tr><td><tt>0 15 10 ? * *</tt></td><td>Fire at 10:15am every day</td></tr><tr><td><tt>0 15 10 * * ?</tt></td><td>Fire at 10:15am every day</td></tr><tr><td><tt>0 15 10 * * ? *</tt></td><td>Fire at 10:15am every day</td></tr><tr><td><tt>0 15 10 * * ? 2005</tt></td><td>Fire at 10:15am every day during the year 2005</td></tr><tr><td><tt>0 * 14 * * ?</tt></td><td>Fire every minute starting at 2pm and ending at 2:59pm, every day</td></tr><tr><td><tt>0 0/5 14 * * ?</tt></td><td>Fire every 5 minutes starting at 2pm and ending at 2:55pm, every day</td></tr><tr><td><tt>0 0/5 14,18 * * ?</tt></td><td>Fire every 5 minutes starting at 2pm and ending at 2:55pm, AND fire every 5 minutes starting at 6pm and ending at 6:55pm, every day</td></tr><tr><td><tt>0 0-5 14 * * ?</tt></td><td>Fire every minute starting at 2pm and ending at 2:05pm, every day</td></tr><tr><td><tt>0 10,44 14 ? 3 WED</tt></td><td>Fire at 2:10pm and at 2:44pm every Wednesday in the month of March.</td></tr><tr><td><tt>0 15 10 ? * MON-FRI</tt></td><td>Fire at 10:15am every Monday, Tuesday, Wednesday, Thursday and Friday</td></tr><tr><td><tt>0 15 10 15 * ?</tt></td><td>Fire at 10:15am on the 15th day of every month</td></tr><tr><td><tt>0 15 10 L * ?</tt></td><td>Fire at 10:15am on the last day of every month</td></tr><tr><td><tt>0 15 10 L-2 * ?</tt></td><td>Fire at 10:15am on the 2nd-to-last last day of every month</td></tr><tr><td><tt>0 15 10 ? * 6L</tt></td><td>Fire at 10:15am on the last Friday of every month</td></tr><tr><td><tt>0 15 10 ? * 6L</tt></td><td>Fire at 10:15am on the last Friday of every month</td></tr><tr><td><tt>0 15 10 ? * 6L 2002-2005</tt></td><td>Fire at 10:15am on every last friday of every month during the years 2002, 2003, 2004 and 2005</td></tr><tr><td><tt>0 15 10 ? * 6#3</tt></td><td>Fire at 10:15am on the third Friday of every month</td></tr><tr><td><tt>0 0 12 1/5 * ?</tt></td><td>Fire at 12pm (noon) every 5 days every month, starting on the first day of the month.</td></tr><tr><td><tt>0 11 11 11 11 ?</tt></td><td>Fire every November 11th at 11:11am.</td></tr></tbody></table>

欲了解更多详情，请访问 [quartz-scheduler](http://www.quartz-scheduler.org/documentation/quartz-2.3.0/tutorials/crontrigger.html)

### 固定时间间隔

------

定期执行以秒为单位的固定间隔执行。

## 概念

常用设置：

- 模式：固定时间间隔或 Cron
- 启用：是否启用该任务
- 火车类型：调试或发布
- 可培训模块：参与模块
- 任务执行时间间隔：在此时间段内可以运行任务

可选设置：

- 固定时间间隔：

````text
需要设置`固定时间间隔（秒）`

- 正整数
- 混合：100
````

- 克罗恩表达式：

````text
需要设置`自定义（Corn）`

- 有效的 cron 表达式
````

## 使用

------

### 每天00:00发布
![01-timed-task.png](/assets/images/tutorial/01-timed-task.png)

### 每 72 小时发布一次
![02-timed-task.png](/assets/images/tutorial/02-timed-task.png)