# chuanglan international

253 international SMS API for cloud communication

## Interface specification

Notes on SMS access：
1. API account and password parameters shall be provided by us
2. If you need to push the status report, please provide the callback address to bind our operation personnel (the mass delivery interface does not support status push at present).
3. Only HTTP POST request mode is supported
4. The encoding is unified using utf-8
5. The request header content-type must be set correctly according to the interface requirements, otherwise it may cause parameter passing errors
6. SMS content signature is not mandatory, some countries can be empty, please consult the operation personnel
7. The mobile phone number format is area code + real mobile phone number, for example, China area code is 86, example: 861888888888888

## 目录

 1. [Message issued](#a-messageissued)
 1. [Query balance](#a-querybalance)
 1. [State of the callback](#a-stateofthecallback)
 1. [The upward push](#a-theupwardpush)
 1. [Group messaging（json)](#a-groupmessaging)
 1. [Voice verification code](#a-voicecode)
 1. [Pull up the uplink message details](#a-pulldetails)
 1. [Pull the status report](#a-statusreport)
 1. [Status code](#a-statuscode)


<a id="a-messageissued"></a>
## 1 Message issued

### 1.1 Agreement that
name|instructions
:---|:---
agreement|HTTP POST
Coding format|UTF8
Content-Type|application/json
URL|`http://intapi.253.com/send/json`

### 1.2 Request

& The request is a json string with the following parameters：
```
 {
     "account" : "I6000000",   //API account, no more than 50 digits. mandatory
     "password" : "12345678",   //API account corresponding to the key, contact customer service to obtain. mandatory
     "msg" : "this is your message", //Text message content. Length must not exceed 536 characters
     "mobile" : "8615800000000",   //Mobile phone number, format (area code + mobile phone number), for example: 8615800000000, where 86 is China's area code，The area code does not start with 00, and 15800000000 is the real phone number to receive the SMS. 5-20. mandatory
     "senderId":""   //The sender displayed after the user receives the message is not supported in China or abroad, but needs to communicate with the operator in advance for registration. Please confirm with TIG docking personnel for details. optional
 }
 ```
 
 ### 1.3 Response
 
 & This response is the submission response, please get the status report to confirm whether it was successfully sent to the phone
``` 
  {
     "code" : "0",  //Status code
     "msgid" : "17041010383624511",  //Message id
     "error" : "",  //Status code description (empty string returned on success, return on failure, e.g., insufficient balance)
 }
 ```
 Note: code is the response status code, which can be compared with the submitted response status code
<br/>
<br/>
<br/>
<a id="a-querybalance"></a>
## 2 Query balance


### 2.1 Agreement that

|name|instructions|
|:---|:---|
|agreement|HTTP POST|
|Coding format|UTF8|
|Content-Type|application/json|
|URL|`http://intapi.253.com/balance/json`|

### 2.2 Request

& The request is a json string with the following parameters：

 {<br/> 
     `"account"` : `"I6000000"`, //API account, no more than 50 digits. mandatory<br/> 
     `"password"` : `"12345678"`, //API account corresponding to the key, contact customer service to obtain. mandatory<br/> 
 }<br/>

### 2.3 Response

& This response is the submission response, please get the status report to confirm whether it was successfully sent to the phone

 {<br/>
     `"code"` : `"0"`, //Status code<br/> 
     `"error"` : `""`, //Status code description (empty string returned successfully)<br/> 
     `"balance"` : `"7.298"`, //The remaining available balance, three decimal points<br/> 
 }<br/>
 
 Note: code is the response status code, which can be compared with the submitted response status code
<br/>
<br/>
<br/>

<a id="a-stateofthecallback"></a>
## 3 State of the callback

### 3.1 Agreement that

|name|instructions|
|:---|:---|
|agreement|HTTP GET|
|Coding format|UTF8|
|Content-Type|application/x-www-form-urlencoded|
|pushUrl|This address is provided by the customer, which is provided to the operation binding, one account and one address|

### 3.2 The callback example


`http://pushUrl?receiver=admin&pswd=12345&msgid=12345&reportTime=1012241002&mobile=13900210021&status=DELIVRD¬ifyTime=180828114243&batchSeq=I0123456_1808281142_2188000`


Parameter description is as follows：
```
receiver：The user name (not the account name) verified by the receiving status report is the name configured as required by the user and is empty by default
pswd：Receive the password verified by the status report, which defaults to null
msgid：Msgid returned by platform when SMS is submitted
reportTime：The gateway platform returns the time, the gateway is different, the format has the deviation, the specific return format shall prevail.
notifyTime：Interface server returns time in format YYMMDDhhmmss, where YY= last two digits of year (00-99), MM= month (01-12), DD= day (01-31), hh= hours (00-23) 
, MM= minutes (00-59),ss= seconds (00-59).
mobile：The mobile phone number at the time of submitting the message
status：Status report status code
batchSeq：SMS batch number。
```


```
Note:
1. Response string :OK if received successfully
2. Status is the status code of status report, which can be compared with the status code of status report
```
<br/>
<br/>
<br/>
<a id="a-theupwardpush"></a>

## 4 The upward push

### 4.1 Agreement that

|name|instructions|
|:---|:---|
|agreement|HTTP GET|
|Coding format|UTF8|
|Content-Type|application/x-www-form-urlencoded|
|pushUrl|This address is provided by the customer, which is provided to the operation binding, one account and one address|

### 4.2 The callback example

 `http://pushMoUrl?receiver=admin&pswd=12345&moTime=1208212205&mobile=13800210021&msg=hello&destcode=CHUANGLAN`
 
 Parameter description is as follows：
``` 
receiver：The user name that receives uplink validation (not the account name) is the name configured according to the user's request and is empty by default
pswd：Receive the uplink authenticated password, which defaults to null
moTime：The upside of time
mobile：Uplink phone number
msg：Uplink message content
destcode：User uplink destination number
```


Note:
1. Response string :OK if received successfully
<br/>
<br/>
<br/>

<a id="a-groupmessaging"></a>
## 5 Group messaging（json）

**brief description:**
* SMS group interface（json）

**request URL:**
* `http://intapi.253.com/send`

**request method:**
* POST<br/>
content-type：application/json

**parameter：**

|Parameter name|mandatory|type|instructions|
|:---|:---|:---|:---|
|account|yes|string|account|
|password|yes|string|password|
|msg|yes|yes|Message content|
|mobile|yes|string|phone number|
<br/>

**Sample request**

{<br/>
    `"account"`:"I6428061",<br/>
    `"password"`:"123456",<br/> 
    `"msg":"`【253】你好，您的验证码是：123456",<br/>
    `"mobile"`:"8613011111111,8613022222222,8613033333333"<br/>
}<br/>
<br/>

**Return parameter specification**

|Parameter name|type|instructions|
|:---|:---|:---|
|code|string|Return code|
|message|string|The message|
|data|object|The packet|
|messageId|string|Message id|
|errorPhone|array|Wrong phone number|
<br/>

**Return sample (single)**<br/>

 {<br/>
    `"code"`: "0",<br/>
    `"message"`: "成功",<br/>
    `"data"`: {<br/>
        "messageId": "17122614541000000355"<br/> 
    }<br/>
}<br/>
Single issue returns a single message id
<br/>
<br/>

**Return sample (group)**<br/>
{<br/>
    `"code"`: "0",<br/>
    `"message"`: "成功",<br/>
    `"data"`: {<br/>
        `"messageId"`: "I6428061_1712261459_40",<br/>
         `"errorPhone"`: []<br/>
    }<br/>
}<br/>
A batch message id is returned
<br/>
<br/>

**Return sample (send error)**

{<br/>
    `"code"`: "123",<br/>
    `"message"`: "Text messages cannot be empty",<br/>
    `"data"`: null<br/>
}<br/>

**Return code**

|code|instructions|
|:---|:---|
|0|success|
|101|Account does not exist|
|102|Password mistake|
|106|The text message length exceeds the 536 character limit|
|108|Wrong format of mobile phone number|
|109|Wrong number of mobile phone|
|110|Lack of balance|
|112|Product is wrong|
|114|Client IP error|
|115|Send permission error|
|123|The text message is empty|
|125|A certain customer's phone number must not exceed 10 times on the same day|
|128|Account length is over 50 digits|
|129|Product price configuration error|
<br/>
<br/>
<br/>


<a id="a-voicecode"></a>
## 6 Voice verification code

### 1.1 Agreement that

|name|instructions|
|:--|:--|
|agreement|HTTP POST|
|Coding format|UTF8|
|Content-Type|application/json|
|URL|`http://intapi.253.com/sendVoice/OTP`|

### 1.2 Request

& The request is a json string with the following parameters：

{<br/> 
     `"account"` : "I6000001", //API account, no more than 50 digits. mandatory<br/> 
     `"password"` : "12345678", //API account corresponding to the key, contact customer service to obtain. mandatory<br/> 
     `"intro"` : "Your verification code is", //Introduction to captcha (read before captcha)<br/> 
     `"code"` : "869452", //Verification code<br/> 
     `"outro"` : "don't tell others.", //End (not necessarily read after captcha)<br/> 
     `"mobile"` : "8615800000000" //Mobile phone number, format (area code + mobile phone number), for example: 8615800000000，<br/> Among them, 86 is the Chinese area code, which does not begin with 00, and 1580 million is the real mobile phone number to receive SMS messages. 5-20. mandatory<br/> 
     
 }<br/> 
 
### 1.3  Response

& This response is the submission response, please get the status report to confirm whether it was successfully sent to the phone

 {<br/>
     `"code"` : "0", //Status code<br/>
     `"msgid"` : "17041010383624511", //Message id<br/>
     `"error"` : "", //Status code description (empty string returned on success, return on failure, e.g., insufficient balance)<br/>
 }<br/>
 <br/>
 Note: code is the response status code, which can be compared with the submitted response status code
<br/>
<br/>
<br/>
<a id="a-pulldetails"></a>
## 7 Pull up the uplink message details

### 1.1 Agreement that

|name|instructions|
|:--|:--|
|agreement|HTTP POST|
|Coding format|UTF8|
|Content-Type|application/json|
|URL|`http://intapi.253.com/pull/mo`|

### 1.2 Request

& The request is a json string with the following parameters：

{<br/> 
     `"account"` : "I6000001", //API account, no more than 50 digits. mandatory<br/> 
     `"password"` : "12345678", //API account corresponding to the key, contact customer service to obtain. mandatory<br/> 
     `"count"` : "30", //Pull the number (Max. 100, default 20) and select<br/> 
 }<br/> 
 
 ### 1.3 Response
 
 & This response is the submission response, please get the status report to confirm whether it was successfully sent to the phone
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
Note: code is the response status code, which can be compared with the submitted response status code
<br/>
<br/>
<br/>

<a id="a-statusreport"></a>
## 8 Pull the status report

### 1.1 Agreement that

|name|instructions|
|:--|:--|
|agreement|HTTP POST|
|Coding format|UTF8|
|Content-Type|application/json|
|URL|`http://intapi.253.com/pull/report`|

### 1.2 Request

& The request is a json string with the following parameters：

```
 { 
     "account" : "I6000001", //API account, no more than 50 digits. mandatory
     "password" : "12345678", //API account corresponding to the key, contact customer service to obtain. mandatory
     "count" : "30", //Pull the number (Max. 100, default 20) and select
 }
 ```
 
 ### 1.3 Response
 
 & This response is the submission response, please get the status report to confirm whether it was successfully sent to the phone
 
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
      "status": "DELIVRD"
    },
    {
      "batchSeq": "I2170326_1808150928_5748789",
      "mobile": "8618037170702",
      "msgid": "18081509281005782276",
      "reportTime": "1808150928",
      "status": "DELIVRD"
    }
  ]
}
```
<br/>
<br/>
<br/>
<a id="a-statuscode"></a>

# Status Code

## Status report status code

|Status code|instructions|
|:--|:--|
|DELIVRD|Message sent successfully|
|UNKNOWN|Unknown SMS status|
|REJECTD|The message was rejected by the message center|
|MBBLACK|The destination number is the blacklist number|
|SM11|Gateway validation number format error|
|SM12|We verify that the number format is wrong|
|other|Gateway internal state|

## Submit the response status code

|Status code|instructions|
|:--|:--|
|0|Submitted successfully|
|101|Account does not exist|
|102|Password mistake|
|103|String number format error|
|104|The number of pull strips is not in the range|
|106|Text message length error(>3000)|
|108|Wrong format of mobile phone number(>20或<5)|
|109|Wrong number of mobile phone|
|110|Lack of balance|
|112|Product configuration error|
|114|Request IP and binding IP are not consistent|
|115|No access to domestic SMS|
|116|Account deleted or disabled|
|117|The access number is longer than 20 digits|
|123|Text messages cannot be empty|
|124|The profile or captcha cannot be empty|
|125|A certain customer's phone number must not exceed 10 times on the same day|
|126|Timed message sending time cannot be empty|
|126|Timed message sending time error|
|128|Account length error(>50或<=0)|
|129|Product price configuration error|
|130|Unknown abnormal|
|131|Exceeding the daily delivery limit|
|132|Exceed monthly delivery limit|
|133|Sending limit exceeded|
|134|Exceeding the counter - complaint limit|
