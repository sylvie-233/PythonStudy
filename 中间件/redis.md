# Redis



## 基础介绍


内容k-v数据库


Docker Compose安装：
```yaml
name: sylvie233-pythontest

services:
  redis:
    image: redis:7.4.5
    container_name: redis
    ports:
      - "6379:6379"    # 映射本地端口
    environment:
      REDIS_PASSWORD: "123456"  # 设置访问密码
    command: ["redis-server", "--requirepass", "123456"]  # 强制密码访问
    volumes:
      - redis_data:/data   # 持久化数据
    restart: unless-stopped
    networks: 
      - sylvie233-network

volumes:
  redis_data:
    driver: local

networks:
  sylvie233-network:
    driver: bridge
```



### redis-server
```yaml
redis-server:
    --service-install: # 安装成服务
    --service-run:
```



### redis-cli
```yaml
redis-cli:
    -a:
    --cluster:
        create: # 创建集群
    --stat:
```

### redis-sentinel
```yaml
redis-sentinel:

```


### redis.conf
```yaml
redis.conf:
    aof-use-rdb-preamble:
    appendfilename:
    appendfsync: # AOP策略
    appendonly: # 开启AOF持久化
    bind:
    cluster-config-file:
    cluster-enabled: # 开启集群
    cluster-node-timeout:
    daemonize: # 后台运行
        yes:
    dbfilename:
    dir: # RDB存放路径
    logfile:
    loglevel:
    masterauth: # 连接主服务器时认证密码
    maxmemory: # 最大内存
    maxmemory-policy: # 最大内存淘汰机制
        allkeys-lru:
    port: # 6379
    rename-command: # 禁用远程命令
    replicaof: # 设置当前实例为某主服务器的从服务器
    requirepass: # 密码
    save: # RDB快照规则
    slaveof:
    timeout: # 超时关闭
```




## 核心内容
```yaml
Redis:
    String: # 字符串
        append: # 追加
        decr:
            by:
        get: # 获取
        incr:
            by:
        mget:
        mset:
        set: # 设置
            ex: # 过期设置
            nx: # 不存在才设置       
        strlen: # 字符串长度
    List: # 列表（从0开始）
        lindex: # 根据索引获取
        linsert: # 插入
            after:
            before:
        llen: # 长度
        lpop: # 弹出
        lpush: # 添加
        lrange: # 范围获取
        lrem: # 移除
        lset: # 索引设置
        rpop:
        rpush:
    Hash: # 哈希
        hdel: # 删除内部k
        hexists: # 判断内部k
        hget: # 获取
        hgetall: # 获取所有k-v
        hincrby:
        hkeys: # 获取所有key
        hmget:
        hset: # 设置
        hvals: # 获取所有value
    Set: # 集合
        sadd: # 添加
        scard: # 长度
        sdiff: # 差集
            store:
        sinter: # 交集
            store:
        smembers: # 获取所有数据
        spop: # 随机弹出一个
        srem: # 删除
        sunion: # 并集
            store:
    ZSet: # 有序集合
        zadd:
        zcard:
        zcount:
        zpopmax:
        zpopmin:
        zrange:
        zrangebyscore:
        zrank:
        zrem:
        zrevrange:
        zrevrangebyscore:
        zrevrank:
        zscore:
    Bitmaps: # 位操作
        bitcount:
        bitpos:
        getbit:
        setbit:
    HyperLogLog: # 估算独立元素数量（基数）
    Geo: # 地理位置,纬度查询
    Streams: # 日志流、消息队列（stream -> group）
        XACK:
        XADD:
        XGROUP:
            CREATE:
        XREADGROUP:
    PubSub: # 发布/订阅消息
        PUBLISH:
        SUBSCRIBE :
    auth: # 认证
    clear: # 清空控制台
    discard: # 放弃事务
    exec: # 执行事务
    exists: # key存在判断
    expire: # 过期时间设置
    flushall:
    keys: # 
    multi: # 开启事务
    rename: # key重命名
    select: # 切换数据库，默认0（0~15）
    ttl: # 过期时间
    type: # 获取key数据类型
    watch: # 监听key
```


### String




### List




### Hash




### Set



### ZSet 



### Transaction




### PubSub


发布订阅



### Stream

流式，消息队列模拟




### Persistent

redis持久化


#### RDB

快照持久化、周期性保存全量数据，启动时加载（save）
- Redis 在指定时间间隔内保存内存中的数据快照到磁盘（.rdb 文件）
- 启动时加载最新的快照文件恢复数据

#### AOF

写命令日志、记录每次写操作，重启时重放日志（appendfsync）
- 每次写操作（如 SET/DEL）都追加一条命令到 .aof 文件
- 重启时 Redis 逐条执行日志恢复数据


### 集群


Redis 集群（Redis Cluster）是 Redis 官方提供的分布式架构解决方案
主要用于数据分片和高可用（HA），它解决了单实例内存上限和服务单点故障的问题


#### Sharding 分片

redis 分片规则：
- Redis 集群将 key 的 hash 值映射到 16384 个 slot（插槽）
- 每个节点管理一部分 slot
- 一个 key 落在哪个节点，由 CRC16(key) % 16384 决定


#### 主从复制
```yaml
       +--------+     +--------+     +--------+
       | Master1|     | Master2|     | Master3|
       +--------+     +--------+     +--------+
         /   \           /   \          /   \
        v     v         v     v        v     v
   +--------+ +--------+ +--------+ +--------+ +--------+ +--------+
   | Slave1 | | Slave2 | | Slave3 | | Slot  | | Slot  | | Slot  |
   +--------+ +--------+ +--------+ | 0~5460| |5461~10922|10923~16383
```

- 每个分片节点（Master）可以有一个或多个从节点（Slave）
- 当某个主节点挂了，由其从节点自动顶上（failover）


节点角色：
- 主节点 Master	负责读写、管理 slot
- 从节点 Slave	热备份、容灾，平时不参与写操作


支持一主多从、多主多从集群
多主多从中每个主节点只负责部分数据



#### Sentinel 哨兵模式

- Sentinel 是一个 Redis 守护进程，监控主从状态
- 当 Master 宕机时，自动将某个 Slave 提升为 Master


#### Gossip 协议

- Redis 节点之间通过 Gossip 协议交换状态
- 当某主节点挂掉，超过半数节点判断失联，就进行 自动选主



## Redis应用场景


### 缓存



### 分布式锁



### 消息队列





### 发布订阅






## Redis原理

### RESP 协议

Redis 使用自定义的 RESP 协议（Redis Serialization Protocol）进行通信，是一种轻量、可读性强的文本协议，主要用于客户端与服务端之间传输命令和结果