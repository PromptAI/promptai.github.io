---
layout: en
title: FAQ
parent: 使用指南
nav_order: 3
---
每个项目都有一个默认的FAQ（常见问题解答）模块。 Beta 版本仅允许每个项目有一个常见问题解答。

## FAQ 窗口

单击左侧导航窗格中的“FAQ”。 在FAQ窗口中，您可以添加、修改和删除问题。

![faq_list.jpg](/assets/images/tutorial/faq_list.jpg)

## 添加一个FAQ

点击右上角`+添加`按钮，弹出问题添加界面。

![faq_create.jpg](/assets/images/tutorial/faq_create.jpg)

## 填写问题/答案信息
请针对同一问题填写多个示例，这是 RASA 训练所必需的。 请确保：

- 每个问题只能列出一次，
- 每个问题应有多个示例：它们是同一个问题，但提出的方式不同。

![faq_create_info.jpg](/assets/images/tutorial/faq_create_info.jpg)

## 添加成功

![faq_create_success.jpg](/assets/images/tutorial/faq_create_success.jpg)

## 非结构化内容
如果您有 CSV、Word Doc、PDF、Text、HTML 等文件中的非结构化内容，您可以将这些文件上传到 [talk2bits.com]，该网站提供使用 ChatGPT/GPT4 直接回答您的问题的服务。 PromptDialog已经集成了这个功能。 请检查[知识库部分](https://doc.promptai.us/docs/knowledge_base/).

## 训练选项
当您训练模型时，我们提供三种训练选项：
- RASA 原生：它使用 RASA 自己的例程来训练常见问题解答分类器。 在这种情况下，要求用户提出几个类似的问题。
- ChatGPT/GPT4：它使用ChatGPT/GPT4进行问题比较并检索答案。 这是我们推荐的方法，因为设计者不需要提供许多类似的问题。 这需要通过 [talk2bits.com](talk2bits.com) 完成。 请检查[知识库部分](https://doc.promptai.us/docs/knowledge_base/)。
- 定制BERT模型：可以在本地训练和部署，以最好地保护隐私，并且性能介于RASA FAQ和ChatGPT之间。 对于此选项，请联系我们 [info@promptai.cn](info@promptai.cn)。

