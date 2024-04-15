
## 1 短信下发

### 1.1 协议说明
名称|说明
:---|:---
协议|HTTP POST
编码格式|UTF8
Content-Type|application/json
URL(上海)| https://intapi.253.com/send/sms
URL(新加坡)|http://intapi.sgap.253.com/send/sms

### 1.2 请求头
名称|类型|是否必填|示例|说明
:---|:---|:---|:---|:---
sign|string|是|1234abcd7890qwer|签名，请参照加签方式生成签名
nonce|string|是|1653043349000|时间戳

### 1.3 请求包体
名称|类型|是否必填|示例|说明
:---|:---|:---|:---|:---
account|string|是|I6000000|API账号，50位以内
mobile|string|是|8615800000000|手机号码，格式(区号+手机号码)，例如：8615800000000，其中86为中国的区号， 区号前不使用00开头,15800000000为接收短信的真实手机号码。5-20位
msg|string|否|【253】您的验证码是：2530|短信内容。长度不能超过536个字符。如果开启退订，短信内容后追加退订链接： 2ub.co/xxxxxx或1ub.co/xxxxxx，原短信内容增加14个字符。计费条数可能会增加。和templateId二者必填其一
senderId|string|否|SENDER0|用户收到短信之后显示的发件人，国内不支持自定义，国外支持，但是需要提前和运营商沟通注册，具体请与TIG对接人员确定
uid|string|否|123456|客户自定义批次号，64字以内
tdFlag|int|否|1|退订开启标识，1 开启；0或null 关闭 
templateId|string|否|20989509086|消息模板Id，和msg二者必填其一

> 加签方式：  
1. 将请求头参数名nonce及所有请求体参数名（key）以ASCII码表顺序升序排列；
2. 排序后把参数值非空的参数名（key）参数值（value）依次进行字符串拼接，拼接处不包含其他字符；
3. 拼接成包含kv的长串后，在该长串的尾部拼接账号的password，得到签名字符串的组装；
4. 最后对签名字符串，使用MD5算法加密后，得到MD5加密密文后转为小写，即为请求头sign值
 
 ### 1.4 应答包体
 
 名称|类型|示例|说明
:---|:---|:---|:---
code|string|0|状态码: 0-成功,非0标识失败
error|string|签名错误|状态码说明,成功返回空字符串
msgid|string|17041010383624511|消息id

 注：code为响应状态码，可参照提交响应状态码对比
 
 ### 1.5 加签代码示例
 ```java
 package com.angi;

import com.alibaba.fastjson.JSONObject;
import org.apache.commons.lang3.StringUtils;
import org.springframework.util.DigestUtils;

import java.util.Map;
import java.util.TreeMap;


/**
 * 参数进行加签验签
 */
public class SignUtil {

    private static final String SIGN = "sign";

    /**
     * 发送加签
     */
    public static String sendSign(String password, TreeMap<String, String> paramMap) {
        paramMap.remove(SIGN);
        StringBuilder sb = new StringBuilder();
        for (Map.Entry<String, String> entry : paramMap.entrySet()) {
            if (StringUtils.isNotBlank(entry.getValue())) {
                sb.append(entry.getKey());
                sb.append(entry.getValue());
            }
        }
        return DigestUtils.md5DigestAsHex((sb.toString() + password).getBytes()).toLowerCase();
    }

    /**
     * 发送验签
     */
    public static boolean verifySendSign(String password, TreeMap<String, String> paramMap) {
        String sign = paramMap.remove(SIGN);
        String computed = sendSign(password, paramMap);
        return StringUtils.equals(sign, computed);
    }


    public static void main(String[] args) {
        /**发送加签验签*/
        String password = "4Z7bMS1eLI6895";
        TreeMap<String, String> paramMap = new TreeMap<>();
        paramMap.put("nonce", "222222");
        paramMap.put("account", "IM6742671");
        paramMap.put("mobile", "8618916198813");
        paramMap.put("msg", "test 666661 ");
        System.out.println(JSONObject.toJSONString(paramMap));
        String sign = sendSign(password, paramMap);
        System.out.println(sign);

        TreeMap<String, String> newParamMap = new TreeMap<>(paramMap);
        newParamMap.put(SIGN, sign);

        boolean validate = verifySendSign(password, newParamMap);
        System.out.println(validate);

    }


}

 ```
