# vscode

## 基础介绍








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



### Plugin
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
`vscode`



#### yo
```yaml
yo:
    code:
```

vscode脚手架



#### vsce
```yaml
vsce:
    package: # 打包vscode插件
```

vscode打包