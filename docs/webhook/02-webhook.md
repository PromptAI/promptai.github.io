---
layout: en
title: Webhook例子
parent: Webhook
nav_order: 2
---

# Webhook
{: .no_toc .header }
通过webhook，我们可以通过API调用与第三方系统进行通信：
- 提交信息，
- 接收信息，
- 更新信息。

### 创建业务订单
假设顾客在水果店订购了三个苹果（我们喜欢苹果），需要将用户的订单信息提交给订单系统

API of place fruit order:
```text
API调用地址: https://fruits.shop/api/place/order
请求方法: Post
请求体: {"type":"fruit type", "count": 3}

响应: {"status":200, "message":"已为您成功下单"}
```

Conversation:
```text
聊天机器人：欢迎光临，请问有什么可以帮您的吗？
用户：我想买一些苹果
机器人：你需要多少
用户：三
机器人：好的，请确认您的订单：3 个苹果
用户：是的
// 通过 webhook 调用 API 并收到交易确认
聊天机器人：已为您成功下单
```
用户确认订单信息后，我们调用webhook来下订单。

### Webhook 配置
![webhook_fruit.jpg](/assets/images/webhook_fruit.jpg)

### 通过 Webhook 处理Fallback
Webhook 还可用于处理Fallback。 请见[Fallback](/docs/webhook/03-webhook).
