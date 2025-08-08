# SQLAlchemy

`SQLAlchemy官方文档：https://docs.sqlalchemy.org/en/20/orm/mapping_styles.html#orm-mapping-styles`

## 基础介绍


SQLAlchemy 是 Python 中最强大、最主流的数据库框架之一，支持 ORM(Session) 和原生 SQL(Connection) 构建器
数据库驱动包：
- mysqlclient


SQLAlchemy常用三大组件：Engine、Session、Connection
- 获取数据库引擎(数据库连接信息)Engine -> 获取数据库连接Connection -> 执行SQL 
- 获取数据库引擎(数据库连接信息)Engine -> 数据库表元信息MetaData -> 数据库表信息Table -> metadata创建表 -> 利用Table创建SQL语句(Insert、Delete...) -> 获取数据库连接Connection执行SQL语句
- 获取数据库引擎(数据库连接信息)Engine -> 定义模型类继承基类DeclarativeBase -> 模型类metadata创建表 -> 获取会话Session绑定Engine执行SQL操作    （这种方法类似MyBatis）


一个engine对应一个数据库
模型类中互相持有，就需要定义back_populates后置填充
ORM使用方式：4种
1. Table: 表结构定义
    - Column:
    - mapper(): 手动映射表结构和模型实体类 
2. declarative_base()：模型表结构定义（目前教程大部分）
    - Colomun(Integer):
    - Session操作ORM
        - session.query(Entity)：条件查询
3. DeclarativeBase：模型表结构定义
    - Mapped/mapped_column()：
    - session.query(Entity)
4. select(): sql构造（推荐）
    - session.execute(select(Entity))


sqlalchemy中没有ActiveRecord风格的操作，默认都是要通过session进行操作的（Flask-SQLAlchemy进行了封装）


## 核心内容
```yaml
sqlalchemy:
    engine: # 引擎包
        base:
            Connection: # 连接
                begin(): # 开启事务
                    commit():
                    rollback():
                close():
                execute(): # 执行原始sql
            Engine: # 引擎
                begin():
                connect(): # 获取Connection
                dispose():
        cursor: # 游标结果
            CursorResult:
                inserted_primary_key:
                fetchall():
                fetchone():
    event: # 事件包
        @listens_for():
            load: # 模型加载
            refresh:
            refresh_flush:
        listen():
    ext:
        declarative: # 基类声明创建
            declarative_base():
    orm: # ORM包
        query:
            Query:
                all():
                filter():
                first():
                one():
        DeclarativeBase: # 模型基类声明
            __table__: # Table元表信息
            __tablename__: # 表名
            metadata: # 数据库元表
            registry:
            create_all(): # 创建数据库表
        Mapped: # 模型字段声明
        Session: # 模型操作工具类
            add(): # 添加数据
            add_all():
            begin(): # 开启事务
            close(): # 关闭连接
            commit(): # 提交事务
            delete(): # 删除数据
            flush(): # 刷新（提交事务）
            get(): # 根据组件查询
            get_one():
            query(): # 条件查询（传入ORM实体类）
                all():
                first(): # 第一条
                one(): # 查询一条
                one_or_none():
                where(): # 条件过滤
                filter(): # 条件过滤
                filter_by(): # 条件过滤，可以不写Entity
                    or_(): # 布尔逻辑
                    not_(): # 布尔逻辑 
                join(): # 联表
                limit():
                offset():
                order_by(): # 排序
            refresh():
            scalars(): # 查询结果迭代遍历（select构造语句执行）
                first():
                one():
            update(): # 更新数据
        aliased(): # 定义表别名
        declarative_base(): # 创建模型基类, 旧版SQLAlchemy ≤1.4，新版使用DeclarativeBase
        mapped_column(): # 模型字段属性定义
            nullable: # 可空类型
            primary_key: # 主键i段
            server_default: # 默认值
            unique: # 唯一约束
        registry(): # 命令式映射
            metadata:
        relationship(): # 关联模型字段属性定义
            back_populates: # 后置填充
            backref: # 逆向添加本身引用（给关联表添加一个引用自身的字段）
            cascade: # 级联操作
            lazy:  #懒加载关联字段
            secondary: # 中间表
        sessionmaker(): # 获取session基类(实例化后继续使用)
    sql: # 原始SQL构造查询
        dml:
            Delete:
            Insert:
                values():
            Update:
        func:
            now():
        selectable:
            Select:
                join():
                join_from():
                order_by():
                where():
        and_():
        or_():
    Column: # 旧版字段定义
        nullable:
        primary_key:
        unique:
    Date:
    ForeignKey: # 字段类型 外键
    Integer: # 字段类型 整形
    Metadata: # 数据库元表
        create_all(): # 创建表（创建之前会查询)
    Select:
    String: # 字段类型 字符串
    Table: # 定义表信息
        c: # 所有列
        delete():
        insert():
        join(): # 表连接
        select():
        select_from():
        update():
    Text:
    __version__: # 版本
    bindparam():
    create_engine(): # 创建数据库引擎
        echo: # 显示执行的SQL
    delete(): # 删除sql构造
    insert(): # 插入sql构造
    and_():
    not_():
    or_():
    select(): # 查询sql构造
        join(): # 关联查询
        options(): # 
            selectinload(): # 预加载
        where(): # 查询条件构造
            ==:
            contains():
            in_():
    text(): 
    update(): # 更新sql构造
```


### Model
```python
Base = declarative_base()

class User(Base):
    __tablename__ = 'users'
    id: Mapped[int] = mapped_column(Integer, primary_key=True)
    name: Mapped[str] = mapped_column(String)
```

旧版模型定义：
- declarative_base、Column
- registry、Table
新版模型定义：DeclarativeBase、mapped_column、Mapped





### Session
```python
# session执行模型操作（自带事务）
with Session(engine) as session:
    spongebob = User(
        name="spongebob",
        fullname="Spongebob Squarepants",
        addresses=[Address(email_address="spongebob@sqlalchemy.org")],
    )
    patrick = User(name="patrick", fullname="Patrick Star")
    session.add_all([spongebob, patrick])
    session.commit()
```

Model模型操作工具类




#### Connection


底层数据库连接、常用于底层sql执行、不支持ORM



### Engine
```python
# 创建数据库引擎
from sqlalchemy import create_engine
engine = create_engine("sqlite://", echo=True)

# 创建数据库表（Base继承自DeclarativeBase）
Base.metadata.create_all(engine)
```

数据库连接信息（数据库连接池、连接复用）、建表



### RelationShip

模型关联操作


#### One To One



#### One To Many


#### Many To Many






### Core
```python
mapper_registry = registry()

user_table = Table(
    "user",
    mapper_registry.metadata,
    Column("id", Integer, primary_key=True),
    Column("name", String(50)),
)
```
SQL Build查询构造器模式



### Event

事件机制


- before_cursor_execute