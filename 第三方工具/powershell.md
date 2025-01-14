# powershell

## 基础介绍


CmdLet、Function、Alias、



PS命令不区分大小写



## 核心内容
```yaml
powershell:
    System:
        Array:
            Count:
            IsFixedSize:
        Int32:
        String:
            Length:
            GetType():
    $null:
    $PSVersionTable: # PS版本信息
    $true: # 布尔True
    Get-Alias: # 获取别名
    Get-Command:
        -Name:
    Get-Date:
    Get-ExecutionPolicy:
    Get-Help:
    Get-Member: # 获取对象成员属性、方法
        -MemberType:
    Get-Process: # 获取进程对象
    Get-Service: # 获取所有服务(后台进程)
    Get-Verb:
    Set-ExecutionPolicy:
    Set-Location: # cd 修改当前工作目录
    Set-StrictMode: # 设置代码严格模式
        -Version:
    Where-Object:
    Write-Host: # 控制台输出
```


### 数据类型

```ps1
# 定义变量
$key = value

```


#### String


#### Array

```ps1
# 定义数组
$arr = @(1, 2, 3)

$arr[0]
```



#### Table



### 控制流程
```yaml
:
    #: 单行注释
    <# ... #>: # 多行注释
```

