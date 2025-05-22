# Elasticsearch


## 基础介绍


分布式搜索引擎



## 核心内容
```yaml
GET:
    _analyze: # /_analyze: 测试文本查询
        analyzer:
            standard:
        text:
        --- # /_analyze: 测试文本查询结果、响应token
        tokens:
            start_offset:
            token:
    _cat:
        nodes:
    index: # /index: 查询索引
        _count: # /index/_count: 获取文档数量
        _doc:
            id: # /index/_doc/id: 根据id查询文档
            --- # /index/_doc/id: 查询文档响应结果
        _search: # /index/_search: 条件查询文档
            aggs: # 聚合
                aggs: # 组合聚合
                    stats:
                        field:
                terms:
                    field:
                    size:
            from:
            query:
                bool: # 布尔
                    filter:
                    must:
                    must_not:
                    should:
                highlight:
                    fields:
                        post_tags:
                        pre_tags:
                match: # 支持分词匹配
                match_all:
                multi_match:
                    fields:
                    query:
                range: # 范围
                    gte:
                    lte:
                term: # 精确匹配
                    value:
            size:
            sort:
                asc:
                desc:
            --- # /index/_search: 条件查询文档响应结果
            took:
            timed_out:
            _shards:
            hits:
                total:
                max_score:
                hits:
                    _index:
                    _id:
                    _score:
                    _source: # 原始响应数据
                    highlight: 
            aggregations:
                buckets:
                    key:
                    doc_count:
        --- # /index: 查询索引响应结果
        _index:
            aliases:
            mappings:
                properties:
        settings:

POST:
    _bulk: # /_bulk: 批量操作
        delete:
        index:
    index:
        _doc: 
            id: # /index/_doc/id: 新增文档
        _update:
            id: # /index/_update/id: 增量修改指定文档字段值
                doc:

PUT:
    index: # /index: 创建索引、添加文档结构
        mappings:
            properties:
                analyzer:
                index:
                properties:
                type:
                    keyword:
                    text:
        --- # /index: 创建索引响应结果
        _doc:
            id: # /index/_doc/id: 全量修改，删除旧文档，添加新文档
        _mapping: # /index/_mapping: 新增字段
            properties:

DELETE:
    index: # /index: 删除索引
```


搜索引擎




## LogStash

日志收集与处理引擎
主要用于从各种数据源（日志文件、数据库、消息队列等）收集数据，经过过滤、转换后传输到目标系统（如 Elasticsearch）。

核心是一个数据管道：input → filter → output
Filebeat 发送原始日志，Logstash 解析结构并转发


### 安装目录
```yaml
logstash:
    /bin:
        logstash:
    /config:
    /data:
    /jdk:
    /lib:
    /logstash-core:
    /logstash-core-plugin-api:
    /vendor:
    /x-pack:
    Gemfile:
    Gemfile.lock:
```


#### logstash.conf
```yaml
logstash.conf:
    input:
        file:
            path:
            sincedb_path:
            start_position:
        kafka:
            bootstrap_servers:
            group_id:
            topics:
        stdin:
    filter:
        date:
            match:
            target:
        geoip:
            source:
        grok:
            match:
                message:
        json:
            source:
        mutate:
            remove_field:
            rename:
    output:
        elasticsearch:
            hosts:
            index:
        file:
            path:
        kafka:
        stdout:
            codec:
```


### logstash
```yaml
logstash:
    -e: # 字符串配置
    -f: # 指定conf配置文件
    -t: # 测试配置文件语法
    --config:
        debug:
    --modules:
    --path:
        data:
        logs:
        settings:
    --pipeline:
    --setup:

logstash-plugin:
    install:
    list:
    uninstall:
```


客户端命令




## Filebeat


一个独立运行的轻量级进程
轻量级日志采集器，用于从文件（如日志文件）读取内容并发送到指定目标




## Kibana


