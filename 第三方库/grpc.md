# grpc



## 基础介绍

gRPC 是 Google 开发的一种高性能、开源、通用的远程过程调用（RPC）框架。
- 使用 Protocol Buffers（protobuf） 作为接口定义语言（IDL）和消息交换格式。
- 支持多种语言（Python、Go、Java、C++等），而且自动生成代码。
- 特别适合高性能、低延迟的微服务通信场景

gRPC核心功能：
- Message消息定义
- RPC Service 服务接口定义
- RPC Client Stub客户端定义
- 绑定service接口实现到Server服务器
- 使用生成的Stub客户端存根绑定Channel连接，调用Server rpc服务





### protoc
```yaml
protoc:

```

proto文件编译命令


### .proto
```yaml
.proto:
    syntax: # 语法版本
        proto3:
    package: # 定义模块名
    message: # 消息定义
        string:
    service:
        rpc:
            returns:
```

核心定义文件





## 核心内容
```yaml
grpc:
    server: # grpc服务器
        add_insecure_port(): # 注册服务端口
        start():
        wait_for_termination():
    insecure_channel: # Channel grpc客户端连接，传入stub中进行操作


grpcio:


grpcio_tools: # 编译模块
    protoc: # protoc编译模块，可执行模块
        -I:
        --grpc_python_out: # 服务端代码生成 服务接口
        --python_out: # 客户端代码生成 Message 数据结构
    xxx: # 客户端代码生成 Message
    xxx_grpc: # 服务端代码生成 服务接口
        XxxServicer: # service服务基类，继承并实现具体的service方法
        XxxStub: # Stub客户端存根（Session，依赖channel），调用service
        add_XxxServicer_to_server(): # 注册service实现到服务器
```


### Message

消息模型
RequestMessage、ResponseMessage
Protocol Buffers、一种轻量高效的序列化格式（IDL）


### Service

gRPC服务端Service基类
定义服务及其方法，相当于“接口”


#### Unary RPC

一次请求 → 一次响应


#### Server Streaming RPC

一次请求 → 多次响应（流）


#### Client Streaming RPC

多次请求 → 一次响应


#### Bidirectional Streaming RPC

多次请求 ↔ 多次响应（全双工）



### Channel

客户端与服务端之间的连接（HTTP/2）
Stub客户端存根会显式使用



### Stub

gRPC客户端操作工具、客户端存根
客户端调用服务时使用的本地代理对象，需绑定Channel



### Server

服务端实现
手动实现定义在 proto 文件中的接口




## grpc核心应用




### 简单样例


#### 1. 定义 .proto 文件
```proto
syntax = "proto3";

package hello;

// 定义服务
service Greeter {
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// 定义请求消息
message HelloRequest {
  string name = 1;
}

// 定义响应消息
message HelloReply {
  string message = 1;
}
```


#### 2. 生成 Python 代码
```bash
# python_out 生成 message数据结构
# grpc_python_out 生成 server 接口定义
python -m grpc_tools.protoc -I. --python_out=. --grpc_python_out=. hello.proto
```


#### 3. hello_pb2.py
```python
class HelloRequest(proto.Message):
    name = proto.Field(proto.STRING, number=1)

class HelloReply(proto.Message):
    message = proto.Field(proto.STRING, number=1)
```

消息类定义（用于序列化 / 反序列化）


#### 4. hello_pb2_grpc.py
```python
# 服务接口定义
class GreeterServicer:
    def SayHello(self, request, context):
        raise NotImplementedError()

# 客户端服务存根
class GreeterStub:
    def SayHello(self, request, timeout=None):
        # 实际发起 gRPC 请求

# 注册服务函数
def add_GreeterServicer_to_server(servicer, server):
    # 注册服务端实现到 gRPC server
```



#### 5. 实现服务端
```python
import grpc
from concurrent import futures
import hello_pb2
import hello_pb2_grpc

# rpc service接口实现
class GreeterImpl(hello_pb2_grpc.GreeterServicer):
    def SayHello(self, request, context):
        print("Received:", request.name)
        return hello_pb2.HelloReply(message=f"Hello, {request.name}")

def serve():
    # 创建服务器
    server = grpc.server(futures.ThreadPoolExecutor(max_workers=10))

    # 添加服务接口实现
    hello_pb2_grpc.add_GreeterServicer_to_server(GreeterImpl(), server)
    server.add_insecure_port('[::]:50051')
    server.start()
    print("Server started at port 50051.")
    server.wait_for_termination()

if __name__ == "__main__":
    serve()
```

服务端核心步骤：
- Message消息定义
- RPC Service 服务接口定义
- 绑定service接口实现到Server服务器





#### 6. 实现客户端
```python
import grpc
import hello_pb2
import hello_pb2_grpc

def run():
    # 获取channel连接
    with grpc.insecure_channel('localhost:50051') as channel:
        # 使用生成的客户端存根
        stub = hello_pb2_grpc.GreeterStub(channel)
        response = stub.SayHello(hello_pb2.HelloRequest(name="Alice"))
        print("Server replied:", response.message)

if __name__ == "__main__":
    run()
```

客户端核心步骤：
- Message消息定义
- 使用生成的Stub客户端存根绑定Channel连接，调用Server rpc服务


