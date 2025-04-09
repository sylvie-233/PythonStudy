# postman


## 基础介绍

API 接口测试工具


## 核心内容
```yaml
postman:
    pm:
        environment: # 环境变量
            get():
            set():
        globals:
        request:
            headers:
                add():
        response:
            body:
            to:
                have:
                    responseTime:
                        lessThan():
                    status():
        expect():
        test(): # 测试方法
```



### Script

运行脚本
- Pre-Request
- Post-Response