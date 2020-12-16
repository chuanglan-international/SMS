## 8 拉取状态报告

### 1.1 协议说明

|名称|说明|
|:--|:--|
|协议|HTTP POST|
|编码格式|UTF8|
|Content-Type|application/json|
|URL|http://intapi.253.com/pull/report|

### 1.2 请求包体

& 包体为json字符串，参数如下：

```
 { 
     "account" : "I6000001", //API账号，50位以内。必填
     "password" : "12345678", //API账号对应密钥，联系客服获取。必填
     "count" : "30", //拉取个数（最大100，默认20），选填
 }
 ```
 
 ### 1.3 应答包体
 
 & 该响应为提交响应，发送到手机是否成功请获取状态报告确认
 
 ```
  {
  "code": 0,
  "error": "",
  "result": [
    {
      "batchSeq": "I2170326_1808142031_0000000",
      "mobile": "8618037170702",
      "msgid": "18081420311005732392",
      "reportTime": "1808142031",
      "notifyTime": "180814203101",
      "status": "DELIVRD"
    },
    {
      "batchSeq": "I2170326_1808150928_5748789",
      "mobile": "8618037170702",
      "msgid": "18081509281005782276",
      "reportTime": "1808150928",
       "notifyTime": "180814203101",
      "status": "DELIVRD"
    }
  ]
}
```


