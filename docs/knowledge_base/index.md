---
layout: en
title: Knowledge Base
nav_order: 3
---
PromptDialog中有两种知识库：[FAQ](https://doc.promptai.us/docs/tutorial/faq/)和以文本、word、pdf、html等形式存储的非结构化内容。

FAQ请参考我们的[FAQ](https://doc.promptai.us/docs/tutorial/faq/)。

对于非结构化内容，PromptDialog集成了[talk2bits.com](talk2bits.com) 提供的服务，用户可以上传文档、为其建立索引，并获取 API 通过OpenAI/GPT查询这些文档。

## Talk2Bits
用户正在上传文档的 Talk2bits 屏幕截图。

![01-index.png](/assets/images/knowledge_base/01-index.png)

Talk2bits的屏幕截图，它在自己的界面中回答用户问题。

![02-index.png](/assets/images/knowledge_base/02-index.png)

Talk2bits生成一个可以放入PromptDialog中的链接。

![03-index.png](/assets/images/knowledge_base/03-index.png)

在Prompt Dialog中配置Fallback，以便可以将用户问题作为最后的手段来处理。
![04-index.png](/assets/images/knowledge_base.jpg)

现在机器人可以使用Talk2Bits所提供的回答。
![05-index.png](/assets/images/knowledge_base/05-index.png)
