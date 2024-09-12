# Python

>
> `#TODO Python官方文档教程 Tutorial：https://docs.python.org/3/tutorial/index.html`
>
> `#TODO B站最新用Python操作文件（快速上手）P6`
>


## 基础介绍

### python
```yaml
python:
    --help:
    -m: 模块执行 # 直接执行文件 和 执行模块之间存在区别
        pdb:
        pydoc:
```

### pip
```yaml
pip:
    -i: 指定镜像源
    freeze: 
    install: 安装包
    search: 搜索包
```

pip镜像源：
- `https://pypi.tuna.tsinghua.edu.cn/simple/`




## 核心内容

```yaml
std:
    abc:
    argparse:
    array:
    asyncio:
        get_event_loop():
            run_forever():
            run_until_complete():
    ast: 抽象语法树
        parse():
    base64:
    builtins:
        byte:
            decode(): 解码
        str:
            format(): # 格式化字符串
            upper():
        abs():
        ascii():
        bin():
        bool():
        bytearray():
        callable():
        chr():
        dict():
        dir(): 查看包中信息
        divmod():
        enumerate():
        eval():
        exce():
        filter():
        float():
        format():
        getattr():
        globals():
        hasattr():
        help():
        hex():
        id():
        input():
        int():
        isinstance():
        issubclass():
        iter():
        len():
        list():
        map():
        max():
        next():
        object():
        open(): 打开文件
            encoding: # 编码
            mode: # 打开模式
                r: # 
                w:
                x:
                a: # 添加、写
                b: # 二进制模式
                t: # 文本模式
            --- # file对象
                close():
                read(): # 读取（会移动光标）
                readline():
                readlines():
                seek(): # 移动光标
                write():
        print():
    calendar:
    cmd:
    collections:
    contextlib:
    csv:
    datetime:
        date():
    enum:
    functools:
        wraps():
    gc:
    glob:
    hashlib:
    html:
    http:
        cookies:
        server:
    importlib:
    io:
    ipaddress:
    json:
        dump():
        load():
    logging:
        config:
        handlers:
    math:
    multiprocessing:
    numbers:
    os:
        path:
            exists(): 文件是否存在
        getenv():
    pathlib:
        Path:
            parent:
            joinpath():
            mkdir():
    pdb:
    pickle:
    pydoc:
    random:
    queue:
    re: 正则表达式
        findall():
    readline:
    select:
    shutil: 文件操作工具类
    socket:
    socketserver:
    sqlite3:
    string: 字符串
    struct:
    sys:
        argv:
        builtin_module_names:
        copyright:
        maxsize:
        modules:
        path:
        platform:
        stderr:
        stdin:
        stdout:
        version:
        exc_info():
        exit():
        getdefaultencoding():
        getfilesystemencoding():
        setdefaultencoding():
    test:
    threading:
    time:
    tkinter:
        colorchooser:
        font:
    tomllib:
    types:
    typing:
        List:
        Optional:
    unittest:
    urllib:
        error:
        parse:
        request:
        response:
    venv:
    warnings:
    wsgiref:
    xml:
    zlib:
```

### 数据类型


内置变量:
```yaml
内置变量:
    __file__: 当前文件名
    __name__: 当前模块名（执行模块为__main__）
```


#### 字符串
```python
# 多行字符串
str = """
    多行字符串内容
"""

# 模板字符串
str = f"{ var }"
```





### 控制流程







### 面向对象

Class为type类型的对象实例，基类为object

object为type类型的对象实例，没有基类

type为type自身类型的对象实例，基类为object

（type是type，object也是type；type继承自object，object没有继承；Class是type，继承自object）

`class = type(classname, superclass, attributedict)`

- type为对象的顶点，所有对象都创建自type。
- object为类继承的顶点，所有类都继承自object。


#### 魔术方法&属性
```yaml
:

```


#### metaclass

metaclass影响类本身的创建行为

metaclass继承自type

一旦把自定义类类型 MyClass 的 metaclass 设置成 MyMeta，MyClass 就不再由原生的 ty

类对象创建`__call__() -> __new__() -> __init__()` 


#### 装饰器

![Python基础装饰器](../.assets/python基础装饰器.png)



### 模块


module -> package -> library