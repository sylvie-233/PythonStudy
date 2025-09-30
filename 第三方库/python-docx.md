# python-docx



## 基础介绍

操作 Word 文档库
支持创建、读取、修改 .docx 文件（MS Word 2007及以上版本的格式）
`uv add python-docx`

## 核心内容
```yaml
docx:
    oxml:
        ns:
        OxmlElement:
    section:
        Sections: # 章节
    shared:
        Cm:
    table:
        Table: # 表格
            cell(): # 获取单元格
                paragraphs:
    text:
        paragraph:
            Paragraph: # 段落
    Document: # 文档
        paragraphs: 
            text:
            add_run():
            clear(): # 清理
        add_heading():
        add_page_break(): # 插入分页
        add_paragraph():
        add_picture():
        add_run():
        add_table():
        save():
```
