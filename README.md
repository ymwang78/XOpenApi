# XOpenApi

  Ϊ��������Ӧ�ý���ƽ̨���ض��Ʊ����Žӿڹ淶��

  * ����׼��
    * ����������ƽ̨����ȡAppID�Լ�AppKey
    
  * �ӿ�ͳһҪ��
    * �ӿ�֧��HTTP/HTTPS, ͬʱ֧��GET/POST��ʽ���ã�POST��ʽ�²�����BODY��JSON��ʽ����
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
      
