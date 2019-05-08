# 旁路分析 API 文档

用于判别是否为机器流量。

## **URL**

http://botsonar-api.geetest.com/api/v2/verify

## **HTTP METHOD**

POST

## **BODY TYPE**

application/x-www-form-urlencoded

## **CONTENT**

X-BOTSONAR-INFORMATION 的值

该参数直接通过 OpenResty 插件自动采集实现，并通过 headers 的方式传入到后端，X-BOTSONAR-INFORMATION ，后端业务服务器通过提取并根据 JWT 上传至云端判别。

## **请求示例**
``` python
import requests

headers = {
    "Authorization": "Bearer <jwt token>"
}
requests.post("/api/v1/bot/analyse", data="", headers=headers)
```

## **返回例子**

``` python
{
    "code": 1000,
    "message": "success",
    "detail": "",
    "data": {
        "action": 0, ## 执行动作
        "reason": "bypass", ## 原因
        "code": "0x234", ## reason的代号
        "transaction_id": "e5f5e7f88ca22f982c6924a144b777d992081ab21e67e80a57432b0c07fcd218" ## trace id
    }
}
```