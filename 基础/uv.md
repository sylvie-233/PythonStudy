# uv



## 基础介绍

uv 是一个现代的 Python 包管理器，由 Astral 开发，目标是 比 pip 和 virtualenv 更快、更安全、更现代化
兼容 requirements.txt 和 pyproject.toml


### uv
```yaml
uv:
    --version:
    add: # 添加依赖
    build:
    cache: # 第三方包安装目录
        dir:
    export: # 导出lock文件
    help:
    init: # 新建项目脚手架
    lock: # 生成 第三方包 版本文件
    pip: # pip包管理
        check:
        compile:
        download:
        freeze:
        install:
        list:
        show:
        sync:
        uninstall:
    publish:
    python: # python解释器
        install: # 安装其它python版本
        list:
    remove: # 移除依赖
    run: # 运行
    self: # 自更新 uv 本身
    sync: # 安装依赖（同步）
        --system:
    tool: # uv 工具链
        dir: # 工具链安装目录
        install:
        run: # 运行工具
    tree: # 依赖树
    venv: # 虚拟环境
        --python:
    version:
uvx:
```

### pyproject.yaml
```yaml
pyproject.yaml:
    project: # 项目
        dependencies: # 项目依赖
    tool: # 工具
        uv:
            index-url: # 第三方包 镜像
        pytest:
            ini_options:
                testpaths:
                pythonpath:
    build-system: # 构建 build统一入口
        requires:
        build-backend: # build使用的 构建后端
```


### .vscode
```yaml
settings.json:
    python.analysis.extraPaths: # src
    python.testing.pytestArgs: # tests
```


## 核心内容