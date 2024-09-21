# Textual

## 基础介绍

### textual
```yaml
textual:
    console:
    run:
```


python 控制台界面库


## 核心内容
```yaml
textual:
    app:
        App: # 应用App基类
            CSS: # 类变量定义css样式
            CSS_PATH:
            SUB_TITLE: # 子标题
            TITLE: # 标题
            css:
                load(): # 加载css路径
            css_path: # css文件路径
            screen: # 屏幕
                styles: # 样式
                    background:
                    border:
            view:
                discard():
                dock(): # 固定定位
                    edge:
            compose(): # 定义绘制组件
            exit(): # app退出
            mount(): # 挂载组件
            on_button_pressed():
            on_click(): # 点击钩子
            on_load(): # app启动钩子
            on_mount(): # app挂载钩子
            on_key(): # 按键钩子
            query():
                add_class():
                blur():
                exclude():
                filter():
                focus():
                last():
                refresh():
                remove_class():
                results(): # 类型限定
                set_class():
                toggle_class():
            query_one(): # 组件查询
            run(): # app运行
        ComposeResult: # 组件渲染结果
    containers: # 布局容器
        Container:
            Horizontal:
    events:
        Key:
            key:
    logging:
        TextualHandler:
    widgets:
        Button:
            Pressed:
            label:
            variant:
        Checkbox:
        Collapsible:
        ContentSwitcher:
        DataTable:
        Digits:
        DirectoryTree:
        Footer:
        Input:
        Label:
            id:
        ListView:
        LoadingIndicator:
        Log:
        MarkdownViewer:
        OptionList:
        Placeholder:
        ProgressBar:
        RadioButton:
        RadioSet:
        RichLog:
        Rule:
        Select:
        Switch:
        Tabs:
        TabbedContent:
        TextArea:
        TextInput:
            on_enter:
            on_change:
            value:
        TextView:
            text:
        Welcome:
        Widget:
            render(): # 渲染函数
            style(): # css类
```

### App

### Widgets



### Styles




### Animation

