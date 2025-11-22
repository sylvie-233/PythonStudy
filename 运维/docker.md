# Docker

## 基础介绍


Layers层、Cache缓存

没指定镜像版本时，默认tag为最新latest


- docker run = docker create + docker start

### docker
```yaml
docker:
    -v: # 版本
    build: # 构建镜像
        -f:
        -t: # 设置tag、版本镜像
    commit: # 容器打包镜像
        -c:
    compose: # 批量编排
        -d: # 后台运行
        -f: # 指定配置文件
        down:
        exec:
        logs:
        ps:
        restart:
        start:
        stop:
        top:
        up:
    create: # 创建容器
    exec: # 在运行中的Docker容器内执行命令
        -d: # 后台执行命令
        -i: # 打开控制台接收用户输入
        -t: # 分配一个虚拟的终端或控制台，可以让容器持续运行不会关闭
        -u: # 以指定用户运行
    image: # 镜像管理
        ls:
    images: # 查看镜像
    inspect: # 查看容器信息
    kill: # 停止运行容器（立即关闭）
    load: # 从本地文件中加载镜像
        -i:
    login:
    logs: # 查看容器运行日志
        -f:
    network: # 网络管理
        connect: # 使指定容器加 入某网络
        create: # 创建网络
        disconnect: # 使指定容器离开某网络
        inspect: # 查看网络详细信息
        ls:
        prune:
        rm:
    ps: # 查看运行容器
        -a:
        --format: # 指定输出格式
    pull: # 下载镜像
    push: # 上传镜像
    restart: # 重启容器
    rm: # 删除容器
        -f:
    rmi: # 删除镜像
    run: # 创建、运行容器
        -d: # 后台运行
        -e: # 环境变量
        -p: # 端口映射 主机端口:容器端口
        -v: # 目录挂载 主机目录:容器目录
        --log-driver: # 日志驱动
        --log-opt:
        --name: # 容器名称
        --network:
    save: # 保存镜像为本地文件
        -o:
    start: # 启动容器
        -a:
    stop: # 暂停容器
    system: #
        prune: # 清空所有未使用资源
    volume: # 数据卷
        create:
        inspect:
        ls:
        prune:
        rm:
```


#### Dockerfile
```yaml
Dockerfile:
    FROM: # 镜像继承
    ENV: # 环境变量
    WORKDIR: # 默认镜像内工作目录
    COPY: # 拷贝本地文件进入容器
    ADD: # 拷贝本地文件进入容器，自动解压
    RUN: # 构建过程中执行命令
    CMD: # 最终执行命令
    ENTRYPOINT: # 镜像运行入口、容器默认执行命令
    EXPOSE: # 容器端口暴露
```


#### docker-compose.yml
```yaml
docker-compose.yml:
    networks: # 网络列表
        name:
    services: # 服务列表
        build: # 镜像构建配置
            context: # 上下文（当前目录）
            dockerfile: # 构建配置文件
        command: # 
        container_name: # 容器名
        depends_on: # 容器运行顺序依赖
        environment: # 环境变量
        image: # 镜像
        networks: # 网络
        ports: # 端口
        restart: # 
        volumes: # 数据卷
    version:
```



## 核心内容


### Image


### Container



### Volume

数据卷


### Network

默认情况下，所有容器都是以bridge方式连接到Docker的一个虚拟网桥上面（docker0）


- Bridge:
- Host:
- None:


### Log

Docker 容器的日志主要来自两个地方：
1. 标准输出（stdout）
2. 标准错误（stderr）

默认日志驱动是 json-file，Docker 会将每个容器的 stdout/stderr 写入一个 JSON 格式的文件



#### Logging Driver

Docker 可以通过 日志驱动将容器日志输出到不同目的地
- json-file	默认驱动，写 JSON 文件	无依赖，简单	单机或开发环境
- syslog	写到宿主机 syslog	兼容传统系统	Linux 服务器
- journald	写到 systemd 日志	集中管理	systemd 系统
- fluentd	发送到 Fluentd 收集器	集中收集，支持多输出	生产环境
- gelf	发送到 Graylog Extended Log Format	便于 Graylog 使用	企业日志系统
- awslogs	发送到 AWS CloudWatch	云环境	AWS 云应用
- splunk	发送到 Splunk	企业监控	企业环境


### Docker Compose

Project -> Service -> Container





### Docker Desktop

Docker桌面程序

