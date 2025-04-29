# pika


## 基础介绍


RabbitMQ消息队列操作库


## 核心内容
```yaml
pika:
    BlockingConnection: # conn连接
        channel(): # 获取channel，连接复用
            basic_consume(): # 消息接收
                auto_ack: # 自动应答
                on_message_callback: # 消息接收回调
                queue:
            basic_publish(): # 消息发布
                body:
                exchange:
                routing_key:
            queue_declare(): # 声明channel绑定的队列
            start_consuming():
        close():
    ConnectionParameters: # conn连接参数
        credentials:
        host:
        port:
    PlainCredentials: # conn连接凭证
```


### Connection




### Channel

连接复用



### Queue


### Exchange


### Routing Key

路由键，决定消息去哪个队列