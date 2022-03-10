
## 3 Callback Delivery status

### 3.1 Protocol description

|Name|Description|
|:---|:---|
|Protocol|HTTP GET|
|Code Format|UTF8|
|Content-Type|application/x-www-form-urlencoded|
|pushUrl|A given user provides URL, Chuanglan Operation team will bind this URL with user’s account, one account with one URL|

### 3.2 Callback Sampl


http://pushUrl?receiver=admin&pswd=12345&msgid=12345&reportTime=1012241002&mobile=13900210021&status=DELIVRD¬ifyTime=180828114243&batchSeq=I0123456_1808281142_2188000


Parameter Description As Below
```
receiver：The user name (not the account name) for authentication when receiving the delivery status report, this user name is configured according to the user's requirements, the default value is null
pswd：Password used for authentication when receiving the delivery status report, default value is null 
msgid：Custom message ID returned by platform when messages submitted.
reportTime：Timestamp returned by gateway platform, different gateway causes format discrepancy, specific format returned shall prevail<br/>
notifyTime：Timestamp returned by interface server, format YYMMDDhhmmss, YY= Last two digit of the given year (00-99), MM= month (01-12), DD= Date(01-31), hh= hour (00-23), mm=minute (00-59), ss= second (00-59).
mobile：Mobile phone number when submitting SMS
status：status code of the delivery status report
batchSeq：Sms batch sequence number
```


```
Note：
1.Successful receiving responds a string:OK
2.status status code of the delivery status report, refer to the status report code for reference
```
