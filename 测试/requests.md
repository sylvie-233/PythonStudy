# requests

## 基础介绍

HTTP

## 核心内容
```yaml
requests:
    adapters:
        HTTPAdapter:
    auth: # 认证
        HTTPBasicAuth:
    exceptions:
        Timeout:
        TooManyRedirects:
    models:
        Response:
            content:
            encoding: # 文档编码
            headers:
            request:
            status_code:
            text: # 文档内容
            json():
    packages:
        urllib3:
            util:
                retry:
                    Retry:
    Request: # 请求
    RequestException:
    Response: # 响应
        content: # 二进制内容
        cookies:
        headers:
        status_code:
        text:
        url:
        json():
        write():
    Session: # 会话
        mount():
        request():    
    delete():
    get():
        auth:
        cookies:
        params: # query param
        proxies: # 代理
        timeout:
    head():
    patch():
    post():
        data:
        files:
        json:
        url:
    put():
    request():
```


### Session