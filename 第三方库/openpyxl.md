# openpyxl

xlsx操作库

## 基础介绍


Workbook -> WorkSheet -> Cell



## 核心内容
```yaml
openpyxl:
    cell:
        cell:
            Cell:
                value:
    styles:
        Border: 边框样式
            left:
        Font: 字体样式
            name:
            bold:
            size:
        PatternFill: 填充样式
            start_color:
            end_color:
            fill_type:
        Side:
            style:
    utils:
        column_index_from_string():
        get_column_letter():
    worksheet:
        worksheet:
            WorkSheet: # 工作表对象
                column_dimensions: # 列对象
                    index: # 列索引
                    width: # 列宽
                columns: # 所有列数据
                fill: # 填充
                max_column: # 最大列数
                max_row: # 最大行数
                row_dimentsions: # 行对象
                    height: # 行高
                rows: # 所有行数据
                title: # 标题
                values: # 所有行数据
                append(): # 添加一行数据
                cell(): # 获取单元格
                    alignment:
                    border:
                    coordinate: # 单元格坐标
                    column: # 列号
                    column_letter:
                    data_type: # 数据类型
                        s: # 字符串类型
                    fill:
                    font:
                    number_format: # 数字类型
                    row: # 行号
                    value: # 单元格值
                iter_cols(): # 迭代列
                iter_rows(): # 迭代行
                    max_col:
                    max_row:
                merge_cells(): # 合并单元格
                unmerge_cells():
    Workbook:
        active: 默认表
        sheetnames: # 所有表名
        copy_worksheet(): # 拷贝工作表
        create_sheet(): 创建工作表
            title:
        remove(): # 删除工作表
        save(): # 保存工作簿
    load_workbook(): # 加载工作簿
```