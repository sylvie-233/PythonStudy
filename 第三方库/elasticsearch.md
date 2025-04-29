# ElasticSearch


## 基础介绍

python ElasticSearch分布式搜索引擎操作库


## 核心内容
```yaml
elasticsearch:
    Elasticsearch: # es客户端
        helpers:
            bulk(): # 批量操作
        indices: # 索引
            create(): # 
                body: # 索引配置
                index:
                ignore:
            delete():
        delete(): # 删除文档
        index(): # 添加文档
            document:
            id:
            index:
        ping():
        search(): # 查询文档
            index:
            body: # query dsl
                --- # 
                query:
                    match_all:
                    term: # 精确匹配
        update(): # 更新文档

```

### Index

索引


### Document


文档

