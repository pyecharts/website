## Bar
> 柱状图/条形图 *class pyecharts.charts.Bar*

### API
```python
def __init__(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)

def add_yaxis(
    # 系列名称，用于tooltip的显示，legend 的图例筛选，在 setOption 更新数据和配置项时用于指定对应的系列。
    series_name: str,

    yaxis_data: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    color: Optional[str] = None,

    # 数据堆叠，同个类目轴上系列配置相同的stack值可以堆叠放置。
    stack: Optional[str] = None,

    # 同一系列的柱间距离，默认为类目间距的20%，可设固定值
    category_gap: Union[Numeric, str] = "20%",

    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```


## Boxplot


## Parallel

### ParallelOpts
> *class pyecharts.options.ParallelOpts*

```python
class ParallelOpts(
    pos_left: str = "5%",
    pos_right: str = "13%",
    pos_bottom: str = "10%",
    pos_top: str = "20%",
    layout: Optional[str] = None,
)
```

### ParallelAxisOpts
> *class pyecharts.options.ParallelAxisOpts*

```python
class ParallelAxisOpts(
    dim: Numeric,
    name: str,
    data: Sequence = None,
    type_: Optional[str] = None,
    min_: Union[str, Numeric, None] = None,
    max_: Union[str, Numeric, None] = None,
    is_scale: bool = False,
)
```

## Radar

### RadarIndicatorOpts
> *class pyecahrts.options.RadarIndicatorOpts*

```python
class RadarIndicatorOpts(
    name: Optional[str] = None,
    min_: Optional[Numeric] = None,
    max_: Optional[Numeric] = None,
    color: Optional[str] = None,
)
```

## Graph

### GraphNode
> *class pyecahrts.options.GraphNode*

```python
class GraphNode(
    # 数据项名称。
    name: Optional[str] = None,

    # 节点的初始 x 值。在不指定的时候需要指明layout属性选择布局方式。
    x: Optional[Numeric] = None,

    # 节点的初始 y 值。在不指定的时候需要指明layout属性选择布局方式。
    y: Optional[Numeric] = None,

    # 节点在力引导布局中是否固定。
    is_fixed: bool = False,

    # 数据项值。
    value: Union[str, Sequence, None] = None,

    # 数据项所在类目的 index。
    category: Optional[int] = None,

    # 该类目节点标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 该类目节点标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Union[Numeric, Sequence, None] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,
)
```

### GraphLink
> *class pyecahrts.options.GraphLink*

```python
class GraphLink(
    # 边的源节点名称的字符串，也支持使用数字表示源节点的索引。
    source: Union[str, int, None] = None,

    # 边的目标节点名称的字符串，也支持使用数字表示源节点的索引。
    target: Union[str, int, None] = None,

    # 边的数值，可以在力引导布局中用于映射到边的长度。
    value: Optional[Numeric] = None,

    # 边两端的标记类型，可以是一个数组分别指定两端，也可以是单个统一指定。
    symbol: Union[str, Sequence, None] = None,

    # 边两端的标记大小，可以是一个数组分别指定两端，也可以是单个统一指定。
    symbol_size: Union[Numeric, Sequence, None] = None,

    # 关系边的线条样式，参考 `series_options.LineStyleOpts`
    linestyle_opts: Optional[LineStyleOpts] = None,

    # 标签样式，参考 `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,
)
```

### GraphCategory
> *class pyecharts.options.GraphCategory*

```python
class GraphCategory(
    # 类目名称，用于和 legend 对应以及格式化 tooltip 的内容。
    name: Optional[str] = None,

    # 该类目节点标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 该类目节点标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Union[Numeric, Sequence, None] = None,

    # # 标签样式，参考 `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,
)
```


## Tree

### TreeItem
> *class pyecahrts.options.TreeItem*

```python
class TreeItem(
    name: Optional[str] = None,
    value: Optional[Numeric] = None,
    label_opts: Optional[LabelOpts] = None,
    children: Optional[Sequence] = None,
)
```
