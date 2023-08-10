---
layout: en
title: 自定义 Action
parent: 使用指南
nav_order: 9
---

在机器人响应面板中，设计者可以单击`+Action`添加用Python编写的Action函数，这将为设计者提供插入具有更复杂逻辑的Python代码的工具。 Action python 代码将被放置到 `Actions.py` 文件在 Rasa 中，当机器人给出当前响应时将被触发。

![action-02](/assets/images/tutorial/action/action-02.png)

在弹出的窗口中，设计者可以编写Action函数的Python代码。

![action-01](/assets/images/tutorial/action/action-01.png)


## Rasa 会话
现在让我们看一个示例，展示如何将操作代码添加到 Rasa 文件中： 

- actions/Actions.py
- domain.yml

### Actions.py

Action 在这里被解释[Rasa Action](https://rasa.com/docs/rasa/action-server/sdk-actions/). 这是 Rasa 提供的一种通过自定义 Python 代码控制对话的方法。 它有一个固定的结构，`name`方法声明这个动作类，`run`方法将在会话期间执行。 我们隐藏了`class`和`name`的编辑，只暴露了`run`函数的实现，也就是Action函数。 这是动作函数的一个例子。

```text
Chatbot: 我可以计算你的BMI。 你能告诉我你的身高吗？
User: 当然。 我身高165厘米。                                               [intent: intent_height, {"height": "165"}]
Chatbot: 好的。你的体重是？
User: 60kg.                                                    [intent: intent_weight, {"weight": "60"}]
Chatbot: {action: calculate_BMI}
```
为了完成对话，我们可以使用Action Function来进行计算。

```python

class BotCustomaction_cp_ce1atgfk53b4_0(Action):
    def name(self) -> Text:
        return "action_cp_ce1atgfk53b4_0"
    async def run(self,
                dispatcher,
                tracker: Tracker,
                domain: Dict[Text, Any],) -> List[Dict[Text, Any]]:
        height = float(tracker.get_slot("height"))
        weight = float(tracker.get_slot("weight"))
        bmi = height / (weight * weight)
        dispatcher.utter_message(text="你的BMI是: " + bmi)
        return []
```

上面代码中的类名/方法名：
- 第一行: `class BotCustomaction_uniqueid_index(Action)` 这是类名。 这是系统生成的唯一ID。
- 第二行: `def name(self) -> Text` 返回此操作的名称。 该字符串将在“domain.yml”中声明。 也是系统生成的。
- 第四行: `async def run()` 由开发者编辑。

#### `run` 函数中的参数
这是对“run”函数中一些有用参数的介绍。
在`run`方法中，您可以使用以下命令访问所有聊天机器人信息. [dispatcher](https://rasa.com/docs/rasa/action-server/sdk-dispatcher/) 和 [tracker](https://rasa.com/docs/rasa/action-server/sdk-tracker) 参数.
- dispatcher : 输出对象。 `dispatcher.utter_message()` 方法可用于传递机器人响应。
  ```python
  class BotCustomaction_test_dispatcher(Action):
      def name(self) -> Text:
          return "action_test_dispatcher"
      async def run(self,
                  dispatcher,
                  tracker: Tracker,
                  domain: Dict[Text, Any],) -> List[Dict[Text, Any]]:
          dispatcher.utter_message(text="文本响应")
          dispatcher.utter_message(text="第二个响应")
          return []
  ```
  在会话中:
  ```text
  Chatbot: 文本响应
  Chatbot: 第二个响应
  ```
- tracker：当前用户的跟踪器。 通过使用`tracker.get_slot(slot_name)`获取slot值（即变量对应的值），最新的用户消息`tracker.latest_message`。
    ```python
      class BotCustomaction_test_tracker(Action):
          def name(self) -> Text:
              return "action_test_tracker"
          async def run(self,
                      dispatcher,
                      tracker: Tracker,
                      domain: Dict[Text, Any],) -> List[Dict[Text, Any]]:
              query = tracker.latest_message["text"]
              height = tracker.get_slot("height")
              dispatcher.utter_message(text="你的查询是: " + query)
              dispatcher.utter_message(text="height插槽的值是: " + height)
              return []
    ```
    In the conversation:
    ```text
    user: 我170cm.
    Chatbot: 你的查询: 我170cm.
    Chatbot: height插槽的值是: 170
    ```


<!--
感觉似乎不用说这个？
### stories.yml
action属于一种特殊的bot response，因此也会加入到story中，成为训练数据。
```yaml
version: '3.2'
stories:
- story: story_0
  steps:
  - intent: init
  - action: utter_project_welcome
  - intent: intent_height
  - action: utter_ask_weight
  - intent: intent_weight
  - action: action_cp_ce1atgfk53b4_0
```

`steps` in `story_0`  indicates that when a user tells the height and weight, the bot will call `action_cp_ce1atgfk53b4_0` to give the result. 
-->
### domain.yml
```yaml
version: '3.2'
actions:
  - action_cp_ce1atgfk53b4_0
  - other_action
```
每个操作都有一个唯一的 ID，例如`action_cp_ce1atgfk53b4_0`，它将在`domain.yml`中声明。 只有已声明的动作才能正确执行。
