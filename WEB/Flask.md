# Flask

>
> `#TODO Flask官方文档：https://flask.palletsprojects.com/en/latest/quickstart/#about-responses`
>

## 基础介绍


轻量级WSGI框架 


Flask默认5000端口







### flask
```yaml
flask:
    --app: 指定主模块
    --debug: 开发模式
    --host: 指定ip（公网ip：0.0.0.0）
    run:
```



## 核心内容
```yaml
flask:
    wrappers:
        Request:
        Response: 响应对象
            set_cookie():
    Blueprint:
    Flask:
        errorhandler(): 错误处理
        get():
        post():
        request_context():
        route():
            methods:
        run(): 运行
            debug:
            port:
        test_request_context(): 测试请求上下文
    request: 全局请求对象
        args:
        cookies:
        files:
        form:
        method:
        path:

    session:
    abort():
    make_response(): 生成响应对象
    redirect(): 重定向
    render_template(): 模板渲染
    url_for(): url反向引用


markupsafe:
    Markup:
        escape():
        striptags():
```

### Route

url变量converter：
- int
- float
- string
- path
- uuid



### Blueprint





### 页面模板

Jinja2模板引擎

模板语法：
- `{{ var }}`
- `if`、`else`、`endif`


内置模板变量：
```yaml
:
    config:
    g:
    request:
    session:
    get_flashed_messages():
    url_for():
```


内置过滤器：
```yaml
:
    safe:
```





### 错误处理


### 日志



### 信号




### 测试





### 命令行工具





