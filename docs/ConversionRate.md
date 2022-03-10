#### 回填接口文档 V1

🎈注：回填率数据分析目前仅针对验证码业务 

1. **消息应用场景：** 

![消息应用场景](../RES/CR.jpg)

2. ##### 生产基地址 

 http://id-vivo-cooper.tig253.com/ 

3. ##### **回填明细接口** 

**接口路径：** [/v1/otp/writeTrans](/v1/otp/writeTrans) 

**接口备注：** 接口需要添加ip白名单 

**请求方法：** POST  

**content-type：** applicition/json 

**频率限制：1**万次/分，60万次/小时 

**应用场景：** 用户收到验证码短信，并且使用了验证码，实时回传这个短信相关信息。

**参数说明如下:** 

|属性名称|字段类型|是否可空|字段描述|
|:---|:---|:---|:---|
|phone|String|不可空|手机号|
|time|long|不可空|验证码回填时间戳（单位秒）|
|messageId|String|不可空|创蓝返回的messageId|
|account|String|不可空|api账号|
|countryNum|String|不可空|国家码(如86)|

 

###### **请求示例：**

```JSON
{
    "phone": "8611111111111",
    "time": 1634006690,
    "messageId": "141615506720432128",
    "account": "xxx",
    "countryNum": "86"
}
```

###### **返回示例：**

```json
{
    "code": 0,//0:成功，非0：失败
    "msg": "成功"
}
```

4. ##### **回填成功率接口** 

**接口路径：** [/sms/success/rate](/sms/success/rate)

**接口备注：** 接口需要添加ip白名单 

**请求方法：** POST 

**content-type：** applicition/json 

**频率限制：60** 次/分，3600次/小时 

**应用场景：** 在固定的时间间隔（如每5分钟，0，5，10，15，20...50，55），汇总时间范围内发送的验证码总量，汇总时间范围内已使用的验证码总量，计算回填百分比（已使用验证的验证码总量/验证码总量）。

**参数说明如下:**

|属性名称|字段类型|是否可空|字段描述|
|:---|:---|:---|:---|
|account|String|不可空|api账号|
|startTime|long|不可空|开始时间戳（单位秒）|
|endTime|long|不可空|结束时间戳（单位秒）|
|successRate|array[object]|不可空|回填率列表|
|	countryNum|String|不可空|国家码|
|	rate|String|不可空|回填率|


###### **请求示例：**

```JSON
{
    "account": "xxxx",
    "startTime": 1634004000,
    "endTime": 1634007599,
    "successRate": [
        {
            "countryNum": "86",
            "rate": "99.0"
        },
        {
            "countryNum": "66",
            "rate": "70.0"
        }
    ]
}
```

###### **返回示例：**

```json
{
    "code": 0,//0:成功，非0：失败
    "msg": "成功"
}
```

