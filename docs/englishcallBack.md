## 3 State of the callback

### 3.1 Agreement that

|Name|instructions|
|:---|:---|
|agreement|HTTP GET|
|Coding format|UTF8|
|Content-Type|application/x-www-form-urlencoded|
|pushUrl|This address is provided by the customer, which is provided to the operation binding, one account and one address|

### 3.2 The callback example


`http://pushUrl?receiver=admin&pswd=12345&msgid=12345&reportTime=1012241002&mobile=13900210021&status=DELIVRD¬ifyTime=180828114243&batchSeq=I0123456_1808281142_2188000`


Parameter description is as follows：
```
receive：The user name (not the account name) verified by the receiving status report is the name configured as required by the user and is empty by default
pswd：Receive the password verified by the status report, which defaults to null
msgid：Msgid returned by platform when SMS is submitted
reportTime：The gateway platform returns the time, the gateway is different, the format has the deviation, the specific return format shall prevail.
notifyTime：Interface server returns time in format YYMMDDhhmmss, where YY= last two digits of year (00-99), MM= month (01-12), DD= day (01-31), hh= hours (00-23) 
, MM= minutes (00-59),ss= seconds (00-59).
mobile：The mobile phone number at the time of submitting the message
status：Status report status code
betchSeq：SMS batch number.
```


```
note：
1.Response string received successfully:OK
2.Status is the status code of status report, which can be compared with the status code of status report
```

