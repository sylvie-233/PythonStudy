# SQLAlchemy

## 基础介绍


基础使用：
- 获取数据库引擎(数据库连接信息)Engine -> 获取数据库连接Connection -> 执行SQL 
- 获取数据库引擎(数据库连接信息)Engine -> 数据库表元信息MetaData -> 数据库表信息Table -> metadata创建表 -> 利用Table创建SQL语句(Insert、Delete...) -> 获取数据库连接Connection执行SQL语句
- 获取数据库引擎(数据库连接信息)Engine -> 定义模型类继承基类DeclarativeBase -> 模型类metadata创建表 -> 获取会话Session绑定Engine执行SQL操作    （这种方法类似MyBatis）




数据库驱动包：
- mysqlclient




模型类中互相持有，就需要定义back_populates后置填充



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
        cursor: 游标结果
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
        DeclarativeBase: 模型基类声明
            __table__: 定义表名
            metadata:
            registry:
        Mapped:
        registry:
            metadata:
        Session:
            add():
            add_all():
            commit():
            flush():
            query():
            update():
        declarative_base(): 创建模型基类
        mapped_column():
            nullable:
            primary_key:
            server_default: 默认值
            unique:
        relationship():
            back_populates: 后置填充
            backref: 逆向添加本身引用（给关联表添加一个引用自身的字段）
            lazy: 懒加载关联字段
            secondary: 中间表
        sessionmaker(): 获取session
    sql:
        dml:
            Delete:
            Insert:
                values():
            Update:
        func:
            now():
        selectable:
            Select:
                where():
        and_():
        or_():
    __version__: 版本
    Column:
        nullable:
        primary_key:
        unique:
    Date:
    ForeignKey: 外键字段
    Integer: 
    Metadata: 数据库元表
        create_all(): 创建表（创建之前会查询)
    String: 字符串字段
    Table: 定义表信息
        c: 所有列
        delete():
        insert():
        join(): 表连接
        select():
        select_from():
        update():
    Text:
    create_engine():
        echo: 显示执行的SQL
    text():

typing_extensions:
    Annotated: 字段类型变量（常用于Mapped类型）
```