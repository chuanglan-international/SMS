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
8. 纯英语/拉丁字母内容按照160字母（字符）/条计费；非纯英语/拉丁字母内容都按照70字（字符）/条计费；以上两种类型的内容（符号/文字）混合，将统一按照非纯英文模式70字/条计费。短信内容长度计费超过1条，系统将默认生成占位符（纯英文/拉丁类型7字符，其他类型3字符），使短信计费长度变为153/67字符每条。

## 目录

1. [短信下发](docs/messageIssued.md)
2. [查询余额](docs/queryBalance.md)
3. [回调状态](docs/callBack.md)
4. [上行推送](docs/upwardPush.md)
5. [短信群发（json）](docs/groupMessaging.md)
6. [拉取上行短信明细](docs/pullDetail.md)
7. [拉取状态报告](docs/pullCallback.md)
8. [变量短信](docs/variableMessage.md)
9. [状态码](docs/statusCode.md)
10. [回填率](docs/ConversionRate.md)

## 

[English version of the API](englishAPI/README.md)

