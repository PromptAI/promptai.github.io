---
layout: en
title: Webhook 的概念
parent: Webhook
nav_order: 1
---
下面是一个查询天气的例子，供大家参考。
```text
用户：嗨，你能告诉我纽约的天气吗？
聊天机器人：当然！ 让我为您检查一下当前的天气状况。 请稍等片刻。
# 它需要触发一个与第三方天气服务器通信的 webhook，以查询“纽约”的天气。

# 一旦收到查询结果，就可以将其打包在响应中并发送给用户。
聊天机器人：纽约当前天气为 82°F (28°C)，大部分时间晴朗。 风速为 5 英里/小时（8 公里/小时），湿度约为 60%。 您还有什么想知道的吗？
用户：谢谢您的预测！ 这很有帮助。
```
---
调用 Webhook 有两个步骤。

### 步骤 1.
单击`项目视图`-`Webhooks`。 单击右上角的`+ 添加`。 创建一个 webhook 来调用天气 API（稍后详细介绍）。

![webhook_weather_setting.jpg](/assets/images/webhook_weather_setting.jpg)

### 步骤 2. 
创建一个用于查询天气的流，并在机器人回复节点中选择一个 Webhook。

![webhook_weather_use.jpg](/assets/images/webhook_weather_use.jpg)

以下是步骤1的详细设置说明。
### Basic Settings
- 名称：引用新 webhook 的名称。
- URL：这里的url与http url含义相同。 此处填写时请注意`http/https`协议。 是第三方服务向您提供的访问链接。 另外，URL地址还支持变量值的传输。 当调用webhook时，相应的变量占位符将被替换为其相应的值。 如图所示，如果我们在流程图中定义了一个槽`city`，我们可以使用`{city}`将值发送给第三方服务提供商。
   ```
   app.promptai.us/rpc/gaode/weather?key=c4f69dbbd66cfc7f4e49310fea69dff1&city={city}
   ```
  
### 请求设置
- 请求方法：表示http请求方法，支持以下几种。
   * get
   * post
   * put
   * delete

- 请求头：表示http请求头，当外部接口需要特定的请求头时可以在这里添加。
   * 无: -
   * 自定义: 键值对

- 请求体: 支持四种方式. 

| 类型 | Content-Type                      | 格式化            | 备注                      |
|------|-----------------------------------|-------------------|:-----------------------------|
| 无 | -                                 | -                 | -                            |
| Form | application/x-www-form-urlencoded | 键值对 | 文件暂时不支持            |
| JSON | application/json                  | json string       |                              |
| Text | text/plain                        | text string       |                              |


 * 注意：与 URL 相同，我们也支持在请求正文中使用槽值，例如`{city}`。

### 响应设置
这些设置处理从第三方 API 调用收到的结果，并将其打包为对用户的响应。 如果结果确实出现，我们可以采取以下操作之一。

| 名称                    |  处理过程                                                          | 需要响应的格式 |
|-------------------------|----------------------------------------------------------------------|---------------------------|
| 无响应             | 忽略返回结果并且不输出消息                        | -                         |
| 原始响应       | 不处理响应，展示原始输出                               | -                         |
| 自定义响应     | 通过JsonPath从结果中提取字段，并将其打包到自定义响应中   | json         |

由于多种因素的影响，有时API调用会失败。 当 webhook 请求失败时，我们需要向用户发送提示。 请注意，这种情况与 API 调用返回的空结果不同。 在`调用失败或未收到任何结果返回消息`处设置一条短信。

![webhook6.png](/assets/images/webhook_weather_response_setting.jpg)

以天气查询为例。 假设有一个气象服务响应：
```json
{
  "temperature": "82°F (28°C)",
  "conditions": "Mostly sunny",
  "wind": "5 mph (8 km/h)",
  "humidity": "60%"
}
```
我们可以生成四种类型的响应：
```text
// - 忽略状态码【机器人会回复你设置的内容】
// 由于某种原因，天气服务没有响应，我们设置文本：
// `调用成功返回消息`处的“服务不可用，请稍后再试”
用户：嗨，你能告诉我纽约的天气吗？
机器人聊天 : 服务不可用，请稍后重试

// - 忽略Bot不会回复任何消息】
用户：嗨，你能告诉我纽约的天气吗？

// - 原始响应【机器人将回复任何api返回的内容】
用户：嗨，你能告诉我纽约的天气吗？
机器人聊天：{“温度”：“82°F (28°C)”，“条件”：“大部分晴天”，“风”：“5 英里/小时（8 公里/小时）”，“湿度”：“60%” }

// - 用户自定义响应【机器人将使用从响应中提取的值来回复您设置的内容】
// 例如我们可以设置文本：
// 当然！ 我可以为您提供纽约的天气信息。 这是纽约当前的天气预报：温度：{温度}、风：{风}、条件：{条件}和湿度：{湿度}
// 在`如果调用成功完成则返回消息`

用户：嗨，你能告诉我纽约的天气吗？
机器人聊天：当然！ 我可以为您提供纽约的天气信息。
       这是纽约当前的天气预报：温度：82°F (28°C) 、风：5 英里/小时（8 公里/小时）、条件：大部分晴天和湿度：60%
```

### 将值插入 Rasa 中的槽
上述过程需要一个步骤来从 API 调用中提取值并将其填充到槽中。 假设我们有气象服务 API 发送的以下结果。 

```json
{
  "temperature": "82°F (28°C)",
  "conditions": "大部分晴天",
  "wind": "5 mph (8 km/h)",
  "humidity": "60%",
  "city": "纽约"
}
```
我们将执行以下 JsonPath 引用并将值映射到 Rasa 中的槽。

![52-webhook](/assets/images/webhook_weather_response_overview.jpg)


<!---

Chat
```text
User: Hi, can you please tell me the weather in New York?
Bot : The current temperature in New York is 82°F (28°C)
```
--->

---

## 常见问题
Q1：在 API 调用中引用槽位时，如果槽位不存在或者槽位拼写错误，会发生什么情况？
   
以下面网址为例：`http://localhost/api?area={area}&date={date}`
- 如果area=New York，调用成功时，实际请求的url：
  `http://localhost/api?area=New York`
- 如果slot不存在或者拼写错误，将无法正确调用，实际请求的url可能是： `http://localhost/api?area={area}&date={date}`

Q2：`响应设置`中提取的变量是否可以与对话流中存在的槽同名
他们的名字可以相同。 这些槽将填充提取的值。

Q3：多次调用同一个webhook时，提取的slot值如何变化？
   
提取的槽位将是上次调用 webhook 后提取的值，即槽位的值可以更改。

Q4：webhook 值提取生成的槽可以用于流程设计的其他部分吗？

如果您想使用这些槽位，请提前在项目中定义它们。

更多例子 [click here](/docs/webhook/02-webhook/).
