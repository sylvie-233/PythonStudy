# SQLAlchemy

`SQLAlchemy官方文档：https://docs.sqlalchemy.org/en/20/orm/quickstart.html#simple-select`

## 基础介绍




数据库驱动包：
- mysqlclient

一个engine对应一个数据库

模型类中互相持有，就需要定义back_populates后置填充



基础使用：
- 获取数据库引擎(数据库连接信息)Engine -> 获取数据库连接Connection -> 执行SQL 
- 获取数据库引擎(数据库连接信息)Engine -> 数据库表元信息MetaData -> 数据库表信息Table -> metadata创建表 -> 利用Table创建SQL语句(Insert、Delete...) -> 获取数据库连接Connection执行SQL语句
- 获取数据库引擎(数据库连接信息)Engine -> 定义模型类继承基类DeclarativeBase -> 模型类metadata创建表 -> 获取会话Session绑定Engine执行SQL操作    （这种方法类似MyBatis）




## 核心内容
```yaml
sqlalchemy:
    engine:
        base:
            Connection:
                close():
                commit():
                execute():
            Engine:
                begin():
                connect():
                dispose():
        cursor: # 游标结果
            CursorResult:
                inserted_primary_key:
                fetchall():
                fetchone():
    orm:
        query:
            Query:
                all():
                filter():
                first():
                one():
        DeclarativeBase: # 模型基类声明
            _field: # 
                ==:
                contains():
                in_():
            __table__: # 定义表名
            metadata:
            registry:
        Mapped: # 模型字段声明
        registry:
            metadata:
        Session: # 模型操作工具类
            add(): # 添加数据
            add_all():
            begin(): # 开启事务
            commit(): # 提交事务
            flush():
            get():
            get_one():
            query():
            update():
        aliased(): # 定义表别名
        declarative_base(): # 创建模型基类
        mapped_column(): # 模型字段属性定义
            nullable: # 可空类型
            primary_key: # 主键i段
            server_default: # 默认值
            unique: # 唯一约束
        relationship(): # 关联模型字段属性定义
            back_populates: # 后置填充
            backref: # 逆向添加本身引用（给关联表添加一个引用自身的字段）
            cascade: # 级联操作
            lazy:  #懒加载关联字段
            secondary: # 中间表
        sessionmaker(): # 获取session
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
    Column:
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
    delete():
    select():
    text():
    update():
```


### Model
```python
# 模型定义
class Base(DeclarativeBase):
     ...

class User(Base):
    __tablename__ = "user_account"

    id: Mapped[int] = mapped_column(primary_key=True)
    fullname: Mapped[Optional[str]]
    addresses: Mapped[List["Address"]] = relationship(
        back_populates="user", cascade="all, delete-orphan"
    )

class Address(Base):
    __tablename__ = "address"

    id: Mapped[int] = mapped_column(primary_key=True)
    email_address: Mapped[str]
    user_id: Mapped[int] = mapped_column(ForeignKey("user_account.id"))

    user: Mapped["User"] = relationship(back_populates="addresses")
```

模型定义



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

模型操作工具类



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