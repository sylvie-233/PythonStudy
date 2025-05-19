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
        set():
        setex():
        setnx():
        srandmember():
        zadd():
        zrange():
```