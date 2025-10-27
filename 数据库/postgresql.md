# postgresql


## 基础介绍

一个开源关系型数据库（RDBMS）


Docker Compose安装：
```yaml
name: sylvie233-pythontest

version: '3.8'

services:
  postgres:
    image: bitnami/postgresql:latest
    container_name: postgres
    restart: always
    environment:
      POSTGRES_USER: sylvie233
      POSTGRES_PASSWORD: 123456
      POSTGRES_DB: mydb
      TZ: "Asia/Shanghai"
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - postgres_init:/docker-entrypoint-initdb.d
    networks:
      - sylvie233-network
volumes:
  postgres_data:
    driver: local
  postgres_init:
    driver: local
networks:
  sylvie233-network:
    driver: bridge
```


Database -> Schema -> Table -> View
                            -> Index
                            -> Function
                            -> Sequence
User -> Role -> Privilege


### psql
```yaml
psql:
    -d: # 指定数据库
    -h: # 指定host
    -p:
    -U: # 指定用户
```

postgresql客户端命令


### pg_dump
```yaml
pg_dump:
    -d:
    -h:
    -U:
```



## 核心内容
```yaml
postgresql:
    \?: # 查看 psql 帮助命令
    \c: # 切换数据库
    \d: # 查看表结构
    \df: # 查看函数
    \di: # 查看索引
    \dn: # 查看所有 schema
    \dt: # 
    \du: # 查看用户/角色列表
    \dv: # 查看视图
    \l: # \list 查看数据库
    \q: # 退出
    current_database():
    CURRENT_DATE:
    CURRENT_TIME:
    CURRENT_USER:
    jsonb_array_elements:
    jsonb_build_object:
    PG_DATABASE_SIZE:
    PG_TABLE_SIZE:
    PG_TOTAL_RELATION_SIZE:
    SESSION_USER:
    VERSION():
DDL: # 数据定义语言
    ALTER TABLE:
    CREATE DATABASE:
    CREATE SCHEMA:
    CREATE TABLE:
    CREATE INDEX:
    DROP SCHEMA:
    DROP INDEX:
DML: # 数据操作语言
    SELECT:
    INSERT INTO:    
    UPDATE:
    DELETE FROM:
DCL: # 数据控制语言
    GRANT privilege ON:
        TO:
    REVOKE privilege ON:
        FROM:
    GRANT USAGE ON:
    CREATE ROLE:
        WITH LOGIN PASSWORD:
    ALTER ROLE:
    DROP ROLE:
TCL: # 事务控制语言
    BEGIN:
    COMMIT:
    RELEASE SAVEPOINT:
    ROLLBACK:
    ROLLBACK TO SAVEPOINT:
    SAVEPOINT:
DQL: # 数据查询语言
```

### Schema

数据库中的命名空间，用于组织数据库对象（表、视图、函数、索引等）
默认public



### Function

函数分类：
1. 字符串处理
2. 数学计算
3. 日期时间
4. 聚合函数
5. JSON/数组操作
6. 窗口函数
7. 系统元信息函数


## postgre原理


### default database

#### postgres
默认数据库postgres


##### pg_default


##### pg_global


#### template0
#### template1