# neovim

## 基础介绍

### nvim



#### init.lua
```yaml
:
    vim:
        g:
            mapleader:
        keymap:
            set():
        opt:
            number:
```

nvim核心配置文件


## 核心内容
```yaml
cmdline:
    w: # 写入
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
