# redis

## 基础介绍

redis官方python库



## 核心内容
```yaml
redis:
    asyncio: # 异步io操作
        ConnectionPool: # 连接池
            from_url():
        Redis:
            connection_pool:
            db:
            host:
            port:
            close():
            get():
            set():
    ConnectionPool:
        host:
        port:
    Redis:
        connection_pool:
        host:
        port: 
        delete():
        expire():
        get():
        hget():
        hgetall():
        hmset():
        hset():
        incr():
        linsert():
        lpush():
        ping(): # 连接测试
        set():
        setex():
        setnx():
        srandmember():
        xack(): # stream消息应答ack，   
            stream:
            group:
            message_id:
        xadd(): # stream添加消息
            maxlen: # stream最大长度
            approximate:
        xclaim: # stream 领取（XCLAIM）长时间未确认的消息给另一个消费者（实现重试）
        xdel: # stream 消息删除
        xgroup_create(): # 创建group消费者组
            stream:
            group:
            id: # id='0' 表示从头开始；也可以用 '$'（后续只接收新消息）
            mkstream:
        xinfo_groups:
        xinfo_stream: # 
        xlen(): # stream长度
        xpending(): # stream Pending（未确认）消息查看,[(id, consumer, elapsed_ms, deliveries), ...]
        xrange(): # stream范围查看
        xread(): # stream直接读取，使用'$' 或指定上次读取的 id
        xreadgroup(): # 消费者组消费（可同时消费多个stream）,[(stream_name, [(id, {field: value}), ...])]
            groupname:
            consumername:
            streams: # 使用 '>' 表示消费组读取“尚未被任何消费者分派的新消息”
            count:
            block:
        xtrim: # stream消息截断（避免stream过大）
        zadd():
        zrange():
```