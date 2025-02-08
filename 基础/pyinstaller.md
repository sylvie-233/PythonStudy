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
    --disable-windowed-traceback:
    --help:
    --hidden-import:
    --paths: # 指定python模块搜索路径
    --splash: # 程序启动画面
    --version:
```




## 核心内容
```yaml
:
```


### .spec
```yaml
Analysis:
    datas:
EXE:
PYZ:
```

pyinstaller配置
