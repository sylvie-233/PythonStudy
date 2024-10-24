# PyQt

>
>``
>

## 基础介绍

PyQt & PySide


qtdesigner、pyrcc、pyuic、

`.ui`文件

### pyuic
```yaml
pyuic:
    -o:
```

根据`.ui`文件生成py代码（`Ui_Form`、`retranslateUi()`、`setupUi()`）



`QApplication` -> `QMainWindow` -> `QWidget` -> `Signal` -> `QAction`

`view` -> `model` -> `item`

## 核心内容
```yaml
PySide6:
    QtCore:
        QCoreApplication:
        QDate:
        QDateTime:
        QMetaObject:
            connectSlotsByName(): # 连接信号和槽
        QObject:
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
        QUrl:
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
    QtWidgets:
        QAction:
            triggered:
        QApplication:
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



pyqt:
    
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


### 信号和槽

事件机制、connect()连接处理函数