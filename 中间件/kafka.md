# Kafka


## 基础介绍

Producer -> Topic      -> Consumer Group
         -> Partition  -> Consumer
                              

Kafka核心概念：
- Broker：Kafka 服务器实例
- Topic：消息主题（逻辑分类）
    - Partition：主题的分区（并行和分布式的关键）
    - Offset：消息在分区中的唯一编号
- Producer：生产者，发送消息到 Kafka
- Consumer：消费者，从 Kafka 拉取消息
    - Consumer Group:消费组，实现水平扩展与容错
- Zookeeper / KRaft：用于元数据管理（Kafka 3.x 开始逐步用 KRaft 替代 Zookeeper）


Docker Compose安装：




- 每个主题可有多个分区，分区可以分布在不同的 broker 上
- 整个组一起消费完整个 topic、同一分区的消息只能被一个消费者消费（同一组内），避免重复消费
- 每个 partition 是一个 有序日志文件:
- 每个分区有一个 Leader 和多个 Follower
- 生产者只向 Leader 写数据，Follower 从 Leader 同步
- 消费者读取时只从 Leader 拉取
- 消费者读取时记录自己的 offset、offset 是针对 “分区（Partition）” 而不是整个 Topic 的
- 支持一个 topic 被多个消费者组并行消费
- Kafka 3.x 之后（尤其是 3.3+）可以不需要 ZooKeeper（推荐使用 KRaft 模式）
    - node节点角色：
        - broker：负责存储和转发消息
        - controller：负责元数据管理、分区选举、消费组管理


### 安装目录
```yaml
kafka:
    /bin:
        kafka-console-consumer.sh:
        kafka-console-producer.sh:
        kafka-server-start.sh:
        kafka-topics.sh:
            --create:
                --topic:
                --bootstrap-server:
                --partitions:
                --replication-factor:
        zookeeper-server-start.sh: # 旧版 启动zookeeper
    /config:
        /kraft:
            /server.properties:
        server.properties: # 服务配置
        zookeeper.properties: # zookeeper配置
```





## 核心内容





### Kafka Stream

Kafka 自带的轻量流式计算框架