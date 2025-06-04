# Alembic



## 基础介绍

数据库迁移工具

### 项目结构
```yaml
alembic:
    /versions:
    alembic.ini: # 主要的配置文件
    env.py: # Alembic 迁移环境的脚本，负责数据库连接配置和迁移逻辑
    README: 
    script.py.mako: # 
```


#### alembic.ini:
```yaml
alembic.ini:
    sqlalchemy:
        url:
```



### alembic
```yaml
alembic:
    current: # 显示当前数据库版本
    downgrade: # 回滚迁移
    history: # 迁移历史
    revision: # 生成迁移脚本
        -m:
        --autogenerate:
    upgrade: # 执行迁移
        head:
```


## 核心内容
```yaml
alembic:
    command:
    config:
    context: # 配置
        config: # 访问 Alembic 配置对象
            config_file_name:
            config_ini_section:
            get_main_option():
            get_section(): # 获取配置项
        transaction:
        begin_transaction(): # 开启事务
        configure(): # 配置数据库连接、模型基类（关联sqlchemy模型）
        is_offline_mode():
        run_migrations(): # 执行迁移
    op: # 数据库操作
        add_column():
        add_constraint():
        alter_column():
        create_index():
        create_table():
        drop_column():
        drop_constraint():
        drop_index():
        drop_table():
        execute():
        rename_table():
    runtime:
    script:
    util:
```