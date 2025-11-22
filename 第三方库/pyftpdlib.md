# pyftpdlib


## 基础介绍

ftp服务框架


## 核心内容
```yaml
pyftpdlib:
    authorizers: # 认证授权
        DummyAuthorizer:
            add_user():
    handlers: # 处理器
        FTPHandler:
            authorizer:
    servers: # 服务
        FTPServer:
            serve_forever():
```