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
    worksheet:
        worksheet:
            WorkSheet: # 工作表对象
                fill: # 填充
                max_column: # 最大列数
                max_row: # 最大行数
                title: # 标题
                values: # 所有行数据
                append(): # 添加一行数据
                cell(): # 获取单元格
                    coordinate: # 单元格坐标
                    data_type: # 数据类型
                    column:
                    column_letter:
                    number_format:
                    row:
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