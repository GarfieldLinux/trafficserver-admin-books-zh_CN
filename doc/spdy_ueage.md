SPDY ʹ��˵��
=========

spdy˵����http://www.chromium.org/spdy

#### һ����װ���

> ������
<br>t-ts-fetcher
<br>t-spdylay

    yum insall t-ts-spdy -b test -y
    
#### �������ò��

    vim /etc/trafficserver/plugin.config
    /usr/lib64/trafficserver/plugins/libtsspdy.so
    
#### ��������ATS

    /etc/init.d/trafficserver restart
    
#### �ġ���֤

    /home/a/bin/spdycat -v -n http://127.0.0.1/ --no-tls -3 -H "Host:www.taobao.com"
    
![ATS SPDY USAGE](https://github.com/yanghao-zh/trafficserver-admin-books-zh_CN/raw/master/img/spdy_usage.jpg)