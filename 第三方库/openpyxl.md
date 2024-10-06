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
        Alignment: # 对其
        Border: # 边框样式
            diagonal: # 对角线
            left:
        Font: # 字体样式
            name:
            bold:
            size:
        PatternFill: # 填充样式
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
                print_area: # 打印区域
                print_title_cols:
                print_title_rows:
                row_dimentsions: # 行对象
                    height: # 行高
                rows: # 所有行数据
                sheet_properties: # 工作表属性
                    tabColor:
                title: # 标题
                values: # 所有行数据
                append(): # 添加一行数据
                cell(): # 获取单元格（1行1列开始）
                    alignment: # 
                    border: # 
                    coordinate: # 单元格坐标
                    column: # 列号
                    column_letter:
                    data_type: # 数据类型
                        s: # 字符串类型
                    fill:
                    font: # 字体样式
                    number_format: # 数字类型
                    row: # 行号
                    style: # 
                    value: # 单元格值
                delete_cols():
                    idx: # 起始索引
                    amount: # 个数
                delete_rows():
                insert_cols():
                insert_rows():
                iter_cols(): # 迭代列
                iter_rows(): # 迭代行
                    max_col:
                    max_row:
                merge_cells(): # 合并单元格
                move_range(): # 移动区域
                unmerge_cells():
    Workbook:
        active: # 默认表
        sheetnames: # 所有表名
        worksheets: # 所有工作表
        copy_worksheet(): # 拷贝工作表
        create_sheet(): # 创建工作表
            title:
        remove(): # 删除工作表
        save(): # 保存工作簿
    load_workbook(): # 加载工作簿
```