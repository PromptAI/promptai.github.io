---
layout: en
title: 默认回复
nav_order: 10
parent: 使用指南
---

## 什么是默认回复?

指当系统遇到无法理解或处理的输入时使用的备份计划, 它帮助系统处理以下情况：

- 当用户提出不相关的问题（对话流程和常见问题解答不包括输入）时，系统会回答“我不知道”之类的内容。
- 如果用户的输入不清楚或不明确，系统会要求提供更具体的信息。
- 当系统对响应不确定时，它可能表明其不确定性。
- 如果出现技术问题或错误，系统会向用户解释问题并可能提供解决方案

## PromptDialog支持的默认回复
PromptDialog中支持两种种方法，如下图所示
- webhook
- action

![fallback-mode](/assets/images/tutorial/fallback-mode.jpg)

## 使用Webhook 
PromDialog支持将默认回复交给第三方API处理

- See [Webhook-Fallback](/docs/webhook/03-webhook/)

## 使用 Action Fallback
Action Fallback

## 文本回复
当以上两种方法失败时，我们会使用默认的文本来处理，也就是下图中填写的文字。

![fallback-text](/assets/images/tutorial/fallback-text.jpg)

使用按钮
- Flow: 发布的流图；
- FAQ : FAQ中的用户提问；

默认回复下方出现配置的按钮。

1、为什么配置了按钮未出现？
> 确认所配置的Flow/FAQ是否发布、启用。

2、我修改了配置需要重新训练吗？
> 修改实时生效，无重新需训练。

3、添加个数有限制吗？
> 暂时未限制。

![fallback-text-button](/assets/images/tutorial/allback-text-button.png)