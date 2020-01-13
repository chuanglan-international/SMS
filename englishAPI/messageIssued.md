
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
