# Latext




## 基础介绍

`.tex`文件



## 核心内容
```yaml
latext:
    --- # 内容元数据
    \documentclass:
        {article}: # 文章
            []:
                12pt:
                letterpaper:
        {ctexart}:
    \usepackage:
        {graphicx}: # 图像包
        {inputenc}:
            []:
                utf8:
    \author: # 作者
    \date: # 日期
        \today: # 今天
    \graphicspath: # 图片路径
    \title: # 标题
    --- # 内容主体
    \begin{abstract}: # 文章摘要
    \begin{center}: # 内容居中
    \begin{displaymath}: # 块级数学公式 `\[ ... \]`
    \begin{document}: # 文章主体
        %: # 单行注释
        \part: # 文章部分
            \chapter: # 文章章节
                \section: # 文章段落
                    \subsection: # 文章子段落
                        \subsubsection:
                            \paragraph:
                                \subparagraph:
        \emph:
        \includegraphics: # 引入图片
        \maketitle: # 打印标题内容
        \newline: # 换行
        \newpage: # 换页
        \pageref: # 页码引用
        \ref: # 标签引用
        \tableofcontents: # 打印目录
        \textbf: # 粗体
        \textit: # 斜体
        \underline: # 下划线
    \begin{enumerate}: # 有序列表
        \item: 
    \begin{equation}:
    \begin{figure}: # 图片
        []:
            h:
        \caption:
        \centering: # 居中
        \includegraphics:
            []:
                width:
        \label: # 标签
    \begin{itemize}: # 无序列表
        \item:
    \begin{math}: # 内联数学公式 `$ ... $` 、`\( ... \)`
        \begin{cases}: # 大括号
        \begin{matrix}: # 矩阵
        --- # 样式
        {}: # 分组
        ^: # 上标
        _: # 下表
        \left:
        \right:
        \rm: # 去除样式
        \text:
        --- # 字符
        \alpha:
        \beta:
        \delta:
        \Delta:
        \epsilon:
        \infty:
        \lambda:
        \mathbb:
        \pi:
        \varepsilon:
        \varphi: # phi
        --- # 运算符
        \because:
        \cap:
        \cup:
        \cdot:  
        \div:
        \exists:
        \forall:
        \ge:
        \in:
        \leftarrow:
        \notin:
        \subseteq:
        \therefore:
        \times: # 乘法
        --- # 结构式
        \binom: # 小括号矩阵
        \frac: # 分数
        \int: # 积分
        \lim: # limit
            \limits:
            \to:
        \oint:
        \over: # 分式
        \overrightarrow:
        \prod: # 连乘
        \sqrt: # 根式
        \sum: # 求和
        \vex: # 向量
    \begin{table}: # 表格
        \begin{tabular}: # 表格数据
            \hline:
```