# Inno Setup

`零基础教程】如何使用Inno Setup软件制作.exe安装包：P6`

## 基础介绍


安装包制作工具
`.iss`Inno Setup Scripts脚本



## Inno Setup Compiler
```yaml
Inno Setup Compiler:
    _builtin: # 内置变量
        app: # exe应用安装根目录
        autoprograms: # 开始菜单
        autodesktop: # 桌面
    #define: # 预定义遍历
        MyAppName:
        MyAppVersion:
        MyAppPublisher:
        MyAPPURL:
        MyAppExeName:
    Setup:
        AppId:
        AppName:
        AppVersion:
        AppPublisherURL: # 应用发布链接
        AppSupportURL: # 应用支持链接
        AppUpdatesURL: # 应用更新链接
        DefaultDirName: # 默认安装目录
        DisableProgramGroupPa:
        Uncomment:
        PrivilegesRequired:
        OutputDir:
        OutputBaseFilename:
        Compression:
        SolidCompression:
        WizardImageFile: # 
        Wizardstyle:
    Language:
    Tasks:
    Files:
    Icons:
    Run:
    Code: # 自定义脚本 Pascal
        _lifecycle: # 生命周期函数
            InitializeSetup():
            InitializeWizard():
        Exec():
        MsgBox():
```