# XOpenApi

  为方便其他应用接入平台，特定制本开放接口规范。

  * 接入准备
    * 接入需先向平台方获取AppID以及AppKey
    
  * 接口统一要求
    * 接口支持HTTP/HTTPS, 同时支持GET/POST方式调用，POST方式下参数在BODY以JSON格式传递
    * 每次接口调用需传递调用时间ctime={unixtime}，跟平台时间超过30秒的将直接被拒绝，因此应用应确保自己机器时钟准确
    * 签名规则:
      * 告知签名规则smethod={SignMethod}，目前支持 sha1/md5，如果能够支持sha1，请使用sha1
      * 所有传递参数（除sign本身外）按KEY字母顺序排序
      * 所有传递值进行urlencode编码
      * 尾部增加&appkey={AppKey}
      * 最终拼接成a=v1&b=v2&c=v3&appkey={AppKey}的形式，进行签名得到{sign}
      * 调用时
        * GET：a=v1&b=v2&c=v3&sign={sign}
        * POST: { a:v1, b:v2, c:v3, sign:{sign}}
      * 本接口默认定义的ctime, smethod, appkey, sign 以及其值都使用全小写模式
      
