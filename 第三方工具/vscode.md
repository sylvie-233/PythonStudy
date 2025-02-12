# vscode

## 基础介绍

### code
```yaml
code:

```

#### settings.json
```yaml
内置变量:
    command:
        python:
            interpreterPath:
        PickProcess:
    workspaceFolder:
    <node_internals>:

settings.json:
    [<file_type>]: # 文件类型匹配
    debug:
        console:
            fontSize: # 调试控制台字体大小
        javascript:
            autoAttachFilter:
    editor:
        codeActionsOnSave:
        defaultFormatter:
        fontSize: # 文本编辑器字体大小
        formatOnSave:
        tabSize:
    eslint:
        enable:
        options:
    explorer:
        fileNesting:
            patterns:
    files:
        associations:
        exclude:
    prettier:
        configPath:
        requireConfig:
        semi:
    python:
        analysis:
            diagnosticMode:
            typeCheckingMode:
                basic:
        formatting:
            provider:
        linting: # 
            lintOnSave:
            pylintEnabled:
        testing:
            pytestArgs:
            pytestEnabled:
    terminal:
        integrated:
            fontSize: # 集成终端字体大小
    workbench:
        colorTheme: # 颜色主题
        iconTheme:
```

编辑器配置文件



#### launch.json
```yaml
launch.json:
    configuraions: # 启动配置（可多个）
        address:
        args:
        autoAttachChildProcesses:
        console:
        cwd:
        env: # 环境变量
        environment:
        envFile:
        miDebuggerPath:
        module: # 要运行的python模块
        name:
        outFiles:
        outputCapture:
        port:
        preLaunchTask: # 预执行任务命令
        program: # 启动项目入口文件
        protocol:
        python:
        request:
            attach: # 附加
            launch: # 启动
        resolveSourceMapLocations:
        restart:
        runtimeArgs:
        runtimeExecutable:
        setupCommands: # 启动注释参数
            description:
            ignoreFailures:
            text:
        skipFiles:
        timeout:
        trace:
        type:
            cppdbg:
            pwa-node:
            python:
        url:
        webRoot:
        MIMode:
    version:


```

调试启动配置


#### tasks.json
```yaml
tasks.json:
    tasks:
        args:
        command:
        dependsOn: # 任务依赖
        group: # 任务分组
            isDefault:
            kind:
                build:
        isBackground:
        label: # 任务名称
        options:
            cwd:
        problemMatcher:
        script:
        type:
            npm:
            shell:
    version:
```

vscode 任务执行（类似npm脚本中的script）


#### extensions.json
```yaml
extensions.json:
    recommendations: # 推荐插件
```

插件配置目录



## 核心内容
```yaml
vscode:
    authnetication:
    chat:
    commands:
        registerCommand(): # 注册命令(多级命令用 . 分隔)
    comments:
    debug:
    env:
    extensions:
    i10n:
    languages:
    im:
    notebooks:
    scm:
    tasks:
    tests:
    window:
        activeTextEditor:
        createInputBox():
        createOutputChannel():
        createQuickPick():
        createStatusBarItem():
        createTerminal():
        createTreeView():
        createWebviewPanel():

        registerTreeDataProvider():
        showErrorMessage():
        showInformationMessage():
    workspace:
    ExtensionContext:
        asAbsolutePath():
        subscriptions:
            push():
    TextDocument:
        getText():
        lineAt():
        offsetAt():
        positionAt():
        save():
    TextEditor:
        document:
        options:
        selection:
        selections:
        viewColumn:
        visibleRanges:
        edit():
            editBuilder:
                insert():
    TreeItem:
        command:
            arguments:
            command:
            title:
        description:
        id:
        label:
        tooltip:
    TreeView:
        onDidChangeCheckboxState():
        onDidCollapseElement():
        onDidExpandElemnt():
        badge:
        description:
        message:
        selection:
        title:
        visible:
        dispose():
        getChildren():
        getParent():
        getTreeItem():
        reveal():
    ViewColumn:
        One:
    WebviePanel:
        active:
        iconPath:
        options:
        title:
        viewColumn:
        viewType:
        visible:
        webview:
            html:
vscode-hook:
    activate():
    deactivate():
```


### 快捷键
```yaml
快捷键:
    alt:
        ↑: # 移动代码行
        ↓: # 移动代码行
    ctrl:
        shift:
            .: # 当前内容切换
            p: # 命令面板
            enter: # 向上插入行
        enter: # 向下插入行
        `: # 打开终端
        d: # 重复选择
        f: # 查找
        g: # 跳转行
        l: # 选择行
```



### 插件
```yaml
package.json:
    activationEvents:
        onCommand:
        onView:
    categories:
    contributes:
        commands: # 自定义命令
            command:
            title:
        menus: # 自定义菜单
        snippets: # 自定义代码片段
            language:
        views:
            name:
        viewsContainers: # 自定义视图
            activitybar:
                icon:
                id:
                title:
    description:
    engines:
    main:
    name:
    publisher:
    version:
```
`vscode`Plugin



#### yo
```yaml
yo:
    code:
```

vscode插件开发脚手架



#### vsce
```yaml
vsce:
    package: # 打包vscode插件
```

vscode打包



### 工作区
```yaml
.code-workspace:
    folders:
        name:
        path:
    settings: # settings.json
```

workspace，多根工作区



### 任务命令

Command、Task 命令、任务