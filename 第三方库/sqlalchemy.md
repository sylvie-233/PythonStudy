# SQLAlchemy

## 基础介绍



## 核心内容
```yaml
sqlalchemy:
    engine:
        base:
            Connection:
                execute():
            Engine:
                connect():
        cursor:
            CursorResult:

    orm:
        DeclarativeBase: 模型类声明
            __table__:
            registry:
        Mapped:
        registry:
            metadata:
        Session:
            add_all():
            commit():
        mapped_column():
        relationship():
            back_populates: 后置填充
            secondary: 中间表
    sql:
        dml:
            Delete:
            Insert:
            Update:
        selectable:
            Select:
                where():
    Column:
    ForeignKey: 外键字段
    Metadata: 数据库元表
        create_all():
    String: 字符串字段
    Table: 定义表信息
    Text:
    create_engine():
```