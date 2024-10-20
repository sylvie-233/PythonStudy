# Selenium


## 基础介绍


浏览器自动化库



## 核心内容
```yaml
selenium :
    webdriver:
        ActionChains:
            context_click():
            perform():
        Chrome: # 浏览器
            current_window_handle:
            executable_path:
            switch_to:
                default_content():
                frame():
                window():
            window_handles:
            execute_script():
            find_element():
            find_element_by_xpath(): # xpath  查找元素
            find_elements():
                location:
                text: # 标签文本
                clear():
                click():
                get_attribute():
                send_keys():
                submit():
            get(): # 打开网页
            quit(): # 退出浏览器
        ChromeOptions: # 浏览器配置类
            add_argument():
            add_experimental_option():
        Remote: #
            execute_cdp_cmd():
            set_page_load_timeout():
        WebDriverWait:

```