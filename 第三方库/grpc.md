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


pip依赖：
- grpcio
- grpc-tools
- protobuf





### protoc
```yaml
protoc:
    -I: # protobuf输入文件
    --python_out: # message定义文件输出
    --grpc_python_out: # service定义文件输出
```

proto文件编译命令
`python -m grpc_tools.protoc`


### .proto
```yaml
.proto:
    syntax: # 语法版本
        proto3:
    package: # 定义模块名
    import: # 导入插件
    message: # 消息定义
        bool:
        bytes:
        string:
        int32:
        int64:
        float:
        repeated: # 数组
        map: # 哈希表
        ---
        extend: # 继承
        message: # 消息嵌套定义
    service: # 服务定义
        rpc: # 服务方法定义
            stream: # 流式输入
            returns: # 服务方法返回值
                stream: # 流式响应
```

protobuf协议定义文件





## 核心内容
```yaml
grpc:
    Compression: # 数据压缩
    GenericRpcHandler: # 通用服务处理器（类似中间件）
        service(): # 通用服务处理逻辑
    ServerInterceptor: # 服务器拦截器
        _abort():
        intercept_service():
            continuation:
            handler_call_details: # 类似context  
    StatusCode: # 响应状态码
    server(): # grpc服务器（需传入线程池）
        compression:
        intercepters:
        options: # 服务配置
            grpc.max_receive_message_length:
            grpc.max_send_message_length:
        ---
        add_generic_rpc_handlers(): # 添加通用方法处理器
        add_insecure_port(): # 注册grpc服务端口（grpc服务需要一个单独的端口运行）
        start(): # 开启grpc服务器
        wait_for_termination(): # 开启事件循环
    insecure_channel(): # 创建Channel grpc客户端连接，传入stub中进行操作
    unary_unary_rpc_method_handler(): # unary-unary rpc方法注册

grpcio:

grpcio_tools: # 编译模块
    protoc: # protoc编译模块，可执行模块
        -I:
        --grpc_python_out: # 服务端代码生成 服务接口
        --python_out: # 客户端代码生成 Message 数据结构
    xxx: # 客户端代码生成 Message定义实体类 xxx_pb2.py
        XxxRequest:
        XxResponse:
    xxx_grpc: # 服务端代码生成 服务接口 xxx_pb2_grpc.py
        XxxServicer: # service服务基类，服务端需继承并实现具体的service方法
            request:
                data:    
            context:
                cancel():
                invocation_metadata():
                is_active():
                set_code():
                set_compression(): # 数据压缩
                set_detail():
                set_trailing_metadata():
        XxxStub: # 客户端创建Stub客户端存根（Session，依赖channel），调用service
            with_call(): # 获取调用者元信息 
                compression:
                metadata: # 调用者传递metadata
                timeout:
                ---
                trailing_metadata():
        add_XxxServicer_to_server(): # 注册service(XxxServicer)实现到grpc服务器
```


### Message

消息模型（请求格式、响应格式）
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

grpc服务端实现
手动实现定义在 proto 文件中的接口

#### Metadata


元数据（模拟请求头）


#### Compression

数据压缩


#### StatusCode

响应状态码


#### ServerInterceptor


#### GenericRpcHandler

通用服务处理器


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

服务接口定义


#### 5. 实现服务端
```python
import grpc
from concurrent import futures
import hello_pb2
import hello_pb2_grpc

# rpc service接口实现
class GreeterImpl(hello_pb2_grpc.GreeterServicer):
    def SayHello(self, request, context):
        """
            request: 请求数据
                data:    
            context: 服务上下文
                cancel():
                is_active():
                set_code():
                set_detail():
                set_trailing_metadata():
        """
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


