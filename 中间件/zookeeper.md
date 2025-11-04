# zookeeper


## 基础介绍

分布式服务注册、发现、配置管理中心
一个高可用的、强一致的树形节点ZNode存储系统

依赖Java运行环境
默认只有一个根节点、默认持久节点


Docker Compose安装：
```yaml
version: '3.8'
name: sylvie233-zookeeper

services:
  zookeeper:
    image: zookeeper:3.9.3
    container_name: zookeeper
    restart: unless-stopped
    ports:
      - "2181:2181"
    environment:
      ZOO_MY_ID: 1
      # 移除 ZOO_PORT，使用默认值
      # 单机模式不需要 ZOO_SERVERS，或者正确配置
      ZOO_STANDALONE_ENABLED: "true"
      # 或者完全移除 ZOO_SERVERS 对于单机模式
    volumes:
      - zookeeper_data:/data
      - zookeeper_datalog:/datalog
    healthcheck:
      test: ["CMD", "zkServer.sh", "status"]
      interval: 30s
      timeout: 10s
      retries: 3

volumes:
  zookeeper_data:
    driver: local
  zookeeper_datalog:
    driver: local
```


树状节点系统：
- 类似于 Linux 的目录树，例如：/app/config/db
- 每个 ZNode 可以有子节点，但临时节点不能有子节点


ZNode节点类型、ZNode 有两种类型：
- 持久节点（Persistent）：客户端断开后仍存在
- 临时节点（Ephemeral）：客户端断开即自动删除
    - 只能由客户端创建，不能由其它客户端继承


节点版本号、每个 ZNode 包含三种版本号：
- dataVersion：数据本身的版本
- cVersion：子节点列表的版本
- aclVersion：访问控制列表的版本


会话（Session）：
- 客户端和 ZooKeeper 的连接称为一个会话
- 每个会话有一个唯一 ID 和过期时间（超时后临时节点会被清除）


Watcher（监听机制）：
- 客户端可以对某个节点设置监听器，ZK 的事件触发时通知客户端
- 一次性：触发一次就失效，需要手动重新注册
- 常用于监控节点的变更（如数据变化、子节点变化等）


ACL（访问控制）：
- ZooKeeper 支持对每个节点设置权限（Access Control List）
- 常见权限包括：读（READ）、写（WRITE）、创建（CREATE）、删除（DELETE）、管理（ADMIN）

ZAB 协议、ZAB 是 ZooKeeper 的核心分布式一致性协议，保证以下几点：
- 原子性（所有事务请求要么成功要么失败）
- 顺序一致性（所有节点按同样顺序应用变更）
- 恢复能力（Leader 崩溃后能恢复）


事务日志和快照：
- 所有写操作都会先写入事务日志（Write-Ahead Logging）
- 定期保存内存数据的快照，用于节点重启后的恢复


Leader 选举：
- ZK 集群使用 ZAB 协议（Zookeeper Atomic Broadcast）
- 集群启动时会自动选出一个 Leader，其他是 Follower
- 所有写请求都由 Leader 处理，读请求可由任意节点处理



- Zookeeper端口：如果是单节点，只需要映射 2181 即可；集群模式要暴露 2888 与 3888
    - 2181：客户端连接
    - 2888：集群中 leader 与 follower 通信
    - 3888：集群选举端口
- 默认节点zookeeper、持久化节点
    - config
    - quota
- zookeeper实现服务注册常使用临时顺序节点
    - 服务名为父节点
    - 服务实例为子节点（临时、顺序）
    - 子节点的值为服务实例的ip:port




### 安装目录
```yaml
zookeeper:
    /bin:
        zkCli:
        zkServer:
    /conf:
        configuration.xsl:
        logback.xml:
        zoo_sample.cfg:
    /docs:
    /lib:
```



#### zoo.cfg
```yaml
zoo.cfg:
    clientPort:
    dataDir: # 数据目录
    initLimit:
    server: # 集群节点
    syncLimit:
    tickTime:
```


### zkCli
```yaml
zkCli:
    -server: # 
```

客户端命令行


### zkServer
```yaml
zkServer:
    start:
    status:
    stop:
```

服务端命令工具



## 核心内容
```yaml
zookeeper:
    addauth: # 添加认证信息
        digest: # digest 认证机制,简单的用户名 + 密码的方式（会以哈希存储）
    create: # 创建节点
        digest: # 添加认证信息
            crwda: # 权限标志，每个字母代表一个权限
        -e: # 临时节点
        -s: # 顺序节点
    getAcl: # 获取 ACL 权限信息
    getChildren: # 获取子节点列表
    delete: # 删除节点
    exists: # 检查节点是否存在
        watch:
    get: # 获取节点内容
        watch: # 监听节点
    help: # 显示所有支持命令
    history: # 查看命令历史记录
    ls: # 列出子节点
    ls2: # 同 ls，但带上状态信息
    quit: # 退出客户端
    redo: # 重复执行历史命令
    rmr: # 递归删除节点及其子节点
    set: # 更新节点内容
    setAcl: # 设置 ACL
    stat: # 查看节点状态
    sync: # 同步节点（从 Leader 同步）

四字命令: # ZooKeeper Server 端使用,2181端口
    stat:
```



### ZNode

持久节点（Persistent）：客户端断开后仍存在
临时节点（Ephemeral）：客户端断开即自动删除
顺序节点（Sequential）：ZK 自动在名称后添加序号后缀




### Transaction


#### ZXID

ZooKeeper Transaction ID，事务ID
- 每一个写事务都会生成一个唯一的 ZXID（64位递增整数）
- ZXID 是 ZooKeeper 实现顺序一致性和快照恢复的核心
- 快照、日志回放、Leader 选举都依赖 ZXID




### Cluster


#### ZAB


集群事务执行流程：
1. 所有写操作（事务请求）由 Leader 接收
2. Leader 为每个事务分配一个全局递增的事务 ID（ZXID）
3. Leader 将事务广播给所有 Follower 节点
4. 当半数以上 Follower 反馈 ACK 后，Leader 执行并提交事务
5. 所有节点按顺序应用事务（保证一致性）


## ZooKeeper核心应用

### 分布式锁


核心利用：临时顺序节点


1. 创建临时顺序节点
- 客户端尝试在指定锁目录（如 /locks/mylock）下创建一个临时顺序节点，节点名形如 lock-00000001。

2. 获取锁的判断
- 客户端获取该目录下所有子节点，查看自己创建的节点是否序号最小。

3. 如果是最小节点
- 客户端获得锁，执行临界区代码。

4. 如果不是最小节点
- 监听（watch）比自己序号小的那个节点，一旦该节点被删除（锁被释放），客户端收到通知，再次判断是否成为最小节点，获取锁。

5. 释放锁
执行完成后，客户端删除自己创建的临时顺序节点，释放锁


### 服务注册、发现


1. 服务提供者（服务注册）
- 服务实例启动后，连接 ZooKeeper
- 在 /services/myservice 路径下创建一个临时顺序节点：
- ZooKeeper 自动生成类似 /services/myservice/instance-00000001 的节点
- 该节点是临时的，客户端断开后节点自动删除
- 节点内容通常是服务实例的地址（IP+端口）

2. 服务消费者（服务发现）
- 监听 /services/myservice 目录节点的子节点变化
- 注册监听器（watch）获取节点列表变化事件
- 每当服务注册或注销，客户端收到通知
- 客户端根据子节点内容更新服务列表，实现负载均衡或故障转移




### 配置中心


1. 集中存储配置
- 把配置数据以节点（ZNode）的形式存储在 ZooKeeper 的层级路径中，比如 /config/app1/db_url、/config/app1/timeout。

2. 客户端读取配置
- 应用启动时从 ZooKeeper 读取对应配置节点的数据。

3. 配置动态更新
- 利用 ZooKeeper 的 Watch 机制，客户端监听配置节点，一旦配置变更，ZooKeeper 通知客户端，客户端自动刷新配置。

4. 配置权限控制
- 通过 ACL 机制限制哪些客户端可以读写配置节点