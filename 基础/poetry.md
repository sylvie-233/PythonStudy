# poetry

## 基础介绍

python的项目包依赖管理工具（类似php的composer）



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
        info:
        list:
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
    show: # 显示已安装包
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
    build-backend:
    requires:
tool:
    poetry:
        authors:
        dependencies:
            python:
        descritpion:
        group: # 配置分组
        name: # 包名(源码目录名)
        packages:
            include:
        readme:
        version:
```

#### poetry.lock
```yaml
poetry.lock:

```

## 核心内容

### 缓存

`~/AppData/Local/pypoetry/Cache`
- /artifacts: 包缓存
- /cache:
- virtualenvs: 虚拟环境

