# nacos-sdk-python


## 基础介绍


python Nacos服务发现、注册、配置管理操作库


## 核心内容
```yaml
nacos:
    NacosClient: # nacos客户端
        add_naming_instance(): # 服务注册
        add_config_watcher(): # 配置监听
        get_config(): # 获取配置
        list_naming_instance(): # 服务发现（查询服务）    
        publish_config(): # 发布配置
        remove_naming_instance(): # 注销服务
        send_heartbeat(): # 手动发送心跳
```