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
```yaml
name: sylvie233-pythontest

version: '3.8'

services:
  kafka:
    image: confluentinc/cp-kafka:8.1.0
    container_name: kafka
    ports:
      - "9092:9092"
      - "9093:9093"
    environment:
      # 启用 KRaft 模式（不依赖 Zookeeper）
      KAFKA_KRAFT_MODE: "true"
      KAFKA_PROCESS_ROLES: "broker,controller"
      KAFKA_NODE_ID: 1

      # 监听器配置
      KAFKA_LISTENERS: "PLAINTEXT://:9092,CONTROLLER://:9093"
      KAFKA_ADVERTISED_LISTENERS: "PLAINTEXT://kafka:9092"
      KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: "PLAINTEXT:PLAINTEXT,CONTROLLER:PLAINTEXT"
      KAFKA_CONTROLLER_LISTENER_NAMES: "CONTROLLER"
      KAFKA_CONTROLLER_QUORUM_VOTERS: "1@kafka:9093"

      # 基本参数
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1
      KAFKA_TRANSACTION_STATE_LOG_REPLICATION_FACTOR: 1
      KAFKA_TRANSACTION_STATE_LOG_MIN_ISR: 1
      KAFKA_LOG_DIRS: "/var/lib/kafka/data"
      KAFKA_AUTO_CREATE_TOPICS_ENABLE: "true"

      # 允许明文访问
      KAFKA_ALLOW_PLAINTEXT_LISTENER: "yes"

    volumes:
      - kafka_data:/var/lib/kafka/data
    networks:
      - sylvie233-network

  kafka-ui:
    image: rootpublic/kafka-ui:0.7.2_rootio
    container_name: kafka-ui
    depends_on:
      - kafka
    ports:
      - "8080:8080"
    environment:
      - KAFKA_CLUSTERS_0_NAME=local
      - KAFKA_CLUSTERS_0_BOOTSTRAPSERVERS=kafka:9092
    networks:
      - sylvie233-network

volumes:
  kafka_data:
    driver: local

networks:
  sylvie233-network:
    driver: bridge
```



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