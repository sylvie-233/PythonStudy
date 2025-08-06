# pybreaker


## 基础介绍


实现断路器（Circuit Breaker）模式 的一个库，用于防止雪崩式故障
pybreaker 会监控函数调用失败情况，若连续失败次数超过阈值，则“断开电路”，在一段时间内拒绝调用，从而避免系统资源浪费和连锁故障。


断路器状态：
- Closed（闭合）：一切正常，允许请求。若失败超过阈值 → Open
- Open（打开）：所有请求立即失败，不再调用函数。等待超时后 → Half-Open
- Half-Open（半开）：允许少量请求试探成功率，成功 → Closed，失败 → Open


## 核心内容
```yaml
pybreaker:
    CircuitBreaker: # 
        exclude:
        expected_exception:
        fail_max:
        listeners:
        reset_timeout:
        ---
        close():
        half_open():
        open():
    CircuitBreakerListener:
        state_change():
```