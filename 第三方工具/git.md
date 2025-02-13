# git

`Git实战：P17`

## 基础介绍

分布式版本控制系统

- working directory：工作区
- staging area：暂存区
- repository：仓库

版本管理、代码共享、代码整合


pull = fetch + merge

pull request: 远程代码分支合并

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
        --local:
        --global: # 全局配置
        --system:
        merge:
            tool:
        mergetool:
            keepBackup:
            path:
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
        --graph:
        --pretty-format:
    ls-files: # 列出所有文件
    merge: # 分支合并（把指定的分支合并到当前分支上）
    mergetool: # 分支合并工具
    mv:
    pull: # 下拉（合并到本地分支，下拉到工作区）
    push: # 推送
        -u: # 远程推送（别名 分支）
        --tags: # 推送标签
    rebase: # 切换commit（变基，可合并commit、commit分支转线性、）(rebase应该在push之前)
        --abort:
        --continue:
        edit:
        exec:
        drop:
        fixup:
        pick:
        reword:
        squash: # 合并到前一个commit
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
        -a: # 添加标签
        -d: # 删除标签
        -m: # 标签描述
    worktree:
        lock:
```



#### .gitconfig
```yaml
.gitconfig:
    branch: # 分支配置
        merge:
        remote:
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
    merge:
        tool:
    mergetool:
        path:
    remote: # 远程仓库配置
        fetch:
        url:
    user: # 用户信息配置
        email:
        name:
```

本地配置、全局配置、系统配置
`.git/config`、`~/.gitconfig`


#### .gitignore

git 管理忽略文件


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

