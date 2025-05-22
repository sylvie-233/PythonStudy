# Nginx



## 基础介绍

Nginx（Engine X） 是一个高性能的 HTTP 和反向代理服务器，同时也是一个 IMAP/POP3/SMTP 邮件代理服务器

Nginx核心应用：
- 静态资源服务器
- 负载均衡
- 反向代理
- 网关

### 安装目录
```yaml
nginx:
    /conf:
        nginx.conf:
    /contrib:
    /docs:
    /html:
        index.html:
    /logs:
    /temp:
    nginx.exe:
```

#### nginx.conf
```yaml
nginx.conf:
    error_log: # 错误日志路径与级别
    events: # 连接处理
        multi_accept:
        use: # 连接技术
        worker_connections: # 每个 worker 可同时处理的最大连接数
    http: # http协议
        access_log: # 访问日志路径
        default_type: # 默认 MIME 类型
        gzip: # 启用 gzip 压缩
        gzip_types: # 指定压缩类型
        include: # 导入其它配置文件
        keepalive_timeout: # HTTP 长连接保持时间
        log_format: # 日志格式
        sendfile: # 启用高效文件传输
        server: # http服务配置，可配置多个
            index: # 首页
            listen: # 监听端口 
            location: # 路由配置，可配置多个（= 精确匹配、^~ 匹配前缀并终止后续匹配、~ 正则匹配区分大小写、~* 正则匹配忽略大小写）
                expires: # 缓存过期
                index:
                proxy_pass:
                proxy_set_header:
                rewrite: # url重写  
                root: 
                try_files: # 尝试多个路径
            root: # 根目录
            server_name: # 域名
            ssl_certificate: # ssl证书
            ssl_certificate_key: # ssl密钥
        tcp_nopush:
        upstream: # 负载均衡策略
            server: # 负载均衡 ip:port    
    pid: # PID 文件路径
    worker_processes: # 工作进程数
    user: # # 指定运行 Nginx 的用户和用户组
```



### nginx
```yaml
nginx:
    -s:
        quit: # 优雅停止
        reload: # 重启
        stop: # 停止
    -t: # 测试配置文件是否有误
    -v:
    -V: # 详细版本信息
```

nginx启动命令


## 核心内容
