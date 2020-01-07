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



 1. [Message issued](docs/englishmessageIssued.md )

 1. [Query balance](docs/englishqueryBalance.md )

 1. [State of the callback](docs/englishVersion/englishcallBack.md)

 1. [The upward push](docs/englishupwardPush.md)

 1. [Group messaging（json）](docs/englishgroupMessaging.md)

 1. [Voice verification code](docs/englishvoiceVerificationCode.md)

 1. [Pull up the uplink message details](docs/englishpullDetail.md)

 1. [Pull the status report](docs/englishpullCallback.md)

 1. [Status code](docs/englishstatusCode.md)
