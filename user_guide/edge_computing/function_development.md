# 函数功能开发及示例

函数计算的开发目前仅支持Python3。函数计算基于消息触发模型完成消息的收发及业务处理。

## 函数开发

### 函数计算示例

本例完成当收到消息触发函数计算时，将收到的json数据包中的摄氏温度转换成华氏温度。

```python
"""
设备上云数据筛选示例
1. 子设备往函数计算发送一个 json 消息，格式如下
{
    "id": 123456,
    "celsius": 120
}
表示 id 为 123456，温度为 120 摄氏度
2. 函数计算根据条件筛选数据，实例中的筛选条件为
celsius > 100
3. 将摄氏度转换为华氏度
celsius -> fahrenheit
4. 注意，消息流转需要配置相应的消息路由
"""


import function_sdk
import json
import logging
# import requests # 用于http访问外部请求


# 如果要使用 publish，需要先调用 EdgeClient 构造函数，初始化一个 client
cli = function_sdk.EdgeClient()
cli.logger.info("function config: {}".format(cli.config)) # cli.config 用于获取函数的配置信息

def handler(event, context):
    try:
        # 记录当前函数调用的次数
        cli.redis_client.incr("count")
        # 日志输出，可通过本地webprotal进行查看
        cli.logger.info("function called {} times".format(cli.redis_client.get("count").decode()))

        # 获取消息 topic
        local_topic = event["topic"]
        # payload 为 bytes 类型，需解码为字符串
        msg = json.loads(event["payload"].decode('utf-8'))

        if msg["celsius"] > 100:
            # cloud_topic 可从 local_topic 经过自定义的转换得到
            cloud_topic = local_topic + "/to_cloud"
            # 转换为华氏温标
            msg["fahrenheit"] = msg["celsius"] * 1.8 + 32
            payload = json.dumps(msg).encode('utf-8')
            # 向指定 topic 发送消息
            cli.publish(cloud_topic, payload)

    except Exception:
        logging.exception(context)
```



### 函数计算组成

函数计算需要用户完成两件事情，1. 收到消息，回调函数handler；2. 发送消息，publish；

#### 消息触发回调接口

基于函数计算的框架，用户只需实现`handler(event, context)`接口，当函数计算被消息路由命中时，handler接口会被调用，执行业务逻辑。

1. 函数接口名必须为`handler`；
2. 函数参数：
   - event：触发函数的事件，类型为 dict

|字段|类型|描述|
|-|-|-|
|type|String|事件类型：消息路由触发为 "mqtt"，定时运行为“timer”|
| topic   | String  | 消息topic（定时运行无需此字段）                                         |
| source  | String  | 消息来源：和消息路由一致。分为"本地路由", "IoT Core云平台" 和 "函数计算" 三种（定时运行无需此字段） |
| payload | b:bytes | 消息体（定时运行无需此字段）                                            |

【示例】消息路由触发

```json
{
    'type': 'mqtt',
    'source': 'local',
    'topic': '/test/topic1',
    'payload': b'{"id":1, "celsius":150}'
}
```

【示例】定时运行

```json
{
    'type': 'tmier'
}
```



   - context：函数上下文，类型为dict

| 字段             | 类型   | 描述           |
| ---------------- | ------ | -------------- |
| timestamp        | int    | 函数调用时间戳 |
| functionInvokeID | String | 函数调用ID     |
| functionName     | String | 函数名         |

【示例】

```json
{
    'timestamp': 1587886520,  //Unix时间戳
    'functionName': 'test1',
    'functionInvokeID': 'ac6cbf30-d9e7-4d50-8882-5b4648f6cfde'
}
```





#### 发送消息

发送消息只需构造一个`function_sdk.EdgeClient的对象，通过该对象的`publish`方法发送消息。

```python
cli = function_sdk.EdgeClient()
cli.publish(topic, payload)
```



### 其他功能说明

#### Redis访问
```python
cli = function_sdk.EdgeClient()
cli.redis_client # 获取redis client
```
#### Http访问
```python
import requests # 用于http访问外部请求 
```
具体使用方法请参考[使用方法](https://requests.readthedocs.io/en/master)

#### 获取函数配置
```python
cli = function_sdk.EdgeClient()
cli.config # 用于获取函数的配置信息
```

**配置说明**
函数配置可通过【函数配置】功能以json格式录入配置信息。【函数配置】功能位于网关已分配函数列表中的操作
1、在【已分配函数列表】找到需要配置的函数，点击【函数配置】
![修改函数](../../images/分配函数-5.png)
2、在函数配置功能中进行函数配置
![修改函数](../../images/分配函数-6.png)

#### 定时运行

函数计算支持定时运行功能，在函数配置中开启后，使用corn表达式进行时间表述。


#### 消息转发

函数计算消息转发需要通过[添加消息路由](/uiot-edge/user_guide/message_route/add_msg_route)来实现。函数计算将发送的消息流转到[消息路由](/uiot-edge/user_guide/message_route/overview)，消息路由根据配置的路由规则发送给指定目的地，比如，另一个函数计算、本地设备、物联网云平台。


