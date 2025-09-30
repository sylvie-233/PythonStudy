# pywinauto


## 基础介绍

Windows 专用 的自动化库（不是靠坐标点，而是靠控件句柄）


## 核心内容
```yaml
pywinauto:
    Application: # 应用
        backend:
        ---
        start(): # 启动进程
        connect(): # 连接进程
            process:
            title:
        window(): # 窗口
            title:
            ---
            capture_as_image():
            child_window():
                class_name:
                control_type:
            click():
            drag_mouse_input():
            maximize():
            menu_select():
            minimize():
            print_control_identifiers():
            type_keys():
                with_spaces:
            wait():
            wait_not():
            window_text():
```