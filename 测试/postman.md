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
            unset():
        globals: # 全局变量
        request:
            headers:
                add():
        response:
            body:
            code: # 响应状态码
            responseTime:
            to:
                be:
                    oneOf():
                have:
                    responseTime:
                        lessThan():
                    header():
                    status():
                include():
            json():
            text():
        variables: # 普通变量
        expect():
        sendRequest():
        test(): # 测试方法
```



### Script

运行脚本
- Pre-Request
- Post-Response

脚本执行流程：（collection -> folder -> request）
1. collection pre-request script
2. folder pre-request script
3. request pre-request script
4. collection test
5. folder test script
6. request pre-request test
