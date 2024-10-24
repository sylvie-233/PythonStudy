# Flask

>
> `#TODO Flask官方文档：https://flask.palletsprojects.com/en/latest/quickstart/#about-responses`
>

## 基础介绍


轻量级WSGI框架 


Flask默认5000端口


flask_sqlalchemy只提供Engine、Model、Session，表字段定义仍为原框架SQLAlchemy

flask_login提供登录管理LoginManager、用户模型UserMixin

flask_wtf提供了表单页面、表单模型类、表单字段校验



### 开发目录结构
```yaml
flask:
    /models:
    /routes:
    /services:
    /static:
    /templates:
    app.py:
```







### flask
```yaml
flask:
    --app: 指定主模块
    --debug: 开发模式
    --host: 指定ip（公网ip：0.0.0.0）
    run: 运行
```



## 核心内容
```yaml
flask:
    wrappers:
        Request:
        Response: # 响应对象
            set_cookie():
    Blueprint: # 蓝图（子路由）
    Flask: # 主应用
        config:
            SECRET_KEY:
            SQLALCHEMY_DATABASE_URI:
        static_folder:
        static_url_path:
        template_folders:
        after_request():
        before_first_request():
        before_request():
        errorhandler(): # 错误处理
        get():
        post():
        register_blueprint(): # 注册蓝图
        request_context():
        route():
            methods:
        run(): # 运行
            debug:
            port:
        send_static_file():
        teardown_request():
        test_request_context(): # 测试请求上下文
    request: # 全局请求对象
        args:
        cookies:
        files:
        form:
        method:
        path:
    session:
    abort():
    flash():
        category:
    make_response(): # 生成响应对象
    redirect(): # 重定向
    render_template(): # 模板渲染
    url_for(): # url反向引用

flask_restful:
    fields: # 序列化字段定义
        String:
    inputs: # 输入检验方法
        int_range():
        regex():
    reqparse:
        RequestParser: # 请求参数解析器
            add_argument():
                action: # 同名参数处理
                help:
                location:
                required:
                type:
            parse_args():
    Api:
        add_resource(): # 资源路由注册
            endpoint: # 路由命名
        representation(): # 响应数据处理
    Resource:
        method_decorators: # 装饰器(中间件)
        get():
        set():
    marshal_with(): # Resource响应序列化定义

flask_sqlalchemy:
    SQLAlchemy:
        Model: # 模型基类
        session: # 会话
            get():

flask_migrate:


flask_login:
    LoginManager:
        user_loader():
    UserMixin:
        is_authenticated:
    current_user: 当前用户
    login_required(): 登录拦截
    login_user(): 用户登录
    logout_user(): 用户登出

flask_wtf:
    FlaskForm: # 表单组件
        csrf_token():
        hidden_tag(): csrf
        validate_on_submit():
        
wtforms:
    validators:
        DataRequired:
    HiddenField:
        value():
    PasswordField: 
    StringField:
        class:
        data:
        label:
        placeholder:
        validators: 字段校验器
        label():
    SubmitField:

flask_mail:

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
- `{%  %}`
- `block`
- `extends`
- `if`
- `include`
- `for in`
- `with`


内置模板变量：
```yaml
:
    config:
    current_user: flask_login混入进来的UserMixin
        is_authenticated:
    g:
    request:
    session:
    get_flashed_messages(): 获取flash消息
        with_categories: 消息类别
    url_for():
```


内置过滤器：
```yaml
:
    safe:
```





### 错误处理



### 页面组件


wtforms






### 日志



### 信号




### 测试





### 命令行工具





