# neovim

`Neovim 初学者教程: P5`

## 基础介绍

控制台代码编辑器

config目录：`C:\Users\~\AppData\Local\nvim"`
data目录：`C:\Users\~\AppData\Local\nvim-data`


### 配置目录
```yaml
配置目录: # C:\Users\用户名\AppData\Local
    /nvim: # 核心配置目录
        /lua:
            /config:
            /plugins:
        init.lua:
        lazyvim.json:
    /nvim-data: # 插件安装目录
        /lazy:
        mason.log:
```




### nvim
```yaml
nvim:
    --clean:
```


#### init.lua
```yaml
init.lua:
    lazy:
        setup():
            opts:
            plugins:
    lspconfig:
        lua_ls:
            setup():
    vim:
        api:
            nvim_create_autocmd():
        fn:
            argc():
            remove():
            stdpath():
                config: # `~/AppData/Local/nvim`
                data: # `~/AppData/Local/nvim-data`
            sysytem(): # 执行系统命令
        g:
            mapleader:
        keymap:
            set(): # 快捷键注册
                n:
        loop:
            fs_stat():
        lsp:
            buf:
                code_action():
                definition():
                hover():
        opt:
            number:
            rtp:
                prepend():
        cmd(): # 执行shell命令（设置属性）
            colorscheme:
        print():
```

nvim核心配置文件
默认加载配置文件：`C:\Users\用户名\AppData\Local\nvim\init.lua`
`~/.config/nvim/init.lua`


## 核心内容
```yaml
vim: # Neovim Lua API
    api: # 原生底层 API 接口（直接封装自 C 层）
        nvim_buf_delete():
        nvim_buf_get_lines(): # 获取当前 buffer 的第 xxx 行
        nvim_buf_get_name(): # 获取当前 buffer 的文件名
        nvim_buf_set_lines():
        nvim_buf_set_name():
        nvim_command():
        nvim_create_augroup():
        nvim_create_autocmd():
        nvim_del_autocmd():
        nvim_err_write():
        nvim_exec():
        nvim_get_current_buf():
        nvim_get_current_line():
        nvim_get_current_tabpage():
        nvim_get_current_win(): # 获取当前窗口号
        nvim_get_vvar():
        nvim_list_bufs(): # 获取所有 buffer
        nvim_list_tabpages():
        nvim_list_wins():
        nvim_out_write():
        nvim_set_current_line():
        nvim_win_get_cursor():
        nvim_win_get_height():
        nvim_win_get_width():
        nvim_win_set_cursor():
        nvim_win_set_height():
        nvim_win_set_width():
    fn: # 调用 VimScript 原生函数
        cmd():
        expand(): # 获取允许环境信息
            $: # 环境变量
            ~: # 用户主目录路径
            %: # 当前文件名
            %:e: # 扩展名
            %:p: # 当前文件绝对路径
            %:r: # 不带扩展名的文件名
            %:t: # 文件名部分
        getline(): # 获取当前行内容
        stdpath(): # 获取标准路径
            config: # 配置文件标准路径
        strftime(): # 获取当前时间
        system(): # 运行 shell 命令并获取输出
    keymap: # 快捷键
        set():
    loop: # 异步 IO（LibUV 封装）
    o:
        expandtab:
        number:
        relativenumber:
        shiftwidth:
        tabstop:
        termguicolors:
    opt: # 设置 Neovim 选项（替代 vim.o, vim.bo 等）
        autoread: # 自动同步文件修改
        clipboard:
        colorcolumn: # 高亮第n列
        cursorline: # 高亮当前行
        expandtab: # tab转空格space
        number: # 行号
        relativenumber: # 相对行号（相对当前行）
        rtp:
            prepend():
        shiftwidth: # 缩进占几个空格
        tabstop: # 一个tab占几个空格space
    cmd(): # 执行 Vim 命令
    inspect(): # 用于调试、打印 lua 的 table

cmdline:
    =: # 执行lua表达式
    bd: # 关闭插件
    checkhealth: # 检查nvim配置环境
    close: # 关闭当前栏
    e: # 打开文件
    help:
    lua: # 执行lua 脚本
    luafile: # 执行lua文件
    q: # 退出 quit
    saveas: # 另存为
    sp: # 水平分屏
    tabclose:
    tabedit:
    tabn:
    tabnew:
    tabnext:
    tabonly: # fjeajw
    tabprevious:
    tabp:
    vsp: # 垂直分屏
    w: # 写入 write
    Lazy: # lazy.nvim 设置面板（插件管理）
        ?:
        C: # Check
        D: # Debugs
        H: # Home
        I: # Install nvim插件安装
        L: # Log日志
        P: # Profile
        R: # Restore
        S:
        U: # Update
        X:
    Mason: # LSP 服务器

edit: # Normal、Insert、Visual
    0: # 行首
    {num}:
        k: # 向上移动
        j: # 向下移
        yy: # 复制多行
        G: # 跳转到指定行
    \>: # 向右缩进 
    <: # 向左缩进
    ^: # 首个非空字符
    ;: # 向后重复上次字符搜索
    ,: # 向前重复上次字符搜索
    []:
    ctrl:
        \[: # 切换normal
        b: # 向上翻整页
        d: # 向下翻半页
        f: # 向下翻整页
        u: # 向上翻半页
        v: # 列选择模式
        w: # 切换分栏
            h: # 向左
            j: # 向下
            k: # 向上
            l: # 向右   
    shift:
        g: # 跳转到最后一行
    b: # 上一个单词,begin
    c: # 改变 
        0: # 改变到行首，进入插入模式
        {num}:
            j: # 改变后 num 行
            w: # 改变后 num 个单词，进入插入模式
        ^: # 改变到行第一个非空字符
        $: # 改变到行尾
        a: # arround
        c: # 改变当前行
        i: # inner
            w: # 改变整段单词，进入插入模式
        j: # 改变当前行
        w: # 改变整个单词，并进入插入模式
    d: # 删除
        d: # 删除当前行
        iw: # 删除整个单词
        s: # 删除包裹
        w: # 删除单词
    e: # 下一个单词结尾,end
    f: # 搜索字符移动, 在当前行内跳转
    g: # 跳转
        d: # 跳转到定义
        e: # 跳转上一个单词结尾
        g: # 跳转文件顶部
        h: # 查看定义help
        t: # 下一个tab
        v: # 重新选中上次区域
        T: # 上一个tab
    h:
    i: # 插入模式
    j:
    K:
    l:
    o: # 向下插入新行
    p: # 粘贴到下一行
    t: # 搜索字符移动，下一个的前一个
    u: # 撤销操作
    v: # 进入字符选择模式
        a: # arround
        f: # 向后字符搜索
        i: # inner
            b: # 选中小括号中内容
            e: # 整个文件
            t: # tag 标签内容
            w: # 选中整个单词
            B: # 选中大括号中内容
        w: 
        F: # 向前字符搜索
    w: # 按单词向后移动
    y: # 复制
        y: # 复制当前行
    z:
        b: # 当前行光标放底部
        t: # 
        z: # 当前行光标放中间
    A: # 当前行尾插入
    B: # 字串开头(连续算一个)
    D: # 删除至行尾
    E: # 下一个字串结尾(连续算一个)
    F: # 反向搜索字符移动，在当前行内跳转
    H: # 跳转当前屏幕首行
    I: # 行首插入
    L: # 跳转屏幕尾行
    M: # 跳转当前屏幕中间行
    O: # 向上插入一行
    R: # 替换模式
    T: # 搜索字符移动，上一个的后一个
    G: # 跳转文件尾部
    V: # 行选择
    W: # 下一个单词(连续算一个)

lazy.nvim:

```

vim常见edit编辑操作符:
- d: 删除
- c: 改变
- p: 粘贴
- v: 选择
- y: 复制





### Config
```yaml
Config:
    expandtab:
    tabstop:
    softtabstop:
    shiftwidth:
```




### Plugin


安装 lazy.nvim: `git clone https://github.com/LazyVim/starter $env:LOCALAPPDATA\nvim`


#### lazy.nvim
```lua
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
  vim.fn.system({
    "git",
    "clone",
    "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git",
    "--branch=stable", -- 最新稳定版本
    lazypath,
  })
end
vim.opt.rtp:prepend(lazypath)

require("lazy").setup(plugins, opts)
```
nvim插件管理工具


插件安装完后还要进行setup()配置

#### snacks

Snacks 是一种轻量级的、基于 Python 的构建工具，主要用于 构建和管理 Neovim 插件。它通过使用 Python 脚本和插件规范来简化插件的安装、配置和管理



#### packer.nvim


nvim插件管理工具


## 常用插件

