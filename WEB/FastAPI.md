# FastAPI

>
>`FastAPI官方文档：https://fastapi.tiangolo.com/advanced/path-operation-advanced-configuration/`
>
>``

## 基础介绍

WEB项目核心问题：
- 登录功能
    - 权限功能
    - 第三方登录
- 业务CRUD
    - 中间件
    - 数据校验
    - 实体转换
    - 条件查询
    - 分页功能
    - 异常处理
    - 响应转换
- 数据库存储
    - ORM
    - 数据库事务    
    - 并发锁
- 模板引擎
    - Jinja2
- 日志记录
    - 链路追踪
- 文档功能
    - Swagger
- 通信系统
    - Socket
    - WebSocket
    - gRPC
    - GraphQL
- 缓存功能
    - Redis
- 消息队列
    - RabbitMQ
- 定时任务
- 搜索引擎
- 支付系统





内置工具集：Starlette
- @on_event: 事件机制
- @exception_handler: 异常处理
    - HTTPException
- @middleware: 中间件
    - BaseHTTPMiddleware
    - StaticFiles
- @get():
- @post():
    - Request: 请求对象
    - Response: 响应对象
        - FileResponse: 文件响应
        - HTMLResponse: 页面响应
        - RedirectResponse: 重定向
        - StreamingResponse: 二进制流响应
    - File
    - Form: 表单
    - Header
    - Path
    - Query
    - BackgroundTasks: 后台任务(异步) 
- BaseModel: 模型基类(请求参数、响应结果)
    - Field: 字段校验


### 项目结构
```txt
my_project/
│
├── pyproject.toml            # Poetry 配置文件，管理依赖等
├── poetry.lock               # 依赖锁定文件
├── src/                      # 存放源代码
│   └── my_project/           # 主程序包，和项目名称相同
│       ├── __init__.py       # 主程序包的初始化文件
│       ├── main.py           # FastAPI 的入口文件，定义应用和路由
│       ├── api/              # 存放路由相关代码
│       │   ├── __init__.py   # API 包初始化文件
│       │   ├── v1/           # 路由版本目录
│       │   │   ├── __init__.py
│       │   │   ├── endpoints.py  # 路由定义
│       │   │   └── models.py    # 路由相关的 Pydantic 模型
│       │   └── ...           # 其他版本的 API 或其他模块
│       ├── core/             # 存放项目核心逻辑
│       │   ├── __init__.py
│       │   ├── config.py     # 配置文件
│       │   └── security.py   # 安全相关的代码（如 JWT 认证）
│       ├── db/               # 数据库相关文件
│       │   ├── __init__.py
│       │   ├── models.py     # 数据库模型
│       │   └── crud.py       # 数据库操作代码
│       └── tests/            # 测试文件夹
│           ├── __init__.py
│           ├── test_api.py   # API 测试代码
│           └── test_db.py    # 数据库测试代码
├── alembic/                  # 数据库迁移文件（如果使用 Alembic）
├── .gitignore                # Git 忽略文件
├── README.md                 # 项目说明文件
└── Dockerfile                # 如果需要部署容器化，这里是 Docker 配置文件
```

推荐目录结构


### fastapi
```yaml
fastapi:
    dev:
    run:
```


### uvicorn
```yaml
uvicorn:
    --host:
    --log-config:
    --workers:
    --port:
    --reload: # 热重载
```


ASGI服务器：基于Starlette、Pydantic



## 核心内容
```yaml
fastapi:
    encoders:
        jsonable_encoder(): # 类json字典序列化
    exception: # 异常类
        RequestValidationError: # 请求校验异常
            body:
            errors():
    exception_handlers: # 内置异常处理器
        http_exception_handler(): 
        request_validation_exception_handler():
    middleware:
        base:
            BaseHTTPMiddleware:
                dispathc(): # (request, call_next)
        cors:
            CORSMiddleware:
                allow_credentials:
                allow_headers:
                allow_methods:
                allow_origin_regex:
                allow_origins:
                expose_headers:
                max_age:
    responses:
        HTMLResponse: # HTML页面响应
        PlainTextResponse: # 普通文本响应
        RedirectResponse: # 重定向响应类
        StreamingResponse: # 二进制流
            media_type:
    security: # 认证/授权模块
        base:
            SecurityBase:
        oauth2:
            OAuth2:
        OAuth2PasswordBearer: # oauth2 获取Authorization中的token（不带Bearer）
            tokenUrl: # 获取token的endpoint
        OAuth2PasswordRequestForm: # oauth2 password 登录表单（username、password）
            username:
            password:
            scope:
            grant_type:
    staticfiles: # 静态文件
        StaticFiles: # 静态文件挂载
            directory:
    status: # HTTP状态码
        HTTP_201_CREATED:
    templating: # 页面模板
        Jinja2Templates:
            TemplateResponse: # 模板渲染
            directory:
    testclient: # 测试客户端
        TestClient: # 传入app实例
            delete():
            get(): # 路由响应测试
                json():
                status_code():
            post():
            put():
    APIRouter: # 子路由
        dependencies: # 子路由依赖
        prefix:
        tags:
        @get():
        @post():
            response_model: # 响应模型类
            response_model_exclude: # 排除字段
            response_model_exclude_defaults:
            response_model_exclude_none:
            response_model_exclude_unset: # 排除未设置的字段
            response_model_include: # 使用字段
    BackgroundTasks: # 后台任务
        add_task():
    Body: # 请求体参数
        embed: # 内嵌字段
        examples:
        openapi_examples:
            converted:
            invalid:
            normal:
                description:
                summary:
                value:
    Cookie:     
    Depends: # 依赖注入 类型
        use_cache: # 单例注入
    FastAPI: # 项目应用APP
        dependencies: # 全局依赖
        descriptioin: # 项目文档描述
        docs_url: # 关闭doc文档
        redoc_url: # 关闭redoc文档
        state: # 全局应用状态（用于传递全局变量）
        title: # 项目文档标题
        version: # 项目文档版本
        add_exception_handler(): # 全局异常处理
        add_event_handler(): # 全局事件处理
        add_middleware(): # 全局中间件
        inclue_router(): # include子路由
            prefix:
            responses:
            tags:
        mount(): # 挂载子应用（可实现子路由、静态文件）
            name: # 子应用名称
        @exception_handler(): # 异常处理
        @get(): # GET handle
            dependencies: # 依赖
            deprecated: # 过期接口
            description:
            response_class:
            response_description:
            response_model: # 响应模型类
            status_code: # 响应状态码
            summary: # 概述
            tags: # openapi标签（用于文档分组）
        @middleware(): # 中间件
            http:
        @on_event(): # app事件
            startup: # 应用启动时
            shutdown:
        @post(): # POST handle
        @websocket(): # websocket handle
    File: # 文件上传（字节文件）
        default:
        description:
    Form: # form表单
    Header: # header类型标注
        convert_underscores:
    HTTPException: # HTTP异常
        detail:
        headers: # 响应头
        status_code:
    Path: # 路径参数
        title:
    Query: # 请求参数
        alias: # 参数别名
        deprecated: # 字段过期
        description: # 文档描述
        ge: # 大于等于
        gt:
        include_in_schema: # 文档字段包含
        le:
        lt:
        max_length: # 最大长度
        min_length:
        pattern: # 正则匹配
        regex:
        title: # 文档标题
    Request: # 请求对象
        app: # fastapi应用实例引用
        client:
            host:
        headers:
        query_params:
        url:
        form():
        json():
    Response: # 响应对象
        set_cookie():
            key:
            value:
    UploadFile: # 上传文件（对象文件）
        content_type: # 文件类型（MIME）
        file: # python文件对象
        filename: # 文件名（原始） 
        close():
        read():
        seek():
        write():
    Websocket: # websocket
        accept():
        receive_text():
        send_text():

starlette: # ASGI开发工具集
    applications:
        Starlette:
    background:
        BackgroundTask:
    middleware:
        base:
            BaseHTTPMiddleware: # 中间件基类
    requests:
        Request:
    responses:
        FileResponse:
            background: # 响应后置任务
            filename:
        JSONResponse:
        Response:
    routing:
        Route:
    staticfiles: # 静态文件挂载
        StaticFiles:
            directory:
    status:
    templating: # 模板引擎
        Jinja2Templates:
            TemplateResponse: # 页面响应
            directory:

pydantic: # 请求参数映射
    BaseModel: # 参数映射基类
        Config:
            schema_extra:
                example:
        model_config:
            extra:
                forbid: # 禁止多余字段
            json_schema_extra:
                examples: # 请求样例
        dict(): # 获取属性字典
        from_dict(): # 根据字典创建
        model_copy(): # 模型实例复制 
            update: # 模型实例复制更新
        model_dump(): # 获取属性字典
            exclude_unset:
    BaseSettings: # 基础设置
    EmailStr:
    Field: # 字段校验
        default:
        description:
        examples: # 字段样例
        gt:
        max_length:
        title:
    HttpUrl:

sqlmodel: # 官方主推ORM框架
    Field: # 模型字段定义
        default:
        index:
        primary_key:
    Session:
        add():
        commit():
        delete():
        exec():
            all():
        get():
        refresh():
    SQLModel: # 模型基类
        metadata:
            create_all(): #建表
        table: #  data model、table model
        --- # 模型实例
        sqlmodel_update(): # 字段更新
    create_engine(): # 创建引擎 
        connect_args:
            check_same_thread:
    select():
        limit():
        offset():

uvicorn: # ASGI服务器
    run(): # 运行主程序
```

### Request

#### Path Parameters
```python
@app.get("/items/{item_id}")
async def read_item(item_id: int):
    return {"item_id": item_id}
```

path路径参数

##### Path convertor
```yaml
Path convertor:
    path:
```



#### Query Parameters

url请求参数


#### Request Body

body请求体

多结构体请求参数

数据绑定、校验



#### Form

表单参数


#### Cookie

cookie


#### Header

请求头



### Pydantic

数据验证
请求参数映射、响应结果校验


#### BaseModel

数据模型


#### Validation

字段校验



#### Response Model

response_model响应模型、响应结果字段过滤

DTO




### Templates

HTML模板

#### Jinja2Templates
```yaml
jinja2:
    {{  }}: # 模板变量
    {%  %}: # 模板语句
    block ... endblock: # 模板插槽
    extends: # 模板继承
    for ... in ... endfor: # 列表渲染
    if ... elif ... else ... endif: # 条件渲染
    include: # 模板引入
    macro ... endmacro: # 宏函数
    with: # 上下文管理

filter:
    join:
    replace:
    trim:
    upper:
```

##### Filter



##### Macro

宏



### Event

全局事件监听：startup、shutdown





### Middleware
```python
@app.middleware("http")
async def add_process_time_header(request: Request, call_next):
    start_time = time.perf_counter()
    response = await call_next(request)
    process_time = time.perf_counter() - start_time
    response.headers["X-Process-Time"] = str(process_time)
    return response
```
中间件

默认全局中间件
局部中间件只能自定义中间件、子路由依赖


#### Static File

StaticFiles


#### Custom Middleware

BaseHTTPMiddleware







### Error Handler
```python
@app.exception_handler(UnicornException)
async def unicorn_exception_handler(request: Request, exc: UnicornException):
    return JSONResponse(
        status_code=418,
        content={"message": f"Oops! {exc.name} did something. There goes a rainbow..."},
    )
```

异常处理

`@app.exception_handler()`


#### Custom Error

自定义异常













### Dependency Injection
```python
# 类依赖
class CommonQueryParams:
    def __init__(self, q: str | None = None, skip: int = 0, limit: int = 100):
        self.q = q
        self.skip = skip
        self.limit = limit

@app.get("/items/")
async def read_items(commons: CommonQueryParams = Depends(CommonQueryParams)):
    ...

# 装饰器使用依赖
@app.get("/items/", dependencies=[Depends(verify_token)])
async def read_items():
    return [{"item": "Foo"}]
```

- 函数声明（可调用即可）、Depends调用
- 类声明
- path装饰器依赖
- 全局依赖
- yield函数依赖（yield只能用一次、yield后代码在响应发送前被调用）

一个请求中只执行一次（即 请求级单例）
使用依赖注入可实现参数预处理、子路由中间件

依赖yield退出代码，在中间件后面执行




### Background Task

BackgroundTasks
后台任务、异步执行



### Swagger

`/docs`: swagger文档链接
`/openapi.json`: OpenAPI的Schema json文档


####  ReDoc
`/redoc`: redoc文档链接


### Security

#### OAuth2

OAuth2登录简化流程
```
[1] 用户点击“用GitHub登录” →
[2] 重定向到 GitHub 授权页面 →
[3] 用户授权后 GitHub 重定向回你的服务端 →
[4] 服务端获取 code，换取 access_token →
[5] 使用 access_token 拉取用户信息（如用户名、邮箱） →
[6] 应用登录或注册该用户
```


Github OAuth2登录流程
1. 注册 GitHub OAuth App
    - 填写Callback URL
    - 得到 client_id 和 client_secret
2. 服务端实现 OAuth2 登录
    - 实现login接口：携带client_id客户端id，重定向到 GitHub登录页面
    - 实现Callback接口
        - 携带client_id、client_secret、code(刚刚获取)，请求获取access_token
        - 携带access_token获取用户信息
        - 完成登录




### SQLModel

fastapi作者推出的ORM框架、基于sqlalchemy



#### Model



#### Session



#### Engine




## 第三方集成


### Tortoise ORM

