# Prometheus

## 基础介绍


服务监控系统、时间序列服务器

`/metrics`独立路由api

核心数据：时间序列、每个时间序列由唯一的指标名称和一组标签 来标识
指标类型：
- Counter：只增不减的计数器
- Gauge：可增可减的仪表盘
- Histogram：直方图
- Summary：与 Histogram 类似，用于计算分位数

Exporters(Client Libraries、Pushgateway、Service Discovery) -> Prometheus Server(TSDB) -> Grafana(AlertManager)
![prometheus架构](../.assets/prometheus架构.svg)
核心组件：
- Prometheus Server：
    - Retrieval：负责抓取目标上的指标
    - TSDB：内置的时序数据库，用于存储抓取到的指标数据
    - HTTP Server：提供 PromQL 查询接口和 Web UI
- Client Libraries：官方或第三方提供的客户端库、在应用程序代码中嵌入这些库来定义和暴露指标
- Exporters：导出器、当应用程序本身无法直接提供 Prometheus 格式的指标时（如监控 Linux 主机、MySQL、Nginx），使用 Exporter 作为“翻译官”。它从目标应用收集原生数据，并将其转换为 Prometheus 可识别的格式
- Service Discovery：服务发现、Prometheus 支持从各种来源（如 Kubernetes API、Consul、文件）自动发现要抓取的目标
- Alertmanager：告警管理器。一个独立的组件，负责处理由 Prometheus Server 发送的告警。它负责告警的去重、分组、静默和路由（通过邮件、Slack、PagerDuty 等通知）
- Pushgateway：一个特殊的组件，用于允许短生命周期的任务（如定时任务、批处理作业）将它们的指标推送到此处，然后由 Prometheus 从中抓取。主要用于弥补 Prometheus 默认的 Pull 模型的不足


Docker Compose安装：
```yaml
name: sylvie233-pythontest
version: '3.8'

services:
  prometheus:
    image: prom/prometheus:v3.7.3
    container_name: prometheus
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
    ports:
      - "9090:9090"
    networks:
      - sylvie233-network
    restart: unless-stopped

  grafana:
    image: grafana/grafana:10.1.1
    container_name: grafana
    environment:
      - GF_SECURITY_ADMIN_PASSWORD=admin
    ports:
      - "3000:3000"
    networks:
      - sylvie233-network
    restart: unless-stopped

networks:
  sylvie233-network:
    driver: bridge
```



- Prometheus默认是Pull模型
- Pushgateway实现Push模型、将指标主动 HTTP POST 到 Pushgateway，Prometheus 再从 Pushgateway 抓取


### prometheus.yaml
```yaml
prometheus.yaml:
    global: # 全局设置，为其他配置项提供默认值
        scrape_interval: # 默认抓取目标的频率（每次抓取间隔）
        evaluation_interval: # 规则评估频率（每隔多久计算一次记录规则和警报规则）
        external_labels: # 
    scrape_configs: # 抓取配置，定义Prometheus要监控哪些目标
        job_name: # 任务名称
        scrape_interval: # 覆盖全局抓取间隔
        static_configs: # 静态目标配置
            targets: # 要抓取的目标列表
            labels: # 为这组目标添加额外的标签
        kubernetes_sd_configs: # 使用Kubernetes服务发现
        relabel_configs: # 重新标记配置：在抓取前，对发现的元数据进行处理，生成最终的标签
            source_labels:
            action:
            regex:
    rule_files: # 规则文件路径，用于加载记录规则或警报规则
    alerting: # 告警配置，用于设置Alertmanager
        alertmanagers:
```


## 核心内容


## PromQL

