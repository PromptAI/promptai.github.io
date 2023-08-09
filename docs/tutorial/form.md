---
layout: en
title: Form
parent: 使用指南
nav_order: 7
---
在PromptDialog中，Form是一个从用户收集一组信息的组件。 该信息将存储在槽中。 在下面的示例中，机器人向用户收集水果类型和数量信息，并在完成后与用户确认。 该信息收集对话可以通过具有两个必需槽的表单来实现：水果类型和数量。

```text
Bot : 你好!
      我能为你做什么?
User: 我想买一些水果。

# 通过表单收集用户订购的水果种类和数量
Bot : 好的，你想购买什么水果呢?
User: 我要一些苹果。
Bot : 需要多少水果呢?
User: 需要5个苹果

Bot : 好的，你需要5个苹果。
User: 谢谢
Bot : 不客气！ 我会为您准备 5 个苹果!
```
表单还可以处理其他类似的场景：
- 查看天气：收集地点和时间，实时查看天气情况。
- 预订机票：通过获取用户的出行时间和出发机场来预订机票。
- ...


## 如何使用表单?
接下来，我们将介绍如何创建上面提到的用户订购水果的示例。
### 创建一个“水果”的流程
![img.png](/assets/images/form_fruit_create_flow.jpg)

接下来，我们创建一个“智能回复”节点来打招呼，并创建一个“用户输入”节点来显示购买水果的意图
![img_1.png](/assets/images/form_fruit_create_hello.jpg)

## 创建一个表单
单击`用户`节点并在弹出菜单中选择`表单`
![img_3.png](/assets/images/form_fruit_create_form.jpg)
表单的名称可以根据功能来设置，这里我们填写`水果订单`
![img_2.png](/assets/images/form_fruit_create_form_info.jpg)

创建`水果订单`后需要填写三项信息
![img_4.png](/assets/images/form_fruit_create_form_success.jpg)

|  名称        |  是否必填 | 描述                                                   |
|--------------|----------|--------------------------------------------------------|
| Slots        |    是   | 需要收集的插槽                        |
| Interrupts   |    否    | 填写表格或退出表格时可能出现的问题 |
| Confirm      |    是   | 表单收集成功后                       |
  
## Slots
我们需要通过Slots收集用户的`水果类型`和`数量`，然后详细说明如何添加`水果类型`

单击`Slots`节点，然后从弹出菜单中选择`Add Slot`
![img_5.png](/assets/images/form_fruit_create_slot.jpg)

在弹出的Slot窗口中，我们需要注意输入`Slot Name`，这里填写Slot的名称`水果类型`（输入名称后按回车即可创建）
![img_6.png](/assets/images/form_fruit_create_slot_info.jpg)

蓝色部分是保存Slot后自动创建的：

- "水果类型" : 插槽名字
- "-"          : `反问` 节点用于输出一句话提示用户输入信息。
![img_8.png](/assets/images/form_fruit_create_slot_success.jpg)
双击`反问`节点并填写 "您想订购什么种类的水果？" 询问用户想要购买什么类型的水果。
![img_11.png](/assets/images/form_fruit_create_rhe_info.jpg)

在`反问`节点之后，我们需要添加一个用户输入来获取用户需要的水果类型，这时候我们需要标记出想要的水果类型。
![img_9.png](/assets/images/form_fruit_rhe_after_fruitType.jpg)
![img_10.png](/assets/images/form_fruit_rhe_after_fruitType_info.jpg)

到目前为止，`水果类型`槽已创建。

![img_12.png](/assets/images/form_fruit_rhe_after_fruitType_success.jpg)
添加`数量`插槽，如下所示:
![img_13.png](/assets/images/form_fruit_rhe_after_count.jpg)

## Interrupts
在订购过程中，用户可能会提出一些问题或退出对话
- 苹果有甜味吗？ （回答完问题后，返回From）
- 事实上，我改变了主意。 今天不买水果了 （退出，停止订单）
    
### 苹果甜吗？
![img_14.png](/assets/images/form_fruit_interrupt_1.jpg)

### 跳出表单
Interrupt中添加用户退出的用户输入，并使用`break`节点退出表单
![img_15.png](/assets/images/form_fruit_interrupt_2.jpg)

## Confirm
`Confirm`节点处理集合表单的完成，这里我们向用户确认订单
![img_16.png](/assets/images/form_fruit_confirm.jpg)

## 完整流程图如下
![img_17.png](/assets/images/form_fruit_overview_1.jpg)
![img_18.png](/assets/images/form_fruit_overview_2.jpg)
![img_19.png](/assets/images/form_fruit_overview_3.jpg)

---

# FAQ

## 我可以用一句话填补多个插槽吗？
是的，我们支持在一句话中填充多个槽位。
例子: 
```text
Bot : 你好!
      我能为你做什么?
User: 我想卖一水果。

Bot : 你想买什么水果?
# 数量 和 水果类型 都在这句话中。
User: 我要5斤苹果。

Bot : 好的，我知道了
User: 谢谢
Bot : 谢谢你的光临，我正在为你准备5斤苹果，还有其它需要的嘛!
```

在表单中的`Slots`节点中标记多个插槽
![form-21](/assets/images/form_fruit_required_slots.jpg)
