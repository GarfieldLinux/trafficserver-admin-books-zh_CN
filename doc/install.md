### **һ����װ�����**
��װTS�������������
- t-libevent
- t-openssl-libs
- t-spdylay
- tcl

��yum ��װ

    yum install trafficserver -b current -y


### **���������ļ�˵��**

##### 1.�����ļ�
TS �������ļ�ȫ����/etc/trafficserver/ Ŀ¼�£������Ƿ�ģ�����ã�һ�������ļ�����һ�ֹ���
```
/etc/trafficserver/ #������Ŀ¼
������ ae_ua.config
������ cache.config          #Cache��������
������ cluster.config        #cluster�����б��Զ�����
������ congestion.config     #��������
������ default_cluster.config
������ health_check.config   #�߲㽡���������
������ hosting.config        #���̷�����������
������ icp.config            #icp��ѯ����
������ ip_allow.config       #ip���ʿ�������
������ log_hosts.config      #
������ logs_xml.config       #��־ϵͳ����
������ mgr.cnf
������ parent.config         #parent��Դ����
������ plugin.config         #�������
������ plugin.db             
������ proxy.pac
������ records.config        #TS���Ʋ�������
������ remap.config          #ҵ���������
������ snapshots
������ socks.config
������ splitdns.config       #splitdns����
������ ssl_multicert.config  #SSL ����
������ stats.config.xml      #ͳ����Ϣ����
������ storage.config        #�洢����
������ update.config         #Ԥ������
������ vaddrs.config         #
������ volume.config         #���̷�������
������ wpad.dat
```

##### 2.��־�ļ�
������־����¼TS������״̬��һЩdebug��Ϣ

    /var/log/trafficserver/traffic.out

Error log
���ʳ������־

    /var/log/trafficserver/error.log


##### 3.�����й���
TS �ṩ�����еĲ������ߣ����������������ò���
<br>������ȡ����ֵ

    traffic_line -r proxy.config.proxy_name

�޸Ĳ���ֵ

    traffic_line -s traffic_line -r proxy.config.proxy_name -v cn8


### **������������**

    /etc/init.d/trafficserver start


### **�ġ��������**

    /etc/init.d/trafficserver activate


