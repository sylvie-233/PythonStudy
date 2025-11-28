# ubuntu


## 基础介绍


Ubuntu 是基于 Debian 的 Linux 发行版




- Ubuntu 下所有用户记录在`/etc/passwd`，`用户名:x:UID:GID:描述:家目录:默认shell`
- 所有组记录在`/etc/group`，`组名:组密码:组ID(GID):组成员列表`
- 用户密码在：`/etc/shadow` 存放用户密码（加密）`


### 安装目录
```yaml
ubuntu:
    /bin:
    /boot:
    /cdrom:
    /data:
    /dev:
    /etc:
        /apt:
            /sources.list.d:
                ubuntu.sources: # ubuntu apt 包安装镜像
            sources.list:
        passwd: # 所有用户信息
    /home:
        /<user>:
    /lib:
    /lib64:
    /lost+found:
    /media:
    /mnt:
    /opt:
    /porc:
    /root:
    /run:
    /sbin:
    /snap:
    /srv:
    /sys:
    /tmp:
    /usr:
    /var:
```



## 核心内容
```yaml
ubuntu:
    apt: # 内置包管理工具
        download:
        install:
            --reinstall:
        remove:
        search:
        show:
        update:
        upgrade:
    alias: # 命令别名
    awk: # Aho, Weinberger, Kernighan 基于字段的文本分析与报告
        -f: # 从脚本文件中读取 awk 命令
        -v: # 向 awk 传入 shell 变量
        -F: # 指定字段分隔符
    bash: # 运行脚本
    cat: # 查看小文件
    cd: # 切换目录
    chmod: # 改变文件权限
    chown: # 改变所有权
    clear: # 清屏
    cp: # 拷贝文件、目录
        -r: # 递归
    cut: # 按列切割文本
        -b: # 指定“字节”位置
        -c: # 指定“字符”位置
        -d: # 指定“字段分隔符”（delimiter）    
        -f: # 指定“字段编号”（field）
    date: # 日期
    df: # 查看磁盘空间
    diff: # 文件差异比较
    dpkg:
    du:
    echo: # 内容回显
    find: # 文件查找
        -name:
    grep: # Global Regular Expression Print 查找/匹配文本
        -i: # 忽略大小写
        -n: # 显示匹配行的行号
        -r: # 递归搜索目录
        -C: # 显示匹配行及前后 NUM 行（上下文）
    head:
    history: # 历史命令
    ln: # 链接
        -s:
    ip: # ip地址查看
        addr:
    iptables:
    kill:
    less:
    ls: # 查看目录
        -l:
    lsblk:
    netplan: # 
    netstat: # 网络状态
    man: # 帮助文档
    mkdir: # 创建目录
        -p: # 递归创建
    more:
    mount:
    mv: # 移动、重命名文件
    ping:
    ps:
    pwd: # 当前目录
    read: # 读取输入
    rm: # 删除文件、目录
    sed: # Stream Editor 文本替换、删除、插入、编辑
        -e: # 添加多个编辑命令
        -i: # 
        -n: # 静默模式
    sleep: # 线程睡眠
    sort: # 排序
    source: # 执行sh脚本
    ss: # 新版 netstat
    ssh: # ssh连接
    stat: # 查看文件属性
    sudo: # 提升权限执行命令
    systemctl: # 服务管理
        disable:
        enable:
        start:
        status:
        stop:
        restart:
        reload:
    tail: # 查看文件尾部
    tar: # tar压缩包
        -c: # 创建归档文件
        -f: # 指定归档文件名
        -t: # 查看归档文件内容
        -x: # 解压归档文件    
        -v: # 显示详细过程
        -z: # gzip压缩
        -C: # 在指定目录操作
    top:
    touch: # 创建文件
    traceroute: # 路由跟踪
    ufw: # ubantu 防火墙
        allow:
        enable:
        status:
    uniq: # 去重
    unmount:
    uptime:
    unzip: # zip解压
    vi:
    wc: # 行数、统计
    which: # 可执行文件位置
    who: # 连接终端
    whoami: # 显示当前用户
    wget:
    zip: # zip压缩包
        -r: # 递归压缩
```



### Command

#### apt

`.deb`
apt只能用于基于Debian的系统 



#### systemctl

service服务管理


#### ufw


防火墙





### Bash


#### DataTypes

##### Array

数组





#### ControlFlow
```yaml
Control Flow:
    !!: # 运行上条命令
    \>: # 输出重定向
    \>>: # 追加 
    (( )): # 表达式计算
    $(expr ...): # 表达式计算
    $#: # 参数个数
    $@: # 所有参数
    $0: # 脚本名
    $1: # 第一个参数
    let: # 变量初始化
    case in ... esac: # case 条件判断
        1): # 
        *): # default
    for in do ... done: # for 循环
    if []; then ... elif []; then ... else ... fi: # 条件判断
        =~: # 正则匹配
        -d: # 目录存在
        -eq: # 相等
        -f: # 文件存在
        -lt: # 小于
        -n: # 变量不为空
        -ne: # 不等
        -z: # 变量为空
    select in do ... done: # 生成交互式菜单的
    while [] do ... done: # while循环
```


#### Function