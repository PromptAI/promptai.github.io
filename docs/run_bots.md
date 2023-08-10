---
layout: en
title: 运行
nav_order: 3
has_children: false
---
{: .no_toc .header }

成功创建帐户后，您可以立即开始设计聊天机器人。有两种方法可以训练和测试您的设计。

- 云端: 这是首选选项，因为它支持RASA不具备的许多新功能。您还可以下载生成的RASA代码（它启用DIET和TEDPolicy作为默认训练选项）并在您自己的RASA环境中运行它。
- 本地: 您可以创建如下所示的本地运行环境，它为您打包了所有内容，并允许您与PromptDialog进行通信以运行和测试您的机器人。如果您更喜欢在本地设计、训练和运行机器人的完整云解决方案，请联系我们[info@promptai.cn](info@promptai.cn)。

##  本地运行环境 (LRE)
本地运行环境使用打包RASA 3.2.0的docker实现以及在PromptDialog Cloud和本地RASA环境之间通信的代理。PromptDialog Cloud管理设计的各个方面，本地RASA环境负责训练模型。

![03-local-running-env.png](/assets/images/local_running_env/03-local-running-env.png)

### 创建第一个Agent
本地机器应满足最低系统要求：
```text
操作系统   ：Linux/Mac操作系统
内存      ：至少8GB
GPU       ：CUDA 11.7 或更高版本（可选）
磁盘      ：空间：至少32GB可用
Docker环境：20.10.6 或更高版本
```
- [Docker是什么？](https://www.docker.com/)
- [安装Docker](https://docs.docker.com/get-docker/)

点击右上角`本地运行环境`-`管理代理`。 它将弹出一个窗口，您可以在其中添加代理。单击“+代理”，然后单击“安装代理”，您将看到以下内容。
![00-local-running-env.png](/assets/images/local_running_env/00-local-running-env.png)

或者单击“请安装您自己的本地代理来测试您的机器人。”[如果您可以看到此通知]

![01-local-running-env.png](/assets/images/run_bots_install_agent_2.jpg)

在安装和后续使用过程中，请确保本机能够通过网络访问Prompt Dialog服务。

- 允许网络访问 https://app.promptai.cn 端口：443

请根据您本地机器的操作系统执行弹窗中显示的安装命令：
```shell
curl -o install_agent.sh 'https://app.promptai.cn/rpc/install/install_agent.sh?key=your_config' && chmod +x install_agent.sh && ./install_agent.sh install
```
注意：安装往往与网络有关，请耐心等待。如果您需要帮助请通过 [info@promptai.cn](info@promptai.cn) 联系我们。

安装成功后，进入“管理Agents”页面可以看到已安装的Agent
![02-local-running-env.png](/assets/images/local_running_env/02-local-running-env.png)

安装完成，可以使用PromptDialog Cloud中的所有功能！

## 什么是Agent？
以下部分介绍代理的详细信息,您无需阅读本部分即可在PromptDialog中成功运行聊天机器人。

- 接收训练/部署任务
- 上传任务执行步骤、结果
- 接收和响应对话请求
- 创建、停止和升级AI容器


代理只会在您机器的以下目录中创建和操作。

- 操作系统：Linux / MacOS
- 位置    ：$HOME/zbot

* 请不要修改上述目录中的任何文件。


Agent安装成功后，会在“$HOME/zbot”目录下创建“install_agent.sh”脚本，用于升级和卸载Agent。
```shell
$HOME/zbot/install_agent.sh
```

Agent的实现是由Docker完成的，包括两个镜像和多个容器。

- Docker 镜像

| 名称  | 镜像                        | 解释                             |
|:------|:-----------------------------|----------------------------------|
|  AI   | registry.cn-hangzhou.aliyuncs.com/promptai/zbotai:release      | 人工智能模型                              |
| Agent | registry.cn-hangzhou.aliyuncs.com/promptai/zbot-agent:latest   | 代理服务，对AI容器进行管理 |


- Docker 容器

| 名称   |     容器     | 解释
|:------|:-------------|---------------------------------------------------|
|  AI   | zbot_a1_xxxx | "xxxx"为调试或发布的模型，可能有多个，数量与发布的项目有关 |
| Agent | zbot_agent   | 代理服务, 用于管理AI模型, 这只会有一个                 |


## 在Rasa中运行

当开发人员需要调试和验证设计的流程时，他们还可以使用“下载Rasa文件”功能在自己的RASA设置中下载生成的RASA代码。 但是，PromptDialog Cloud 中的一些有用功能将丢失。

### 仅在 PromptDialog Cloud 中可用的功能

<!---
| Features                  | Prompt Dialog | Run In Rasa |
|---------------------------|--------------|-------------|
| Attachment bot reply      |         ✅   |       ❌    |
| Chat history              |         ✅   |       ❌    |
| Condition reply           |         ✅   |       ❌    |
| Dashboard                 |         ✅   |       ❌    |        
| Debug chatbot             |         ✅   |       ❌    |
| FAQ:First message to user |         ✅   |       ❌    |
| FAQ:Last message to user  |         ✅   |       ❌    |
| FAQ:Multi bot replies     |         ✅   |       ❌    |
| Image bot reply           |         ✅   |       ❌    |
| Release                   |         ✅   |       ❌    |
| User Feedback             |         ✅   |       ❌    |

--->

| 特点         | Prompt Dialog| Run in Rasa |
|-------------|---------------|------------|
| 聊天记录     |       ✅      |     ❌     |
| 仪表板       |       ✅      |     ❌     |
| 调试聊天机器人|       ✅      |     ❌     |
| 多个机器回复  |       ✅      |     ❌     |
| 发布         |       ✅      |     ❌     |
| 用户反馈     |       ✅      |     ❌     |


### 下载Rasa文件

单击右上角的“下载 RASA 文件”。 将弹出下载框，其中包含以下选项：

* 下载当前模块，下载当前对话框流程，
* 下载选定的模块，选择当前项目下多个对话流的集合，
* 下载全部，查看当前工程下的所有对话框流程图。

![download-rasa](/assets/images/download_rasa_file_current.png)

- 如果当前项目有包含错误节点的流程图时，会在弹出框中将其分类为“不可用模块”，将鼠标移到模块上可查看错误消息的数量。 模块名称旁边的链接可以指向相应的流程图进行修改。

![download_rasa_file_selected.png](/assets/images/download_rasa_file_selected.png)  

### 准备Rasa环境

本地安装需要你本地的python版本3.8以上（推荐3.8.10）并且需要通过pip安装以下依赖包

```text
rasa==3.2.0
jieba==0.42.1
transformers==4.24.0
jsonpath==0.82
```

安装完成后在命令行输入‘rasa init’进行验证如图。

![rasa-env](/assets/images/dev_guide/download-rasa-env.png)

### 运行RASA
步骤 1：在 Rasa 环境中解压下载的 Rasa 文件：

![download-rasa-debug-1](/assets/images/dev_guide/download-rasa-debug-1.jpg)

第 2 步：训练模型。
```shell

# 训练模型
rasa train

# 必要时启动操作[如果包含Webhook或自定义的Action代码]
rasa run actions

# 打开另一个命令窗口来运行机器人
rasa shell
```

步骤3：观察输出并验证，如图所示。   
![download-rasa-debug-2](/assets/images/dev_guide/download-rasa-debug-2.jpg)
