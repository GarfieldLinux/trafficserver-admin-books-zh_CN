�ȵ���ɢģ��
=========

### ʹ�ó���

��һ����Hash �ĳ���������Ĵ��ļ����أ�������������������أ���ͬ��URIȫ��Hash��һ̨�����ϣ���ʱ����ɵ�������������������IO����������������������ȴ��Խϵͣ������һ������Ҫ�õ��ȵ���ɢģ�飬���ȵ��ļ���ɢ���������еĻ����ϡ�

### ���ò���

* �ȵ�URL�����Ŀ
   <br> ���ã� ```records.config```
   <br> ��λ�� ����
   <br> ˵���� ����ܳ���100��0��ʾ�������ȵ㷢�ֹ��ܡ����鲻Ҫ����10���������������Ϊ5
   
        proxy.config.http.hoturls.max_count
   <br>
   
* ���ʱ����
   <br> ���ã� ```records.config```
   <br> ��λ�� ��
   <br> ˵���� ����ʱ����������Ϊ1�룬��಻�ܳ���300�룬��������Ϊ10��
   
        proxy.config.http.hoturls.detect_interval_secs
   <br>
   
* ���������ֵ
   <br> ���ã� ```records.config```
   <br> ��λ�� bps
   <br> ˵���� �������������������������ȵ��⣬������������Ⱥ�������й�
   
        proxy.config.http.hoturls.detect_on_bps
   <br>
   
* ��������������������ֵ
   <br> ���ã� ```records.config```
   <br> ��λ�� �ٷֱȣ����ͣ�������
   <br> ˵���� cluster��������Ͷ�������������ֲ����������£��������ȵ��⡣��������Ϊ0.50����ʾ�����������һ������������á�����Ϊ0.25��ʾ�����������3��������²����ü�⹦��
   
        proxy.config.http.hoturls.detect_on_bps_ratio
   <br>
   
* ��ⵥ��URL����ռ����ֵ
   <br> ���ã� ```records.config```
   <br> ��λ�� �ٷֱȣ����ͣ�������
   <br> ˵���� ����URL����ռ�ȳ�����ֵ������ѡΪ�ȵ�URL�������������Ϊ0.10����ʾ����URL������ռ�ȳ���10%����ѡ
   
        proxy.config.http.hoturls.single_url_bps_ratio
   <br>
   
* �����URL����ռ����ֵ
   <br> ���ã� ```records.config```
   <br> ��λ�� �ٷֱȣ����ͣ�������
   <br> ˵���� ����URL����ռ�ȳ�����ֵ�����⼸��URL����ѡΪ�ȵ�URL������Ϊ0.00��ʾ��������URL�ۼ�ɸѡ
   
        proxy.config.http.hoturls.multi_url_bps_ratio
   <br>
   
* �ȵ�url����ʱ��
   <br> ���ã� ```records.config```
   <br> ��λ�� ���������ͣ�����
   <br> ˵���� �ȵ�URL���������������������ݹ���PURGE�ģ�Ŀ����ȷ��PURGE�ɾ�����СֵΪ1�죬���ֵΪ31�졣ͨ������Ϊ1�켴�ɣ������ļ���/var/run/trafficserver/hoturl.binlog
   
        proxy.config.http.hoturls.keep_days
   <br>