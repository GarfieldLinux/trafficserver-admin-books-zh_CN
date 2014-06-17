ATS������ݲɼ�
============

### Tsar ����
Tsar���Ա���һ�������ռ�������ϵͳ��Ӧ����Ϣ�Ĳɼ����湤�ߣ����ռ���������ϵͳ��Ϣ��cpu��mem�ȣ����Լ�Ӧ�����ݣ��ռ��������ݴ洢�ڷ����������ϣ�������ʱ��ѯ��ʷ��Ϣ��Ҳ���Խ����ݷ��͵�nagios������

Tsar�ܹ��ȽϷ��������ģ�飬ֻ��Ҫ����tsar��Ҫ���д���ݵĲɼ�������չ�ֺ������Ϳ��԰��Զ����ģ����뵽tsar��

##### Tsar ��װ

��Դ��

```bash
#git clone git://github.com/kongjian/tsar.git
#cd tsar
#make
#make install
```

##### Tsar����ATSģ��

```vim /etc/tsar/tsar.conf```

```bash
#debug_level(INFO DEBUG WARN ERROR FATAL)
debug_level FATAL
#[module] on/off to enable mod
mod_swap on
mod_tcp on
mod_io on
mod_pcsw on
mod_partition on
mod_tcpx on
mod_load on
mod_percpu on
mod_ts_client on  #tsǰ����Ϣ
mod_ts_os on      #ts��Դ��Ϣ
mod_ts_cache on   #ts Cache��Ϣ
mod_ts_err on     #ts err��Ϣ
mod_ts_storage on #ts �洢��Ϣ
mod_ts_conn on    #ts ������Ϣ
mod_ts_codes on   #ts http_code

#output type:file,nagios,db
output_interface file

#[output_file] original data to store
output_file_path /var/log/tsar.data

#[output_stdio] these mod will be show as using tsar
output_stdio_mod mod_swap,mod_partition,mod_cpu,mod_mem,mod_traffic,mod_load,mod_tcp,mod_udp,mod_tcpx,mod_pcsw,mod_io,mod_ts_client,mod_ts_os,mod_ts_cache,mod_ts_err,mod_ts_storage,mod_ts_conn,mod_ts_codes
```

##### TS �������˵��
```bash
#tsar --ts
Time           --------------------ts------------------ 
Time              qps    cons     Bps      rt     rpc   
28/01/14-16:10   3.4K    1.2K   87.8M   64.66    2.87   
28/01/14-16:15   3.4K    1.2K   89.8M   61.59    2.83   
28/01/14-16:20   3.5K    1.2K   87.3M   63.80    2.82 
```
- qps  ����������/s
- cons �½�����/s
- Bps  ����/s
- rt   ��Ӧʱ��(ms)
- rpc  ���Ӹ�����(ƽ��ÿ�����ӷ�����ٸ�������)

------------------------------------------
```bash
#tsar --ts_os
Time           --------------ts_os------------- 
Time              qps    cons    mbps     rpc   
28/01/14-16:15 198.75    6.54    5.5M   30.39   
28/01/14-16:20 199.32    6.73    5.1M   29.62   
28/01/14-16:25 198.24    6.74    5.1M   29.40
```
- qps  ��Դ������/s
- cons ��Դ�½�����/s
- mbps ��Դ����
- rpc  ��Դ���Ӹ���

------------------------------------------
```bash
#tsar --ts_cache
Time           -------------ts_cache----------- 
Time              hit  ramhit    band  ssdhit   
28/01/14-16:15  94.50   84.80   91.70    0.00   
28/01/14-16:20  94.70   84.70   94.70    0.00   
28/01/14-16:25  94.60   84.80   93.80    0.00
```
- hit     ����������
- ramhit  �ڴ�������
- band    �ֽ�������
- ssdhit  �ּ��洢��ssd������

------------------------------------------
```bash
#tsar --ts_storage
Time           ------------ts_storage---------- 
Time              ram    disk    objs    size   
28/01/14-16:15  24.0G    4.3T  130.1M   34.1K   
28/01/14-16:20  24.0G    4.3T  130.1M   34.1K   
28/01/14-16:25  24.0G    4.3T  130.2M   34.1K 
```
- ram    �ڴ�ʹ�ô�С
- disk   ����ʹ�ô�С
- objs   object����
- size   ƽ��object��С

------------------------------------------

```bash
#tsar --ts_conn
Time           -------------------------ts_conn------------------------ 
Time           client  server   cache    open   c_act   t_cli   t_srv   
28/01/14-16:20  96.3K  167.00   47.00   96.5K  168.00  268.00   13.00   
28/01/14-16:25  94.8K  149.00   49.00   94.9K  166.00  273.00   16.00   
28/01/14-16:30  96.4K  184.00   35.00   96.6K  127.00  261.00   16.00 
```
- client   ǰ��������,#���ļ����Ҫ��ϸ�
- server   ��Դ������
- cache    ��ȡCache��������
- open     �ܼƴ򿪵�����
- c_act    ��Ծ��client������
- t_cli    ���ڴ����client����������ռ���ڴ�ģ�һ������ռ��16k
- t_srv    ���ڴ���Ļ�Դ������