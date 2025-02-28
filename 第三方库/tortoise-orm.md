# tortoise-orm

## 基础介绍

python 异步ORM框架




### aerich
```yaml
aerich:
    init-db:
```

数据库迁移工具



## 核心内容
```yaml
tortoise:
    contrib: # 第三方集成
        fastapi:
            register_tortoise(): # Tortoise ORM 将能够与 FastAPI 的事件生命周期管理（如启动时连接数据库、关闭时断开连接）进行集成。
                add_exception_handlers:
                app:
                config: # ORM配置
                    apps:
                        models: # 模型定义使用
                            default_connection:
                            models:
                    connections: # 数据库连接信息
                        default:
                            credentials:
                                database:
                                echo:
                                host:
                                password:
                                port:
                                user:
                            engine:
                db_url:
                modules:
                generate_schemas:
    fields: # 模型字段
        CharField: # 字符串字段
            max_length:
            unique:
            verbose_name:
        DatetimeField: # 日期字段
            auto_now_add:
        ForeignKeyField: # 外键定义(用于定义多对一的关系)
            related_name: # 关联字段
        IntField: # 整型字段
            pk: # 主键
        ManyToManyField: # 多对多关联字段
            description:
            related_name:
        OneToOneField: # 一对一关联字段
            related_name:
        ReverseRelation: # 反向关联(用于定义一对多关系的反向访问)
        TextField:
    models: # 模型
        Model: # 模型基类
            Meta: # 模型元信息
                table: # 表明
            all(): # 所有结果
            count():
            create(): # 创建
            filter(): # 条件查询
                __{field}: # 字段值判断
                __contains: # 包含

            first():
            get():
            limit():
            offset():
            order_by(): # 排序 
                -: # 倒序
            prefetch_related(): # 预加载字段
            --- # 模型实例
            delete(): # 删除
            save(): # 保存修改
    transactions:
        in_transaction(): # 上下文事务管理
    Tortoise:
        close_connections():
        generate_schemas(): # 初始化数据库
        init(): # 初始化连接
            db_url: # 数据库连接
            modules: # 指定模型所在模块
                models:
    run_async(): # 异步运行
```



### Model