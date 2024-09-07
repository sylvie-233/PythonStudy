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
            WorkSheet:
                fill: 填充
                title: 标题
                cell(): 获取单元格
                    row:
                    column:
                    value:
    Workbook:
        active: 默认表
        copy_worksheet(): 拷贝工作表
        create_sheet(): 创建工作表
            title:
        save(): 保存工作簿

```