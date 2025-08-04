# python-consul



## 基础介绍

Consul SDK




## 核心内容
```yaml
consul:
    Check: # Consul 服务健康检查
        tcp():
            interval:
            timeout:
    Consul: # Consul客户端
        agent: # Agent
            service: # Service
                deregister():
                register():
                    address:
                    check: # 健康检查配置
                    name: # 服务名称
                    port:
                    service_id: # 服务唯一id
                    tags:
                    ---
        health: # Health
            service(): # 获取所有健康的 my-service 实例
        kv: # KV
            get():
                index:
```