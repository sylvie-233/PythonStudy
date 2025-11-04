# jaeger


## 基础介绍

链路追踪中间件


Docker Compose安装：
```yaml
name: sylvie233-pythontest
version: '3.8'

services:
  jaeger:
    image: jaegertracing/all-in-one:latest
    container_name: jaeger
    ports:
      - "16686:16686"  # Jaeger UI
      - "4318:4318"    # OTLP HTTP 接收端口
      - "4317:4317"    # OTLP gRPC 接收端口
    environment:
      COLLECTOR_ZIPKIN_HTTP_PORT: 9411
    networks:
      - sylvie233-network
    restart: unless-stopped

networks:
  sylvie233-network:
    driver: bridge
```



## 核心内容
```yaml
```

### Context

#### Trace

#### Span





## Jaeger UI


### Search

Trace轨迹搜索


### Compare

Trace轨迹比较

### System Architecture
### Monitor