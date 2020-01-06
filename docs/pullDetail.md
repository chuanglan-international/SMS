## 7 拉取上行短信明细

### 1.1 协议说明

|名称|说明|
|:--|:--|
|协议|HTTP POST|
|编码格式|UTF8|
|Content-Type|application/json|
|URL|http://intapi.253.com/pull/mo|

### 1.2 请求包体

& 包体为json字符串，参数如下：

{<br/> 
     `"account"` : "I6000001", //API账号，50位以内。必填<br/> 
     `"password"` : "12345678", //API账号对应密钥，联系客服获取。必填<br/> 
     `"count"` : "30", //拉取个数（最大100，默认20），选填<br/> 
 }<br/> 
 
 ### 1.3 应答包体
 
 & 该响应为提交响应，发送到手机是否成功请获取状态报告确认
 ```
  {
  "code": 0,
  "error": "",
  "result": [
    {
      "destcode": "10690141880",
      "moTime": "1534732783355",
      "mobile": "18037170702",
      "msg": "test message"
    },
    {
      "destcode": "10690141881",
      "moTime": "1534732787359",
      "mobile": "18037170702",
      "msg": "test message content"
    }
  ]
}
```
注：code为响应状态码，可参照提交响应状态码对比

