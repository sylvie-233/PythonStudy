# pylint



## 基础介绍

python版eslint
python代码格式化


### pylint
```yaml
pylint:
    --disable:
        C0103: # 命名不规范
        C0114: # 缺少模块 docstring
        E1101: # 访问不存在的成员（通常来自未导入的库）
        R0903: # 类太简单
        W0611: # 未使用导入
        W0612: # 未使用变量
    --generate-rcfile:
    --output-format:
```


#### .pylintrc
```yaml
.pylintrc:
    FORMAT: # 格式控制
        max-line-length:
        indent-string:
    MAIN: # 主配置
    MESSAGES CONTROL: # 消息控制
        disable:
            trailing-whitespace:
    TYPECHECK: # 类型检查
        ignored-modules:
```


pylint配置文件


## 核心内容