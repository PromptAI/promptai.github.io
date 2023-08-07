---
layout: en
title: 变量回复列表
parent: 更多功能
nav_order: 4
spliter: true
---
让我们创建一个水果营养专家的聊天机器人，它可以给出常见水果的每日摄入量：
```text
聊天机器人：欢迎来到水果营养专家！ 我可以帮助您了解各种常见水果的每日摄入量建议。 请告诉我您想了解哪种水果。
用户：苹果
聊天机器人：太棒了！ 对于成年人来说，每天吃1-2个苹果是不错的选择。 苹果富含膳食纤维、维生素和矿物质，有助于维持健康的消化系统和免疫功能。
用户： 香蕉
聊天机器人：对于成年人来说，每天吃1-2根香蕉是适度的。 香蕉是极好的能量来源，富含钾、维生素B6和膳食纤维，有助于维持正常的心脏和肌肉功能。
...
```
<!---
User: Grapes

Chatbot: Adults can consume a small bunch of grapes, about 10-15 grapes per day. Grapes contain abundant antioxidants and vitamin C, which can help protect cells from oxidative damage.

User: Watermelon

Chatbot: Watermelon is a refreshing fruit for the summer! Consuming a small slice of watermelon (about 200 grams) per day is a good choice. It has a high water content, helping to maintain body hydration, and is also rich in vitamins A and C.
--->
这项任务要求我们根据水果的类型做出不同的反应。

## 例子
创建一个对话流程，获取用户输入的水果放入`fruit_type`中，并根据`fruit_type`给出建议。

![condition_response_overview.jpg](/assets/images/condition_response_overview.jpg)

双击“请尝试另一种水果！”
- 如果没有匹配到水果类型，机器人会回复：“请尝试其他水果！”

单击“条件响应变体”进入编辑窗格。

![condition_response_bot.jpg](/assets/images/condition_response_bot.jpg)

选择要匹配的槽位，这里我们输入`fruit_type`。

![img_3.png](/assets/images/tutorial/conditional_response/03-slot-reply-list.png)

单击“添加新行”。

![img_1.png](/assets/images/tutorial/conditional_response/04-slot-reply-list.png)

添加槽值。

![img_2.png](/assets/images/tutorial/conditional_response/05-slot-reply-list.png)

输入需要匹配的槽位值，这里是`apple`。 `回复`是机器人将发送的响应。

![img.png](/assets/images/tutorial/conditional_response/06-slot-reply-list.png)

添加机器人回复。

![img_4.png](/assets/images/tutorial/conditional_response/07-slot-reply-list.png)

## 对话

![img.png](/assets/images/tutorial/conditional_response/08-slot-reply-list.png)
