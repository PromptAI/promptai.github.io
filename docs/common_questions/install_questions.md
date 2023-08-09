---
layout: en
title: 安装问题
parent: 常见问题
nav_order: 1
---
### 如何安装`本地运行环境`？
本地运行环境可以通过以下步骤安装：
- 登录系统
- 点击右上角`本地运行环境`
- 在弹出窗口中点击`管理代理`【如果没有代理，点击`+代理`按钮进行创建】
- 在弹出窗口中单击`安装代理`
- 您可以在`Install`下看到安装命令

![01-install-questions.png](/assets/images/install_agent.jpg)

### 我有多台服务器/电脑，如何安装？
如果您有多台计算机则需要创建相应数量的代理并分别安装在每台计算机上。

### 如何删除代理?
如果代理没有安装成功，可通过“管理代理”管理面板进行删除。
![02-install-questions.png](/assets/images/delete_agent.jpg)

正在使用的代理无法通过`管理代理`管理面板删除。 卸载命令需要在安装Agent的机器上执行。 执行卸载命令成功执行后`管理代理`中的代理将被删除。
- 注意：执行卸载命令时需要保持网络畅通。

### 如何升级代理？

- 登录安装了agent的机器
- 在 shell 中执行 `~/zbot/install_agent.sh upgrade`
- 输入`y`确认升级【更新期间服务将暂时不可用】
- 等待升级完成

```shell
# ~/zbot/install_agent.sh upgrade
Nvidia GPU found.
start upgrade PromptAI Agent...
This action will cause the service to be unavailable, continue (y/n)? y
latest: Pulling from promptai/zbot-agent
Digest: sha256:xxxxx
Status: Image is up to date for promptai/zbot-agent:latest
docker.io/promptai/zbot-agent:latest
xxxxx
```

### 如何在服务器中卸载代理？

- 登录安装Agent的机器
- 在shell中执行`promptai uninstall`
- 输入`y`确认卸载
- 等待卸载完成

注意：此过程需要保持网络通畅，否则将导致无法成功卸载.

```shell
# ~/zbot/install_agent.sh uninstall
start uninstall PromptAI Agent...
This action will remove PromptAI Agent, continue (y/n)? y
finish uninstall PromptAI Agent
```
