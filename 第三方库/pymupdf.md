# pymupdf


## 基础介绍



对象结构
```
fitz.Document ────> fitz.Page ───> fitz.Text / Pixmap / Annotation / Link
         │                          └──> get_images() → Image
         ├──> metadata / outlines / toc
         └──> insert_pdf(), save(), new_page(), etc.
```


## 核心内容
```yaml
fitz:
    Annotation:
    Document: # 文档对象
        is_encrypted:
        authenticate():
        close():
        insert_pdf():
        save():
    Font:
    Image:
    Link:
    Matrix:
    Metadata:
    Outline:
    Page: # 页面对象
        get_images():
        get_pixmap():
        get_text():
        insert_image():
        insert_text():
        set_cropbox():
        set_rotation():
    Pixmap:
    Point:
    Rect:
    TextPage:
    TextPageDict:
    TextPageHTML:
    TextWriter:
    TOC:
    Xref:
    open(): # pdf文档对象 Document
```