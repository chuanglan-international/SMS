# 创蓝国际

253云通讯国际短信api

## 接口说明

短信接入注意事项：
1. API账号、密码参数由我方统一提供
2. 如需推送状态报告，请提供回调地址给我方运营人员绑定(群发接口目前不支持状态推送)
3. 仅支持HTTP POST请求方式
4. 编码统一使用UTF-8
5. 请求头Content-Type必须根据接口要求设置正确，否则可能会导致参数传递错误
6. 短信内容签名没有强制要求，部分国家可为空，具体请咨询运营人员
7. 手机号码格式为区号+真实手机号码，比如中国区号为86，示例：8618888888888

## 目录

 1. [短信下发](docs/messageIssued.md)
 1. [查询余额](docs/queryBalance.md)
 1. [回调状态](docs/callBack.md)
 1. [上行推送](docs/upwardPush.md)
 1. [短信群发（json）](docs/groupMessaging.md)
 1. [语音验证码](docs/voiceVerificationCode.md)
 1. [拉取上行短信明细](docs/pullDetail.md)
 1. [拉取状态报告](docs/pullCallback.md)
 1. [状态码](docs/statusCode.md)
##
--------------------------------------------------- English version of the API-------------------------------------------------------

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

 1. [message issued](englishAPI/messageIssued.md)
 1. [查询余额](docs/queryBalance.md)
 1. [回调状态](docs/callBack.md)
 1. [上行推送](docs/upwardPush.md)
 1. [短信群发（json）](docs/groupMessaging.md)
 1. [语音验证码](docs/voiceVerificationCode.md)
 1. [拉取上行短信明细](docs/pullDetail.md)
 1. [拉取状态报告](docs/pullCallback.md)
 1. [状态码](docs/statusCode.md)
