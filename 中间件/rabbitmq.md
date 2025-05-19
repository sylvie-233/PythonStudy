# rabbitmq

``

## 基础介绍


一个流行的 开源消息队列中间件
实现了高级消息队列协议（AMQP），核心作用是实现 异步解耦、流量削峰、消息传递可靠性 等

AMQP协议通信端口：5672
WEB控制台端口：15672
Node集群节点通信端口：25672


Exchage默认 direct 直连交换机（fanout、direct、topic）
交换机绑定方式：RoutingKey、Arguments


队列特性feature：


队列中Message消息状态：Ready、Unacked

用户标签Ta：Admin、Monitoring、Policymaker、Administrator
用户持有对应的Virtual Host资源



Broker核心操作：Exchange、Queue、Binding


RabbitMQ可靠机制：
- 生产者重连
- 生产者确认ACK、编写回调方法（Confirm回调：确认消息到达交换机、Return回调：确保消息到达队列）
- 消息持久化、惰性队列
- 消费者确认
- 消费者失败消息处理（MessageRecoverer）
- 业务幂等性判断（自己手动处理）



RabbitMQ核心应用：
- 异步任务
- 流量削峰
- 延时任务、死信交换机、延迟消息
- RPC调用：


RabbitMQ核心组件：
- Virtual Host（虚拟主机）	多租户隔离机制，一个虚拟机可有多个用户、交换机、队列等
- Exchange（交换机）	消息路由器，决定消息发往哪个队列
- Binding（绑定）	建立 exchange 与 queue 的关系及路由规则
- Queue（队列）	消息中转的存储结构，消息最终进入队列并被消费
- Routing Key（路由键）	用于交换机路由消息到队列的键值
- Message（消息）	数据单元，通常包含 body + headers
    - Ack / Nack	确认/拒绝机制，保障消息可靠投递和消费
    - Durable / Persistent	决定队列或消息是否持久化以防崩溃丢失
- Producer（生产者）	发送消息的应用程序或服务
- Consumer（消费者）	接收并处理消息的应用程序或服务
- Channel	与 RabbitMQ 之间的逻辑连接，基于 TCP 连接复用，轻量、高效
    - Connection	应用与 RabbitMQ broker 的一个 TCP 连接


RabbitMQ核心问题：
- 消息幂等性：唯一消息ID、业务判断




### rabbitmq-server
```yaml
rabbitmq-server:
    start:
    stop:
```

rabbitmq服务启动


### rabbitmqctl
```yaml
rabbitmqctl:
    add_user:
    add_vhost:
    delete_vhost:
    change_password:
    cluster_status: # 集群状态
    delete_user:
    join_cluster: # 加入集群
    list_bindings:
    list_channels:
    list_connections:
    list_exchanges:
    list_permissions:
    list_queues:
    list_users:
    list_user_permissions:
    list_vhosts:
    restart:
        rabbitmq-server:
    set_permissions: 
    set_user_tags: # 设置用户标签
        administrator:
    status:
    stop:
    
```

rabbit控制命令





### rabbitmq-plugins
```yaml
rabbitmq-plugins:
    disable:
    enable:
    list:
```


rabbitmq插件管理



## 核心内容

### Virtual Host 

虚拟主机
环境隔离


### Exchange



#### Direct Exchange

直连交换机
路由方式：精确匹配 routing key
适用场景：一对一精确路由，比如点对点通信、日志等级分类等


#### Fanout Exchange

扇形交换机
路由方式：广播，消息发送到绑定该交换机的所有队列，不考虑 routing key
适用场景：广播通知、多消费者消息推送（如系统通知、日志广播）



#### Topic Exchange

主题交换机
路由方式：模糊匹配 routing key（支持通配符）
适用场景：多级分类、模糊匹配，适合日志系统、消息分类广播等


#### Headers Exchange

头部交换机
路由方式：根据消息的 headers 属性匹配（不是 routing key）
适用场景：需要根据多个字段组合条件路由的场景



#### DeadLetter Exchange

死信交换机
处理过期消息、堆积消息


### Queue






### Message




### User





### 集群



## RabbitMQ核心应用



### RPC

RPC实现原理
```txt
Client                       RabbitMQ                    Server
   |                             |                           |
   | -- [fib(10),reply_to,Q,id] -> rpc_queue                 |
   |                             | -- 消费请求 ------------>  |
   |                             |<---- 结果,correlation_id-- |
   |<-- 结果消息 (corr_id match) -- callback_queue            |
```
1. 客户端 发送请求消息到一个请求队列（rpc_queue）。
2. 服务端 监听请求队列，接收到消息后处理，并将结果发回。
3. 客户端 使用临时队列（回调队列）接收响应。
4. 利用消息的 correlation_id 字段，实现请求和响应的 一一对应。
