---
layout: en
title: 概览
nav_order: 1
has_children: false
---
PromptAI提供了一个用于构建、运行和部署对话机器人的一体化DevOps平台。它支持所有四种运行模式：即可本地，也可云端部署的对话机器人设计和运维环境。

* 在云端设计机器人，在本地运行
* 在云端设计机器人，在云端运行（当前版本）
* 本地设计机器人，本地运行
* 在本地设计机器人，在云端运行

当前版本支持基于云的对话机器人设计/测试/训练/运行/维护。对于其他三个设置感兴趣的朋友请联系[info@promptai.cn](mailto:info@promptai.cn)。

PromptAI强调对用户数据的保护，并受到严格的加密和访问控制。它采用最先进的安全技术和措施，确保您的数据在传输和存储过程中得到持续的保护。

有两种方法可以训练和运行你的机器人。如果您设置了自己的Rasa环境，可随时下载根据您的设计， 自动生成的Rasa代码并测试您的机器人。或者您可以创建本地运行环境，如下所示，它为您打包了所有代码和执行环境。 具体分三个步骤：设计对话机器人、创建本地运行环境（您只需执行一次）、训练模型并使用 PromptDialog 运行机器人。

## 步骤 1 - 创建对话流
创建您的第一个对话流。

![overview_create_dialog_flow.jpg](/assets/images/overview/overview_create_dialog_flow.jpg)

## 步骤 2 - 创建本地环境 【可选】
只需一行命令即可搭建本地运行环境。 有关详细信息，请查看[运行聊天机器人：LRE](/docs/run_bots)，如果您有任何疑问，请查看[安装问题](/docs/common_questions/install_questions)。

![overview_create_agent.jpg](/assets/images/overview/overview_create_agent.jpg)


![05-overview.png](/assets/images/overview/05-overview.png)

## 步骤 3 - 调试和发布
现在您可以在 PromptDialog 中调试/运行新的聊天机器人。
![overview_running_debug_bot.png](/assets/images/overview/overview_running_debug_bot.png)

一旦您对结果感到满意就可以发布了，我们提供了多种[发布](/docs/tutorial/release/release_project/) 的方式。

* 发布

![overview_release_page.png](/assets/images/tutorial/release_released.jpg)

* Web应用程序

![chat-release-03](/assets/images/tutorial/release_web_script_demo_1.jpg)

* 对话记录和仪表板

![overview_chat_history.png](/assets/images/overview/overview_chat_history.png)

![overview_dashboard.png](/assets/images/overview/overview_dashboard.png)
