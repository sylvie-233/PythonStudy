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
    cache:
    export: # 导出lock文件
    help:
    init: # 新建项目脚手架
    lock:
    pip:
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
    python:
    remove: # 移除依赖
    run: # 运行
    self: # 自更新 uv 本身
    sync: # 安装依赖
        --system:
    tool: # uv 工具链
        install:
    tree: # 依赖树
    venv: # 创建虚拟环境
        --python:
    version:
uvx:
```


## 核心内容