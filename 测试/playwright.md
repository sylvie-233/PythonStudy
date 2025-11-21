# playwright

``

## 基础介绍


浏览器自动化库
Playwright -> Browser -> BrowserContext -> Page -> Locator



- 支持css selector和xpath两种元素定位方式
- 元素定位locator缺省等待时间为30s

### playwright
```yaml
playwright:
    codegen: # 录制宏，代码生成
    install: # 安装浏览器驱动
    show-trace: # 显示上下文跟踪可视化数据
```




## 核心内容
```yaml
playwright:
    async_api:
        AsyncPlaywright:
            chromium:
                launch(): # 启动浏览器
                    headless:
            start():
            stop():
        async_playwright():
    sync_api: # 同步api
        Browser: # 浏览器
            close(): # 关闭
            new_context():
        BrowserContext: # 浏览器上下文
            pages:
            tracing: # 上下文跟踪
                start():
                stop():
            new_page():
        ElementHandle:
        Locator: # 元素定位
            all(): # 获取所有匹配的元素
            all_inner_texts():
            check():
            clear(): # 元素清空
            click(): # 元素点击
            drag_to(): # 元素拖拽
            fill(): # 元素填充
            get_attribute(): # 获取属性
            hover():
            inner_html():
            inner_text(): # 元素文本内容
                timeout: # 等待时间（默认30s）
            input_value(): # 输入框内容
            is_checked():
            is_visible():
            screenshot(): # 节点截屏保存
            select_option():
                index:
                label:
                value:
            select_text(): # 选中文本
            set_input_files(): # 设置文件输入内容
            text_contents(): # 元素文本内容（包含隐藏元素）
            uncheck():
            wait_for(): # 等待元素出现
        Page: # 页面
            keyboard:
            mouse:
            check():
            click(): # 元素点击
            close(): # 关闭
            content():
            drag_and_drop(): # 元素拖拽
            expect_download():
            expect_response():
            expect_popup():
            eval_on_selector(): # 选中元素执行eval脚本
            fill():
            frame_locator():
            get_by_label():
            get_by_placeholder():
                exact:
            get_by_role(): # aria role属性获取元素
                level:
                name:
            goto(): # 页面跳转
            go_back():
            hover():
            locator(): # 元素定位
            on(): # 事件监听
                dialog: # 弹出框
                    message: 
                    accept():
            query_selector_all():
            reload():
            screenshot(): # 屏幕截屏
            select_option():
            set_input_files():
            set_viewport_size():
            title(): # 页面标题
            wait_for_load_state():
            wait_for_selector():
            wait_for_timeout(): # 等待指定时间
        Playwright:
            chromium:
                launch():
                    headless:
            devices:
            start():
            stop(): # 关闭
        Request:
        Response:
        expect():
        sync_playwright():
```