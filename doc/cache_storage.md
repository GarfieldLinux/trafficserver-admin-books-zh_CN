Cache ����
=========


#### Disk Cache
* ����Disk Cache(```storage.config```)

    1���༭```/etc/trafficserver/storage.config```
    <br> Ŀ¼���÷�ʽ

        # Ŀ¼  �����С
        /var/cache/trafficserver 256M

    <br> �������÷�ʽ
    
        # ֱ����д���̽�ȥ��һ��һ��
        /dev/sdb
        /dev/sdc
        /dev/sdd
        
      
    2������Ӧ��
    
        /etc/init.d/trafficserver restart

* ���̷����洢(```volume.config```��```hosting.config```)
    <br> volume.config
    
#### Ram Cache
* Ram ������С
  <br> ���ã� ```records.config```
  <br> ��λ�� byte
     
         proxy.config.cache.ram_cache.size
  <br>  

* ���Ram Cache ����
  <br> ���ã� ```records.config```
  <br> ��λ�� byte
        
        proxy.config.cache.ram_cache_cutoff
  <br>
  
* Ram ��̭�㷨
  <br> ���ã� ```records.config```
  <br> ### 0 - CLFUS
  <br> ### 1 - LRU
  
        proxy.config.cache.ram_cache.algorithm
  <br>
    