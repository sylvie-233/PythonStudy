# Lua

>
>`Lua官网：https://www.lua.org/`
>
>

## 基础介绍


弱类型语言、区分大小写
lua默认变量是全局的，可使用local声明局部变量

字符串拼接使用`..`（类似php）
获取字符串、数组长度`#`




### lua
```yaml
lua:
    -e: # 执行字符串脚本
    -i: # 交互模式
    -l: # require 库
    -v: # 版本信息
    -E: # 忽略环境变量
```


#### luac
```yaml
luac:
    -l:
    -o: # 指定输出
    -p:
    -s:
    -v:
```






## 核心内容
```yaml
std:
    basic: # 内置
        _G:
        _VERSION:
        assert():
        colectgarbage():
        dofile():
        error(): # 抛出异常
        getmetatable(): # 获取元表
        ipairs(): # 索引数组遍历，i-v 索引
        load():
        loadfile():
        next():
        pairs(): # 关联数组遍历,k-v 索引
        pcall(): # 异常处理包装函数调用
        print(): # 控制台打印
        rawequal(): # 
        rawget(): # 原始索引获取（不触发元表）
        rawlen(): # 原始长度获取（不触发元表）
        rawset(): # 原始索引设置（不触发元表）
        require(): # 模块引入
        select(): # 用于返回从起点 n 开始到结束位置的所有参数列表（# 获取参数个数）,2种用法
        setmetatable(): # 设置元表
        tonumber(): # 转数值
        tostring(): # 转字符串
        type(): # 获取数据类型, 字符串
        warn():
        xpcall(): # 异常处理、同pcall（多接收一个异常处理函数参数）
    coroutine:
        close():
        create(): # 创建协程（创建后默认不启动）
        isyieldable():
        resume(): # 唤醒协程
        running():
        status(): # 协程状态：dead，suspended，running
        warp(): # 协程包装器（可直接调用，不用resume）
        yield(): # 中断协程
    debug:
        debug():
        gethook():
        getinfo():
        getlocal():
        getmetatable():
        getregistry():
        getupvalue():
        getuservalue():
        sethook():
        setlocal():
        setmetatable():
        setupvalue():
        traceback():
        upvalueid():
        upvaluejoin():
    io:
        close():
        flush():
        input():
        lines():
        open(): # file对象
            close():
            flush():
            lines():
            read():
            seek():
            setvbuf():
            write():
        output():
        popen():
        read():
        stderr():
        stdin():
        stdout():
        tmpfile():
        type():
        write():
    math:
        pi:
        abs():
        ceil():
        exp():
        floor():
        log():
        max():
        min():
        random():
        randomseed():
    os:
        clock():
        date():
        difftime():
        execute():
        exit():
        getenv():
        remove():
        rename():
        setlocale():
        time():
        tmpname():
    package: # 模块、包
        config:
        cpath:
        path: # 模块搜索路径
        loaded():
        loadlib():
        prelaod():
        searchers():
        searchpath():
    string: # 字符串
        byte:
        char(): # 转字符串
        dump():
        find(): # 字符串查找
        format(): # 字符串格式化
        gmatch(): # 字符串匹配
        gsub(): # 字符串替换
        len(): # 字符串长度
        lower():
        match(): # 字符串匹配
        pack():
        packsize():
        rep():
        reverse():
        sub(): # 字符串截取
        unpack():
        upper(): # 转大写
    table: # 表
        concat(): # 数组元素拼接
        insert(): # 插入元素
        move():
        pack():
        remove(): # 移除元素（默认最后一个）
        sort():
        unpack():
    utf8:
        len(): # 获取字符串长度

metamethods: # 元方法
    __add():
    __band():
    __call(): # 类函数调用
    __close():
    __concat():
    __eq():
    __gc():
    __index(): # 获取索引元素
    __len():
    __metatable():
    __mode():
    __name():
    __newindex(): # 设置索引元素
    __pairs():
    __sub():
    __tostring(): # print打印输出
    __unm():
```

### 数据类型
```yaml
Data Types:
    nil:
    boolean:
    number:
    string:
    function:
    userdata:
    thread:
    table:
```
8大数据类型

变量默认定义全局变量，`local`定义局部变量
变量默认值`nil`

支持变量解构



#### string
```lua
-- 多行字符串 [[ ]]
local str = [[
    ...
]]

-- 字符串拼接 .. 
local str3 = str1 .. str2
```


### 控制结构
```yaml
Control Flow:
    --: # 单行注释
    --[[]]: # 多行注释
    #: # 返回字符串、数组长度
    : / .: # :冒号运算自动传入self(table表)（自动把:前面的东西作为第一个参数传入方法，作为self隐式存在）
    //: # 整除运算
    ~=: # 不等
    nil: # 空值
    true / false: # 布尔字面量
    and or not: # 逻辑运算符
    local: # 局部变量定义
    function ... end: # 函数定义
    if ... then ... elseif ... else ... end: # 条件语句
    for ... do ... end:
    for ... in pair() do end: # 循环遍历
    repeat ... until ...:
    while ... do ... end:
        break:
```

#### 注释
```lua
-- 单行注释

--[[
    多行注释
]]
```



#### 迭代器

常配合for in循环遍历

迭代函数、状态常量(数组)、控制变量(索引)（将状态常量和控制变量作为参数调用迭代函数）

- 无状态的迭代器（无数组）
- 多状态的迭代器（无参闭包）


#### 异常处理

`pcall()`、`xpcall()`、``


### 函数
```lua
-- 
function myfunc(a, b)
    ...
end
```

可使用local定义局部函数

可变参数: `...`

#### 可变参数
```lua
function myfunc(...)
    local len = select("#", ...)
end
```




### table
```lua
local tb = {"key": "value", ...}

-- k-v遍历
for k, v in pair(t) do
    ...
end 

-- 数组索引遍历，table自动索引从1开始编号
for i, v in ipair(t) do
    ...
end
```

关联数组
可利用table实现array、set、map、object
使用table表当lua数组使用时，索引默认从1开始



#### Metatable 元表
```yaml
metatable:
    __add: # 控制 + 运算符的行为
    __call: # 函数一样可调用
    __eq:
    __index: # 	控制表访问不存在的字段时的行为（常用于继承）
    __newindex: # 控制给表中不存在字段赋值时的行为
    __tostring: # 
```

魔术方法、原型链结构
`setmetatable()`、`getmetatable()`


#### 面向对象
```lua
-- 定义 Person 类
Person = {}
Person.__index = Person

-- Person 的构造函数
function Person:new(name, age)
    local obj = {}  -- 创建一个新的表作为对象
    setmetatable(obj, self)  -- 设置元表，使其成为 Person 的实例
    self.__index = self  -- 设置索引元方法，指向 Person

    obj.name = name
    obj.age = age
    return obj
end

-- 添加方法：打印个人信息
function Person:introduce()
    print("My name is " .. self.name .. " and I am " .. self.age .. " years old.")
end


-- 创建一个 Person 对象（new中self为Person）
local person1 = Person:new("Alice", 30)

-- 调用对象的方法（introduce中的self为person1）
person1:introduce()  -- 输出 "My name is Alice and I am 30 years old."
```


- 创建新对象(table)
- 对象设置元表(属性查找)
- 元表table的__index指向自身

self获取函数调用`:`前的对象（类或类实例）

元表链形成类继承


### 模块

模块定义：table + return
模块加载：require()
模块搜索路径：package.path、LUA_PATH



### 协程

coroutine


