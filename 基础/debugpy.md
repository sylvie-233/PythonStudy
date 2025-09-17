# debugpy


## 基础介绍

python远程调试


### launch.json
```yaml
launch.json:
    name:
    type:
        python:
    request:
        attach:
    connect:
        host: 
        port: 
    pathMappings: 
        localRoot: # 本地目录
        remoteRoot: # 远程项目目录
```


## 核心内容
```yaml
debugpy:
    breakpoint():
    listen():
    wait_for_client():
```