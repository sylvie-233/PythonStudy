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
    contrib:
        fastapi:
            register_tortoise():
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
    fields: # 模型字段类
        CharField:
            max_length:
            verbose_name:
        ForeignKeyField: # 外键定义
        IntField:
        ManyToManyField: # 多对多字段
            description:
            related_name:
    models:
        Model: # 模型基类
            --- # 模型实例
            all(): # 所有结果
            filter(): # 过滤
            first():
            get():
            limit():
            order_by():
```