---
layout: en
title: Fallback
nav_order: 10
parent: 使用指南
---

## What is Fallback?

Fallback PromptDialog 是指当系统遇到无法理解或处理的输入时使用的备份计划。 它帮助系统处理以下情况：

- 当用户提出不相关的问题（对话流程和常见问题解答不包括输入）时，系统会回答“我不知道”之类的内容。
- 如果用户的输入不清楚或不明确，系统会要求提供更具体的信息。
- 当系统对响应不确定时，它可能表明其不确定性。
- 如果出现技术问题或错误，系统会向用户解释问题并可能提供解决方案

## PromptAI 支持 Fallback 模式
PrompttAI中支持三种方法，如下图所示
- webhook
- action
- Talk2bits

![fallback-mode](/assets/images/tutorial/fallback-mode.jpg)
## 使用 Webhook Fallback
PromDialog还支持将默认回复交给第三方API处理

- See [Webhook-Fallback](docs/webhook/03-webhook/)

## 使用 Action Fallback
Action Fallback

## 使用 Talk2Bits Fallback
PrompDialog支持一键访问Talk2bits处理默认回复，让对话体验更加流畅
- [Knowledge of Talk2bits](/docs/knowledge_base/)

对于一些文本、文档和网络资料，可以通过Talk2Bits快速阅读构建知识库，并且可以通过连接Talk2Bits这样的平台与PromptAI互补。
本文将解释如何将 Talk2Bits 集成到 Fallback 中。

* 温馨提示：其他平台可以通过Webhook访问，如果您有任何疑问或要求，请联系我们。

### Talk2Bits

Talk2Bits可以在添加内容后自动生成配置码，不仅可以导入网页直接在右下角生成Chatbot，还可以通过手机扫码直接对话。
![01-default-reply.jpg](/assets/images/default_reply/01-default-reply.jpg)

* 欲了解更多详情，请访问：https://talk2bits.com/
* 聊天机器人介绍：https://talk2bits.com/app/publish

### 例子
接下来，我们将演示如何将 Fallback 连接到 Talk2Bits。

### Talk2Bits 代码

登录Talk2Bits后，点击“Chatbot”打开代码弹窗，然后点击“复制”按钮或手动复制即可获取导入的代码。![02-default-reply.jpg](/assets/images/default_reply/02-default-reply.jpg)


### 配置使用 Talk2bits Fallback

在项目“Overview”-“Fallback”中切换到“Talk2Bits”并粘贴上一步获得的代码，最后点击Save。
![03-default-reply.jpg](/assets/images/default_reply/03-default-reply.jpg)

### 测试
通过 Talk2Bits 响应用户输入。
![04-default-reply.jpg](/assets/images/tutorial/fallback_talk2bits_result.jpg)

## 默认 Fallback
当以上三种方法失败时，我们会使用默认的方法来处理Fallback，也就是下图中填写的文字。
![fallback-text](/assets/images/tutorial/fallback-text.jpg)