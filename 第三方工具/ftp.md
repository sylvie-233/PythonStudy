# FTP


## 基础介绍


文件传输协议


Docker Compose安装：
```yaml
services:
  vsftpd:
    image: fauria/vsftpd
    container_name: vsftpd
    restart: unless-stopped
    ports:
      - "20:20"
      - "21:21"
      - "10000-10100:10000-10100"
    environment:
      FTP_USER: "admin"
      FTP_PASS: "123456"
      PASV_ADDRESS: "0.0.0.0"  
      PASV_MIN_PORT: "10000"
      PASV_MAX_PORT: "10100"
      LOG_STDOUT: "TRUE"
      ANONYMOUS_ENABLE: "YES"
      FILE_OPEN_MODE: "0777"
      LOCAL_UMASK: "000"
      PASV_ENABLE: "YES"  # 确保被动模式启用
      WRITE_ENABLE: "YES"  # 允许写入操作
    volumes:
      - ./ftpdata:/home/vsftpd
    network_mode: "bridge"
    # 确保容器有正确的权限
    user: "root:root"
```



FTP主动模式连接
```
客户端                      服务器
  |                           |
  | 命令连接(客户端N→服务器21)  |
  |---------------------->    | PORT命令，告知客户端N+1端口
  |<----------------------    |
  |                           |
  | 数据连接(服务器20→客户端N+1)| ← 服务器主动发起
  |<----------------------    |    
```


FTP被动模式连接
```
客户端                      服务器
  |                          |
  | 命令连接(客户端N→服务器21) |
  |---------------------->   | PASV命令
  |<----------------------   |
  |                           |
  | 数据连接(客户端M→服务器P)   | ← 客户端主动发起
  |---------------------->    |
```


## 核心内容