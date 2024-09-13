# FastAPI

## 基础介绍


### uvicorn
```yaml
uvicorn:
    --host:
    --port:
    --reload: # 热重载
```


ASGI服务器



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
    BackgroundTasks: # 后台任务
        add_task():
    Body: # 请求体参数校验
    Cookie:     
    FastAPI: # 项目应用
        descriptioin:
        title:
        version:
        add_middleware(): # 添加中间件
        get():
            description:
            response_class:
            response_model: # 响应模型类
            summary:
            tags: # 标签
        middleware(): # 中间件
        mount(): # 挂载目录
        post():
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

uvicorn: # ASGI服务器
    run(): # 运行主程序

pydantic: # 请求参数映射
    BaseModel: # 参数映射基类
        Config:
            schema_extra:
                example:
        dict():
    Field:
```


### Pydantic

请求参数映射




### Swagger

`/docs`: swagger文档链接