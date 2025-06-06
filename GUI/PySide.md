# PySide

>
>`QML6(Qt Quick)开发教程: P3`
>`【王铭东】从零入门PySide6: P7`

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
        QDateTime:
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
        QThread:
            finished:
            started:
            run():
            start():
        QTimer: # 定时器
            timeout:
            setInteval():
            singleShot():
            start():
            stop():
        QUrl: # url路径
        Signal: # 信号（多窗口通信）
            connect(): # 连接函数
            emit(): # 触发信号
    QtGui:
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
    QtQuick:
        QQuickView: # qml视图
            setSource():
            show():
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
        QComboBox:
            currentIndexChanged:
            currentTextChanged:
            addItems():
        QDialog:
        QFileDialog:
            getOpenFileName():
        QFormLayout:
            addRow():
        QFrame:
        QGridLayout:
            addWidget():
        QHeaderView:
        QInputDialog:
            getInt():
            getItem():
            getMultiLineText():
            getText():
        QLabel:
            setAlignment():
            setText():
        QLineEdit:
            setPlaceholderText():
            text():
        QListView:
            setModel():
        QListWidget:
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
        QMainWindow:
            setCentralWidget():
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
        QPushButton:
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
        QTextEdit: # 文本框
            textChanged:
            setText():
            toPlainText():
        QToolBar:
        QToolBox: # 选项卡
            addItem():
        QVBoxLayout:
            addLayout():
            addWidget():
        QWidget:
            addAction():
            close():
            hide():
            resize():
            sender(): # 信号发出者
            setAttribute():
            setContextMenuPolicy():
            setGeometry(): # 位置
            setWindowFlag():
            show():
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
        Button:
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
    Rectangle: # 矩形
        anchors: # 布局属性
            centerIn: # 居中
                parent:
        color:    
        font:
            pointSize:    
        height: # 高度
        width: # 宽度
    SequentialAnimation:
    State:
    Text: # 文本
        text:    
    Timer:
    TouchArea:
    Transition:
    Window: # 窗口
        height:
        visible:
        width:
    qsTr(): # 字符串
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
