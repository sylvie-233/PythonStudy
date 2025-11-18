# playwright

`Playwright web自动化：P11`

## 基础介绍


浏览器自动化库
Playwright -> Browser -> BrowserContext -> Page -> Locator



- 支持css selector和xpath两种元素定位方式

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
            tracing: # 上下文跟踪
                start():
                stop():
            new_page():
        ElementHandle:
        Locator: # 元素定位
            all():
            click(): # 元素点击
            fill(): # 元素填充
            inner_text(): # 元素文本内容
        Page: # 页面
            keyboard:
            mouse:
            check():
            click(): # 元素点击
            close(): # 关闭
            content():
            expect_download():
            expect_response():
            expect_popup():
            eval_on_selector(): # 选中元素执行eval脚本
            fill():
            goto(): # 页面跳转
            hover():
            locator(): # 元素定位
            query_selector_all():
            screenshot():
            select_option():
            set_input_files():
            title():
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