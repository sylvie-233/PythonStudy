# neovim

## 基础介绍

控制台代码编辑器




### nvim
```yaml
nvim:

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
                config: `~/AppData/Local/nvim`
                data: `~/AppData/Local/nvim-data`
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

`~/.config/nvim/init.lua`

nvim核心配置文件


## 核心内容
```yaml
cmdline:
    bd: # 关闭插件
    w: # 写入
    Lazy: # lazy.nvim插件
    Mason: # LSP 服务器

edit:
    {num}:
        j: # 向下移动
        k: # 向上移动
        yy: # 复制多行
    []:
    shift:
        g: # 跳转到最后一行
    b: # 按单词向前移动
    c:
        iw: # 删除整个单词进入插入模式
    d: # 删除
        iw: # 删除整个单词
        w: # 删除单词
    f: # 搜索字符移动
    h:
    i: # 插入模式
    j:
    K:
    l:
    o: # 向下插入新行
    p: # 粘贴
    u: # 撤销操作
    v:
        iw: # 选中整个单词
        w: 
    w: # 按单词向后移动
    y: # 复制
```

### Config
```yaml
Config:
    expandtab:
    tabstop:
    softtabstop:
    shiftwidth:
```




### Plugin


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




#### packer.nvim


nvim插件管理工具


## 常用插件

