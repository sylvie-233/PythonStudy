# minio


## 基础介绍

MinIO SDK

- 创建的Bucket桶默认是private私有的，得设置公共访问策略


## 核心内容
```yaml
minio:
    commonconfig:
        CopySource:
        Tags:
    error:
        S3Error:
    notificationconfig:
        NotificationConfig:
            queue_configs:
        QueueConfig:
            arn: # 目标类型和队列名
            events: # 监听事件
    post_policy:
        PostPolicy:
    sse:
        SseCustomerKey:
        SseS3:
    Minio: # minio客户端
        endpoint: # MinIO 服务地址
        access_key: # 账号 
        secret_key: # 密码
        secure: # 是否使用 HTTPS
        ---
        bucket_exists(): # 检查桶是否存在
        copy_object(): # 复制对象
        delete_bucket_encryption():
        delete_bucket_lifecycle():
        fget_object(): # 保存到本地文件
            bucket_name:
            file_path:
            object_name:
        fput_object(): # 直接上传文件
            bucket_name:
            object_name:
            file_path:
            content_type:
        get_bucket_encryption():
        get_bucket_lifecycle():
        get_bucket_notification():
        get_bucket_policy(): # 获取桶的策略
        get_object(): # 以流的方式获取
        list_buckets(): # 列出所有桶
        list_incomplete_uploads():
        list_objects(): # 列出所有对象
        make_bucket(): # 创建桶
        presigned_get_object(): # 生成 GET 访问 URL
        presigned_post_policy():
        presigned_put_object(): # 生成 PUT 上传 URL
        put_object(): # 流式上传
        remove_all_bucket_notification():
        remove_bucket(): # 删除桶
        remove_object(): # 单个对象删除
        remove_objects(): # 批量删除
        set_bucket_encryption(): # 桶加密
        set_bucket_lifecycle():
        set_bucket_notification():
        set_bucket_policy(): # 设置桶的策略 json
        set_bucket_tags():
        stat_object(): # 获取对象信息
```


### Tag

标签


### Stat

对象信息

### Presigned

预签名：一个短期有效的 URL，让别人临时访问或上传对象
URL 内包含了 签名信息，服务器验证签名合法性后允许访问



### Policy
```yaml
Policy:
    Version: # 策略语法版本，固定 2012-10-17
    Statement:
        Effect: # 允许或拒绝权限
        Action: # 权限列表
            s3:DeleteObject:
            s3:GetObject:
            s3:GetBucketLocation:
            s3:ListAllMyBuckets:
            s3:PutObject:
            s3:ListBucket:
        Principal: # 指定该策略适用于哪些用户 {"AWS": ["*"]}表示匿名/所有用户
        Resource: # ARN 列表，指定策略作用的桶或对象，arn:aws:s3:::xxx
        Condition: # 限制策略生效条件，例如 IP、时间等
            IpAddress:
                aws:SourceIp:
```

策略

公共访问策略
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": ["s3:GetObject"],
            "Effect": "Allow",
            "Principal": {"AWS": ["*"]},
            "Resource": ["arn:aws:s3:::uploads/*"]
        }
    ]
}
```

Resource资源格式：
```
arn:aws:s3:::bucket_name        # 指桶本身
arn:aws:s3:::bucket_name/*      # 指桶下所有对象
arn:aws:s3:::bucket_name/prefix/* # 指桶下特定目录
```

### Encryption

加密：存储加密


### Notification

通知，事件监听（与redis、消息队列绑定）