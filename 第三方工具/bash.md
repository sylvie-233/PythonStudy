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
    awk: # Aho, Weinberger, Kernighan	基于字段的文本分析与报告
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
    tail:
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



### 控制流程
```yaml
Control Flow:
    !!: # 运行上条命令
    \>: # 输出重定向
    \>>: # 追加 
    (( )): # 表达式计算
    $(expr ...): # 表达式计算
    let: # 变量初始化
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


#### 变量


##### 数字
##### 字符串
##### 数组
```bash
arr=(apple banana cherry)

# 元素索引
${arr[0]}

# 数组长度
${#arr[@]}


```


##### 关联数组
```bash
declare -A person

person[name]="Alice"

${person[name]}   # Alice
```


#### 函数
```bash
# 函数定义
my_func() {
    echo "Hello, $1"
    return 0
}

# 函数调用
my_func "Alice"

# 函数参数
$@	# 所有参数列表（分别展开）
$*	# 所有参数（整体当成一个字符串）
$#	# 参数个数
$?  # 上个函数返回值

# 函数局部变量
local x=10 

# 函数调用，获取返回值，返回值配合echo使用
$(myfunc "xxx") # echo + $(...) 是 Bash 中的主流“函数返回值”写法
```



### 软件包管理


### 系统管理


### 网络命令

### 用户与权限

### 文件与目录


### 字符串处理

#### awk
```yaml
awk: # awk [选项] 'pattern { action }' 文件
    $0: # 当前整行文本
```


#### cut


#### grep



#### sed
```yaml
sed: # sed [选项] '地址范围 命令' 文件
    s/old/new/g: # 替换
    /pattern/d: # 删除匹配的行
    /errorpattern/p: # 打印匹配的行
    N a 内容: # 在第 N 行前插入
    N c 内容: # 替换整行
    N i 内容: # 在第 N 行后追加
```



基础字符串操作
```bash
name="Sylvie"

# 模板字符串
greeting="Hello, ${name}!"

# 字符串长度
${#str}

# 字符串查找
$(expr index "$str" "w")

# 字符串截取 
${var:start:length}

# 字符串替换
${str/old/new}	# 替换第一个
${str//old/new}	# 替换全部
${str/#old/new}	# 替换开头
${str/%old/new}	# 替换结尾

# 去除前缀/后缀
${str#pattern}	# 去掉最短前缀	
${str##pattern}	# 去掉最长前缀	
${str%pattern}	# 去掉最短后缀	
${str%%pattern}	# 去掉最长后缀

# 大小写转换
${str^^} # 全大写
${str^}  # 首字母大写
${str,,} # 全小写
```







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

