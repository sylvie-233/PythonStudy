# Numpy & Pandas & Matplotlib


## 基础介绍

np数组进行布尔运算时，返回数组每个元素对应布尔值（判断取舍）`[False True True]`，`arr[arr > 0]`



## 核心内容
```yaml
numpy:
    ndarray:
        dtype: 元素类型
        itemsize: 每个元素大小
        ndim:
        shape:
        size:
        all():
        any():
        argmax():
        astype(): 元素类型转换
        copy(): 数组拷贝
        max():
        reshape(): 修改数组形状
        sum(): # 数组求和
        transpose(): # 矩阵转置
        vstack(): # 竖直合并
    version:
        version:
    arange(): 序列数组生成（左闭右开）
    array():
    eye():
    linspace(): 间隔生成
    load(): 文件加载
    loadtxt():
    ones():
    save(): 文件保存
    savetxt():
    zeros():

pandas:
    DataFrame: # 二维表
        columns:
        dtypes: # 每一列的数据类型
        shape:
        values:
        agg(): # 表聚合
        append(): # 添加数据
        astype():
        concat():
        drop_duplicates(): # 删除重复值
        fillna():
        from_records():
        groupby(): # 分组
        head():
        info():
        isnull():
        join(): # 表连接
        loc(): # 元素索引
        map():
        query(): # 表查询
        rename():
        replace():
        sample(): # 采样
        set_index(): # 设置索引列
        tail():
        to_excel(): # 文件输出：excel
        unique():
        where(): # 条件查询
    Series: # 二维表的列

    nan:
    date_range():
    merge(): # 合并表
    read_csv():
    read_excel():
```

