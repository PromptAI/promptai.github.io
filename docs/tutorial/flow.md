---
layout: en
title: 对话流图
parent: 使用指南
nav_order: 4
---

## 创建流程
单击左侧导航窗格中的`新增流图`以添加对话框新流程，在弹出的对话框中输入名称和描述。

![flow_create.jpg](/assets/images/tutorial/flow_create.jpg)

## 添加用户输入节点
创建新的对话流后将显示流窗口,单击流程的根节点，在这里我们单击`添加用户节点`。

![flow_add_user_node.jpg](/assets/images/tutorial/flow_add_user_node.jpg)

## 编辑用户输入节点
点击用户输入； 右侧会弹出编辑窗格，尽可能的设置多个训练例句以确保模型正确分类用户意图。

![flow_edit_user_node.jpg](/assets/images/tutorial/flow_edit_user_node.jpg)

以下是您可以为用户话语做出的一些选项。

| 名称                           | 描述            |
|--------------------------------|-------------------|
| 期望用户输入         | 当前节点的期望用户输入    |
| 从意图模版中选        | 从[意图模版](/docs/tutorial/template_user/)中选择   |
| 保存到意图模版            | 保存到[意图模版](/docs/tutorial/template_user/)    |
| 是否需要变量           | 是否从意图中提起变量   |
| 描述                    | 描述当前节点（可选）|
| 重置变量值 | 可以[重置变量值](/docs/advance_control/reset_slot/)   |

## 创建智能回复节点
继续到用户输入节点，然后从弹出菜单中选择`添加机器人节点`。 

![flow_edit_bot_node.jpg](/assets/images/tutorial/flow_edit_bot_node.jpg)

以下是您可以为机器人回复设置的一些选项。

| 名称            | 描述            |
|----------------|-------------------|
| 机器回复        | 聊天机器人将回复的消息|
| 从回答列表中选取 | 从[回答列表](/docs/tutorial/template_bot/)中选择     |
| 保存到回答列表   | 保存到[回答列表](/docs/tutorial/template_bot/)|
| 变量回复列表      | [量回复列表](/docs/advance_control/reply_conditions/)在回复前生效         |
| 重置变量值      | 如果需要，[重置变量值](/docs/advance_control/reset_slot/)可以重置变量插槽               |
| 回复条件        | 通过不同[变量](/docs/advance_control/reply_conditions/)回复不同的消息     |

机器人可以做出五种不同类型的回复：

- Text       : 文本消息
- Image      : 图片消息
- Attachment : 附件消息
- Webhook    : 调用webhook 
- Action     : 运行Action

### 多条智能回复消息
我们可以向机器人响应节点添加多行文本，或者在当前机器人响应节点之后添加另一个机器人响应节点。

- 机器人响应节点添加多个文本响应，如图所示。
  
  ![flow_edit_bot_node_mutilp.jpg](/assets/images/tutorial/flow_edit_bot_node_mutilp.jpg)

- 在当前机器人响应节点之后添加另一个机器人响应节点的实现方法如图所示。
  
  ![flow_edit_bot_node_mutilp2.jpg](/assets/images/tutorial/flow_edit_bot_node_mutilp2.jpg)

<!--
When the machine replies to multiple content, you need to adjust the reply order of each content. You can refer to the following methods
- To adjust the order of multiple texts in the reply node, you can click the icon button, drag it to the desired order, and then release it
![20-bot-text-order.png](/assets/images/tutorial/flow/07-flow.png)
- If you need to adjust the reply order of multiple consecutive machine reply nodes, you only need to use the Recycle Bin function to adjust the order of machine reply nodes

The dialogue effect pictures of the two   methods are as follows:
![10-create-multi-bot-replay](/assets/images/tutorial/flow/08-flow.png)
-->

对话效果如下所示，文件将在对话中显示。 您可以直接点击文件名进行下载：

![flow_dialog_result.jpg](/assets/images/tutorial/flow_dialog_result.jpg)

## 完成

至此，一个简单的对话流程图就完成了。
