# neovim

``

## 基础介绍

现代化vim编辑器
控制台代码编辑器

config目录：`C:\Users\~\AppData\Local\nvim"`
data目录：`C:\Users\~\AppData\Local\nvim-data`

- Neovim 在启动时，会自动将用户配置目录（$XDG_CONFIG_HOME/nvim）下的 lua/目录添加到Lua的搜索路径中
- Neovim会在runtimepath路径下依次查找目录：（`C:\Users\~\AppData\Local\nvim`是默认的runtimepath），默认导入init.lua文件
    - lua：可 require 的 Lua 模块
    - plugin：自动加载插件
    - colors：主题
    - after：延迟加载文件
- 默认加载配置文件：`C:\Users\用户名\AppData\Local\nvim\init.lua`、`~/.config/nvim/init.lua`
- 默认runtimepath：
    - ~\AppData\Local\nvim
    - ~\AppData\Local\nvim-data/site
    - ~/AppData/Local/nvim-data/lazy/lazy.nvim
    - $DOWNLOAD_DIR\nvim
    - $DOWNLOAD_DIR\share/nvim/runtime
    - $DOWNLOAD_DIR\share\nvim\runtime\pack\dist\opt\netrw
    - $DOWNLOAD_DIR\share\nvim\runtime\pack\dist\opt\matchit
    - $DOWNLOAD_DIR/lib/nvim
    - ~\AppData\Local\nvim/after
    - ~/AppData/Local/nvim-data/lazy/readme
- 插件需要安装Nerd Font字体（`JetBrainsMono Nerd Font`）
- neovim默认！终端使用的是cmd，通过vim.opt.shell显示指定
- 使用Mason插件安装 LSP服务
- Tabpage(Tab 页，里面可以有多个 window) -> Window(显示 buffer 的界面窗口，可以有多个 window 显示同一个 buffer) -> Buffer(存储文本内容，可有多个，存在于内存中)


### 配置目录
```yaml
配置目录: # C:\Users\用户名\AppData\Local
    /nvim: # 核心配置目录（默认runtimepath）
        /lua:
            /config:
            /plugins:
                init.lua: # 插件入口，在根init.lua中引入
        init.lua: # 配置主入口文件
        lazyvim.json:
    /nvim-data: # 插件安装目录
        /lazy: # lazy.nvim安装目录
        mason.log:
```




### nvim
```yaml
nvim:
    --clean:
```




## 核心内容
```yaml
vim: # Neovim Lua API
    api: # 原生底层 API 接口（直接封装自 C 层）
        nvim_buf_delete():
        nvim_buf_get_lines(): # 获取当前 buffer 的第 xxx 行
        nvim_buf_get_name(): # 获取当前 buffer 的文件名
        nvim_buf_set_keymap():
        nvim_buf_set_lines():
        nvim_buf_set_name():
        nvim_command():
        nvim_create_augroup():
        nvim_create_autocmd(): # 设置自动命令，自动监听执行
            DiagnosticChanged: # 错误状态变化事件
        nvim_create_user_command(): # 注册自定义命令 
        nvim_del_autocmd():
        nvim_echo():
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
        nvim_set_keymap(): # 设置快捷键(mode模式, keymap快捷键, command命令, option配置)
            mode:
                n:
            keymap:
            command:
            option:
        nvim_win_get_cursor():
        nvim_win_get_height():
        nvim_win_get_width():
        nvim_win_set_cursor():
        nvim_win_set_height():
        nvim_win_set_width():
    diagnostic: # 错误信息提示
        config():
            update_in_insert:
            virtual_text:
        setloclist(): # 设置location信息
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
        getchar(): # 输入字符
        getline(): # 获取当前行内容
        stdpath(): # 获取标准路径
            config: # 配置文件标准路径
            data: # 数据文件标准路径
        strftime(): # 获取当前时间
        system(): # 运行 shell 命令并获取输出
    g:
        mapleader: # 主键leader key <leader>设置
        maplocalleader:
    keymap: # 快捷键
        set(): # (mode, lhs, rhs, opts)
    loop: # 异步 IO api（LibUV 封装）
    lsp: # lsp配置
        enable:
    o:
        expandtab:
        number:
        relativenumber:
        shiftwidth:
        tabstop:
        termguicolors:
    opt: # 设置 Neovim 选项（替代 vim.o, vim.bo 等）可通过:help options查看配置项
        autoread: # 自动同步文件修改
        backup: # 文件备份
        clipboard: # 剪贴板
            unnamedplus: # 使用系统剪贴板
        colorcolumn: # 高亮第n列
        cursorline: # 高亮当前行
        encoding: # 文件编码
        expandtab: # tab转空格space
        fileencodings: # 文件编码
        number: # 行号
        relativenumber: # 相对行号（相对当前行）
        rtp: # lua模块搜索路径，自动将路径下的/lua目录添加到，lua的模块搜索路径中package.path
            prepend():
        shell: # 指定默认 shell
        shellcmdflag: # shell参数
        shellquote:
        shellxquote:
        shiftwidth: # 缩进占几个空格
        splitright:
        termguicolors:
        tabstop: # 一个tab占几个空格space
        wrap: # 单行换行显示
    uv: # 异步 IO api
        fs_stat(): 
    cmd(): # 执行 Vim 命令
    inspect(): # 用于调试、打印 lua 的 table
    notify(): # 消息通知

cmdline:
    =: # 执行lua表达式
    \<<: # 调整代码缩进
    \>>: # 调整代码缩进
    bdelete: # bd 删除指定 buffer
    bnext: # bn 切换下一个缓冲区 
    bprev: # bp 切换上一个缓冲区
    buffer: # b 切换缓冲区
        n: # 切换文件缓冲区
    buffers: # 列出所有的文件缓冲区，打开文件（可切换buffer n）
    checkhealth: # 检查nvim配置环境
    close: # 关闭当前栏
    colorschema:
    e: # 打开文件
    echo: # 控制台输出
        b:
        bufnr():
    help:
    lclose:
    lopen:
    ls: # 列出所有 buffer
    lua: # 执行lua 脚本
    luafile: # 执行lua文件
    map: # 查看快捷键map映射
    q:: # cmdline历史
    q: # 退出 quit
    resize: # 设置分栏高度 n 行
    saveas: # 另存为
    split: # sp水平分屏
    tabclose: # tabc 关闭tab
    tabedit: # tabe编辑tab 
    tabnew: # 新建tab，tab -> window -> buffer
    tabnext: # tabn 下一个tab
    tabonly: # 
    tabprevious: # tabp 上一个tab
    terminal: # term 切换到终端
    undo: # 撤销
    vertical:
        resize: # 设置分栏宽度 n 列
    vsplit: # vsp 垂直分屏
    w: # 写入 write
    DapContinue: # dap运行
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
    LspInfo: # LSP 信息
    LspStart:
    Mason: # LSP 服务器
    MasonInstall: # lsp安装
        cpptools:

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
    .: # 重复上次操作
    ``: # 回到跳转前位置
    []:
    ctrl:
        \[: # 切换normal
        b: # 向上翻整页
        d: # 向下翻半页
        f: # 向下翻整页
        i: # go forward
        o: # go back
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
            b: # 选中小括号中内容
            e: # 整个文件
            t: # tag 标签内容
            w: # 选中整个单词
            B: # 选中大括号中内容
        j: # 改变当前行
        w: # 改变整个单词，并进入插入模式
    d: # 删除
        d: # 删除当前行
        i: # 删除整个单词
            b: # 选中小括号中内容
            e: # 整个文件
            t: # tag 标签内容
            w: # 选中整个单词
            B: # 选中大括号中内容
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
        a: # 切换代码折叠
        b: # 当前行光标放底部
        c: # 代码折叠
        o: # 代码展开
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

lazy.nvim: # lazy插件启动配置
    setup():
        spec: # 安装插件列表
            import:
lazy.plugin: # lazy插件对象格式
    path: # 插件路径
    dependencies: # 插件依赖
    main: # 插件入口
    opts: # 静态配置
    config: # 动态配置
    keys: # 快捷键绑定
    lazy: # 懒加载
    event: # 插件激活事件
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



Neovim 插件主要有两种方式：
- Lua 插件：Lua
- Vimscript 插件：VimL


NewVim插件目录结构
```txt
myplugin/
├── lua/
│   └── myplugin/
│       └── init.lua       # 插件核心逻辑、主要功能入口（定义M对象、提供setup函数）
├── plugin/
│   └── myplugin.lua       # 自动加载插件
├── README.md
└── lua/myplugin/config.lua  # 可选，配置文件
```
- 自定义插件使用`vim.api.nvim_create_user_command`注册自定义命令








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
安装 lazy.nvim: `git clone https://github.com/LazyVim/starter $env:LOCALAPPDATA\nvim`

插件安装完后还要进行setup()配置

#### snacks

Snacks 是一种轻量级的、基于 Python 的构建工具，主要用于 构建和管理 Neovim 插件。它通过使用 Python 脚本和插件规范来简化插件的安装、配置和管理



#### packer.nvim


nvim插件管理工具


### Event

事件机制




### Tabpage

#### Window



#### Buffer





## 常用插件



### akinsho/bufferline.nvim
```yaml
bufferline:
    BufferLineCycleNext: # 跳转下一个buffer tab 
    BufferLineCyclePrev: # 跳转前一个buffer tab
    BufferLineGoToBuffer: # 跳转指定buffer tab
    BufferLinePickClose: # 选择关闭buffer tab
```

buffer tab栏


### ful1e5/onedark.nvim

One Dark主题


### folke/noice.nvim

仿vscode的命令输入面板



### folke/snacks.nvim

插件集合库


### folke/tokyonight.nvim

暗色主题


### kylechui/nvim-surround

编辑环绕添加

### lukas-reineke/indent-blankline.nvim

缩进层级显示

### matze/vim-move

代码块移动
`alt + j/k`


### mfussenegger/nvim-dap
```lua
return {
  -- DAP 核心
  {
    "mfussenegger/nvim-dap",
    dependencies = {
      "nvim-neotest/nvim-nio",
      "rcarriga/nvim-dap-ui",
      "theHamsta/nvim-dap-virtual-text",
      "williamboman/mason.nvim",
      "jay-babu/mason-nvim-dap.nvim",
    },
    config = function()
      local dap = require("dap")
      local dapui = require("dapui")

      -- UI 初始化
      dapui.setup()
      require("nvim-dap-virtual-text").setup()

      -- Mason 自动安装调试器
      require("mason-nvim-dap").setup({
        ensure_installed = { "codelldb", "cpptools" }, -- 可用 gdb, codelldb, cpptools
        automatic_installation = true,
      })

      -------------------------
      -- C / C++ 调试配置 GDB
      -------------------------

      dap.adapters.cppdbg = {
        id = 'cppdbg',
        type = 'executable',
        command = vim.fn.stdpath("data") .. '\\mason\\bin\\OpenDebugAD7.cmd',
        options = {
          detached = false
        }
      }
      dap.configurations.cpp = {
        {
          name = "Launch (GDB)",
          type = "cppdbg",
          request = "launch",
          program = function()
            return vim.fn.input('可执行文件路径: ', vim.fn.getcwd() .. '/', 'file')
          end,
          args = {},
          stopAtEntry = true,
          cwd = '${workspaceFolder}',
          environment = {},
          externalConsole = false,
          console = "integratedTerminal",
          MIMode = "gdb",
          setupCommands = {
            {
              text = "-enable-pretty-printing",
              description = "启用 gdb 的 pretty-printing",
              ignoreFailures = true
            }
          }
        }
      }

      dap.configurations.c = dap.configurations.cpp

      -- 自动打开关闭 UI
      dap.listeners.after.event_initialized["dapui_config"] = function()
        dapui.open()
      end
      dap.listeners.before.event_terminated["dapui_config"] = function()
        dapui.close()
      end
      dap.listeners.before.event_exited["dapui_config"] = function()
        dapui.close()
      end

      -- 快捷键（LazyVim 风格）
      vim.keymap.set("n", "<F5>", dap.continue, { desc = "Debug: Continue" })
      vim.keymap.set("n", "<F6>", dap.step_over, { desc = "Debug: Step Over" })
      vim.keymap.set("n", "<F7>", dap.step_into, { desc = "Debug: Step Into" })
      vim.keymap.set("n", "<F8>", dap.step_out, { desc = "Debug: Step Out" })

      -- ==== 断点操作 ====
      vim.keymap.set("n", "<leader>d", dap.toggle_breakpoint, { desc = "Debug: Toggle Breakpoint" })
      vim.keymap.set("n", "<leader>D", function()
        dap.set_breakpoint(vim.fn.input("Breakpoint condition: "))
      end, { desc = "Debug: Conditional Breakpoint" })

      -- ==== 其他操作 ====
      vim.keymap.set("n", "<leader>uu", function() require("dapui").toggle() end, { desc = "Debug: Toggle UI" })
    end,
  },
}
```

可视化调试器
cppdbg支持vscode的launch.json配置


### neovim/nvim-lspconfig

nvim lsp默认配置

### nvim-lualine/lualine.nvim

底部状态栏


### nvim-telescope/telescope.nvim
```yaml
Telescope: # 搜索框
    find_files: # 文件查找
```

搜索框集合插件


### nvim-tree/nvim-tree.lua

侧栏文件树列表


### nvim-tree/nvim-web-devicons

文件图标


### nvim-treesitter/nvim-treesitter

代码抽象语法树解析


### nvimtools/none-ls.nvim

代码格式化


### saghen/blink.cmp

代码补全

### smoka7/hop.nvim

热键快速跳转


### terrortylor/nvim-comment

代码注释


### williamboman/mason.nvim

LSP服务安装


### windwp/nvim-autopairs

自动配对
