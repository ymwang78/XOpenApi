# XOpenApi

## 前言

  为方便其他应用接入平台，特定制本开放接口规范。

  * 接入准备
    * 接入需先向平台方获取AppID以及AppKey
    
  * 接口统一要求
    * 接口支持HTTP/HTTPS, 除非明确说明例外, 否则同时支持GET/POST方式调用，POST方式下参数在BODY以JSON格式传递
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
      
  * 返回统一定义
    * 返回值形式: { "errcode": 0, "errdesc": "", "data" : { ... }}
    * errcode >= 0表明操作成功，data字段返回数据对象
    * errcode <0 表明操作失败，errdesc字段表明错误描述
      
  * 目前接入的应用为深度集成，因此接口比OAuth更为简洁直观，单也带来更高安全性要求，因此部署时需要对调用者来源服务器进行验证。
      
## 账号接口

  * 通过SESSIONID进行账号验证 authBySessionId?appid={AppID}&ctime={UnixTime}&sessionid={SessionId}&smethod={SignMethod}&siteid={SiteId}&sign={Sign}  
  
## 虚拟币接口

  * 查询单个用户币 coinQuery?appid={AppID}&coinname={CoinName}&ctime={UnixTime}&smethod={SignMethod}&uid={UserIdx}&sign={Sign}
  
  * 扣减单个用户币 coinTrade?appid={AppID}&coinname={CoinName}&coinnum={Num}&ctime={UnixTime}&memo={MemoWord}&serialid={TradeUniqueSerialId}&smethod={SignMethod}&uid={UserIdx}&sign={Sign}
  
  * 扣减多个用户币 coinTradeEx?appid={AppID}&ctime={UnixTime}&sign={Sign}，必须通过POST提交
  
    ``` 
    {
    	tradeid:{UniqueTradeId}, 
    	memo:{MemoWord}, 
    	orders:{
    		{ coinname:{CoinName1}, coinnum:{CoinNum1}, uid:{UserIdx1} },
    		{ coinname:{CoinName2}, coinnum:{CoinNum2}, uid:{UserIdx2} }
    	}
    }
    ```
    
  
