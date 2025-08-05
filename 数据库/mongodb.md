# MongoDB

## 基础介绍

基于文档的 NoSQL 数据库
存储格式为 BSON（二进制 JSON）


默认端口：
- 27017


### mongo
```yaml
mongo:
    --authenticationDatabase:
    --eval:
    --host:
    --port:
    --password:
    --tls:
    --username:
```

mongodb客户端命令


#### mongod
```yaml
mongod:
    --config: # 配置文件
    --dbpath: # 数据目录
```


mongodb服务端命令


#### bsondump

#### mongodump
```yaml
mongodump:

```


#### mongoexport

#### mongoimport


#### mongostat

#### mongotop


#### mongofiles

## 核心内容
```yaml
mongodb:
    db:
        _coll: # 集合操作
            aggregate(): # 聚合$count
                $unwind: # 拆分数组字段
                $addFields:
                $group:
                    $count:
                    $sum:
                $match:
                $project:
                $sort:
                $skip:
                $limit:
                $lookup:
            createIndex():
            deleteOne():
            drop():
            dropIndex():
            find():
                $and:
                $not:
                $or:
                $elemMatch:
                    $all:
                    $exists:
                    $gt:
                    $gte:
                    $in:
                    $lt:
                    $nin:
                    $regex:
                    $size:
                    $type:
                $expr:
                $geoWithin:
                    $box:
                $near:
                $options:
                ---
                limit():
                sort():
            findOne():
            getIndexes():
            insertMany():
            insertOne():
            updateOne():
        createCollection():
        currentOp():
        dropDatabase():
        killOp():
        serverStatus():
    show:
        collections:
        dbs:
    use:
```



### Database




### Collection





### Document



#### Index



### GridFS