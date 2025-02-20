# powershell

## 基础介绍

`.ps1`：powershell脚本文件
`.psm1`：powershell模块文件
`.psd1`：powershell模块清单文件

一切皆对象

CmdLet、Function、Alias、Variable

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
            Trim():
    Add-Member: # 添加成员
        -MemberType:
        -Name:
        -Value:
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
    Import-Module: # 导入模块
        -Name: # 导入指定的psd1文件
        -Verbose: # 显示命令执行细节
    New-Item: # 新建元素
        -Name:
        -Type:
            File:
    New-ModuleManifest: # 新建模块清单文件
    New-Object: # 新建对象
        PSObject:
            -Property:
    Set-ExecutionPolicy:
    Set-Location: # cd 修改当前工作目录
    Set-StrictMode: # 设置代码严格模式
        -Version:
    Where-Object:
    Write-Host: # 控制台输出
    Write-Output:
```


### 数据类型
```yaml
DataTypes:
    string:
```

`$`：定义变量
`[Type]`：类型引用



#### String


#### Array
```ps1
# 定义数组
$arr = @(1, 2, 3)

$arr[0]
```

数组索引从0开始



#### Table
```ps1
# 定义哈希表
$map = @{
    "Name" = "Sylvie233"
    "Age" = 24
}

$map["Name"]
```

#### Enum
```ps1
# 定义枚举
enum DaysOfWeek {
    Monday
    Tuesday
}

# 使用枚举
$today = [DaysOfWeek]::Monday
Write-Host $today 
```

枚举类





### 控制流程
```yaml
Control Flow:
    $env: # 环境变量
        PSModulePath:
    $false: # 布尔False
    $null:
    $PSVersionTable: # PS版本信息
    $true: # 布尔True
    switch ... default ...:
```


#### 注释
```ps1
#   单行注释
s
<# 
    多行注释
#>
```



### 函数
```ps1
# 函数声明
function Greet-User {
    param (
        [string]$Name
    )
    Write-Host "Hello, $Name!"
}

# 函数调用
Greet-User -Name "John"
```

`function`：定义函数
`param()`：声明函数参数

支持形参默认值、


#### [Parameter]
```yaml
Parameter:
    Mandatory: # 必填参数
    ValueFromPipeline: # 接收管道输入
```
`[Parameter(Mandatory=$true)]`: 参数限定


### 面向对象
```ps1
class Employer {
    [string]$Name
    [int]$Age

    Employer([string]$name, [int]$age) {
        $this.Name = $name
        $this.Age = $age
    }

    [void] SayHello() {
        Write-Host "Hello, my name is $($this.Name) and I am $($this.Age) years old."
    }
}

$employer = [Employer]::new("Jack", 28)
$employer.SayHello()
```


`class`：定义类
`new()`：实例化类对象
`$this`：自身实例引用


#### 继承
```ps1
class Employer: Employee {
    [string]$EmployeeID

    Employer([string]$name, [string]$employeeID) : base($name) {
        $this.EmployeeID = $employeeID
    }
}
```

`:`：类继承



### 模块
```ps1
New-ModuleManifest -Path "xxx.psd1" -RootModule "./xxx.psm1"

Import-Module -Name "xxx.psd1"

# 直接使用模块内函数
```

`.psm1`和`.ps1`效果一样
`Import-Module`：导入psm1模块文件

#### psd1
```yaml
psd1:
    Author: # 作者
    FunctionsToExport: # 导出的函数
    ModuleVersion:
    RootModule: # 模块文件位置
```
文件夹、清单文件、模块文件