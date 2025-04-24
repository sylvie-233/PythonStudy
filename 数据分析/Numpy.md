# Numpy & Pandas & Matplotlib


## 基础介绍


numpy核心功能：
- 数组操作（属性、索引、数学运算、广播机制）
- 文件读写
- 随机数生成


pandas核心功能：
- Series
- DataFrame
- 文件读写
- 数据分析
    - 数据查看与基础信息
    - 数据清洗与预处理
    - 数据选择与过滤
    - 数据变形
    - 时间序列处理
    - 可视化集成


matplotlib核心功能：
- 基础绘图
    - 折线图
    - 散点图
    - 柱状图
    - 直方图
    - 饼图
    - 箱线图
- 图表定制
- 多图布局
- 图像保存


## Numpy
```yaml
numpy: # np
    linalg: 
        inv(): # 逆矩阵
    ndarray: # n维数组
        dtype: # 数据类型
        itemsize: # 每个元素大小
        ndim: # 维数（轴数）
        shape: # 维度 (rows, columns)
        size: # 元素个数
        T: # 转置矩阵
        all():
        any():
        argmax():
        astype(): # 元素类型转换
        copy(): # 数组拷贝
        max():
        reshape(): # 修改数组形状
        sum(): # 数组求和
        transpose(): # 矩阵转置
        vstack(): # 竖直合并
    random: # 随机
        randint():
        randn():
    version:
        version:
    arange(): # 序列数组生成（左闭右开）
    argmax():
    array():
    concatenate(): # 拼接
    dot(): # 矩阵乘法
    eye(): # 单位矩阵
    linspace(): # 间隔生成
    load(): # 文件加载
    loadtxt():
    max(): # 最大值
    mean(): # 平均值
    min(): # 最小值
    ones(): # 全 1
    reshape(): # 改变形状
    save(): # 文件保存
    savetxt():
    sin(): # 正弦函数
    split(): # 分割
    stack(): # 堆叠
    std(): # 标准差
    sum():
    zeros(): # 全零
```

矩阵、向量运算库






### ndarray
```python
# 索引
a[0]           # 第一行
a[:, 1]        # 第二列
a[1:, :2]      # 第二行到最后行，第一列到第二列
a[a > 2]       # 条件索引
```


广播机制（broadcasting）



## Pandas
```yaml
pandas: # pd
    DataFrame: # 二维excel表，每列可以是不同类型
        columns: # 列名
        dtypes: # 每一列的数据类型
        index: # 索引
        shape: # 形状、行列数
        values:
        agg(): # 表聚合
        append(): # 添加数据
        astype():
        concat():
        describe(): # 数值统计
        drop(): # 删除行、列
        drop_duplicates(): # 删除重复值
        drop_na(): # 删除含缺失值的行
        fillna():
        from_records():
        groupby(): # 分组
        head(): # 查看前n行
        iloc(): # 选择行
        info(): # 数据结构信息
        isnull():
        join(): # 表连接
        loc(): # 选择行
        map():
        query(): # 表查询
        rename(): # 重命名
            columns:
            inplace:
        replace():
        reset_index():
        sample(): # 采样
        set_index(): # 设置索引列
        sort_values(): # 排序
            ascending:
            by:
        tail():
        to_excel(): # 文件输出：excel
        unique():
        where(): # 条件查询
    Series: # 一维带标签数组，二维表的列
        index: # 列索引
    nan:
    concat(): # 连接
        axis:
    date_range():
    merge(): # 合并表，联表
    read_csv():
    read_excel():
    to_csv():
    to_datetime():
```


Python 中最流行的数据分析库，基于 NumPy 构建，专为处理结构化数据（如表格、时间序列）设计




### Series
```python
# 字面量创建
s = pd.Series([10, 20, 30], index=['a', 'b', 'c'])
```

一维带标签数组（类似字典），支持异构数据类型（整数、字符串、浮点数等）


### DataFrame
```python
# 字面量创建
data = {'name': ['Alice', 'Bob'], 'age': [25, 30]}
df = pd.DataFrame(data)
```

二维表格型数据结构（类似 Excel 表），每列可以是不同类型
支持条件筛选




## Matplotlib
```yaml
matplotlib:
    pyplot:
        rcParams: # 资源属性配置
        style: # 图象样式
            use():
        bar(): # 柱状图
            yerr: # 波动值
            set():
        boxplot(): # 箱线图
        barh(): # 条形图
        clf():
        fill_between(): # 填充
        grid():
        hist(): # 直方图
        ion():
        legend(): # 图例
        pie(): # 饼图
        plot(): # 折线图
            label: # 曲线标签
            linewidth: 
        savefig(): # 保存图象
        scatter(): # 散点图
            c:
            s:
            alpha:
        show(): # 显示图象
        subplot(): # 子画布区域
        subplots(): # 生成子画布区域
            nrows:
            ncols:
        title(): # 标题
        tight_layout():
        xlabel(): # x轴标签
        xticks(): # x轴刻度标签
        ylabel(): # y轴标签
        ylim(): # y轴数值限制
```