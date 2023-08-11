---
layout: en
title: 回复条件
parent: 更多功能
nav_order: 2
---
在机器人回复之前，可以通过槽是否有值来确定回复的内容。 您可以使用此机制来实现 if-then-else 的基本逻辑。

## 查询天气
根据用户的话语，有两种可能的回复：
- 回复天气信息或
- 询问用户位置
  
![01-reply-condition.png](/assets/images/tutorial/reply_condition/01-reply-condition.png)

如果用户输入不包含位置信息（此时我们可以使用`回复条件`来检测），机器人需要询问用户：
- 请告诉我你所在的城市？
![02-reply-condition.png](/assets/images/tutorial/reply_condition/02-reply-condition.png)

在这种情况下，我们可以提取"city"来确定位置。 

## 设置回复条件
- 点击`回复条件`
- 选择带有`区域`的`插槽名称`
- 在`条件值`中输入`Not Null`

这意味着当`area`有值时机器人会回复
![03-reply-condition.png](/assets/images/tutorial/reply_condition/03-reply-condition.png)

您可以设置询问位置的条件：
- 点击`回复条件`
- 选择带有`区域`的`插槽名称`
- 在`条件值`中输入`Null`

当`area`没有值时，将发送此回复。

![04-reply-condition.png](/assets/images/tutorial/reply_condition/04-reply-condition.png)

## 技巧
槽值可用于引导对话流到不同的分支。
