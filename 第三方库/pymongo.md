# pymongo



## 基础介绍


MongoDB 官方库

## 核心内容
```yaml
pymongo:
    mongo_client:
        MogoClient:
    collection:
        Collection: # 集合
            create_index():
            delete_many():
            delete_one():
            find():
            find_one():
            find_one_and_update():
            insert_many():
            insert_one():
            update_many():
            update_one():
    database:
        Database: # 数据库
    MongoClient: # 客户端
        _mydb: # 自定义数据库名
            _mycol: # 自定义集合
            command():
bson:
    ObjectId:
    dumps():
    loads():
```