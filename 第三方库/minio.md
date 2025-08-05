# minio


## 基础介绍

MinIO SDK


## 核心内容
```yaml
minio:
    commonconfig:
        Tags:
    error:
        S3Error:
    Minio: # minio客户端
        endpoint: # MinIO 服务地址
        access_key: 
        secret_key:
        secure:
        ---
        bucket_exists():
        fget_object():
            bucket_name:
            file_path:
            object_name:
        fput_object(): 
            bucket_name:
            object_name:
            file_path:
            content_type:
        list_buckets():
        list_objects(): 
        make_bucket():
        presigned_get_object():
        presigned_put_object():
        put_object():
        remove_object():
        stat_object():
```
