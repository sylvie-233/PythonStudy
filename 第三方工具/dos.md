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