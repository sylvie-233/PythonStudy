# pre-commmit


## 基础介绍

python git hooks钩子工具

### pre-commit
```yaml
pre-commit:
    autoupdate:
    clean:
    install: # 安装脚本到.git目录下
    run: # 手动运行脚本
        --all-files:
    uninstall:
```


#### .pre-commit-config.yaml
```yaml
.pre-commit-config.yaml:
    repos: # 仓库，可配置多个repo
        repo:
        rev: # 版本
        hooks: # hooks
            id: # 使用指定的hook插件    
```


## 核心内容


### .pre-commit-hooks

自定义pre-commit hook钩子


#### hooks.yaml
```yaml
hooks.yaml:
    id:
    name:
    entry: # 入口脚本
    language:
    files: # 匹配文件
```