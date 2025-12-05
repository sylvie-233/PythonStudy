# Terraform


## 基础介绍

Terraform 是用来用代码管理基础设施的工具，能创建 AWS/Azure/GCP/K8s/阿里云等各种资源
云平台资源管理工具


### terraform
```yaml
terraform:
    -v:
    apply: # 应用（执行）
    destroy: # 销毁
    fmt:
    import:
    init: # 初始化
    plan: # 规划（预览）
    show:
    state:
        list:
    validate:
```

terraform命令行工具



## 核心内容
```yaml
tf:
    provider: # 云服务提供商
        region: # 服务区域
    resource: # 云服务资源
        aws_instance:
            web:
                ami:
                instance_type:
                tags: # 标签
                    Name:
        kubernetes_deployment:
            nginx:
    data:
    variable:
    output:
        value:
```
