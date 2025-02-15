# FastAPI

>
>`FastAPI官方文档：https://fastapi.tiangolo.com/tutorial/middleware/`
>

## 基础介绍

内置工具集：Starlette



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
        cors:
            CORSMiddleware:
    responses:
        HTMLResponse: # HTML页面响应
        PlainTextResponse: # 普通文本响应
        RedirectResponse: # 重定向响应类
        StreamingResponse:
            media_type:
    security: # 认证/授权模块
        base:
            SecurityBase:
        oauth2:
            OAuth2:
        OAuth2PasswordBearer:
            tokenUrl:
        OAuth2PasswordRequestForm:
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
            directory:
            TemplateResponse:
    APIRouter: # 子路由
        prefix:
        tags:
        @get():
        @post():
            response_model: # 响应模型类
            response_model_exclude_defaults:
            response_model_exclude_none:
            response_model_exclude_unset:
            response_model_include:
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
        title: # 项目文档标题
        version: # 项目文档版本
        add_middleware(): # 添加中间件
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
            summary:
            tags: # openapi标签（用于文档分组）
        @middleware(): # 中间件
            http:
        @on_event(): # app事件
            startup:
        @post(): # POST handle
        @websocket(): # websocket handle
    File: # 文件上传（类型位置标注）
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
        headers:
        query_params:
        form():
        json():
    Response: # 响应对象
        set_cookie():
            key:
            value:
    UploadFile: # 上传文件
        content_type: # 文件类型（MIME）
        file: # python文件对象
        filename: # 文件名（原始） 
        close():
        read():
        seek():
        write():

starlette: # ASGI开发工具集
    applications:
        Starlette:
    background:
        BackgroundTask:
    middleware:
        base:
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
        model_copy(): # 模型实例复制 
            update: # 模型实例复制更新
        model_dump(): # 获取属性字典
            exclude_unset:
    EmailStr:
    Field: # 字段校验
        default:
        description:
        examples: # 字段样例
        gt:
        max_length:
        title:
    HttpUrl:

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


#### Cookie


#### Header



### Pydantic

请求参数映射

数据验证


#### Response Model

响应模型、响应结果字段过滤


### Templates

HTML模板



### Event

事件监听

### Middleware

中间件


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

使用依赖注入可实现参数预处理





### Swagger

`/docs`: swagger文档链接
`/openapi.json`: OpenAPI的Schema json文档


####  ReDoc
`/redoc`: redoc文档链接


### Security

#### OAuth2