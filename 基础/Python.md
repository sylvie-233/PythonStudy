# Python

>
> `#TODO Python官方文档教程 Tutorial：https://docs.python.org/3/tutorial/index.html`
>
> ``
>


## 基础介绍

### python
```yaml
python:
    --help:
    -m: # 模块执行 直接执行文件 和 执行模块之间存在区别
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


### pdb
```yaml
pdb:
    break: # 断点
    clear:
    continue: # 下一个断点
    disable: # 禁用断点
    down:
    enable:
    help:
    list:
    longlist:
    next:
    print:
    step: # 步入
    until:
    up: # 上下文切换
    where: # 函数调用堆栈
```


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
        Event: # 事件
            set(): # 事件触发
            wait():
        Runner:
        Task:
            cancel():
        TaskGroup:
        all_tasks():
        create_task(): # 根据co对象创建task
        current_task():
        gather(): # task聚合
        get_event_loop():
        run():
        sleep(): # 异步sleep
        to_thread(): # 异步多线程包装
        wait():
        get_event_loop():
            run_forever():
            run_until_complete():
    ast: # 抽象语法树
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
        bool:
        bytes: # 字节数组
            decode(): # 解码
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
        float:
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
            title(): # 首字母大写转换
            upper(): # 转大写
        tuple:
        StopIteration: # 停止迭代异常
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
        enumerate(): # 带索引迭代
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
            # file对象，可迭代遍历每行
            close(): # 关闭文件
            flush(): 
            read(): # 读取（会移动光标）
            readline(): # 读取一行
            readlines():
            seek(): # 移动光标
            tell(): # 光标位置
            write(): # 写入内容（缓冲区）
        print():
        set(): # 集合
        type():
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
    configparser: # ini配置文件解析
        ConfigParser: # ini配置文件解析(段落 -> 选项)
            add_section(): # 添加节点
            get(): # 获取value值
            has_section():
            items(): # 根据名称获取指定段落的k-v
            read(): # 读入配置
            remove_option():
            remove_section():
            sections(): # ini段落
            set(): # 设置value值
            write(): # 写出配置
    contextlib:
        contextmanager:
    csv:
    dataclasses:
        dataclass(): # 数据类dataclass
        asdict():
    datetime:
        datetime:
            now(): # 当前时间
            strftime(): # 格式化时间
        date():
    enum:
        Enum:
        Flag: # 按位枚举
        IntFlag:
        unique:
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
            fileConfig():
        handlers:
            RotatingFileHandler: # 循环覆盖日志
        DEBUG:
        INFO:
        FileHandler: # 日志处理器Handler
            addFilter(): # 添加日志过滤器
            setFormatter(): # 添加日志格式化器
            setLevel():
        Filter: # 日志过滤器
            filter():
        Formatter: # 日志格式化器Formatter
        Handler:
        StreamHandler:
            setFormatter():
            setLevel():
        basicConfig(): # 日志基础配置
            filename:
            filemode:
            format: # 日志格式化
                asctime: # 时间
                filename: # 文件名
                funcName:
                levelname:
                lineno:
                message: # 日志内容
                pathname:
                process:
                thread:
                threadName:
            level:
        critical():
        debug():
        error():
        getLogger(): # 返回日志记录器Logger
            addHandler(): # 添加日志处理器
            setLevel():
        info():
        warning():
    math:
        pi:
        sqrt(): # 平方根
    multiprocessing: # 多进程
        Pool: # 进程池
            starmap():
        Process:
            target:
            join():
            start():
        Value: # 共享内存
            value:
    numbers:
    operator:
        attrgetter:
        itemgetter:
    os:
        curdir:
        pardir:
        path:
            abspath(): # 绝对路径
            dirname(): # 上级目录名
            exists(): # 文件是否存在
            getatime():
            isdir(): # 是否为目录
            join(): # 路径合并
        chdir():
        getcwd(): # 获取当前工作路径
        getcwdb():
        getenv(): # 获取环境变量
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
    queue:
    random:
        randint(): # 随机整数
        random(): # 随机浮点数
    re: # 正则表达式
        findall():
        search():
            group():
    readline:
    select:
    shutil: # 文件操作工具类
        copy():
        copytree():
        make_archive(): # 压缩包生成
            base_name:
            format:
                zip:
            root_dir:
        move():
        retree():
        uppack_archive(): # 解压压缩包
            filename: # 解压文件名
            extract_dir: # 解压目录
            format: # 解压格式
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
        digits:
    struct:
    sys:
        argv: # 程序参数
        builtin_module_names:
        copyright:
        maxsize:
        modules:
        path: # path模块搜索路径
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
        Barrie:
        Condition:
        Event:
        Lock:
        RLock:
        Semaphore:
        Thread:
            getName():
            is_alive():
            isDaemon():
            join():
            setDaemon():
            start():
        Timer:
        activeCount():
        current_thread():
        enumerate():
        get_ident():
        local(): # ThreadLocal
    time:
        perf_counter(): # 执行计数
        sleep(): # 线程睡眠
    tkinter:
        colorchooser:
        font:
        messagebox: # 消息窗口
            askokcancel():
            showerror():
            showinfo():
            showwarning():
        ttk:
            Combobox:
                textvariable:
                values:
        Button:
            command: # 函数绑定
            font:
            text:
        CheckButton:
            onvalue:
            text:
            variable:
        Entry: # 输入框组件
            font:
            state:
            textvariable: # 绑定变量
            width:
        IntVar: # 整型变量
        Label: # 标签组件
            bg:
            fg: # 前景色
            font:
            text:
            grid(): # 网格布局
            pack(): # 填充布局
            place(): # 自定义布局（位置）
        ListBox:
            insert():
        Menu: # 菜单组件（可嵌套）
            tearoff:
            add_cascade():
                label: # 菜单标签
            add_command(): # 子功能标签
        RadioButton: # 单选按钮
            text:
            value:
            variable:
        StringVar: # 字符串变量（组件值绑定）
            get():
            set():
        Tk: # 窗口程序
            attributes(): # 窗口属性
                -alpha:
                -topmost:
            config():
                menu: # 菜单栏
            configure(): # 窗口配置 
                bg: # 窗口背景颜色
            destroy(): # 窗口销毁
            geometry(): # 窗口大小（位置）
            iconbitmap(): # 窗口图标
            mainloop(): # 开启事件循环
            maxsize(): # 屏幕尺寸
            protocol(): # 绑定钩子函数
            resizable(): # 屏幕缩放
            title(): # 窗口标题
        TopLevel: # 顶层窗口（内层窗口）
            focus_set():
    tomllib:
    types: # 类型类
        FunctionType:
        MethodType: # 方法类型
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
        Sequence: # 只读列表
        Set: # 集合
        Tuple: # 元组
        TypeVar: # 类型变量T
        Union: # 联合参数
    unittest: # 单元测试
    urllib: # 网络请求
        error:
        parse:
        request:
        response:
    venv:
    warnings:
    weakref:
        WeakKeyDictionary:
        WeakSet:
        WeakValueDictionary: # 弱引用字典
        ref():
    wsgiref:
    xml:
        dom:
        etree:
            ElementTree: # 标签树类 （根标签）（可迭代遍历）
                find():
                findall():
                findtext():
                getroot(): # 获取根标签
                iter():
                makeelement(): # 创建标签元素
                parse(): # 解析文件
                write(): # xml内容写出
                XML():
        parsers:
        Element: # 标签元素类
            attrib:
            tag: # 标签名
            text: # 标签文本内容
            append(): # 添加子标签
            extend():
            find():
            findall():
            findtext():
            getchildren():
            getiterator():
            insert():
            iter(): # 迭代指定标签
            iterfind():
            itertext():
            remove(): # 删除标签
            set(): # 修改标签attr
        SubElement: # 创建子标签
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
```yaml
:
    for ... else:
    for ... in:
    if ... elif ... else:
    while ... else:
        break:
        continue:
    with ... as:
```





#### 异常处理



#### 上下文管理

with语句，`__enter__()`、`__exit__()`

上下文管理可以与装饰器结合起来
```python
@contextmanager
def change_dir(path: str):
    old_path = os.getcwd()
    os.chdir(path)
    yield old_path  # yield之前为__enter__()内部实现，yield返回值为__enter__()返回值
    os.chdir(old_path) # yield之后为__exit__()内部实现

with change_dir("/xxx") as old_path:
    pass
```


### 函数


#### 生成器
```python
def simple_generator():
    yield 1
    yield 2
    yield 3

gen = simple_generator() # 获取生成器对象
print(next(gen))  # 输出: 1
print(next(gen))  # 输出: 2
print(gen.__next__())  # 输出: 3
next(gen)  # 如果再调用 next(gen)，将抛出 StopIteration 异常



def simple_coroutine():
    print("Start coroutine")
    x = yield 1
    print(f"Received: {x}")
    y = yield 2
    print(f"Received: {y}")

gen = simple_coroutine() # 获取生成器对象
# 首次调用生成器时，必须传递 None，因为生成器还没有遇到任何 yield 表达式。传其他值会报错
print(gen.send(None)) # 输出: Start coroutine, 然后输出: 1
print(gen.send(10))  # 输出: Received: 10, 然后输出: 2
print(gen.send(20))  # 输出: Received: 20, 然后生成器结束，抛出 StopIteration 异常
```

每一次next()、send()都执行到yield（之前的语句）为止

带yield返回值的函数



#### 装饰器

高阶函数

![Python基础装饰器](../.assets/python基础装饰器.png)




#### 泛型



### 面向对象

Class为type类型的对象实例，基类为object

object为type类型的对象实例，没有基类

type为type自身类型的对象实例，基类为object

（type是type，object也是type；type继承自object，object没有继承；Class是type，继承自object）

`class = type(classname, superclass, attributedict)`

- type为对象的顶点，所有对象都创建自type。
- object为类继承的顶点，所有类都继承自object。




类对象无法修改类变量的值，通过类对象对类变量赋值，只会修改自己对象中的变量值



#### 魔术方法&属性
```yaml
:
    __del__(): # 析构犯法
    __delete__():
    __dict__(): # 查看类属性字典
    __dir__(): # 查看类方法、属性
    __enter__(): # 上下文管理（进入），返回值为with接收值
    __exit__(): # 上下文管理（退出），可进行异常处理
        exc_type:
        exc_value:
        traceback:
    __get__():
    __getitem__():
    __init__(): # 构造方法
    __iter__():
    __next__():
    __new__(): # 实例化对象时调用
    __repr__(): # 类对象打印信息
    __set__():
    __str__():
    super():
```


#### 装饰器
```yaml
:
    @classmethod:
    @property: # 属性
        fdel:
        fdoc:
        fget:
        fset:
        deleter:
        setter:
    @staticmethod:
```

![Property装饰器](../.assets/Property装饰器.png)


#### 迭代器

`__getitem__`

`__iter__`->`__next__()`，iter生成迭代器、next实现元素迭代






#### metaclass

metaclass影响类本身的创建行为

metaclass继承自type

一旦把自定义类类型 MyClass 的 metaclass 设置成 MyMeta，MyClass 就不再由原生的 type生成

类对象创建`__call__() -> __new__() -> __init__()` 

`__new__()`生成一个空对象 


类实例化对象，本质上在调用元类的`__call__()`



```python
# 通过type()创建类对象

MyClass = type("MyClass", (object,), {"column": "value"})

# 自定义metaclass
class MyType(type):
    def __init__(self, *args, **kwargs):
        pass

    def __new__(cls, *args, **kwargs):
        new_cls = super().__new__(cls, *args, **kwargs)

    def __call__(self, *args, **kwargs):
        empty_object = self.__new__(self)
        self.__init__(empty_object, *args, **kwargs)
        return empty_object
```

自定义metaclass，执行其中的__new__()方法生成类对象，也会执行元类中的__init__()初始化对象



#### 泛型




### 模块


module -> package -> library

import生成module实例 ，import只会执行一次（同一个实例）


同名目录 比 同名文件模块 优先级要高


### 多线程

event事件、semaphore信号、lock锁、Barrier、Condition条件变量







#### 异步IO

 event loop -> executor  -> coroutine -> task

 async函数返回corouotine协程对象

可根据coroutine对象创建task
