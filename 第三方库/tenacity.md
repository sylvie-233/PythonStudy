# tenacity


## 基础介绍

一个强大且灵活的 Python 重试（retry）库
用于自动处理临时失败（如网络超时、服务不稳定等）
可以让你优雅地为函数添加 失败重试机制，并支持配置重试次数、间隔、异常类型、退避策略等

## 核心内容
```yaml
tenacity:
    @retry: # 异常触发重试
        after: # hook
        before: # hook
        before_sleep:
        reraise: # 所有重试失败后是否抛出最后一次异常
        retry: # 设置什么样的异常或条件需要重试
        retry_error_callback: # 所有重试都失败后，调用的函数
        stop: # 设置什么时候停止重试（如重试几次或总时间）
        wait: # 设置每次重试之间的等待时间
    after_log():
    before_log():
    retry_if_exception_type(): # retry 只对特定异常重试
    retry_if_result():
    stop_after_attempt(): # stop 限定最多重试次数
    stop_after_delay():
    wait_exponential(): # wait 指数退避策略
    wait_fixed(): # wait 固定等待时间
    wait_random():
```