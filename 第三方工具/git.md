# git

`Git实战：P17`

## 基础介绍

分布式版本控制系统

- working directory：工作区
- staging area：暂存区
- repository：仓库

版本管理、代码共享、代码整合

### git
```yaml
git:
    --version:
    add: # 缓存stash
        .: # 当前目录所有文件
    archive: # 创建文件归档
    bisect:
    branch: # 创建分支
        -d: # 删除分支
        -v: # 查看分支
    bundle:
    check: # 切换分支
        -b: # 指定分支
    cherry-pick: # 选择并应用commit修改
    clean: # 从工作区中移除未跟踪的文件
    clone: # 克隆仓库
    commit: # 提交
        -a: # 所有文件
        -m: # 提交备注信息
    config:
        --list: # 列出所有配置
        --global: # 全局配置
        user: # 用户信息配置
            email:
            name:
    diff: # 显示文件修改差异
    fetch: # 仅下拉（下拉到本地仓库）
    gc:
    grep: # 代码库中查找指定片段 (文本查找)
    help:
    init: # 仓库初始化
    log: # commit日志
    ls-files: # 列出所有文件
    merge: # 分支合并（把指定的分支合并到当前分支上）
    mv:
    pull: # 下拉（合并到本地分支，下拉到工作区）
    push: # 推送
        -u: # 远程推送（别名 分支）
    rebase: # 切换分支（变基到指定分支）
    reflog: # 查看commit提交记录信息
        -n: # 查看数量
    remote: # 远程仓库管理
        -v: # 查看远程仓库
        add: # 添加远程仓库（仓库别名 url）（默认origin）
        rm:
        show:
    reset: # commit回滚
        --hard: # 切换commit记录
        --mix: # 回滚到暂存区之前（红色）
        --soft: # 回滚到暂存区
    restore: # 去除文件修改
        --staged: # 移除暂存区文件
    revert: # 撤销指定提交的修改
    rm:
        --cached: # 移除暂存区文件
    shortlog:
    show: # 查看提交的详细信息
    show-branch:
    stash: # 暂存所有修改
    status: # 仓库状态
    submodule: # 管理子模块
    switch:
    tag: # 列出标签
        -d: # 删除标签
    worktree:
        lock:
```



#### .gitconfig
```yaml
.gitconfig:
    core:
        excludesfile:
    credential:
        provider:
    filter:
        clean:
        process:
        required:
        smudge:
    http:
        sslVerify:
    user:
        email:
        name:
```
`~/.gitconfig`


## 核心内容
### branch

默认分支：master


#### pull request

请求将目标分支合并到指定分支（远程）



### commit

提交

#### tag



### .git
```yaml
.git:
    /hooks:
    /info:
    /logs:
    /objects:
    /refs:
    COMMIT_EDITMSG:
    config:
    description:
    HEAD: # commit指针
    index:
    ORRG_HEAD: # 远程commit指针
```

git工作区文件


## github

### github desktop

github官方GUI工具







## gitlab

国内gitlab代理

可本地搭建



### gitlab-ctl
```yaml
gitlab-ctl:
    start:
```


### 提交

#### Pull request

#### 标记

（不是commit的标签）

#### 议题


### 工作流


#### Runner






### 用户管理

用户、访问级别、群组、


#### 群组

