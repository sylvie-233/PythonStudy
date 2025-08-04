# twisted


## 基础介绍

基于事件驱动Reactor模式的网络通信框架
- tcp服务器
- http服务器


twisted核心组件：
- Reactor：核心事件循环（Reactor 模式）
- Protocol：定义通信协议行为（如 TCP 读写）
- Factory：生成 Protocol 实例的工厂
- Deferred：异步回调对象，类似于 Promise
- Transport：负责实际网络读写
- Endpoint：抽象的连接方式


## 核心内容
```yaml
twisted:
    application: # 服务管理脚本框架
    conch: # SSH 协议支持
    enterprise: # 数据库异步访问支持
    internet: # 网络
        defer: # 异步操作
            Deferred:
                addCallback(): # 添加回调方法
                addErrback(): # 添加异常回调
                callback(): # 触发回调链
            @inlineCallbacks:
                addCallback():
            returnValue():
        protocol: # 协议
            ClientFactory: # 客户端工厂
                buildProtocol():
                clientConnectionFailed():
                clientConnectionLost():
            Factory: # 服务端工厂
                buildProtocol(): # 构建协议
            Protocol: # 协议
                transport:
                connectionLost():
                connectionMade():
                dataReceived(): # 
        reactor: # 反应堆  
            callLater(): # 延迟调用
            listenTCP(): # tcp监听
            run():
            stop():
        threads: # 线程池 
            deferToThread():
    mail: # SMTP/IMAP 支持
    names: # DNS 支持
    web: # HTTP/WSGI 服务
        resource:
            Resource: # http资源
                render_GET():
        server:
            Site(): # 资源站点
    words: # IRC 聊天协议
```