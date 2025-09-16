# werkzeug

>
> `#TODO https://werkzeug.palletsprojects.com/en/3.0.x/`
>

## 基础介绍



## 核心内容
```yaml
werkzeug:
    exceptions:
        HTTPException:
        NotFound:
    middleware:
        shared_data:
            SharedDataMiddleware:
    routing:
        Map:
            bind_to_environ():
            match():
        Rule:
            endpoint:
    security:
        check_password_hash():
        gen_salt():
        generate_password_hash():
    serving:
        run_simple(): # 服务运行
            use_debugger:
            use_relaoder:
    urls:
        url_parse():
    utils:
        redirect:
    wrappers:
        Request:
            args:
            environ:
            form:
            method:
        Response:
            mimetype:
```

