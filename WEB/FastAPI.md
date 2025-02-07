# FastAPI

>
>`FastAPI官方文档：https://fastapi.tiangolo.com/tutorial/query-params-str-validations/`
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
    middleware:
        cors:
            CORSMiddleware:
    responses:
        HTMLResponse:
        RedirectResponse:
        StreamingResponse:
            media_type:
    staticfiles:
        StaticFiles:
    templating:
        Jinja2Templates:
            directory:
            TemplateResponse():
    APIRouter: # 子路由
        prefix:
        tags:
        get():
        post():
    BackgroundTasks: # 后台任务
        add_task():
    Body: # 请求体参数
    Cookie:     
    Depends:
    FastAPI: # 项目应用APP
        descriptioin: # 项目文档描述
        title: # 项目文档标题
        version: # 项目文档版本
        add_middleware(): # 添加中间件
        get(): # GET handle
            description:
            response_class:
            response_model: # 响应模型类
            summary:
            tags: # 标签
        inclue_router(): # include子路由
            prefix:
            responses:
            tags:
        middleware(): # 中间件
            http:
        mount(): # 挂载子应用（可实现子路由、静态文件）
            name:
        on_event():
            startup:
        post(): # POST handle
        websocket(): # websocket handle
    File: # 文件上传
        default:
    Form: # 请求体校验
    Header:
    HTTPException:
    Path: # 路径参数校验
    Query: # 请求参数校验
        alias: # 参数别名
        description:
        ge:
        max_length: 
        regex:
        title:
    Request:
        headers:
    Response:
        set_cookie():
            key:
            value:
    UploadFile: # 上传文件
        content_type: # 文件类型
        file: # python文件对象
        filename: # 文件名 
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
        dict(): # 获取属性字典
    Field:

uvicorn: # ASGI服务器
    run(): # 运行主程序

typing_extensions:
    Annotated: # 注解
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



### Templates

HTML模板



### Event

事件监听

### Middleware

中间件


### Error Handler

异常处理


### Dependency Injection








### Swagger

`/docs`: swagger文档链接
`/openapi.json`: OpenAPI的Schema json文档


####  ReDoc
`/redoc`: redoc文档链接


### Security

#### OAuth2