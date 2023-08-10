---
layout: en
title: 项目发布
nav_order: 2
parent: 发布
grand_parent: 使用指南
---

## 选择模块发布
单击左侧导航栏的项目工具，单击发布，选择要发布的模块，然后单击发布按钮。 

- 如果发布后有更新，需要再次点击发布才能使更新生效。

![release_not_release.jpg](/assets/images/tutorial/release_not_release.jpg)

## 发布
如图，当前选中需要发布的模块后，发布按钮左侧会出现图标提示任务状态，并且发布按钮的文字会变为正在发布。 此时用户可以跳转到其他页面进行操作，或者停留在这里等待训练完成，
或者点击“停止”停止发布。

![release_releasing.jpg](/assets/images/tutorial/release_releasing.jpg)

## 发布完成

如图所示，发布完成后旁边的图标会发生变化，将鼠标放在该图标上会提示发布完成。

![release_completed.jpg](/assets/images/tutorial/release_completed.jpg)

## 测试
如图所示，在机器人对话窗口中输入聊天信息，验证机器人是否按预期回复。

![release_test.jpg](/assets/images/tutorial/release_test.jpg)

## 在您的应用程序中发布
发布的项目可以通过二维码部署并嵌入任意网页

要求：
  - 互联网支持
  - 允许访问：https://app.promptai.cn 端口：443
  - 现代浏览器：例如最新版本的Chrome

### 二维码 [移动端]
当您需要访问移动端时，可以通过访问移动端链接或扫描二维码进行体验。
![release_qrcode.jpg](/assets/images/tutorial/release_qrcode.jpg)

* 将二维码嵌入网站，用户通过手机浏览器扫描或微信扫描即可体验已发布的项目

![release_mobile_demo.jpg](/assets/images/tutorial/release_mobile_demo.jpg)

### Web 页面
1. 如图，这里我们准备了一个项目，并在项目中发布
   ![release_web_script.jpg](/assets/images/tutorial/release_web_script.jpg)

    - 将“Web(javascript)”粘贴到您的 html 中
    ```html
        '<!DOCTYPE html>
        <html lang="en">
        <head>
          <meta charset="UTF-8">
          <meta http-equiv="X-UA-Compatible" content="IE=edge">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <title>Document</title>
          <style>
            * {
              margin: 0;
              padding: 0;
              box-sizing: border-box;
            }
            body {
              background-color: linen;
            }
            main {
              display: flex;
              justify-content: center;
              align-items: center;
              height: 100vh;
            }
          </style>
        </head>
        <body>
          <main>
            <h1>Your App...</h1>
          </main>
          {Your script is here.}      
        </body>
        </html>  '  
    ```

2. 当我们打开网站时，我们可以看到网站的右下角多了一些聊天框。 单击“打开”启动智能会话。 至此，我们的j机器人发布成功。
   ![release_web_script_demo_1.jpg](/assets/images/tutorial/release_web_script_demo_1.jpg)
