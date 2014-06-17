Remap��Lua
==========
���°汾�lua�ѿ�Ƕ�뵽remap.config�֧�ָ����Ļ���http header���

ts-lua �ӿ��ĵ�https://github.com/portl4t/ts-lua

### ����˵��
Remap ��֧������Lua Hook�������׶�

* do_remap 

        remapǰ�׶Σ��ý׶ο����޸Ĵ洢key���ܾ�����ȵȲ���

* send_request

        ��Դ����request �׶Σ��ý׶ο��Զ�ȡ���޸Ļ�Դrequest header

* read_response

        ��ȡ��Դresponse �׶Σ��ý׶ο��Զ�ȡ���޸Ļ�Դ���յ�response header

* send_response

        ���͸�client response �׶Σ��ý׶ο��Զ�ȡ���޸ķ��͸��û�response header

* cache_lookup_complete

        Cache ��ȡ�׶Σ��ý׶ο����ж϶�����Cache״̬����ȡCache�е�response header��
        

### ����ʾ��

> ע�� һ��remap �����ʹ�ö��״̬�����״̬��ϳ�һ���ű�ʹ��

* do_remap

        http www.taobao.com {
            map / http://www.taobao.com.inner.taobao.com {
                script do_remap {
                    -- �ж�Useragent ����ת
                    ts.ctx['is_forbidden'] = 0
                    local uagent = ts.client_request.header['User-Agent']
                    if string.find(uagent, 'haoyu') then
                        ts.ctx['is_forbidden'] = 1
                        ts.http.set_resp(302, "302 Moved")
                        return TS_LUA_REMAP_DID_REMAP_STOP
                    end
                }
                
                script send_response {
                    if ts.ctx['is_forbidden'] == 1 then
                        ts.client_response.header['Location'] = 'http://err.haoyu.com/'
                        return 0
                    end
                }
            }
        }
        

* send_request
        
        http www.taobao.com {
            map / http://www.taobao.com.inner.taobao.com {
                script send_request {
                    -- �ѻ�Դrequest Host �ĳ�www.tmall.com
                    ts.client_request.header['Host'] = 'www.tmall.com'
                }
            }
        }
        

* read_response
        
        http www.taobao.com {
            map / http://www.taobao.com.inner.taobao.com {
                script read_response {
                    -- ����Accept-Test ���ั������
                    ts.server_response.header['Vary'] = "Accept-Test"
                }
            }
        }
        
* send_response
        
        http www.taobao.com {
            map / http://www.taobao.com.inner.taobao.com {
                script send_response {
                    -- ���Response Header
                    ts.client_response.header['Test'] = 'yes'
                }
            }
        }
        
* cache_lookup_complete

        http www.taobao.com {
            map / http://www.taobao.com.inner.taobao.com {
                script cache_lookup_complete {
                    -- ���Cache ״̬
                    local cache_status = ts.http.get_cache_lookup_status()
                    if cached_status == TS_LUA_CACHE_LOOKUP_HIT_FRESH then
                        ts.ctx['cstatus'] = 'hit'
                    else
                        ts.ctx['cstatus'] = 'miss'
                    end
                }
                
                script send_response {
                    -- ���Cache״̬ͷ
                    ts.client_response.header['Cache-Status'] = ts.ctx['cstatus']
                }
            }
        }
        
