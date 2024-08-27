# Python


## 基础介绍





## 核心内容

```yaml
std:
    abc:
    argparse:
    array:
    asyncio:
    ast: 抽象语法树
        parse():
    base64:
    builtins:
        abs():
        ascii():
        bin():
        bool():
        bytearray():
        callable():
        chr():
        dict():
        dir():
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
        open():
        print():
    calendar:
    cmd:
    collections:
    contextlib:
    csv:
    datetime:
    enum:
    functools:
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
    logging:
        config:
        handlers:
    math:
    multiprocessing:
    numbers:
    os:
        path:
    pathlib:
    pdb:
    pickle:
    pydoc:
    random:
    queue:
    re: 正则表达式
    readline:
    select:
    shutil: 文件操作工具类
    socket:
    socketserver:
    sqlite3:
    string: 字符串
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


### 面向对象

Class为type类型的对象实例，基类为object

object为type类型的对象实例，没有基类

type为type自身类型的对象实例，基类为object

（type是type，object也是type；type继承自object，object没有继承；Class是type，继承自object）

`class = type(classname, superclass, attributedict)`

- type为对象的顶点，所有对象都创建自type。
- object为类继承的顶点，所有类都继承自object。



#### metaclass

metaclass影响类本身的创建行为

metaclass继承自type

一旦把自定义类类型 MyClass 的 metaclass 设置成 MyMeta，MyClass 就不再由原生的 ty

类对象创建`__call__() -> __new__() -> __init__()` 
