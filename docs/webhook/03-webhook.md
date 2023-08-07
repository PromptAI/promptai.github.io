---
layout: en
title: Webhook - Fallback
parent: Webhook
nav_order: 3
---

当用户的意图无法识别时，webhook提供了另一种方式Fallback，例如可以调用大语言模型的API返回答案。

## Webhook
Webhook支持通过slots获取最新的用户输入和会话ID。
-latest_message：触发 webhook 时的用户输入。 如果是Fallback触发的webhook，则为触发fallback时的用户输入
- send_id：当前会话ID

### 例子
接下来，我们将演示如何将 Fallback 连接到 Webhook。 Webhook 需要调用外部 API 来获取响应。 假设我们有一个如下所示的 API：
```shell
curl http://localhost/chat?input=What can PromptAI do?&chatId=xxxx

{
	"message": "PromptAI是一个基于云的平台，用于设计专业智能助手。 它提供了一系列功能，包括可视化设计工具、快速定制和便捷集成。 PromptAI 可用于创建复杂的对话流并将其集成到业务系统中。"
}
```

通过 Http Get 请求将问题和会话 ID 作为输入，响应返回 JSON 格式的数据，其中消息字段为回复。
### Webhook 配置

![03-1-webhook.png](/assets/images/webhook_fallback.jpg)

首先，我们配置名称和请求地址，并根据API要求使用请求地址中内置的槽`{latest_message}`和`{send_id}`将用户输入和会话id发送到API。 收到返回的消息后，我们将`message`放入响应处理部分的`relpy`中，并将`{reply}`发送给用户。

### 使用Webhook配置Fallback

选择左侧导航窗格中的“Overview”，然后单击图中的“Fallback”。 

![03-3-webhook.jpg](/assets/images/webhook_falllbak_use.jpg)