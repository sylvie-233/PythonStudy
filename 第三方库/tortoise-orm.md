# tortoise-orm

## 基础介绍

python 异步ORM框架


所有操作均为异步，需要await



### aerich
```yaml
aerich:
    downgrade: # 版本回退
    history: # 历史记录
    init: # 初始化仓库（生成pyproject.toml 和/migrations迁移文件目录）
        -t: # 指定数据库配置信息对象（models配置添加aerich.models用于记录迁移版本）
    init-db: # 数据库中创建表结构
    migrate: # 生成迁移脚本
        --name: # 本次迁移名称
    reset: # 重置，删除所有迁移
    upgrade: # 执行迁移
```

数据库迁移工具


#### TORTOISE_ORM 
```python
TORTOISE_ORM = {
    "connections": {
        "default": "sqlite://db.sqlite3",  # 数据库连接 URL
    },
    "apps": {
        "models": {  # 模型定义
            "models": ["my_project.models"],  # 这里是模型所在模块
            "default_connection": "default",  # 连接名称
        },
    },
}
```



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
            source: # 字段名映射
            unique:
            verbose_name:
        DatetimeField: # 日期字段
            auto_now_add:
        ForeignKeyField: # 外键定义(用于定义多对一的关系)
            related_query_name: # 反向关系查询字段
            related_name: # 反向关联字段
        IntField: # 整型字段
            pk: # 主键
        ManyToManyField: # 多对多关联字段
            description:
            related_name:
        OneToOneField: # 一对一关联字段
            related_name:
        ReverseRelation: # 反向关联(用于定义一对多关系的反向访问，提供代码提示)，定义类型，从而确保在反向访问时类型更明确，让你在访问反向关系时可以显式地理解它的类型
        TextField:
    models: # 模型
        Model: # 模型基类
            Meta: # 模型元信息
                table: # 表明
            all(): # 所有结果
            count():
            create(): # 创建
            delete():
            filter(): # 条件查询（传入Q实现动态构造更新参数）
                __{field}: # 字段值判断
                __contains: # 包含
                __range: # 范围in
                values(): # 获取字典，支持select
            first():
            get(): # 主键查询
            limit():
            offset():
            order_by(): # 排序 
                -: # 倒序
            prefetch_related(): # 预加载字段
            update(): # 更新（可传入字典动态构造更新参数）
            --- # 模型实例
            add():
            clear():
            delete(): # 删除
            save(): # 新增、保存修改
            values():
    queryset: # 查询构造器
        Q: # 支持逻辑运算拼接
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




### Relation

related_name 是一个用于定义反向关系的字段选项。当你定义模型时，related_name 可以让你指定通过外键（ForeignKey）、一对多（OneToMany）或多对多（ManyToMany）关系来访问反向关系的名称。

related_name在其中一方定义即可


#### One To Many
```python
class Author(Model):
    id = fields.IntField(pk=True)
    name = fields.CharField(max_length=100)

class Book(Model):
    id = fields.IntField(pk=True)
    title = fields.CharField(max_length=100)
    author = fields.ForeignKeyField('models.Author', related_name='books')  # 使用 related_name

# 查询作者和书籍
author = await Author.get(id=1)
books = await author.books.all()  # 通过 related_name 获取该作者的所有书籍
```

一对多关系


### Transaction
```python
from tortoise import Tortoise
from tortoise.transactions import in_transaction
from models import User

async def example_transaction():
    async with in_transaction() as conn:
        # 在事务中执行的数据库操作
        user1 = await User.create(username="user1", email="user1@example.com")
        user2 = await User.create(username="user2", email="user2@example.com")

        # 假设这里有一个错误导致回滚
        if user1.username == "user1":
            raise ValueError("Something went wrong, rolling back transaction")
        
        # 事务提交到数据库
        await conn.commit()

```


事务