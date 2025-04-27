# dos


## 基础介绍


windows shell脚本

`.bat`：批处理文件


## 核心内容
```yaml
dos:
    ::: # 批处理注释
    \>:
    \>>: # 内容重定向
    &: # 顺序执行多条命令（不管前面命令是否执行成功）
    &&: # 顺序执行多条命令（前面命令必须执行成功）
    \|: # 管道符
    \||: #  顺序执行多条命令（前面命令执行成功则结束）
    %%: # 变量引用（环境变量）
    %0: # 批处理文件本身
    %1:
    %2:
    %3: # 批处理参数
    cd: # 切换目录
        ..: # 上级目录
    call: # 调用函数
    cls: # 清屏
    dir:
    echo:
        off: # 取消命令回显
        on:
    exit: # 推出dos窗口
    find:
        /c: # 总个数
        /i:
    goto: # 批处理跳转
        :eof: # 批处理末尾
    help:
    md: # 创建目录
    more: # 按需显示文件内容
    pause: # 暂停
    ping:
    rem: # 批处理注释
    rd: # 删除目录
    set: # 设置变量
    start: # 调用外部命令
    title: # 设置cmd标题
    tree: # 显示目录结构
    type: # 显示文本内容
```

### 控制流程
```yaml
Control Flow:
    for %%i in ... do ...: # for循环
    if ... else ...: # 条件判断
        exist: # 判断文件存在
```

### 函数
```shell
call :myfunc "arg1","arg2"

:myfunc      :: 定义函数名
    echo %0  :: 函数名
    echo %1  :: 函数参数1
    echo %2  :: 函数参数2
goto :eof 
```

函数没有返回值



## Windows

### 注册表
```yaml
regedit:
    /HKEY_CLASSES_ROOT: # 	存放文件关联、COM 组件等信息，决定某种文件类型用哪个程序打开
        /*:
            /shell:
                /VSCode:
                    /command: # 命令执行
                        (默认):
                    (默认):
                    Icon:
    /HKEY_CURRENT_USER: # 当前登录用户的个性化设置（如桌面、壁纸、快捷方式等）
        /Software:
            /Microsoft:
                /Windows:
                    /CurrentVersion:
                        /Run: # 这个路径下的项会在用户登录时自动启动
    /HKEY_LOCAL_MACHINE: # 	整个计算机的设置（适用于所有用户），包括驱动、服务、硬件等
        /SYSTEM:
            /CurrentControlSet:
                /Services: # 包含了所有系统服务的注册信息（如启动类型、依赖项等）
    /HKEY_USERS: # 系统中所有用户的设置，HKCU 实际上就是其中当前用户的子项
    /HKEY_CURRENT_CONFIG: # 当前硬件配置的快捷方式（如显示器、打印机配置），从 HKLM 派生
```



### COM

COM(Component Object Model) 就是 Windows 的跨语言组件系统：你可以写一个功能模块（组件），注册到系统里，其他程序就能调用它，就像调用自己的代码一样