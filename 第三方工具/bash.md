# bash


## 基础介绍

linux shell脚本





## 核心内容
```yaml
bash:
    alias: # 命令别名
    apt: # ubantu包管理工具
        install:
        remove:
        update:
        upgrade:    
    awk:
    bash: # 运行脚本
    cat: # 查看小文件
    cd: # 切换目录
    chmod: # 改变文件权限
    chown: # 改变所有权
    clear: # 清屏
    cp: # 拷贝文件、目录
    cut: # 截取
    date: # 日期
    df: # 查看磁盘空间
    diff: # 文件差异比较
    dpkg:
    du:
    echo: # 内容回显
    find: # 文件查找
        -name:
    grep: # 文本搜索
    head:
    history: # 历史命令
    ip:
    iptables:
    kill:
    less:
    ls: # 查看目录
        -l:
    lsblk:
    netstat: # 网络状态
    man: # 帮助文档
    mkdir: # 创建目录
    more:
    mount:
    mv: # 移动、重命名文件
    ping:
    ps:
    pwd: # 当前目录
    read: # 读取输入
    rm: # 删除文件、目录
    sleep: # 线程睡眠
    sort: # 排序
    ssh: # ssh连接
    stat: # 查看文件属性
    sudo: # 提升权限执行命令
    tail:
    top:
    touch: # 创建文件
    traceroute: # 路由跟踪
    ufw: # ubantu 防火墙
    uniq: # 去重
    unmount:
    uptime:
    vi:
    wc: # 行数、统计
    which: # 可执行文件位置
    who: # 连接终端
    whoami: # 显示当前用户
    wget:
```

### 控制流程
```yaml
Control Flow:
    !!: # 运行上条命令
    \>: # 输出重定向
    \>>: # 追加 
    =: # 变量定义
    $#: # 参数个数
    $@: # 所有参数
    $0: # 脚本名
    $1: # 第一个参数
    case in ... esac: # case 条件判断
        1): # 
        *): # default
    for in do ... done: # for 循环
    if []; then ... elif []; then ... else ... fi: # 条件判断
        -d: # 目录存在
        -eq: # 相等
        -f: # 文件存在
        -lt: # 小于
        -ne: # 不等
        -z: # 变量为空
    while [] do ... done: # while循环
```

### 软件包管理


### 系统管理


### 网络命令

### 用户与权限

### 文件与目录


### 字符串处理







## 第三方命令


### curl
```yaml
curl:
    -b: # 使用cookie（文件）
    -c: # 保存cookie
    -d: # 请求数据
    -o: # 输出文件
    -r: # 分段下载
    -v:
    -x: # 使用代理服务器发送请求
    -A: # 请求代理
    -D: # 保存响应头
    -H: # 请求头设置
    -L: # 自动重定向
    -X: # 请求方法
```

Request url 请求

