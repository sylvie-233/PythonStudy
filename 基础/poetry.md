# poetry

## 基础介绍

python的项目包依赖管理工具（类似php的composer）


`POETRY_VIRTUALENVS_PATH`: poetry安装虚拟环境目录
`POETRY_VIRTUALENVS_IN_PROJECT`：在项目内创建虚拟环境
虚拟环境目录的名称：`{project}-{hash}-{pythonversion}`


### poetry
```yaml
poetry:
    -h:
    -n:
    -q:
    -v:
    -C:
    -V:
    --group:
    --version:
    about: # poetry相关信息
    add: # 添加第三方模块
        -E:
        --dev:
    build: # 构建(在dist目录生成whl、.tar.gz两个文件)
    cache:
        clear:
        list:
    check: # 检查pyproject.toml语法
    config:
        --list:
        --local:
        --unset:
        cache-dir: # package缓存目录
        installer:
            modern-installation:
        virtualenvs:
            in-project: # 虚拟环境放在项目下（默认false）
            options:
                no-pip:
            prompt:
    debug:
        info:
        resolve:
    env: # 虚拟环境
        exit: # 退出虚拟环境
        ---
        activate: # 激活虚拟环境
        info:
        list: # 列出所有的虚拟环境
        remove:
        use: # 创建&使用 虚拟环境(./venv)
    export: # 导出requirements.txt文件
    help:
    init: # 初始化项目(pyproject.toml、poetry.lock)
        -n:
    install: # 安装项目依赖
    list:
    lock:
    new: # 新建项目
    publish: # 发布项目到pypi中
    remove:
    run: # 在虚拟环境中运行命令
    search:
    self:
        add:
        install:
        lock:
        remove:
        show:
        update:
    shell: # 进入虚拟环境venv
        exit: # 退出虚拟环境
    show: # 显示项目依赖
    source: # 镜像源管理
        add:
        remove:
        show:
    update:
    version:
```


#### pyproject.toml
```yaml
build-system:
    build-backend: # 构建系统依赖
    requires:
tool:
    poetry: # poetry构建工具配置
        authors:
        dependencies:
            python:
        descritpion:
        dev-dependencies:
        extras:
        group: # 配置分组
            dev: # 开发配置
                dependencies:
        name: # 包名(源码目录名)
        packages: # 源码目录（可设置多个目录，都会被打包）
            from:
            include:
        plugins: # 插件
        readme:
        scripts: # 自定义脚本片段
        version:
project: # 项目配置
    authors:
        email:
        name:
    dependencies: # 项目模块依赖
    description: # 项目描述
    name: # 项目包名
    readme:
    requires-python: # python版本依赖
    version: # 项目版本
```

#### poetry.lock
```yaml
poetry.lock:
```

包依赖版本锁




## 核心内容

### 缓存

`~/AppData/Local/pypoetry/Cache`
- /artifacts: 包缓存
- /cache:
- virtualenvs: 虚拟环境

