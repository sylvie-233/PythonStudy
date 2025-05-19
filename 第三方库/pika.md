# pika


## 基础介绍


RabbitMQ消息队列操作库


## 核心内容
```yaml
pika:
    BasicProperties: # 消息属性
        content_type:    
        correlation_id: # 消息id
        delivery_mode:
        headers:
        reply_to: # 消息回复队列
    BlockingConnection: # conn连接
        Channel:
        channel(): # 获取channel，连接复用
            add_on_return_callback(): # 注册回调处理返回 (channel, method, properties, body)
            basic_ack(): # 消息应答
                delivery_tag:
            basic_consume(): # 消息接收
                auto_ack: # 自动应答
                no_ack:
                on_message_callback: # 消息接收回调 (channel,method,properties,body)
                    method:
                        delivery_tag:        
                        queue:
                    properties:
                        correlation_id:
                        replay_to:
                queue:
            basic_publish(): # 消息发布
                body: # 消息体
                exchange: # 发送交换机
                mandatory:
                properties: # 消息属性配置
                routing_key:
            basic_qos():
                prefetch_count:
            confirm_delivery(): # 生产者启用发布确认模式
            exchange_declare(): # 声明交换机，自动创建
                durable:
                exchange:
                exchange_type:
                    direct:
                    fanout:
                    topic:
            queue_bind(): # 声明交换机、队列绑定
                exchange:
                queue:
                routing_key:
            queue_declare(): # 声明channel绑定的队列，自动创建
                durable: # 持久化
                exclusive:
                queue:
                --- # result
                    method:
                        queue:
            start_consuming(): # 开始消费
        close(): # 关闭连接
        process_data_events():
    ConnectionParameters: # conn连接参数
        credentials: # 连接凭证
        host:
        port:
    PlainCredentials: # conn连接凭证
    SelectConnection:
```


### Connection




### Channel

连接复用



### Queue


### Exchange


### Routing Key

路由键，决定消息去哪个队列