# grpc



## 基础介绍

gRPC 是 Google 开发的一种高性能、开源、通用的远程过程调用（RPC）框架。
- 使用 Protocol Buffers（protobuf） 作为接口定义语言（IDL）和消息交换格式。
- 支持多种语言（Python、Go、Java、C++等），而且自动生成代码。
- 特别适合高性能、低延迟的微服务通信场景

### .proto
```yaml
.proto:
    
```

## 核心内容
```yaml
grpc:
    server: # grpc服务器
        add_insecure_port(): # 注册服务端口
        start():
        wait_for_termination():
    insecure_channel: # grpc客户端连接，传入stub中进行操作


grpcio:
grpcio_tools: # 
    protoc: # proto编译模块
        -I:
        --grpc_python_out: # 服务端代码生成 服务接口
        --python_out: # 客户端代码生成 Message
    xxx: # 客户端代码生成 Message
    xxx_grpc: # 服务端代码生成 服务接口
        XxxServicer: # service服务基类，继承并实现具体的service方法
        XxxStub: # Stub客户端存根（Session，依赖channel），调用service
        add_XxxServicer_to_server(): # 注册service实现到服务器
```


### Message

消息模型

### Servicer

gRPC服务端Service基类


### Stub

gRPC客户端操作工具