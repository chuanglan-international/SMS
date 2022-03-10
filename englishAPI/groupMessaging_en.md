## 5 Bulk SMS（json）

**Brief description:**
* International bulk sms API（JSON version）

**Request URL:**
* http://intapi.253.com/send

**Request Method:**
* POST<br/>
content-type：application/json

**Parameter：**

|Parameter Name|Required|Type|Description|
|:---|:---|:---|:---|
|account|Yes|string|Account|
|password|Yes|string|Password|
|msg|Yes|string|SMS content|
|mobile|Yes|string|Mobile phone number|
|uid|No|string|Default Batch number|
|senderId|No|string|sender|
|tdFlag|No|int|Unsubscribe button|
**Request Sample**
```json
{
  "account": "I6000000", //API account，within 50 digits。required 
  "password": "12345678",//API account corresponding Key，contact the customer service to obtain your API Key. Required 
  "msg": "【253】您的验证码是：2530",//sms content。Length no more than 536 digits. Required  
  "mobile": "8613011111111,8613022222222,8613033333333",//Mobile phone number，format(country code+phone number)，e.g.：8615800000000，86 is China country code，00 should not be added as a prefix before the country code,15800000000 is real phone number for receiving the sms 。5-20 digits。Required 
  "uid": "123456",//Default batch number defined by user，within 64 digits。Optional 
  "senderId": "",//The sender displayed upon the user receives the SMS，sender id cannot be default for domestic sms, international sms supports default sender id ，but advance registration with operators are required, please contact TIG assigned account manager for more registration details . Optional 
  "tdFlag": 1 //unsubscribe flag，1  On；0or null turn off Optional
}
 ```
 

**Return Parameter Description**

|Parameter name|type|description|
|:---|:---|:---|
|code|string|return code|
|message|string|message|
|data|object|data pack|
|messageId|string|message id|
|errorPhone|array|Bulk sms wrong mobile phone number|

**Return Sample (Single text message)**<br/>
```json
 {
  "code": "0",
  "message": "成功",
  "data": {
    "messageId": "17122614541000000355"
  }
}
```
single message delivery returns a single message id
<br/>
<br/>

**Return Sample (bulk sms messaging)**<br/>
```json
{
  "code": "0",
  "message": "成功",
  "data": {
    "messageId": "I6428061_1712261459_40",
    "errorPhone": []
  }
}
```
bulk sms messaging return batchs of sms ids
<br/>
<br/>

**Return Sample ( Delivery error)**
```json
{
  "code": "123",
  "message": "短信内容不能为空",
  "data": null
}
```
**Return Code**

|code|Discription|
|:---|:---|
|0|Delivered successfully|
|101|Account does not exist|
|102|Wrong password|
|103|sms segments requested in wrong format|
|104|sms segments requested not in the range|
|105| batch sequence number is greater than 64 bits|
|106|sms content length error (>3000)|
|108|mobile phone number format wrong (>20 or <5)|
|109|the digits of mobile phone number wrong|
|110|Insufficient balance|
|112|product configured wrong|
|114|The request ip and the bind ip are inconsistent|
|115|No domestic SMS permission|
|116|Account deleted or barred|
|117|sender ID digits length over 20digits|
|119|wrong account server endpoint|
|123|sms content cannot be null|
|124|brief intro or verification code cannot be null|
|125|A specific customer mobile number cannot be used more than ten times in the same day|
|126|delivery timestamp value cannot be null for timed sms|
|126|delivery time error for timed sms|
|128|account digit length error (>50 or <=0)|
|129|Product price configured wrong|
|130|unknown abnormal|
|131|Exceed the daily sending limit|
|132|Exceed the monthly sending limit|
|133|Exceed the sending limit|
|134|Exceeding the counter-complaint limit|
|135|sms content does not match|




