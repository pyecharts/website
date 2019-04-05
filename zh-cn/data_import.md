## borax.fetch 模块

> 项目地址： https://github.com/kinegratii/borax

### 安装

borax 要求 Python3.5 以上，可以使用以下命令安装这个库。

```shell
$ pip install borax
```

### 函数定义文档

该模块使用 `fetch` 函数，签名如下：

```python
fetch(iterable, key, *keys, default=EMPTY, defaults=None, getter=None)
```

各参数的意义如下：

- iterable：数据列表
- key / keys：键值、属性访问方式的索引
- default：默认值，用于选择单个属性
- defaults：默认值字典，用于选择多个属性
- getter：自定义访问回调函数

应当注意的是，在使用时， *default* 、 *defaults* 和 *getter* 参数必须使用关键字方式传递，详情参考 [PEP 3102](https://www.python.org/dev/peps/pep-3102/)。

### 示例

选取多个属性

```python
from borax.fetch import fetch

objects = [
    {'id': 282, 'name': 'Alice', 'age': 30},
    {'id': 217, 'name': 'Bob', 'age': 56},
    {'id': 328, 'name': 'Charlie', 'age': 56},
]

names, ages = fetch(objects, 'name', 'age')
print(names)
print(ages)
```

输出

```
['Alice', 'Bob', 'Charlie']
[30, 56, 56]
```

## networkx 库

> 项目地址： https://github.com/networkx/networkx

对于复杂的关系图，可以使用 [networkx](https://github.com/networkx/networkx) 库构建节点和连线，并传递给 add 函数。如下面的例子。

```python
# coding=utf8

from __future__ import unicode_literals

import networkx as nx
from networkx.readwrite import json_graph
from pyecharts import Graph

g = nx.Graph()
categories = ['网关', '节点']
g.add_node('FF12C904', name='Gateway 1', symbolSize=40, category=0)
g.add_node('FF12CA02', name='Node 11', category=1)
g.add_node('FF12C326', name='Node 12', category=1)
g.add_node('FF45C023', name='Node 111', category=1)
g.add_node('FF230933', name='Node 1111', category=1)

g.add_edge('FF12C904', 'FF12CA02')
g.add_edge('FF12C904', 'FF12C326')
g.add_edge('FF12CA02', 'FF45C023')
g.add_edge('FF45C023', 'FF230933')

g_data = json_graph.node_link_data(g)
eg = Graph('设备最新拓扑图')
eg.add('Devices', nodes=g_data['nodes'], links=g_data['links'], categories=categories)
# eg.show_config()
eg.render()
```

结果

![networkx-demo](http://django-echarts.readthedocs.io/zh_CN/latest/_images/networkx-graph-demo.png)
