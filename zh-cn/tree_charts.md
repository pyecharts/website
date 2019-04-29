## Tree：树图

> *class pyecharts.charts.Tree*

```python
class Tree(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.Tree.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据项
    data: List[Union[opts.TreeItem, dict]],

    # 树图的布局，有 正交 和 径向 两种。这里的 正交布局 就是我们通常所说的水平 和 垂直 方向，
    # 对应的参数取值为 'orthogonal' 。而 径向布局 是指以根节点为圆心，每一层节点为环，
    # 一层层向外发散绘制而成的布局，对应的参数取值为 'radial'
    layout: str = "orthogonal",

    # 标记的图形。ECharts 提供的标记类型包括 'emptyCircle', 'circle', 'rect', 'roundRect', 
    # 'triangle', 'diamond', 'pin', 'arrow', 'none'。
    symbol: str = "emptyCircle",

    # 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Numeric = 7,

    # 树图中 正交布局 的方向，也就是说只有在 layout = 'orthogonal' 的时候，
    # 该配置项才生效。对应有 水平 方向的 从左到右，从右到左；以及垂直方向的从上到下，
    # 从下到上。取值分别为 'LR' , 'RL', 'TB', 'BT'。注意，之前的配置项值 'horizontal' 
    # 等同于 'LR'， 'vertical' 等同于 'TB'。
    orient: str = "LR",

    # tree组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Optional[str] = None,

    # tree 组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: Optional[str] = None,

    # tree 组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_bottom: Optional[str] = None,

    # tree 组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_right: Optional[str] = None,

    # 折叠节点间隔，当节点过多时可以解决节点显示过杂间隔。
    collapse_interval: Numeric = 0,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 叶子节点标签配置项，参考 `series_options.LabelOpts`
    leaves_label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### TreeItem

> *class pyecahrts.options.TreeItem*

```python
class TreeItem(
    # 树节点的名称，用来标识每一个节点。
    name: Optional[str] = None,

    # 节点的值，在 tooltip 中显示。
    value: Optional[Numeric] = None,

    # 该节点的样式，参考 `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,

    # 子节点，嵌套定义。
    children: Optional[Sequence] = None,
)
```

### Demo

> Tree-基本示例

```python
import json
import os

from pyecharts import options as opts
from pyecharts.charts import Page, Tree


def tree_base() -> Tree:
    data = [
        {
            "children": [
                {"name": "B"},
                {
                    "children": [
                        {"children": [{"name": "I"}], "name": "E"},
                        {"name": "F"},
                    ],
                    "name": "C",
                },
                {
                    "children": [
                        {"children": [{"name": "J"}, {"name": "K"}], "name": "G"},
                        {"name": "H"},
                    ],
                    "name": "D",
                },
            ],
            "name": "A",
        }
    ]
    c = (
        Tree()
        .add("", data)
        .set_global_opts(title_opts=opts.TitleOpts(title="Tree-基本示例"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55934121-365b1500-5c62-11e9-8a42-6bf302f50e8a.png)

> Tree-左右方向

```python
def tree_lr() -> Tree:
    with open(os.path.join("fixtures", "flare.json"), "r", encoding="utf-8") as f:
        j = json.load(f)
    c = (
        Tree()
        .add("", [j], collapse_interval=2)
        .set_global_opts(title_opts=opts.TitleOpts(title="Tree-左右方向"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55934142-4672f480-5c62-11e9-81b7-9bff73fec63e.png)

> Tree-右左方向

```python
def tree_rl() -> Tree:
    with open(os.path.join("fixtures", "flare.json"), "r", encoding="utf-8") as f:
        j = json.load(f)
    c = (
        Tree()
        .add("", [j], collapse_interval=2, orient="RL")
        .set_global_opts(title_opts=opts.TitleOpts(title="Tree-右左方向"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55934158-525eb680-5c62-11e9-83a2-b97ec2443675.png)

> Tree-上下方向

```python
def tree_tb() -> Tree:
    with open(os.path.join("fixtures", "flare.json"), "r", encoding="utf-8") as f:
        j = json.load(f)
    c = (
        Tree()
        .add(
            "",
            [j],
            collapse_interval=2,
            orient="TB",
            label_opts=opts.LabelOpts(
                position="top",
                horizontal_align="right",
                vertical_align="middle",
                rotate=-90,
            ),
        )
        .set_global_opts(title_opts=opts.TitleOpts(title="Tree-上下方向"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55934179-60143c00-5c62-11e9-9e6e-d5394b6d0a8f.png)

> Tree-下上方向

```python
def tree_bt() -> Tree:
    with open(os.path.join("fixtures", "flare.json"), "r", encoding="utf-8") as f:
        j = json.load(f)
    c = (
        Tree()
        .add(
            "",
            [j],
            collapse_interval=2,
            orient="BT",
            label_opts=opts.LabelOpts(
                position="top",
                horizontal_align="right",
                vertical_align="middle",
                rotate=-90,
            ),
        )
        .set_global_opts(title_opts=opts.TitleOpts(title="Tree-下上方向"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55934194-6f938500-5c62-11e9-93bb-f70f6e8608d5.png)

> Tree-Layout

```python
def tree_layout() -> Tree:
    with open(os.path.join("fixtures", "flare.json"), "r", encoding="utf-8") as f:
        j = json.load(f)
    c = (
        Tree()
        .add("", [j], collapse_interval=2, layout="radial")
        .set_global_opts(title_opts=opts.TitleOpts(title="Tree-Layout"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55934220-7e7a3780-5c62-11e9-9fe7-d072d17056ee.png)


## TreeMap：矩形树图

> *class pyecharts.charts.TreeMap*

```python
class TreeMap(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.TreeMap.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据项
    data: List[Union[opts.TreeItem, dict]],

    # 是否选中图例。
    is_selected: bool = True,

    # leaf_depth 表示『展示几层』，层次更深的节点则被隐藏起来。
    # 设置了 leafDepth 后，下钻（drill down）功能开启。drill down 功能即点击后才展示子层级。
    # 例如，leafDepth 设置为 1，表示展示一层节点。
    leaf_depth: Optional[Numeric] = None,

    # treemap 组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: Optional[str] = None,

    # treemap 组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_right: Optional[str] = None,

    # treemap 组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Optional[str] = None,

    # treemap 组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_bottom: Optional[str] = None,

    # 当节点可以下钻时的提示符。只能是字符。
    drilldown_icon: str = "▶",

    # 当前层级的最小 value 值。如果不设置则自动统计。
    visual_min: Optional[Numeric] = None,

    # 当前层级的最大 value 值。如果不设置则自动统计。
    visual_max: Optional[Numeric] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### Demo

> TreeMap-基本示例

```python
import json
import os

from pyecharts import options as opts
from pyecharts.charts import Page, TreeMap


def treemap_base() -> TreeMap:
    data = [
        {"value": 40, "name": "我是A"},
        {
            "value": 180,
            "name": "我是B",
            "children": [
                {
                    "value": 76,
                    "name": "我是B.children",
                    "children": [
                        {"value": 12, "name": "我是B.children.a"},
                        {"value": 28, "name": "我是B.children.b"},
                        {"value": 20, "name": "我是B.children.c"},
                        {"value": 16, "name": "我是B.children.d"},
                    ],
                }
            ],
        },
    ]

    c = (
        TreeMap()
        .add("演示数据", data)
        .set_global_opts(title_opts=opts.TitleOpts(title="TreeMap-基本示例"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55934288-ae293f80-5c62-11e9-8010-fd8a313d60ca.png)

> TreeMap-官方示例

```python
def treemap_official():
    with open(os.path.join("fixtures", "treemap.json"), "r", encoding="utf-8") as f:
        data = json.load(f)
    c = (
        TreeMap()
        .add("演示数据", data)
        .set_global_opts(title_opts=opts.TitleOpts(title="TreeMap-官方示例"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55934306-c13c0f80-5c62-11e9-98f1-c9c0296736be.png)
