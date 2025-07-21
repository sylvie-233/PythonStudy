# jupyter


## 基础介绍

Jupyter 是一个 Web 应用程序，允许你创建和共享文档，文档中可以包含代码、数学公式、可视化内容、以及文本说明。常用在 Python、R 和 Julia 等语言的交互式计算中


### jupyter
```yaml
jupyter:
    kernelspec: # 安装的内核
        list:
    nbconvert: # 把 .ipynb 文件转成其他格式
    notebook:
        --generate-config:
        --no-browser:
        --notebook-dir:
        --port:
    notebookextension:
    troubleshoot: # 打印环境信息，帮助你定位问题
```


## 核心内容
```yaml
jupyter notebook:
    %run: # 运行外部文件
    %time: # 耗时统计
    %timeit: # 多次运行耗时统计
        -n:
        -r:
    %who: # 当前环境值
    %who_ls:
    %whos:
    %%timeit: # 多行运行耗时测试
    lsmagic:
```



### 快捷键
```yaml
jupyter notebook:

```
