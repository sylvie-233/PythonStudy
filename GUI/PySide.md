# PySide

>
>`QML6(Qt Quick)开发教程: P3`
>`【王铭东】从零入门PySide6: P13`

## 基础介绍

PySide
`QApplication` -> `QMainWindow` -> `QWidget` -> `Signal` -> `QAction`

安装：`pip install pyside6`



qtdesigner、pyrcc、pyuic、
`.ui`文件




### pyuic
```yaml
pyuic:
    -o:
```

根据`.ui`文件生成py代码（`Ui_Form`、`retranslateUi()`、`setupUi()`）



`view` -> `model` -> `item`



## 核心内容
```yaml
PySide6:
    QtCore: # Qt核心模块
        QCoreApplication:
        QDate:
        QDateTime: # 日期和时间类
        QMetaObject:
            connectSlotsByName(): # 连接信号和槽
        QObject: # Qt基类对象
            objectName:
        QPoint:
        QRect:
        QSize:
        Qt:
            AlignmentFlag:
                AlignCenter:
            Orientation:
                Horizontal:
        QThread: # 线程类
            finished:
            started:
            run():
            start(): 
        QTimer: # 定时器
            timeout: # 定时信号
            setInteval():
            singleShot():
            start(): # 开始
            stop():
        QUrl: # url路径
        Signal: # 信号（多窗口通信）
            connect(): # 连接函数
            emit(): # 触发信号
    QtGui: # 提供了对图形、图像、字体、颜色等的支持
        QBrush:
        QColor:
            fromRgb():
        QCursor:
        QFont:
        QIcon:
        QImage:
        QPainter:
        QPixmap:
        QSqlDatabase:
            addDatabase():
            setDatabaseName():
        QSqlQueryModel:
            setQuery():
        QSqlTableModel:
            select():
            setTable():
        QStandardItem:
        QStandardItemModel:
            setItem():
        QTransform:
    QtMultimedia: # 提供了多媒体相关的功能，如音频、视频播放等
    QtQuick:
        QQuickView: # qml视图
            resize():
            setSource():
            show():
    QtSvg: # 提供了对 SVG（可伸缩矢量图形）的支持
    QtWidgets: # Widget
        QAction:
            triggered:
        QApplication: # 主应用
            exec(): # 事件循环
        QButtonGroup:
            checkedButton:
        QCheckBox:
            stateChanged:
            setCheckState():
        QComboBox: # 下拉框
            currentIndexChanged:
            currentTextChanged:
            addItems():
        QDialog:
        QFileDialog:
            getOpenFileName():
        QFormLayout: # 表单布局
            addRow():
        QFrame:
        QGridLayout: # 网格布局
            addWidget():
        QHBoxLayout: # 行排列
            setStretch(): # 组件弹性因子
        QHeaderView:
        QInputDialog:
            getInt():
            getItem():
            getMultiLineText():
            getText():
        QLabel: # 标签
            setAlignment():
            setText():
        QLineEdit: # 单行文本框
            setPlaceholderText():
            text():
        QListView:
            setModel():
        QListWidget: # 显示列表
            currentItemChanged:
            addItem():
            clear():
            count():
            findItems():
            insertItem():
            item():
            sortItems():
            takeItem():
        QListWidgetItem:
            setText():
            value():
        QMainWindow: # 主窗口类，可以包含菜单栏、工具栏、状态栏等
            setCentralWidget(): # 中心组件
            setLayout():
            show():
        QMenu:
        QMenuBar:
        QMessageBox:
            StandardButton:
                Apply:
                Cancel:
                Discad:
                No:
                Ok:
            about():
            critical():
            infomation():
            question():
            warning():
        QPixmap:
        QPlainTextEdit:
        QPushButton: # 按钮
            clicked:
            setText():
            setToolTip():
        QRadioButton:
        QSlider:
            setRange():
            value():
        QStackedWidgt:
        QStatusBar:
        QStyle:
            StandardPixmap:
        QTableView:
            setModel():
        QTableWidget: # 表格
            cellClicked:
            findItems():
            item():
            selectedItems():
            setColumnCount():
            setHorizontalHeaderLabels():
            setItem():
            setRowCount():
            setSpan():
        QTableWidgetItem:
            column():
            row():
            setBackground():
        QTabWidget:
            addTab():
            setTabsClosable():
        QTabWidgetItem:
        QTextEdit: # 多行文本框
            textChanged:
            setText():
            toPlainText():
        QToolBar:
        QToolBox: # 选项卡
            addItem():
        QVBoxLayout:
            addLayout():
            addWidget():
        QWidget: # 窗口，窗口小部件的基类
            addAction():
            close():
            hide():
            resize(): # 窗口大小
            sender(): # 信号发出者
            setAttribute():
            setContextMenuPolicy():
            setGeometry(): # 位置
            setWindowFlag():
            setWindowTitle(): # 窗口标题
            show(): # 显示窗口
            styleSheet: # QSS样式
```








### Signal

信号、槽机制
事件机制、connect()连接处理函数



## QtQuick
```yaml
QtQuick:
    Controls:
        Extras:
            Popup:
            ToolTip:
        Material:
        Universal:
        ApplicationWindow:
        Button: # 按钮
            background:
            id:
            onClicked: # 点击回调    
        CheckBox:
        ComboBox:
        Dial:
        Dialog:
        Label:
        Menu:
        MenuBar:
        ProgressBar:
        RadioButton:
        Slider: 
        SpinBox:
        Switch:
        TabBar:
        TabButton:
        TextArea:
        TextField:
        ToolButton:
        ToolTip:
        ScrollBar:
        ScrollView:
    Layouts:
        ColumnLayout:
        GridLayout:
        RowLayout:
    Shapes:
        Shape:
        ShapePath:
    Animation:
    Behavior:
    Flickable:
    FocusScope:
    GridView:
    Image: # 图片
        anchors:
            bottom:
            centerIn:
            fill: # 填充
                parent:
            horizontalCenter:
        id:
        source:
    Item:
    Keys:
    ListView:
    Loader:
    MouseArea:
        onClicked:
    NumberAnimation:
    ParallelAnimation:
    PathView:
    Qt: # Qt工具库
        rgba():
    Rectangle: # 矩形
        property: # 属性定义
            int:
        anchors: # 布局属性
            bottom:
            centerIn: # 居中
                parent:
            horizontalCenter:
        color: # 背景色
        font:
            pointSize:    
        height: # 高度
        radius: # 圆角
        width: # 宽度
    SequentialAnimation:
    State:
    Text: # 文本
        WordWrap:
        color:
        text:    
        wrapMode:
    Timer:
    TouchArea:
    Transition:
    Window: # 窗口
        height:
        title:
        visible:
        width:
    qsTr(): # 字符串
    
JavaScript:
    Math: # 数据库
        random():
    console:
        log():
```




### qmlproject
```yaml
qmlproject:
    Project:
        mainFile:
```



### QML

输入控件、展示控件、布局控件、系统交互控件(文件选择)


#### 列表渲染

QListView、QTableView、

view -> model


#### 条件渲染


#### 页面路由

QStackedWidget、QTabWidget


### QSS
```yaml
qss:
    background-color:
    border:
    border-radius:
    color:
```



### QRC

资源文件，XML格式
