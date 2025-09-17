# mypy




## 基础介绍


python版tsconfig.json



mypy 是 Python 的静态类型检查器，用于在运行前检测类型错误。
配合 Python 的 类型注解（type hints），可以在不影响运行的情况下，增强代码的可靠性、可维护性、自动补全体验
- 类型推导
- 插件机制
- 策略配置
- 复杂类型检查 

`# type: ignore` 忽略检查


### mypy
```yaml
mypy:
    --check-untyped-defs: # 检查没有类型注解的函数体
    --disallow-incomplete-defs: # 禁止缺少参数类型但有返回值注解的函数
    --disallow-untyped-defs: # 禁止没有类型注解的函数定义
    --ignore-missing-imports: # 忽略第三方库未提供类型的报错（推荐）
    --show-error-codes: # 显示每条报错的错误码（便于定制规则）
    --strict: # 开启所有严格模式检查
    --warn-unused-ignores: # 报告没有实际作用的
```


#### .mypy.ini
```yaml
mypy:
    disallow_untyped_defs:
    python_version:
    ignore_missing_imports:
    show_error_codes:
    strict_optional:
    warn_unused_ignores:
```


#### settings.json
```yaml
settings.json:
    python.linting.enabled:
    python.linting.lintOnSave:
    python.linting.mypyArgs:
    python.linting.mypyEnabled:
```



## 核心内容
```yaml
mypy:
    nodes:
        CallExpr:
    plugin:
        Plugin:
    types:
        Instance:
```

### 插件

自定义声明文件（代码类型提示）



