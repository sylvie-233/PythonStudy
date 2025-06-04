# slowapi


## 基础介绍

实现请求速率限制（Rate Limiting）
通常用于控制 Web 应用或 API 的访问频率，以避免过载或滥用
通常与 FastAPI 一起使用



## 核心内容
```yaml
slowapi:
    storage:
        RedisStorage:
    util:
        get_remote_address():
    Limiter:
        storage:
        @limit():
```