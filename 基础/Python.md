# Python

>
> `#TODO Python官方文档教程 Tutorial：https://docs.python.org/3/tutorial/index.html`
>
> `#TODO B站最新用Python操作文件（快速上手）P11`
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
    argparse: # 命令行解析工具
        ArgumentParser:
            description:
            add_argument(): # 添加命令行参数
            parse_args(): # 参数解析返回args
    array: # 相同元素数组
        array(): 
            typecode: # 元素类型
            append():
            extend():
            insert():
            pop():
            remove():
            reverse():
            tobytes():
            tolist():
    asyncio: # 异步
        Runner:
        Task:
            cancel():
        TaskGroup:
        all_tasks():
        create_task():
        current_task():
        gather():
        get_event_loop():
        run():
        sleep():
        wait():
    ast: # 抽象语法树
        get_event_loop():
            run_forever():
            run_until_complete():
    base64: # base64编码
        b64decode():
        b64encode():
    builtins:
        __builtins__:
        __debug__:
        __doc__:
        __file__:
        __name__:
        __package__:
        byte:
            decode(): 解码
        complex:
        dict:
            clear():
            copy():
            get():
            items():
            keys():
            pop():
            popitem():
            update():
            values():
        int:
        list:
            append(): # 添加元素
            clear():
            copy():
            count():
            extend():
            index():
            insert():
            pop():
            remove():
            reverse():
            sort():
        set:
            add():
            clear():
            difference():
            intersection():
            issubset():
            pop():
            remove():
            update():
        str:
            encode(): # 编码
            format(): # 格式化字符串
            replace():
            split():
            startswith():
            strip(): # 剔除空白符
            upper(): # 转大写
        abs(): # 取绝对值
        all(): # 判定是否全部为True
        any(): # 判定是否存在True
        ascii(): # 转ascii码
        bin(): # 转二进制
        bool(): # 转布尔值
        bytearray():
        callable(): # 判定对象是否可以调用
        chr(): # 转字符
        dir(): # 获取对象属性、方法
        divmod(): # 整除取余
        enumerate():
        eval(): # 执行表达式
        exce():
        exit(): # 程序退出
        filter(): # 元素过滤
        float(): # 浮点数转换
        format():
        getattr():
        globals():
        hasattr():
        help(): # 获取帮助信息
        hex(): # 转16进制
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
        open(): # 打开文件
            encoding: # 编码
            mode: # 打开模式
                r: # 
                w:
                x:
                a: # 添加、写
                b: # 二进制模式
                t: # 文本模式
            --- # file对象
                close(): # 关闭文件
                read(): # 读取（会移动光标）
                readline(): # 读取一行
                readlines():
                seek(): # 移动光标
                tell(): # 光标位置
                write(): # 写入内容（缓冲区）
        print():
        set(): # 集合
        zip():
    calendar: # 日历
        TextCalendar:
            formatmonth():
        day_name:
        firstweekday():
        isleap():
        prcal(): # 打印一年的日历
        setfirstweekday():
    collections:
        Counter: # 计数器
        defaultdict: # 默认字典 
        deque:
            append():
            appendleft():
        namedtuple:
        UserDict:
        UserList:
        UserString:
    concurrent: # 并发库
        futures:
            ThreadPoolExecutor: # 线程池
                max_workers:
                submit(): # 提交执行任务Task
                    cancel():
                    done():
            as_completed(): # Task完成迭代
            wait(): # Task等待
    contextlib:
    csv:
    datetime:
        datetime:
            now(): # 当前时间
            strftime(): # 格式化时间
        date():
    enum:
    functools: # 函数工具库
        reduce(): # 迭代计数
        wraps():
    gc:
    glob: # 文件索引
        escape():
        glob():
            recursive():
    hashlib:
        md5(): # md5加密
            digest(): # 
            hexdigest(): # 
        new():
        sha1():
        sha224():
    html:
    http:
        cookies:
        server:
    importlib:
        util:
        import_module(): # 动态导入模块
    io:
    ipaddress:
    itertools: # 迭代工具库
        chain(): # 合并
        permutations(): # 
    json:
        dump(): # json序列化
        load(): # json反序列化
    logging: # 日志库（Logger、Handler、Formatter、Filter）
        config:
        handlers:
        FileHandler: # 日志处理器Handler
            addFilter(): # 添加日志过滤器
            setFormatter(): # 添加日志格式化器
            setLevel():
        Filter: # 日志过滤器
            filter():
        Formatter: # 日志格式化器Formatter
        Handler:
        basicConfig(): # 日志基础配置
            filename:
            filemode:
            format: # 日志格式化
            level:
        debug():
        error():
        getLogger(): # 返回日志记录器Logger
            addHandler(): # 添加日志处理器
            setLevel():
        info():
    math:
        pi:
        sqrt(): # 平方根
    multiprocessing: # 多进程
    numbers:
    os:
        curdir:
        pardir:
        path:
            abspath():
            exists(): # 文件是否存在
            getatime():
            isdir(): # 是否为目录
        chdir():
        getcwd(): # 获取当前工作路径
        getcwdb():
        getenv():
        listdir(): # 列出目录列表
        makedirs(): # 创建目录
        rmdir(): # 删除目录
        removedirs():
        rename():
    pathlib:
        Path:
            parent:
            joinpath():
            mkdir():
    pdb:
    pickle:
    pydoc:
    random:
        randint(): # 随机整数
        random(): # 随机浮点数
    queue:
    re: 正则表达式
        findall():
        search():
            group():
    readline:
    select:
    shutil: 文件操作工具类
        move():
    socket: # socket
    socketserver:
    sqlite3: # Connection、Cursor
        connect(): # 连接数据库 返回连接Connection
            :memory: # 内存数据库
            close():
            commit(): # 提交执行
            cursor(): # 获取Cursor游标对象
                rowcount: # 获取受影响的行数
                execute(): # 执行sql语句 
                executemany():
                fetchall(): # 获取所有数据

    string: # 字符串
    struct:
    sys:
        argv: # 程序参数
        builtin_module_names:
        copyright:
        maxsize:
        modules:
        path:
        platform:
        stderr:
        stdin:
        stdout:
        version: # python版本
        exc_info():
        exit():
        getdefaultencoding():
        getfilesystemencoding():
        setdefaultencoding():
    test:
    threading: # 多线程
        Thread:
            getName():
        current_thread():
        local(): # ThreadLocal
    time:
        perf_counter(): # 执行计数
        sleep(): # 线程睡眠
    tkinter:
        colorchooser:
        font:
    tomllib:
    types: # 类型类
        FunctionType:
        MethodType:
    typing: # 类型注解
        Any:
        Callable:
        Dict: # 字典
        List: # 列表
        Mapping:
        NamedTuple:
        NewType: # 自定义类型
        NoReturn:
        Optional: # 可选参数
        Sequence:
        Set: # 几何
        Tuple: # 元组
        TypeVar: # 类型变量T
        Union:
    unittest: # 单元测试
    urllib: # 网络请求
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

# 原串
str = r"xxx"
```





### 控制流程


#### 异常处理




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


### 多线程

