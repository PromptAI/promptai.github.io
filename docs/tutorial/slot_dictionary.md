---
layout: en
title: 字典
parent: 使用指南
nav_order: 18
---
当我们在进行实体识别来填充槽位时，有时可以预先定义实体的名称。 在这种情况下，字典可以促进实体识别。

## 新增一个字典
这里我们向槽`State Name`添加一个字典。 美国各州词典可以这样描述：

```text
Alabama
Alaska
Arizona
Arkansas
California
Colorado
Connecticut
Delaware
Florida
Georgia
...
```
点击`State Name`后面的`Upload`按钮，上传词典。

![slot_upload_dictionary.jpg](/assets/images/tutorial/slot_upload_dictionary.jpg)

上传成功后，您可以点击`详情`查看哪些词典已上传成功，也可以`下载`查看词典。

![slot_upload_dictionary_success.jpg](/assets/images/tutorial/slot_upload_dictionary_success.jpg)

## 一个例子
假设我们创建一个对话流程图“你来自哪里？”。

1. 添加用户节点如下：
   
   ![dict-04](/assets/images/tutorial/dict_user.png)
   
   `注意`: 为了提高词典的识别准确率，这里至少需要标注两个例子。
2. 当用户提及状态名称并成功提取时，机器人可以回复如下：
   
   ![dict-05](/assets/images/tutorial/dict_bot.png)


