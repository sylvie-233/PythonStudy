# git

``

## 基础介绍

分布式版本控制系统

- working directory：工作区
- staging area：暂存区
- repository：仓库

版本管理、代码共享、代码整合


pull = fetch + merge

pull request: 远程代码分支合并


git-object类型：
- blob: 	文件内容
- tree: 	文件夹结构，记录 blob 和 tree 的引用
- commit:	一次提交，记录 tree 的快照和父 commit
- tag:	    提交的标签


git文件状态：
- untracked
- modified
- staged
- unmodified


分离头指针：Head指向具体的commit，而不是某一branch分支



### git
```yaml
git:
    --version:
    add: # 缓存stash
        .: # 当前目录所有文件
    apply: # 使用patch补丁
    archive: # 创建文件归档
    bisect:
    branch: # 创建分支
        -d: # 删除分支
        -D:
        -r: # 远程分支
        -v: # 查看分支
    bundle: 
    cat-file: # 查看objects文件
        -p: # 查看对象内容
        -s: # 查看文件长度
        -t: # 查看对象类型
    checkout: # 切换分支
        -b: # 指定分支
    cherry-pick: # 选择并应用指定的commit修改，多分支操作
    clean: # 从工作区中移除未跟踪的文件
    clone: # 克隆仓库
    commit: # 提交
        -a: # 所有文件
        -m: # 提交备注信息
        --amend: # 把当前暂存区（staged）的内容合并进上一次提交，不产生新的commit
            --no-edit: # 保留commit信息
    config:
        -l:
        --list: # 列出所有配置
        --local:
        --global: # 全局配置
        --system:
        alias: # 命令别名
        merge:
            tool:
        mergetool:
            keepBackup:
            path:
        user: # 用户信息配置
            email:
            name:
    diff: # 显示文件修改差异
        --cached:
    fetch: # 仅下拉（下拉到本地仓库）,修改本地远程仓库信息
        --prune: # 清空悬空垃圾objects对象
    format-patch: # 创建patch补丁
    fsck: # 查看悬空垃圾objects对象
    gc: # objects对象压缩
    grep: # 代码库中查找指定片段 (文本查找)
    help:
    init: # 仓库初始化
    log: # commit日志
        --graph:
        --pretty-format:
    ls-files: # 查看index索引文件,列出所有文件
        -s: # staged的文件
    ls-tree:
    merge: # 分支合并（把指定的分支合并到当前分支上）
    mergetool: # 分支合并工具
    mv:
    prune: # 清空悬空垃圾objects对象
    pull: # 下拉（合并到本地分支，下拉到工作区）
    push: # 推送
        -d: # 删除远程分支
        -u: # set-upstream别名，远程推送（别名 分支）
        --set-upstream: # 设置远程仓库关联分支
        --tags: # 推送标签
    rebase: # 切换commit（分支线性变基，用于合并commit、commit分支转线性、）(rebase应该在push之前)
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
        prune: # 清空悬空垃圾objects对象
        rm:
        show: # 显示远程仓库信息
    reset: # commit回滚
        --hard: # 切换commit记录
        --mix: # 回滚到暂存区之前（红色）
        --soft: # 回滚到暂存区
        ORIG_HEAD:
    restore: # 去除文件修改
        --staged: # 移除暂存区文件
    revert: # 撤销指定提交的修改
    rm:
        --cached: # 移除暂存区文件
    shortlog:
    show: # 查看提交的详细信息
    show-branch:
    stash: # 暂存所有修改
        pop: # 取出暂存区修改
    status: # 仓库状态
    submodule: # 管理子模块
        add: # 添加子模块
        status:
        update:
            --init:
            --recursive:
            --remote:
    switch: # 切换分支
    tag: # 列出标签
        -a: # 添加标签
        -d: # 删除标签
        -m: # 标签描述
    unpack-objects: # 解压缩 objects pack
    verify-pack: # 查看 objects pack 压缩信息
        -v:
    worktree: # 工作树
        add:
        list:
        lock:
        remove:
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
    remote: # 远程仓库配置，origin名称可选
        fetch:
        url:
    submodule: # git子模块
        path:
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
```yaml
.git:
    /hooks:
    /info:
        exclude:
    /logs: # commit日志
        /refs:
            /heads:
                master:
    /objects: # hash，所有对象（blob, tree, commit）都存这里
        /info:
        /pack: # objects 合并压缩
            pack-xxx.idx:
            pack-xxx.pack:
    /refs: # 保存分支（refs/heads）和 tag（refs/tags）
        /heads: # 分支指针
            master: # master分支指针，指向objects中的hash commit
        /remotes: # 远程仓库
            /origin: # 自定义origin远程仓库名
                master:
        /tags: # 标签
            v1.0.0:
    COMMIT_EDITMSG:
    branches:
    config: # 本地git配置，局部项目配置
    description:
    FETCH_HEAD:
    HEAD: # 当前分支指针
    index: # 暂存区（staging area）
    ORIG_HEAD: # 上一次HEAD commit 指针
    ORRG_HEAD: # 远程commit指针
    packed-refs: # 远程仓库master commit信息
```

git工作区文件


objects文件中包含了object类型、长度、文件内容




### Branch

默认分支：master

branch分支仅仅是commit的指针



#### Pull Request

请求将目标分支合并到指定分支（远程）



### Commit
```yaml
commit规范:
    chore: # 维护任务，更新构建任务等
    docs: # 文档变更
    feat: # 添加新特性
    fix: # 修复bug
    perf: # 优化相关的性能提升
    refactor: # 重构（即代码改动，但不影响功能）
    style: # 代码格式（如缩进、空格等），不影响代码逻辑
    test: # 增加或修改测试代码
```
提交

![gitcommit生成信息](../.assets/gitcommit生成信息.png)
![多级commit结构](../.assets/多级commit结构.png)
commit -> tree -> file



#### Tag

commit语义化标签







### HOOKS


![githooks执行流程](../.assets/githooks执行流程.png)
- pre-commit
- post-commit
- pre-push
- update


bash脚本


### SubModule

子模块



### WorkTree

多分支同时操作



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

