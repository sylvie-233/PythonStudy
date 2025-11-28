# MySQL

## 基础介绍

关系型SQL数据库
- DDL：数据定义语言
- DML：数据操作语言
- DQL：数据查询语言
- DCL：数据控制语言
- TCL：事务控制语言

内置函数
- 字符串函数
- 数学函数
- 日期时间函数
- 聚合函数
- 条件函数
- 类型转换函数


Docker Compose安装：
```yaml
name: sylvie233

services:
  # MySQL数据库服务
  mysql:
    # 使用官方MySQL镜像
    image: mysql:8.0
    container_name: sylvie233-mysql
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: ${DB_PASSWORD:-123456}
      MYSQL_DATABASE: ${DB_NAME:-testms}
      MYSQL_USER: ${DB_USER:-sylvie233}
      MYSQL_PASSWORD: ${DB_PASSWORD:-123456}
      TZ: Asia/Shanghai
    ports:
      - "3307:3306"
    volumes:
      - mysql_data:/var/lib/mysql
      - ./backend/scripts/init-database.sql:/docker-entrypoint-initdb.d/init.sql
    networks:
      - sylvie233-network
    command: --default-authentication-plugin=mysql_native_password --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
    healthcheck:
      test: ["CMD", "mysqladmin", "ping", "-h", "localhost"]
      timeout: 20s
      retries: 10
```


系统默认库
- information_schema
- mysql
- performance_schema
- sys

MySQL架构：Client连接管理 → Parser SQL 解析 → Optimizer查询优化 → Executor执行器 → 存储引擎 → 日志系统 → 结果返回
- Server层：主要处理SQL解析、优化、执行、缓存、日志管理等
    - 连接管理（用户认证、权限管理）
    - 查询解析器（SQL 解析、语法分析、语义分析）
    - 查询优化器（执行计划生成、索引选择）
    - 查询缓存（MySQL 8.0 已移除）
    - 日志管理（binlog、redo log、undo log）
    - 事务管理（ACID 支持）
    - 锁机制（行锁、表锁）
- 存储引擎层：管理数据存储、索引、事务，不同存储引擎提供不同的底层数据存储方式
    - InnoDB（支持事务、MVCC、行锁）
    - MyISAM（无事务，读写性能高）
    - Memory（内存存储，适用于临时数据）


MySQL 权限控制由以下三部分组成：
1. 认证（Authentication）：你是谁？
2. 授权（Authorization）：你能做什么？
3. 访问控制（Access Control）：对库/表/列/例程的权限检查
    - user: 用户账号信息（用户名、密码、全局权限）
    - db: 库级权限
    - tables_priv: 表级权限
    - columns_priv: 列级权限
    - procs_priv: 存储过程和函数权限
    - global_grants: 8.0 新增，全局角色与动态权限


- 用户定义变量以@符号开头，可以在查询中直接使用
- 创建用户`CREATE USER 'app'@'%' IDENTIFIED BY 'pwd123';`后面的`%`为用户允许登录的主机，mysql的登录账号使用 用户名 + 主机名（IP）作为联合主键，登录时默认使用最精确的那个


### 安装目录
```yaml
目录结构:
    /bin:
    /data: # 数据存储目录，包含数据库、表和 InnoDB 事务日志
        /mysql:
        /performance_schema:
        /sys:
        #ib_xxx_xxx.dblwr:
        auto.cnf: # 服务器UUID配置
        binlog.xxx: # 二进制日志文件、存储数据库变更数据，用于恢复/主从复制
        binlog.index:
        error.log: # MySQL错误日志
        general.log: # MySQL通用查询日志
        slow.log: # MySQL慢查询日志
        ib_logfile: # InnoDB 事务日志、记录事务操作
        ibdata1: # InnoDB 共享表空间、存储 InnoDB 表的元数据和事务数据
        ibtmp: # InnoDB 临时表空间、存储CREATE TEMPORARY TABLE数据
        mysql.ibd: # 存储`mysql`数据库的InnoDB共享表、mysql 数据库的表数据
        relay-log.xxx: # 复制中继日志、从服务器用于主从复制
        relay-log.index: # 复制中继日志索引
        undo_xxx: # InnoDB undo 日志文件、用于事务回滚
    /include:
    /lib:
    /share:
    /support-files: # 额外配置文件和 MySQL 服务相关的脚本
    my.ini: # MySQL 配置文件
```


#### my.ini
```yaml
my.ini:
    datadir: # 数据存储目录
    max_connections:
    plugin-dir:
```


mysql配置文件





### mysql
```yaml
mysql:
    -u: # 用户名
    -p: # 密码

mysqladmin:

mysqlbinlog: # 根据binlog做数据恢复
    --database:
    --start-datetime:
    --start-position:
    --stop-datetime:
    --stop-positio:

mysqlcheck:

mysqld:

mysqldump:

mysqlimport:

mysql_secure_installation:
```




## 核心内容
```yaml
Command:
    alter:
        table: # 修改数据表
            add: # 添加字段
            change: # 修改字段名
            drop: # 删除字段
            execute: # 函数、存储过程执行
            modify: # 修改字段类型
            rename: # 修改表名
        user:
    create:
        database: # 创建数据库
        index: # 创建索引
            on:
        procedure: # 创建存储过程
        role: # 创建角色
        table: # 创建数据表 
            if not exists:
            _datatype: # 数据类型
                bigint:
                binary:
                blob:
                char:
                date:
                datetime:
                decimal:
                double:
                enum:
                float:
                int:
                integer:
                json:
                longblob:
                longtext:
                mediumblob:
                mediumint:
                mediumtext:
                set:
                smallint:
                time:
                timestamp:
                tinyblob:
                tinyint:
                tinytext:
                varbinary:
                varchar:
                year:
            _constraints: # 数据约束
                auto_increment: # id自增长
                default: # 默认值
                foreign key: # 外键定义
                    references:
                primary key: # 主键
                unique: # 唯一约束
        trigger: # 创建触发器 
        user: # 创建用户
            identified by: # 
                password:
        view: # 创建视图
            as:
    desc: # 表描述信息
    drop:
        database: # 删除数据库
        index:
            on:
        procedure: # 删除存储过程
        table:
        user: # 
    explain: # 分析SQL语句的执行计划
    flush:
        privileges:
    grant: # 赋予用户权限
        _privilege_type: # 权限
            all privileges:
            delete:
            insert:
            select:
            update:
        on:
        to:
    install:
        plugin:
    lock:
        tables: # 表锁
            read:
            write:
    revoke: # 撤销用户权限
        on:
        from:
    set:
        default role: # 赋予用户角色
            to:
    show:
        binlog:
        databases: # 显示所有数据库
        engine: # 查看数据库引擎状态
        global:
            status: # 查看全局状态变量
                like:
            variables: # 查看全局变量
                like:
                --- 
                autocommit:
                long_query_time:
                slow_query_log: # 开启慢查询日志
                transaction_isolation:
        index: # 查看索引
            from:
        plugins:
        processlist: # 显示正在执行的sql，可用于查看登录用户
        session:
            variables:
        table:
            stauts:
        tables: # 显示所有数据表
        variables: # 查看变量
    start transaction: # 开启事务
        commit:
        rollback:
            to:
        savepoint:
    truncate:
        table: # 清空数据表
    uninstall:
        plugin:
    unlock:
        tables:
    use: # 使用数据库
SQL:
    delete:
        from:
        where:
    insert:
        into:
        values:
    select:
        from:
        inner join:
        left join:
        right join:
            on:
        where:
            select: # 子查询
            between:
            in:
            like:
            not null:
        order by:
            asc:
            desc:
        limit: # 分页查询
            offset:
            count:
        for update:
        lock in share mode:
    update:
        set:
        where:
    abs():
    avg():
    cast():
    ceil():
    char_length():
    concat():
    concat_ws():
    convert():
    count():
    current_date():
    current_time():
    current_user(): # 当前用户
    date_add():
    date_format():
    date_sub():
    datediff():
    group_concat():
    if():
    ifnull():
    instr():
    json_object():
    left():
    length():
    locate():
    lower():
    ltrim():
    max():
    min():
    now():
    rand():
    replace():
    reverse():
    right():
    rtrim():
    str_to_date():
    strcmp():
    substring():
    sum():
    trim():
    upper():
    unix_timestamp():
    uuid():
```

### 数据类型
- 数值类型：用于存储整数或浮点数。
- 日期和时间类型：用于存储日期、时间或时间戳。
- 字符串类型：用于存储文本数据。
- 二进制类型：用于存储二进制数据。
- 枚举和集合类型：用于存储预定义的值。
- JSON 类型：用于存储 JSON 数据。



### 函数
```sql
-- 使用动态库注册函数
CREATE FUNCTION square RETURNS INTEGER SONAME 'udf_square.so';
```

函数封装处理、依赖底层C++动态库


### 存储过程
```sql
-- 定义存储过程
DELIMITER $$
CREATE PROCEDURE get_user_name(IN user_id INT, OUT user_name VARCHAR(100))
BEGIN
    SELECT name INTO user_name FROM users WHERE id = user_id;
END $$
DELIMITER ;

-- 调用存储过程
CALL get_user_name(1, @name);
SELECT @name;
```



主要用于定义批处理




#### 控制流程
```yaml
Control Flow:
    declare: # 变量声明
    delimiter: # 修改结束符
    if ... then ... else ... end if:
    set: # 变量赋值
    while ... do ... end while:
```


#### 异常处理
```sql
DECLARE EXIT HANDLER FOR SQLEXCEPTION
BEGIN
    SELECT 'An error occurred!';
END;
```



### 触发器





### 视图



### 用户




### 事件








## MySQL原理


### 内置数据库
```yaml
mysql内置数据库:
    information_schema: # 元数据、数据库结构
        innodb_locks:
        innodb_trx:
        processlist: # 显示正在执行的sql
    mysql: # 核心权限、用户管理、执行日志
        columns_priv:
        db:
        general_log:
        procs_priv:
        slow_log:
        tables_priv:
        uesr: # 存储用户账户信息、认证方式、权限等
            localhost:
            user:
    performance_schema:
        events_statements_summary_by_digest:
        file_summary_by_instance:
        table_io_waits_summary_by_table:
        threads:
    sys:
        io_global_by_file_by_bytes:
        memory_global_by_current_bytes:
        schema_table_statistics:
        statement_analysis:
```


#### information_schema

提供MySQL数据库、表、列、索引等对象的元数据，是一个只读的虚拟数据库


##### columns
字段信息

##### key_column_usage

主键、外键


##### schemata
数据库列表


##### statistics

索引信息

##### tables
表列表、行数估计等


#### mysql


存储MySQL服务器运行所需的核心数据，如用户权限、数据库定义、存储过程等

##### columns_priv

更细粒度，对单个字段做权限控制

##### db

限制用户对某个数据库的操作权限
##### global_priv

8.0 以后权限存储整合到了 global_priv JSON 字段中
部分系统已废弃 user 表内的权限列

##### procs_priv

存储过程与函数权限
##### proxies_priv

代理用户权限（Proxy 权限）,A 用户可代理 B 用户执行操作

##### roles_mapping

用户 → 角色
MySQL 8 加入了角色（Role）能力


##### ssl_rsa

存储 SSL/TLS 所需的密钥与证书信息

##### tables_priv

存储用户对具体表的访问权限

##### user


存储用户的账号、密码、全局权限（对整个实例生效）。



#### performance_schema

监控MySQL服务器的性能，包括SQ 语句执行时间、锁等待、I/O 统计等。

##### events_statements_history

最近 SQL 执行

##### events_transactions_summary_by_account_by_event_name

事务耗时

##### events_waits_summary_by_instance

锁等待


#### sys

基于performance_schema，提供更易读的性能分析视图，帮助DBA进行调优









### InnoDB

- 数据页（Data Page）：默认16KB一页，采用B+Tree结构存储数据
- 索引组织表（Clustered Index）：数据按主键索引（PK）存储
- 二级索引（Secondary Index）：查询需要回表查主键

















#### 日志


##### binlog

- 记录所有数据变更（INSERT、UPDATE、DELETE）。
- 用于数据恢复、主从复制。

Binlog 只记录数据变更、不记录SELECT和事务回滚（ROLLBACK）
记录包含：
- 数据库名、表名
- 执行的SQL语句
- 变更时间
- 事务ID



##### redolog

重做日志


##### undolog

回滚日志



##### relaylog




##### slowlog

慢查询日志、记录执行时间超过long_query_time的SQL语句


##### generallog

##### errorlog


#### 索引

##### B+Tree

- 适用于范围查询和排序。
- PRIMARY KEY和UNIQUE KEY默认使用B+Tree。

##### Hash

- 适用于等值查询（=）。
- Memory存储引擎使用哈希索引


#### 事务

MySQL事务依赖redolog（重做日志）和 undolog（回滚日志）保障ACID特性

事务隔离问题：
- 脏读：读取了未提交的事务数据
    - 事务A还未提交，事务B读到了数据，A回滚后，B读到的数据就成了“脏数据”。
- 幻读：同一个事务内，查询记录条数不一致
    - 事务A读取符合条件的记录，事务B插入新记录，事务A重新查询发现“幻影”数据。
- 不可重复读：同一个事务内，多次查询数据不一致
    - 事务A查询后，事务B修改并提交，事务A再次查询，数据发生变化。


MySQL提供4种隔离级别
- 读未提交：
- 读已提交：
- 可重复读： 默认
- 串行化读：






#### 锁

##### 表锁



##### 行锁
- 共享锁（S锁）：当事务对某行数据加上共享锁时，其他事务只能读取数据，无法修改数据
- 排它锁（X锁）：当事务对某行数据加上排它锁时，其他事务无法读取或修改该数据


##### 间隙锁