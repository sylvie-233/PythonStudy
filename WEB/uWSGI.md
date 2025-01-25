# uWSGI


## 基础介绍

Python Web Server Gateway Interface

WSGI、uwsgi协议实现


### uwsgi
```yaml
uwsgi:
    --ini: # 指定配置文件
    --reload:
    --stop:
```

#### iwsgi.ini
```yaml
uwsgi:
    callable: # application变量名
    chdir: # 项目目录
    daemonize: # 后台运行日志
    http: # 同socket
    pidfile:
    process: # 进程数
    socket: # ip port
    stats: # uwsgi服务运行信息 ip port
    threads: # 线程数
    wsgi-file: # 启动文件（入口文件）
```


## 核心内容