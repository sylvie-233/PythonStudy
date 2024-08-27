# poetry

## 基础介绍


python的项目包依赖管理工具，类似php的composer



### poetry
```yaml
poetry:
    add: 添加第三方模块
        --dev:
    build: 构建(在dist目录生成whl、.tar.gz两个文件)
    config:
        --list:
    env: 虚拟环境
        exit: 退出虚拟环境
        ---
        remove:
        use: 创建&使用 虚拟环境(./venv)

    help:
    init: 初始化项目(pyproject.toml)
    new: 新建项目
    publish: 发布项目到pypi中
    remove:
    shell: 进入虚拟环境
    show: 显示已安装包
    update:
```


### pyproject.toml
```yaml
build-system:
    build-backend:
    requires:
tool:
    poetry:
        authors:
        dependencies:
            python:
        descritpion:
        name: 包名(源码目录名)
        packages:
            include:
        readme:
        version:
```


## 核心内容


