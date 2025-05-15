# rocketmq-client-python


## 基础介绍

python操作rocketmq


## 核心内容
```yaml
rocketmq:
    client:
        Message: # 消息
            set_body(): # 消息体
            set_keys():
            set_tags():
        MessageListener: # 消息监听器
            consume(): # 消费消息
        Producer: # 生产者
            send_sync(): # 发送消息
            set_name_server_address():
            shutdown(): # 关闭
            start():
        PushConsumer: # 消费者
            register_message_listener(): # 注册消息监听器
            set_name_server_address():
            shutdown():
            start():
            subscribe(): # 消息订阅
```