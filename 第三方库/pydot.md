# pydot


## 基础介绍

Graphviz操作库
- Graph（图）：由节点和边组成，可以是有向图 (digraph) 或无向图 (graph)。
- Edge（边）：节点之间的关系。
- Node（节点）：图中的点。


## 核心内容
```yaml
pydot:
    Cluster:
    Dot:
        graph_type:
        add_edge():
        add_node():
        set_prog():
        write_png():
    Edge:
    Node:
        color:
        shape:
        style:
    graph_from_dot_data():
    graph_from_dot_file():
```