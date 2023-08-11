---
layout: en
title: 同义词
parent: 使用指南
nav_order: 19
spliter: true
---
一些实体具有同义词，可用于训练数据以改进意图分类和实体识别。

- 用户变量提取，系统提取的变量将被转换成标准词

```text
Bot : 你好，我可以帮你查询天气。可以试着对我说："成都天气怎么样？"

User: 蓉城天气怎么样？

Bot : 成都市的当前气温为31摄氏度。
```

在这个例子中，在给'成都'添加'蓉城'的同义词，在提取变量时会自动转换成标准词'成都'。

## 新增
在左侧导航栏中选择`项目视图`-`同义词`，点击右上角的`添加`按钮添加同义词。
![synonyms_overview.jpg](/assets/images/tutorial/synonyms_overview.jpg)

## 使用
在这里，我们将`pineapple`的同义词添加到训练示例中。

![synonyms_use.jpg](/assets/images/tutorial/synonyms_use.jpg)