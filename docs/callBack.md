
## 3 回调状态

### 3.1 协议说明

|名称|说明|
|:---|:---|
|协议|HTTP GET|
|编码格式|UTF8|
|Content-Type|application/x-www-form-urlencoded|
|pushUrl|此地址客户提供，提供给运营绑定，一个账号一个地址|

### 3.2 回调示例


http://pushUrl?receiver=admin&pswd=12345&msgid=12345&reportTime=1012241002&mobile=13900210021&status=DELIVRD¬ifyTime=180828114243&batchSeq=I0123456_1808281142_2188000


参数说明如下：
```
`receiver`：接收状态报告验证的用户名（不是账户名），是按照用户要求配置的名称，默认为空<br/>
`pswd`：接收状态报告验证的密码，默认为空<br/>
`msgid`：提交短信时平台返回的msgid<br/>
`reportTime`：网关平台返回的时间,网关不同，格式有偏差，以具体返回格式为准.<br/>
`notifyTime`：接口服务器返回的时间，格式YYMMDDhhmmss，其中YY=年份的最后两位（00-99），MM=月份（01-12），DD=日（01-31），hh=小时（00-23）<br/>，mm=分钟（00-59）,ss=秒（00-59）。<br/>
`mobile`：提交短信时的手机号码<br/>
`status`：状态报告状态码<br/>
`betchSeq`：短信批次号。<br/>
```


```
注：
1.成功接收请响应字符串:OK
2.status 为状态报告状态码，可参照状态报告状态码对比
```
