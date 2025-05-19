# Redis



## 基础介绍


### redis-server
```yaml
redis-server:
    
```



### redis-cli
```yaml
redis-cli:
    -a:
    --stat:
```



### redis.conf
```yaml
redis.conf:
    appendfilename:
    appendfsync:
    appendonly: # AOF持久化
    bind:
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
    timeout: # 超时关闭
```




## 核心内容
```yaml
Redis:
    String: # 字符串
        append: # 追加
        decr:
        exists: # key存在判断
        expire: # 过期事件设置
        flushall:
        get:
        incr:
            by:
        keys: # 
        mget:
        mset:
        rename: # key重命名
        set:
            ex: # 过期设置
            nx: # 不存在才设置       
        strlen: # 字符串长度
        ttl: # 过期时间
        type: # 获取key数据类型
        watch: # 监听key
    List: # 列表
        lindex: # 索引
        linsert: # 插入
            after:
            before:
        llen: # 长度
        lpop: # 弹出
        lpush: # 添加
        lrange: # 范围获取
        lrem: # 移除
        lset: # 索引设置
        rpush:
    Hash: # 哈希
        hdel:
        hexists:
        hget: # 获取
        hgetall:
        hincrby:
        hkeys:
        hmget:
        hset: # 设置
        hvals:
    Set: # 集合
        sadd:
        scard: # 长度
        sdiff:
        sinter:
        smembers:  
        spop:  
        srem:
        sunion:
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
    Streams: # 日志流、消息队列
    PubSub: # 发布/订阅消息
    discard: # 放弃事务
    exec: # 执行事务
    select: # 切换数据库，默认0（0~15）
    multi: # 开启事务
```


### String




### List




### Hash




### Set



### ZSet 



### Transaction




### PubSub




### Persistent

redis持久化


#### RDB



#### AOF



### 集群




## Redis应用场景


### 缓存



### 分布式锁



### 消息队列





### 发布订阅






## Redis原理

### RESP 协议

Redis 使用自定义的 RESP 协议（Redis Serialization Protocol）进行通信，是一种轻量、可读性强的文本协议，主要用于客户端与服务端之间传输命令和结果