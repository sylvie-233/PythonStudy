# pywin32


## 基础介绍


Python 在 Windows 平台上与 Win32 API 交互的扩展库，允许你操作 Windows 系统功能（注册表、进程、窗口、COM 组件、Office 自动化等）


## 核心内容
```yaml
win32api: # 调用 Windows API，例如文件、进程、消息框等
    GetAsyncKeyState():
    GetComputerName():
    GetUserName():
    MessageBox():
    RegOpenKeyEx():
win32clipboard: # 访问剪贴板
win32com: # COM 自动化（Excel、Word、Outlook 等） 
    client:
        Dispatch():
win32con: # Windows 常量集合（键码、窗口消息等）
win32event: # 事件对象，进程/线程同步
win32gui: # 图形界面窗口管理，操作窗口、菜单、鼠标键盘消息
    FindWindow():
    GetWindowText():
win32process: # 创建、管理进程与线程
    CreateProcess():
win32security: # 安全与权限控制
win32service: # 操作 Windows 服务（启动/停止/注册服务）
win32serviceutil: # 
    StartService():
```