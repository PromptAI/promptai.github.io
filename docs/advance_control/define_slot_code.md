---
layout: en
title: 动态插槽
parent: 更多功能
nav_order: 1
---
<!-- 如果您想实现定义Form中Slot的多样性,我们强烈推荐您使用`Form Define Slot Code`该功能! -->
<!-- 该功能可以最大可能的定义您Form中那些Slot,比如:-->
<!-- 根据用户输入`age_slot_name`的值,是否等于18的数据来条件获取的相应Slot定义 -->
 
如果一组固定的槽位无法满足您对表单的需求，我们强烈建议使用`所需槽位`功能，该功能允许根据用户在表单中的输入动态更改表单中所需的槽位。 这是一个例子。
```text
用户：我想预订一家中餐厅。
机器人：你想坐在外面吗？
用户：是/否
机器人：你想坐在阴凉处还是阳光下？ / 请提供额外的偏好
```
这是用户和餐厅预订助理之间的对话。 助手要求用户填写`seat`槽位。 如果用户回答`是`，机器人需要询问详细信息。 但是，如果用户回答`否`，机器人将不会收集座位偏好槽。 我们可以通过下面的代码来实现这个对话。


```python
class ValidateRestaurantForm(FormValidationAction):
    def name(self) -> Text:
        return "validate_restaurant_form"

    async def required_slots(
        self,
        domain_slots: List[Text],
        dispatcher: "CollectingDispatcher",
        tracker: "Tracker",
        domain: "DomainDict",
    ) -> List[Text]:
        additional_slots = ["outdoor_seating"]
        if tracker.slots.get("outdoor_seating") is True:
            # 如果用户想坐在外面，请询问
            # 如果他们想坐在阴凉处或阳光下。
            additional_slots.append("shade_or_sun")

        return additional_slots + domain_slots
```
`required_slots` 函数返回表单需要收集的槽列表。 在聊天机器人请求填充任何槽位之前，rasa 将执行`required_slots`函数来确定应收集哪些槽位。 因此，我们可以使用 tracker.get_slot 函数来获取之前填充的槽位，然后返回需要收集的槽位。 请注意，如果您不需要动态更改所需的插槽，则无需触及此功能。 PromptDialog会根据表单图自动生成所需的槽位。

当您单击 `Slots` 节点，然后选择编辑节点时，该功能可用。 它将显示在右侧面板上。
