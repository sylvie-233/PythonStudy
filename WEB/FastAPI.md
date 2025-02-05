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
    Body: # 请求体参数校验
    Cookie:     
    FastAPI: # 项目应用APP
        descriptioin:
        title:
        version:
        add_middleware(): # 添加中间件
        get(): # GET handle
            description:
            response_class:
            response_model: # 响应模型类
            summary:
            tags: # 标签
        inclue_router(): # include子路由
        middleware(): # 中间件
        mount(): # 挂载子应用（可实现子路由）
        post(): # POST handle
        websocket(): # websocket handle
    File:
    Form: # 请求体校验
    Header:
    Path: # 路径参数校验
    Query: # 请求参数校验
        alias: # 参数别名
        description:
        ge:
        max_length: 
        regex:
        title:
    Request:
    Response:
        set_cookie():
            key:
            value:
    UploadFile:
        content_type:
        file:
        filename:
        close():
        read():
        seek():
        write():



pydantic: # 请求参数映射
    BaseModel: # 参数映射基类
        Config:
            schema_extra:
                example:
        dict(): # 获取属性字典
    Field:

starlette: # ASGI开发工具集
    middleware:
        base:
    responses:

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

数据绑定、校验


#### Form


#### Cookie


#### Header



### Pydantic

请求参数映射

数据验证



### Templates

HTML模板


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