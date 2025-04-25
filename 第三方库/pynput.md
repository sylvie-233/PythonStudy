# pynput


## 基础介绍

pynput 是一个功能强大的库，适用于 监听键盘和鼠标事件，支持跨平台（Windows、macOS、Linux）。你可以用它来监听按键、控制鼠标等


## 核心内容
```yaml
pynput:
    keyboard:
        Controller:
            press():
            release():
            type():
        Key:
            ctrl_l:
        KeyCode:
            from_char():
        Listener:
            on_press:
            on_release:
            join():
            start():
            stop():
    mouse:
        Controller:
            position:
            click():
        Listener:
            on_click:
            on_move:
            join():
```