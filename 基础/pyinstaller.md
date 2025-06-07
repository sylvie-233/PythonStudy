# pyinstaller


## 基础介绍

py文件打包为exe程序


### pyinstaller
```yaml
pyinstaller:
    -D: # 文件夹模式，打包生成文件夹
    -F: # 单文件模式，打包只生成一个EXE文件
    -c: # exe程序带控制台
    -d: # debug版本可执行程序
    -i: # 程序图标
    -n: # 名称
    -p: # 指定python模块搜索路径
    -w: # exe程序隐藏控制台
    --add-data: # 添加文件、文件夹
    --add-binary: # 添加文件、文件夹
    --console: # 控制台程序
    --disable-windowed-traceback:
    --help:
    --hidden-import: # 添加依赖的模块
    --icon:
    --noconsole:
    --nowindowed: # 无窗口
    --onedir: # 单目录
    --onefile: # 单文件
    --paths: # 指定python模块搜索路径
    --splash: # 程序启动画面
    --version:
    --windowed:
```


### main.spec
```yaml
main.spec:
    Analysis: # 打包分析，配置入口脚本文件
        binaries: # 包含的二进制文件，外部二进制文件（如 DLL、so 文件）
        cipher: # 加密
        datas: # 资源文件
        excludes: # 排除的模块
        hiddenimports: # 隐式导入的模块，没有自动检测到的隐式导入模块
        hookspath: # 自定义 hook 路径
        pathex: # 需要扫描的路径，项目所在路径
        runtime_hooks: # 运行时钩子
        win_no_prefer_redirects:
        win_private_assemblies:
        ---
        binaries: # 二进制文件
        datas:
        pure: # Analysis 对象中的纯 Python 代码（所有分析出来的 Python 文件）
        scripts: # 入口脚本
        zipfiles:
        zipped_data: # 所有依赖的 Python 模块
    COLLECT: # 用于将生成的可执行文件、二进制文件、数据文件等收集到一起，依赖之前生成的 EXE 文件
    EXE: # 生成exe配置，依赖之前生成的 PYZ 文件
        console:
        icon:
    PYZ: # 打包核心，PYZ 对象将所有 Python 代码打包成一个 .pyz 文件，.pyz 文件是一个包含了你所有 Python 脚本的压缩归档文件
        cipher: # .pyz 文件进行加密
```

pyinstaller打包配置


## 核心内容



### Resource Path
```python
import os
import sys

# 获取可执行文件所在的目录
if getattr(sys, 'frozen', False):  # 当应用打包后，sys.frozen为True
    base_path = sys._MEIPASS  # 获取临时文件路径
else:
    base_path = os.path.dirname(__file__)  # 如果是开发环境，使用脚本的路径

# 资源文件的路径
resource_path = os.path.join(base_path, 'resources', 'config.json')

# 读取资源文件
with open(resource_path, 'r') as file:
    config = file.read()

print(config)
```

资源文件路径问题


