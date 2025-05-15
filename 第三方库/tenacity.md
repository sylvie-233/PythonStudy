# tenacity


## 基础介绍

一个强大且灵活的 Python 重试（retry）库
用于自动处理临时失败（如网络超时、服务不稳定等）
可以让你优雅地为函数添加 失败重试机制，并支持配置重试次数、间隔、异常类型、退避策略等

## 核心内容
```yaml
tenacity:
    retry_if_exception_type():
    retry_if_result():
    stop_after_attempt():
    stop_after_delay():
    wait_exponential():
    wait_fixed():
    wait_random():
    @retry:
        after: # hook
        before: # hook
        before_sleep:
        retry:
        retry_error_callback:
        stop:
        wait:
```