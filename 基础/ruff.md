# ruff

## 基础介绍

python 代码格式化工具


### ruff
```yaml
ruff:
    check: # 代码检查
        --diff:
        --fix: # 代码修复
        --watch:
    rule:
    config:
    linter:
    clean:
    format: # 代码格式化
    server:
    analyze:
    version:
    help:
```


### pyproject.toml
```yaml
pyproject.toml:
    tool.ruff:
        lint:
            extend-select: # 规则继承
            ignore: # 规则忽略
```


## 核心内容
