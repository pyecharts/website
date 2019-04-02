## Calendar：日历图

> *class pyecharts.charts.Calendar*

```python
class Calendar(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyeachrts.charts.Calendar.add*

```python
def add(
    # 系列名称，用于tooltip的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    yaxis_data: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 日历坐标系组件配置项，参考 `CalendarOpts`
    calendar_opts: Union[opts.CalendarOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### CalendarOpts
> 日历坐标系组件配置项 *class pyecahrts.options.CalendarOpts*

```python
class CalendarOpts(
    # calendar组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: Optional[str] = None,

    # calendar组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Optional[str] = None,

    # calendar组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    # 默认自适应。
    pos_right: Optional[str] = None,

    # calendar组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    # 默认自适应。
    pos_bottom: Optional[str] = None,

    # 日历坐标的布局朝向。可选：
    # 'horizontal', 'vertical'
    orient: Optional[str] = None,
    # 必填，日历坐标的范围 支持多种格式，使用示例：
    # 某一年 range: 2017
    # 某个月 range: '2017-02'
    # 某个区间 range: ['2017-01-02', '2017-02-23']
    # 注意 此写法会识别为['2017-01-01', '2017-02-01']
    # range: ['2017-01', '2017-02']
    range_: Union[str, Sequence, int] = None,

    # 星期轴的样式，参考 `series_options.LabelOpts`
    daylabel_opts: Union[LabelOpts, dict, None] = None,

    # 月份轴的样式，参考 `series_options.LabelOpts`
    monthlabel_opts: Union[LabelOpts, dict, None] = None,

    # 年份的样式，参考 `series_options.LabelOpts`
    yearlabel_opts: Union[LabelOpts, dict, None] = None,
)
```

## Funnel：漏斗图

> *class pyecharts.charts.Funnel*

```python
class Funnel(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.Funnel.add*

```python
def add(
    series_name: str,
    data_pair: Sequence,
    is_selected: bool = True,
    color: Optional[str] = None,
    sort_: str = "descending",
    gap: Numeric = 0,
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

## Gauge：仪表盘

> *class pyecharts.charts.Gauge*

```python
class Gauge(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.Gauge.add*

```python
def add(
    series_name: str,
    data_pair: Sequence,
    is_selected: bool = True,
    min_: Numeric = 0,
    max_: Numeric = 100,
    start_angle: Numeric = 225,
    end_angle: Numeric = -45,
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

## Geo：地理坐标系

> *class pyecharts.charts.Geo*
```python
```

#### EffectOpts

> *class pyecharts.options.EffectOpts*

```python
class EffectOpts(
    is_show: bool = True,
    brush_type: str = "stroke",
    scale: Numeric = 2.5,
    period: Numeric = 4,
    color: Optional[str] = None,
    symbol: Optional[str] = None,
    symbol_size: Optional[Numeric] = None,
)
```

## Graph：关系图

> *class pyecharts.charts.Graph*
```python
```

#### GraphNode
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
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 该类目节点标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Union[Numeric, Sequence, None] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,
)
```

#### GraphLink
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

#### GraphCategory
> *class pyecharts.options.GraphCategory*

```python
class GraphCategory(
    # 类目名称，用于和 legend 对应以及格式化 tooltip 的内容。
    name: Optional[str] = None,

    # 该类目节点标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 该类目节点标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Union[Numeric, Sequence, None] = None,

    # # 标签样式，参考 `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,
)
```

## Liquid：水球图

> *class pyecharts.charts.Liquid*
```python
```

## Map：地图

> *class pyecharts.charts.Map*
```python
```

## Parallel：平行坐标系

> *class pyecharts.charts.Parallel*
```python
```

#### ParallelOpts
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

#### ParallelAxisOpts
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

## Pie：饼图

> *class pyecharts.charts.Pie*
```python
```

## Polar：极坐标系

> *class pyecharts.charts.Polar*
```python
```

## Radar：雷达图

> *class pyecharts.charts.Radar*
```python
```

#### RadarIndicatorOpts
> *class pyecahrts.options.RadarIndicatorOpts*

```python
class RadarIndicatorOpts(
    name: Optional[str] = None,
    min_: Optional[Numeric] = None,
    max_: Optional[Numeric] = None,
    color: Optional[str] = None,
)
```

## Sankey：桑基图

> *class pyecharts.charts.Sankey*

```python
```

## ThemeRiver：主题河流图

> *class pyecharts.charts.ThemeRiver*
```python
```

## Tree：树图

> *class pyecharts.charts.Tree*
```python
```

#### TreeItem
> *class pyecahrts.options.TreeItem*

```python
class TreeItem(
    name: Optional[str] = None,
    value: Optional[Numeric] = None,
    label_opts: Optional[LabelOpts] = None,
    children: Optional[Sequence] = None,
)
```


## TreeMap：矩形树图

> *class pyecharts.charts.TreeMap*
```python
```

## WordCloud：词云图

> *class pyecharts.charts.WordCloud*
```python
```
