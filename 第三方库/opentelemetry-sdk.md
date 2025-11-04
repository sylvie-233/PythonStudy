# opentelemetry-sdk


## 基础介绍

OpenTelemetry（简称 OTel）是一个云原生、厂商中立的可观测性框架
提供了一组统一的 API、库、代理和收集器服务，用于采集、生成和导出遥测数据
- 链路追踪（Traces）： 单个请求在分布式系统中流转的完整路径 
- 指标（Metrics）： 系统的数值度量，如 QPS、错误率、延迟等
- 日志（Logs）： 离散的事件记录

OTel 的目标是取代旧的、分裂的遥测方案（如 OpenTracing 和 OpenCensus），成为可观测性数据采集的全球标准

OpenTelemetry核心概念：
- Trace: 代表一个事务或工作流在分布式系统中的完整生命周期。它由一个 TraceId 唯一标识
- Span: Trace 中的一个独立操作单元。它有一个 SpanId，包含名称、时间戳、事件、属性等。一个 Trace 由一个或多个 Span 组成
- Context Propagation: 在服务之间传递 TraceId 和 SpanId 等上下文信息，以便将多个服务的 Span 关联到同一个 Trace 中


pip包：
- opentelemetry-api
- opentelemetry-sdk
- opentelemetry-instrumentation-fastapi
- opentelemetry-exporter-jaeger
- `opentelemetry-exporter-otlp[grpc]`


- instrumentation -> resource -> tracer_provider -> tracer -> span_processor -> exporter
- HTTP headers传递trace信息


## 核心内容
```yaml
opentelemetry:
    exporter: # 导出器
        jaeger:
            thrift:
                JaegerExporter: # 导出到jaeger
                    agent_host_name:
                    agent_port:
    instrumentation: # 系统集成
        fastapi:
            FastAPIInstrumentor:
        httpx:
    sdk:
        resources:
            Resource: # resource
            SERVICE_NAME:
            SERVICE_VERSION:
        trace:
            export:
                BatchSpanProcessor:
            TracerProvider: # trace-provider
    trace:
        get_tracer(): # 获取tracer
            start_as_current_span(): # 创建span
                set_attribute(): # 设置属性
        get_tracer_provider(): # 
        set_tracer_provider(): # 设置provider
```