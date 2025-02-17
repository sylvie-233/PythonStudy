# svn

## 基础介绍

SVN Server默认端口：8443

集中式版本管理工具

`.svn`：项目隐藏目录


### svn
```yaml
svn:
    add: # 添加文件（提交暂存区）
        --force: # 递归添加
        --non-recursive: # 非递归
    blame: # 显示内嵌文件信息
    cat: # 显示文件内容
    checkout: # 检出、拉取仓库 svn checkout https://计算机名:8443/svn/仓库名/
    cleanup: # 递归清理
    co: # checkout 简写
    commit: # 提交仓库
        -m: # 提交备注信息
    copy: # 文件拷贝
    delete: # 删除文件
    diff: # 显示差异、特定行级详细信息
        -r: # 版本号
    export: # 显示目录结构树
    help: # 帮助命令
    import: # 指定提交
    info: # 文件信息
    list: # 列出文件信息
    log: # 仓库信息
        -r:
    merge:
    mkdir: # 创建目录
    move: # 文件移动
    propdel: # 属性删除
    propedit: # 属性编辑
    propget: # 属性获取
    propset: # 属性设置
        -v:
        svn:
            ignore: # 设置忽略文件
    resolved: # 删除工作拷贝文件或目录的“冲突”状态
    revert: # 版本回退、取消add
        -R: # 递归
    st: # status 简写
    status: # 仓库状态
        --no-ignore:
    update: # 更新仓库
```


### svnadmin
```yaml
svnadmin:
    create: # 创建版本库
    dump: # 将文件系统的内容转储到标准输出
    help:
    hotcopy: # 版本库热备份
    list-dblogs:
    load:
    lstxns: # 列出所有未提交文件
    recover: 
    rmtxns:
    setlog:
    verify:
```

版本库的管理工具

### svnlook
```yaml
svnlook:
    author: # 查看作者
    cat:
    changed:
    date: # 时间戳
    diff:
    dirs-changed:
    help:
    history: # 历史记录
    info: # 文件信息
    log:
    propget:
    proplist:
    tree: # 目录结构
    uuid:
    youngest: # 最新版本
```

svn信息查看器


### svnserve
```yaml
svnserve:

```


### svnversion
```yaml
svnversion:
```


## 核心内容
