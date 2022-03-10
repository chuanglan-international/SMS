## 4 上行推送

### 4.1 协议说明

|名称|说明|
|:---|:---|
|协议|HTTP GET|
|编码格式|UTF8|
|Content-Type|application/x-www-form-urlencoded|
|pushUrl|此地址客户提供，提供给运营绑定，一个账号一个地址|

### 4.2 回调示例

 http://pushMoUrl?receiver=admin&pswd=12345&moTime=1208212205&mobile=13800210021&msg=hello&destcode=CHUANGLAN
 
 参数说明如下：

|参数|说明|
|:---|:---|
|`receiver`：|接收上行验证的用户名（不是账户名），是按照用户要求配置的名称，默认为空<br/>|
|`pswd`：|接收上行验证的密码，默认为空<br/>|
|`moTime`：|上行时间<br/>|
|`mobile`：|上行手机号码<br/>|
|`msg`：|上行短信内容<br/>|
|`destcode`：|用户上行的目的号码<br/>|



注：
1.成功接收请响应字符串:OK

