# XOpenApi

## ǰ��

  Ϊ��������Ӧ�ý���ƽ̨���ض��Ʊ����Žӿڹ淶��

  * ����׼��
    * ����������ƽ̨����ȡAppID�Լ�AppKey
    
  * �ӿ�ͳһҪ��
    * �ӿ�֧��HTTP/HTTPS, ������ȷ˵������, ����ͬʱ֧��GET/POST��ʽ���ã�POST��ʽ�²�����BODY��JSON��ʽ����
    * ÿ�νӿڵ����贫�ݵ���ʱ��ctime={unixtime}����ƽ̨ʱ�䳬��30��Ľ�ֱ�ӱ��ܾ������Ӧ��Ӧȷ���Լ�����ʱ��׼ȷ
    * ǩ������:
      * ��֪ǩ������smethod={SignMethod}��Ŀǰ֧�� sha1/md5������ܹ�֧��sha1����ʹ��sha1
      * ���д��ݲ�������sign�����⣩��KEY��ĸ˳������
      * ���д���ֵ����urlencode����
      * β������&appkey={AppKey}
      * ����ƴ�ӳ�a=v1&b=v2&c=v3&appkey={AppKey}����ʽ������ǩ���õ�{sign}
      * ����ʱ
        * GET��a=v1&b=v2&c=v3&sign={sign}
        * POST: { a:v1, b:v2, c:v3, sign:{sign}}
      * ���ӿ�Ĭ�϶����ctime, smethod, appkey, sign �Լ���ֵ��ʹ��ȫСдģʽ
      
  * ����ͳһ����
    * ����ֵ��ʽ: { "errcode": 0, "errdesc": "", "data" : { ... }}
    * errcode >= 0���������ɹ���data�ֶη������ݶ���
    * errcode <0 ��������ʧ�ܣ�errdesc�ֶα�����������
      
  * Ŀǰ�����Ӧ��Ϊ��ȼ��ɣ���˽ӿڱ�OAuth��Ϊ���ֱ�ۣ���Ҳ�������߰�ȫ��Ҫ����˲���ʱ��Ҫ�Ե�������Դ������������֤��
      
## �˺Žӿ�

  * ͨ��SESSIONID�����˺���֤ authBySessionId?appid={AppID}&ctime={UnixTime}&sessionid={SessionId}&sign={Sign}  
  
## ����ҽӿ�

  * ��ѯ�����û��� coinQuery?appid={AppID}&coinname={CoinName}&ctime={UnixTime}&uid={UserIdx}&sign={Sign}
  
  * �ۼ������û��� coinTrade?appid={AppID}&coinname={CoinName}&coinnum={Num}&ctime={UnixTime}&memo={MemoWord}&serialid={TradeUniqueSerialId}&uid={UserIdx}&sign={Sign}
  
  * �ۼ�����û��� coinTradeEx������ͨ��POST�ύ
  
    ``` 
    { 
    	tradeid:{UniqueTradeId}, 
    	memo:{MeomoWord}, 
    	orders:{
    		{ coinname:{CoinName1}, coinnum:{CoinNum1}, uid:{UserIdx1} },
    		{ coinname:{CoinName2}, coinnum:{CoinNum2}, uid:{UserIdx2} }
    	}
    }
    ```
    
  