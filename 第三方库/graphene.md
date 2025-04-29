# Graphene


## 基础介绍



## 核心内容
```yaml
graphene:
    Enum:
    Field: # 模型字段
    ID: # id类型
    InputObjectType: # 复杂输入
    Int: # 整型
    List: # 列表类型，一对多
    Mutation: # 修改模型基类
        Arguments: # 修改模型参数定义 
        Field: # 
        mutate(): # 修改逻辑
    ObjectType: # 查询模型基类
    Schema:
        mutation:
        query:
        execute(): # 执行query字符串
    String: # 字符串类型
```

### Schema

模型定义
`resolve_<字段名>()`执行具体的模型字段解析


### Query

查询模型ObjectType


### Mutation

修改模型,依赖ObjectType



### RelationShip




