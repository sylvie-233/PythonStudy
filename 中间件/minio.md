# Minio


## 基础介绍


分布式文件存储中间件

Docker Compose安装：
```yaml
name: sylvie233-pythontest

services:
  minio:
    image: minio/minio:latest
    container_name: minio
    restart: unless-stopped
    ports:
      - "9000:9000"   # API 端口
      - "9001:9001"   # 控制台端口
    environment:
      MINIO_ROOT_USER: minioadmin        # 管理员账号
      MINIO_ROOT_PASSWORD: minioadmin # 管理员密码（至少 8 位）
    command: server /data --console-address ":9001"
    volumes:
      - minio_data:/data  # 使用 local 卷挂载

volumes:
  minio_data:
    driver: local
```


## 核心内容