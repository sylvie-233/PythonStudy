# ETCD


## 基础介绍

一个分布式的键值存储系统，用于配置共享、服务注册发现等
- 支持强一致性（Raft 协议）
- Watch 机制（可监听 key 的变动）
- 支持 gRPC、HTTP 接口
- 常用于 Kubernetes、APISIX、Consul 等系统的底层存储



etcd核心概念：
- Key-Value：etcd以键值对存储
- Lease：支持“临时键”（TTL），用于服务注册
- Watch：实时监听 key 的变更
- Revision：所有变更都有版本号，可回滚
- Cluster：多节点组成集群（Raft）
- Member：每个 etcd 实例就是一个 Member
- Role/User：支持权限认证和 RBAC 管理


### etcdctl
```yaml
etcdctl:
    del:
    endpoint:
        status: # 查看集群状态
    get:
        --endpoints:
        --prefix:
    lease: # TTL
        grant: # 设置 过时 租约
        revoke: # 撤销
    member:
        list: # 成员列表
    put:
    role: # 角色
        add:
    snapshot: # 
        restore: # 恢复快照
        save: # 快照备份
    user: # 用户
        add:
    watch:
```


### api-http:
```yaml
etcd:
    /v3:
        /kv/put: # 写入键值
        /kv/range: # 查询键值
```


## 核心内容
```yaml

```