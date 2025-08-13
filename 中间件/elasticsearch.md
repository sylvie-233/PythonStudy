# Elasticsearch


## 基础介绍


分布式搜索引擎



## 核心内容
```yaml
GET:
    /_analyze: # 分词分析接口
        analyzer:
            standard:
        text:
        --- # /_analyze: 测试文本查询结果、响应token
        tokens:
            start_offset:
            token:
    /_cat/indices: # 查看所有索引信息
    /_cat/nodes: # 查看节点列表
    /_cat/shards: # 查看索引分片分布
    /_cluster/health: # 查看集群健康状态
        --- 
        cluster_name:
        status:    
        number_of_nodes:
        active_primary_shards:
        active_shards:
    /_cluster/state: # 查看集群状态
    /_tasks: # 列出所有任务
    /:index: # /index: 查看索引信息
        --- # /index: 查询索引响应结果
        _index:
            aliases:
            mappings:
                properties:
        settings:
    /:index/_count: # /index/_count: 获取文档数量
    /:index/_doc/:id: # /:index/_doc/:id: 根据id查询文档
        --- # 查询文档响应结果
        _index:
        _source: # doc文档数据
        _type:
        _id:
        found:
    /:index/_mapping: # 查看索引 Mapping
    /:index/_search: # /index/_search: 条件查询文档
        aggs: # 聚合查询
            aggs: # 组合聚合
                stats:
                    field:
            terms:
                field:
                size:
        from: # skip个数
        query: # 条件查询
            bool: # 布尔查询
                filter:
                must: # 必须
                    match:
                must_not:
                should:
            highlight: # 高亮字段
                fields:
                    post_tags:
                    pre_tags:
            match: # 支持分词匹配
            match_all:
            multi_match:
                fields:
                query:
            range: # 范围查询
                gte:
                lte:
            term: # 精确匹配
                value:
        size: # limit个数
        sort: # 排序
            asc:
            desc:
        --- # /index/_search: 条件查询文档响应结果
        took:
        timed_out:
        _shards:
        hits:
            total:
                value:
            max_score:
            hits:
                _index:
                _id:
                _score:
                _source: # 原始响应文档数据
                highlight: 
        aggregations:
            buckets:
                key:
                doc_count:
    /:index/_settings: # 查看索引 Setting
POST:
    /_aliases: # 别名操作
    /_bulk: # /_bulk: 批量操作
        delete:
        index:
    /:index/_close: # 关闭索引
    /:index/_doc: # /index/_doc: 新增文档（自动生成 ID）
        ---
        _index:
        _type:
        _id:
        _version:
        result:
    /:index/_open: # 打开索引
    /:index/_update/:id: # /index/_update/id: 更新文档字段（增量）
        doc: # 更新指定的字段
        ---
        _index:
        _id:
        result:

PUT:
    /_index_template/:template: # 自定义索引模板
        index_patterns:
        template:
            mappings:
                properties:
            settings:
    /:index: # /:index: 创建索引、添加文档结构
        mappings: # 文档结构
            properties: # 属性定义
                analyzer:
                index:
                properties:
                type: # 属性类型
                    keyword:
                    text:
        --- # /:index: 创建索引响应结果
        acknowledged:
        shards_acknowledged:
        index:
    /:index/_doc/:id: # /:index/_doc/:id: 插入文档（指定 ID）
        ---
        _index:
        _type:
        _id:
        _version:
        result:
    /:index/_mapping: # /:index/_mapping: 新增字段
        properties:
    /:index/_settings: # 修改索引设置
        number_of_replicas: # 索引副本数
DELETE:
    /:index: # /index: 删除索引
        ---
        acknowledged:
    /:index/_doc/:id: # 删除指定文档
HEAD:
    /:index: # 判断索引是否存在
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


