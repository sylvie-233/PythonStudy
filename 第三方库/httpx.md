# httpx


## 基础介绍

Python HTTP 客户端库，它支持同步和异步请求，是 requests 库的一个强大替代品

## 核心内容
```yaml
httpx:
    AsyncClient: # 异步客户端
        base_url:
        headers:
        timeout:
        get():
        post():
    Client:
    Timeout:
    get():
    post():
        auth:
        data:
        files:
        headers:
        params:
        proxies:
        ---
        status_code:
        text:
        json():
        raise_for_status():
    stream(): # 流式响应
        iter_bytes():      
```