# beautifulsoup4

## 基础介绍

BeautifulSoup -> Tag


## 核心内容
```yaml
bs4:
    BeautifulSoup: # 主文档类（需指定文档解析器）
        a:
            string: # 字符串内容
            get():
        attrs:
        head:
        name:
        title:
        find(): # 查找元素
            class:
            id:
        findall(): # 查找所有元素
            attrs: # 属性查找
            limit:
            name:
        pretty(): # 格式化文档
        select(): # CSS选择器查找元素
        select_one():
    Tag:
        children:
        contents:
        next_elements:
        next_sibling: # 下一个兄弟节点
        parents:
        prettify:
        text: # 文本内容
        get(): # 获取属性值
        select(): # CSS选择器
```