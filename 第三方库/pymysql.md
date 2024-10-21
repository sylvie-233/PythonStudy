# pymysql


## 核心内容
```yaml
pymysql:
    Connection:
        autocommit: # 自动提交
        host: # ip
        port: # 端口
        user: # 用户名
        password: # 密码
        database: # 数据库
        charset:
        close():
        commit(): # 提交
        cursor(): # 游标对象
        get_host_info():
        get_server_info():
        insert_id(): # 插入返回的id
        select_db(): # 选择数据库
    Cursor:
        close():
        execute(): # 执行sql
        executemany():
        fetchall(): # 获取所有数据（元组）
        fetchone():
    connect():
```