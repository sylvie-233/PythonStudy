# Kazoo



## 基础介绍

python zookeeper库


## 核心内容
```yaml
kazoo:
    client: # 客户端
        KazooClient: # 客户端
            hosts: # 主机地址 ip port
            ---
            @DataWatch: # 节点监听 (data, stat, event)
                data:
                stat:
                event:
                    type:
                    path:
            close(): # 关闭连接
            create(): # 创建节点（默认永久节点）
                ephemeral: # 临时节点
                sequence: # 有序节点
                value:    
            exists(): # 节点存在 stat(ZnodeStat)
                ---
                stat:
                    ephemeralOwner: # 0 → 普通持久节点（Persistent）、非 0 → 临时节点（Ephemeral）
            get(): # 获取节点 data, stat
                data:
                stat:
            get_children(): # 获取子节点
                watch:
            set(): # 设置节点
            start(): # 开始连接
            stop(): # 停止连接
    exceptions: # 异常
        NodeExistsError:
        NoNodeError:
    recipe:
        lock:
            Lock: # 分布式锁，上下文管理
```