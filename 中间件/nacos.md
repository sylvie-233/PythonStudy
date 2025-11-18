# Nacos


## 基础介绍


服务注册中间件


Docker Compose安装：
```yaml
name: sylvie233-nacos

version: '3.8'

services:
  nacos:
    image: nacos/nacos-server:v2.3.2
    container_name: nacos
    environment:
      MODE: standalone
      # 使用内存模式存储数据，不依赖MySQL
      SPRING_DATASOURCE_PLATFORM: ""
      NACOS_AUTH_ENABLE: "false"              # ✅ 关闭鉴权
      JVM_XMS: 512m
      JVM_XMX: 512m
      JVM_XMN: 256m
      # 优化配置参数
      NACOS_SERVER_IP: 127.0.0.1
      NACOS_APPLICATION_PORT: 8848
      TOMCAT_ACCESSLOG_ENABLED: "true"
      NACOS_DEBUG: "false"
    ports:
      - "8848:8848"
      - "9848:9848"
      - "9849:9849"
    volumes:
      - nacos_data:/home/nacos/data
      - nacos_logs:/home/nacos/logs
    networks:
      - sylvie233-network
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8848/nacos/v1/ns/operator/metrics"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 60s
    restart: unless-stopped

volumes:
  nacos_data:
    driver: local
  nacos_logs:
    driver: local

networks:
  sylvie233-network:
    driver: bridge
```


## 核心内容
