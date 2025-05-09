# WEB


## 基础介绍

WEB技术分析


### 系统架构


#### 单体架构


##### SOLID

SOLID 是面向对象编程中设计原则的一个缩写，用来指导开发者编写 可维护、可扩展、低耦合、高内聚 的代码，每个字母代表一个设计原则


##### IOC

控制反转



##### MVC






##### DDD

实现 DDD 时，关键是将复杂的业务逻辑进行建模，分成 实体（Entity）、值对象（Value Object）、聚合根（Aggregate Root） 和 服务（Service），并通过 仓储（Repository） 来持久化和管理这些对象

![DDD领域设计](image.png)

- Controller:
- Command:
- Query:
- Service: 聚合根无法完成业务逻辑时的替代品、可跨领域
- Domain
    - Factory:
    - Event:
    - Event Handler:
- Infrastructure:
    - Repository:





#### 微服务






#### Serverless





### 接口设计



#### WebSocket




#### GraphQL

GraphQL 是一种 API 查询语言（Query Language for APIs），也是一套服务器端运行的执行规范。
它由 Facebook 在 2012 年提出，2015 年开源，目的是取代传统的 REST API 通信方式
允许前端或客户端：
- 精确地指定 想要什么数据
- 一次请求 就拿到所有需要的信息
- 避免过多的接口调用 和 冗余数据

GraphQL核心概念：
- Schema	定义数据结构和查询规则（就像数据库建表一样）
- Query	客户端发起的读取数据请求
- Mutation	客户端发起的修改数据请求（新增、更新、删除）
- Resolver	服务器端处理 Query 或 Mutation 的实际函数
- Subscription	用于实时推送数据变化（如 WebSocket 通信）- 


### 数据库


#### ElasticSearch





### 消息队列




### 权限认证



### 日志



### API文档




### 第三方服务




### CI & CD


部署、运维





