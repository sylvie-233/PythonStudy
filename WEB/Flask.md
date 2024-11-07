# Flask

>
> `#TODO Flask官方文档：https://flask.palletsprojects.com/en/latest/quickstart/#about-responses`
>
>
>
>

## 基础介绍


轻量级WSGI框架 

werkzeug提供基础套件


Flask默认5000端口


flask_sqlalchemy只提供Engine、Model、Session，表字段定义仍为原框架SQLAlchemy

flask_login提供登录管理LoginManager、用户模型UserMixin

flask_wtf提供了表单页面、表单模型类、表单字段校验



### 项目结构
```yaml
flask:
    /migrations: # 数据库迁移
        /versions:
        alembic.ini:
        env.py:
        scrip.py.mako:
    /models: # 模型文件
    /routes:
    /services:
    /static: # 静态文件
    /templates: # 模板页面
    app.py:
    config.py:
```







### flask
```yaml
flask:
    --app: 指定主模块
    --debug: 开发模式
    --host: 指定ip（公网ip：0.0.0.0）
    db:
        init:
        migrate: # 生成数据库迁移文件
        upgrade: # 数据库迁移 
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
        url_prefix: # 子路由url
        @route():
    Flask: # 主应用
        config: # 应用配置
            MAIL_SERVER:
            SECRET_KEY: # 秘钥（session使用）
            SQLALCHEMY_DATABASE_URI: # 数据库信息
            from_object():
        static_folder:
        static_url_path:
        template_folders:
        @after_request():
        @before_first_request():
        @before_request():
        @context_processor(): # 模板上下文处理器（返回上下文变量）
        @errorhandler(): # 错误处理
        @get():
        @post():
        @route():
            methods:
        add_template_filter(): # 添加过滤器
        app_context(): # 应用上下文
        register_blueprint(): # 注册蓝图
        request_context():
        run(): # 服务运行
            debug: # 调试模式
            host: # 主机名
            port:
        send_static_file():
        teardown_request():
        test_request_context(): # 测试请求上下文
    g: # app全局对象
    request: # 全局请求对象
        args: # query参数
            get():
        cookies:
        files:
        form: # 表单参数
        method:
        path:
    session: # flask的session经过加密存储在客户端cookie中
        clear():
        get():
    abort():
    flash(): # 一次性传递上下文变量
        category:
    jsonify():
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
    query:
        Query:
            all():
            filter_by():
            first():
            get():
            order_by():
    SQLAlchemy: # db
        Column: # 模型字段
            autoincrement:
            default:
            nullable:
            primary_key:
            unique:
            desc():
        DateTime:
        ForeignKey: # 外键字段
        Integer:
        Model: # 模型基类
            __tablename__: 表名
            query: # 查询对象
        String:
        Text:
        engine: # 数据库引擎
        session: # 会话（操作对象）
            add():
            add_all():
            commit():
            delete():
            get():
        backref(): # 反向引用
            order_by:
        create_all(): # 创建表
        init_app(): # 从APP中读取配置，初始化引擎
        relationship(): # 定义关联字段（直接操作外键对象）
            back_popolates: # 定义反向引用字段
            backref:
flask_migrate:
    Migrate: # 数据库迁移类

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
    validators: # 校验器
        DataRequired:
        Email:
            message:
        EqualTo:
        Length:
            max:
            min:
    Form: # 表单基类（页面组件渲染、表单字段校验）
        errors:
        validate(): # 表单校验
        validate_[field]():
    HiddenField:
        value():
    PasswordField: 
    StringField: # 字符串字段
        class:
        data: # 字段值
        label:
        placeholder:
        validators: # 字段校验器
        label():
    SubmitField:
    ValidationError: # 字段校验异常
        message:

flask_mail:
    Mail: # 邮箱工具类
        init_app(): # 初始化邮箱（和sqlalchemy一样）
        send():
    Message: # 消息类
        recipients:
        subject:

markupsafe:
    Markup:
        escape():
        striptags():
```

### Route

url_path路径参数converter：
- int
- float
- string
- path
- uuid

query查询参数




### Blueprint

子路由实现




### SQLAlchemy

ORM框架

db -> engine -> connection -> cursor

db -> Model -> session

`app.config[SQLALCHEMY_DATABASE_URI]`：配置数据库链接

反向引用：一对多




### 页面模板

Jinja2模板引擎

#### 模板语法：
- `{{ var }}`: 模板变量
- `{%  %}`: 模板语句
- `block | endblock`: 模板插槽
- `extends`: 模板继承
- `if | elif | else | endif`
- `include`
- `for in | endfor`
- `with`


#### 内置模板变量：
```yaml
:
    config:
    current_user: # flask_login混入进来的UserMixin
        is_authenticated:
    g:
    request:
    session:
    get_flashed_messages(): # 获取flash消息
        with_categories: # 消息类别
    url_for(): # 反向引用
```


#### 内置过滤器：
```yaml
:
    abs:
    length:
    safe:
```

自定义过滤器
```python
def my_filter(value, args):
    return xxx

app.add_template_filter(my_filter, "my_filter")
```



### 错误处理

`@errorhandle()`



### 页面组件


wtforms

flask_wtf

wtforms自定义字段校验



### 信号


### 命令行工具




### 日志





### 测试










