---
layout: en
title: 设计问题
parent: 常见问题
nav_order: 2
---

### 机器回复可以回复附件吗？
可以，请参考[创建对话流图 - 添加机器回复节点](/docs/tutorial/flow/#添加机器回复节点).

### 支持在一句华中提取多个变量吗? 例如, "我想要五个苹果"
支持. 您可以在用户输入节点的训练语句中标注多个变量。

其他：
- 信息收集: [一句话提取多个变量](/docs/tutorial/form/#can-i-fill-multiple-slots-in-one-sentence). 

### 在对话过程中，我想根据不同的用户输入输出不同的回答应该怎么办？
有几种方法可供参考。

方案一：对对话流进行分支，并在每个分支中添加一个条件。 条件可以是槽值是否为空。 请参考[机器回复条件](/docs/zh/tutorial/advance_control/reply_conditions/)。

方案二：不同的slot值触发不同的响应。 请参阅[条件响应](/docs/zh/tutorial/advance_control/条件响应)。 此解决方案可以减少流程的分支数量。

方案三：调用Webhook。 响应是通过调用 [webhook](/docs/tutorial/webhook/02-webhook/) 检索到的值动态生成的。 例如查询账户余额。

方案四：使用Action [Action](/docs/tutorial/tutorial/bot_action/)，通过Python代码可以实现不同的响应。

### 我可以将自己的项目添加到项目模板中吗？
模板项目由系统管理员创建并管理，自己的账号暂无法添加到项目模板。

- Tips: 如果需要在项目之间复制FAQ/和对话流图，可使用收藏功能。

### 为什么提示"训练中，请稍后再试"？
出现这个提示是由于其他FAQ/会话流图正在调试中，由于资源限制只能同时发起一个调试任务。

### 用户有一段时间没有活跃了, 机器人可主动发送询问吗？
暂时不支持。
