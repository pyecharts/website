## Calendar：日历图

> *class pyecharts.charts.Calendar*

```python
class Calendar(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyeachrts.charts.Calendar.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据，格式为 [(date1, value1), (date2, value2), ...]
    yaxis_data: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 日历坐标系组件配置项，参考 `CalendarOpts`
    calendar_opts: Union[opts.CalendarOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### CalendarOpts：日历坐标系组件配置项

> *class pyecharts.options.CalendarOpts*

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

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Calendar/README)


## Funnel：漏斗图

> *class pyecharts.charts.Funnel*

```python
class Funnel(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Funnel.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据项，格式为 [(key1, value1), (key2, value2)]
    data_pair: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 数据排序， 可以取 'ascending'，'descending'，'none'（表示按 data 顺序）
    sort_: str = "descending",

    # 数据图形间距
    gap: Numeric = 0,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Funnel/README)


## Gauge：仪表盘

> *class pyecharts.charts.Gauge*

```python
class Gauge(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Gauge.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据项，格式为 [(key1, value1), (key2, value2)]
    data_pair: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 最小的数据值
    min_: Numeric = 0,

    # 最大的数据值
    max_: Numeric = 100,

    # 仪表盘平均分割段数
    split_number: Numeric = 10,

    # 仪表盘半径，可以是相对于容器高宽中较小的一项的一半的百分比，也可以是绝对的数值。
    radius: types.Union[types.Numeric, str] = "75%",

    # 仪表盘起始角度。圆心 正右手侧为0度，正上方为 90 度，正左手侧为 180 度。
    start_angle: Numeric = 225,

    # 仪表盘结束角度。
    end_angle: Numeric = -45,

    # 仪表盘刻度是否是顺时针增长。
    is_clock_wise: bool = True,
    
    # 轮盘内标题文本项标签配置项，参考 `chart_options.GaugeTitleOpts`
    title_label_opts: types.GaugeTitle = opts.GaugeTitleOpts(),
    
    # 轮盘内数据项标签配置项，参考 `chart_options.GaugeDetailOpts`
    detail_label_opts: types.GaugeDetail = opts.GaugeDetailOpts(formatter="{value}%"),

    # 仪表盘指针配置项目，参考 `chart_options.GaugePointerOpts`
    pointer: types.GaugePointer = opts.GaugePointerOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### GaugeTitleOpts：仪表盘数据标题配置项

```python
class GaugeTitleOpts(
)
```

### GaugeDetailOpts：仪表盘数据内容配置项

```python
class GaugeDetailOpts(
    # 是否显示详情。
    is_show: bool = True,

    # 文字块背景色。
    # 可以是直接的颜色值，例如：'#123234', 'red', 'rgba(0,23,11,0.3)'。
    background_color: str = "transparent",

    # 文字块边框宽度。
    border_width: Numeric = 0,

    # 文字块边框颜色。
    border_color: str = "transparent",

    # 相对于仪表盘中心的偏移位置，数组第一项是水平方向的偏移，第二项是垂直方向的偏移。
    # 可以是绝对的数值，也可以是相对于仪表盘半径的百分比。
    offset_center: Sequence = [0, "-40%"],

    # 格式化函数或者字符串
    formatter: Optional[JSFunc] = None,

    # 文字的颜色。
    color: str = "auto",

    # 文字字体的风格。可选：'normal'，'italic'，'oblique'
    font_style: str = "normal",

    # 文字字体的粗细。可选：'normal'，'bold'，'bolder'， 'lighter'， 100 | 200 | 300 | 400...
    font_weight: str = "normal",
    
    # 文字的字体系列。还可以是 'serif' , 'monospace', 'Arial', 'Courier New', 'Microsoft YaHei', ...
    font_family: str = "sans-serif",

    # 文字的字体大小
    font_size: Numeric = 15,

    # 文字块的圆角。
    border_radius: Numeric = 0,

    # 文字块的内边距。例如：
    # padding: [3, 4, 5, 6]：表示 [上, 右, 下, 左] 的边距。
    # padding: 4：表示 padding: [4, 4, 4, 4]。
    # padding: [3, 4]：表示 padding: [3, 4, 3, 4]。
    # 注意，文字块的 width 和 height 指定的是内容高宽，不包含 padding。
    padding: Numeric = 0,

    # 文字块的背景阴影颜色。
    shadow_color: Optional[str] = "transparent",

    # 文字块的背景阴影长度。
    shadow_blur: Optional[Numeric] = 0,

    # 文字块的背景阴影 X 偏移。
    shadow_offset_x: Numeric = 0,

    # 文字块的背景阴影 Y 偏移。
    shadow_offset_y: Numeric = 0,
)
```

### GaugePointerOpts：仪表盘指针配置项

```python
class GaugePointerOpts(
    # 是否显示指针。
    is_show: bool = True,
    
    # 指针长度，可以是绝对数值，也可以是相对于半径的半分比。
    length: Union[str, Numeric] = "80%",

    # 指针宽度。
    width: Numeric = 8,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Gauge/README)


## Graph：关系图

> *class pyecharts.charts.Graph*

```python
class Graph(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *class pyecharts.charts.Graph.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 关系图节点数据项列表，参考 `opts.GraphNode`
    nodes: Sequence[Union[opts.GraphNode, dict]],

    # 关系图节点间关系数据项列表，参考 `opts.GraphLink`
    links: Sequence[Union[opts.GraphLink, dict]],

    # 关系图节点分类的类目列表，参考 `opts.GraphCategory`
    categories: Union[Sequence[Union[opts.GraphCategory, dict]], None] = None,

    # 是否选中图例。
    is_selected: bool = True,

    # 是否在鼠标移到节点上的时候突出显示节点以及节点的边和邻接节点。
    is_focusnode: bool = True,

    # 是否开启鼠标缩放和平移漫游。
    is_roam: bool = True,
    
    # 节点是否可拖拽，只在使用力引导布局的时候有用。
    is_draggable: bool = False,

    # 是否旋转标签，默认不旋转。
    is_rotate_label: bool = False,

    # 图的布局。可选：
    # 'none' 不采用任何布局，使用节点中提供的 x， y 作为节点的位置。
    # 'circular' 采用环形布局。
    # 'force' 采用力引导布局。
    layout: str = "force",

    # 关系图节点标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,
    
    # 关系图节点标记的大小
    # 可以设置成诸如 10 这样单一的数字
    # 也可以用数组分开表示宽和高，例如 [20, 10] 表示标记宽为20，高为10。
    symbol_size: types.Numeric = 10,

    # 边的两个节点之间的距离，这个距离也会受 repulsion。
    # 支持设置成数组表达边长的范围，此时不同大小的值会线性映射到不同的长度。值越小则长度越长。
    edge_length: Numeric = 50,

    # 节点受到的向中心的引力因子。该值越大节点越往中心点靠拢。
    gravity: Numeric = 0.2,

    # 节点之间的斥力因子。
    # 支持设置成数组表达斥力的范围，此时不同大小的值会线性映射到不同的斥力。值越大则斥力越大
    repulsion: Numeric = 50,

     # Graph 图节点边的 Label 配置（即在边上显示数据或标注的配置）
    edge_label: types.Label = None,

    # 边两端的标记类型，可以是一个数组分别指定两端，也可以是单个统一指定。
    # 默认不显示标记，常见的可以设置为箭头，如下：edgeSymbol: ['circle', 'arrow']
    edge_symbol: Optional[str] = None,
    
    # 边两端的标记大小，可以是一个数组分别指定两端，也可以是单个统一指定。
    edge_symbol_size: Numeric = 10,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 关系边的公用线条样式。
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### GraphNode：关系图的节点数据项

> *class pyecharts.options.GraphNode*

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

### GraphLink：节点间的关系数据

> *class pyecharts.options.GraphLink*

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

### GraphCategory：节点分类的类目

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

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Graph/README)


## Liquid：水球图

> *class pyecharts.charts.Liquid*

```python
class Liquid(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Liquid.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据，格式为 [value1, value2, ....]
    data: Sequence,

    # 水球外形，有' circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow' 可选。
    # 默认 'circle'。也可以为自定义的 SVG 路径。
    shape: str = "circle",

    # 波浪颜色。
    color: Optional[Sequence[str]] = None,

    # 背景颜色
    background_color: types.Union[str, dict, None] = None,

    # 是否显示波浪动画。
    is_animation: bool = True,

    # 是否显示边框。
    is_outline_show: bool = True,

    # 外沿边框宽度
    outline_border_distance: types.Numeric = 8,

    # 外沿样式
    outline_itemstyle_opts: types.ItemStyle = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(font_size=50, position="inside"),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Liquid/README)


## Parallel：平行坐标系

> *class pyecharts.charts.Parallel*

```python
class Parallel(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Parallel.add_schema*

```python
def add_schema(
    schema: Sequence[Union[opts.ParallelAxisOpts, dict]],
    parallel_opts: Union[opts.ParallelOpts, dict, None] = None,
)
```

> *func pyecharts.charts.Parallel.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    data: types.Sequence[types.Union[opts.ParallelItem, dict]],

    # 是否选中图例。
    is_selected: bool = True,

    # 是否平滑曲线
    is_smooth: bool = False,

    # 线条样式，参考 `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### ParallelOpts：平行坐标系配置项

> *class pyecharts.options.ParallelOpts*

```python
class ParallelOpts(
    # parallel 组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: str = "5%",

    # parallel 组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_right: str = "13%",

    # parallel 组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_bottom: str = "10%",

    # parallel 组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: str = "20%",

    # 布局方式，可选值为：
    # 'horizontal'：水平排布各个坐标轴。
    # 'vertical'：竖直排布各个坐标轴。
    layout: Optional[str] = None,
)
```

### ParallelAxisOpts：平行坐标系轴配置项

> *class pyecharts.options.ParallelAxisOpts*

```python
class ParallelAxisOpts(
    # 坐标轴的维度序号。
    dim: Numeric,

    # 坐标轴名称。
    name: str,

    # 坐标轴数据项
    data: Sequence = None,

    # 坐标轴类型。可选：
    # 'value': 数值轴，适用于连续数据。
    # 'category': 类目轴，适用于离散的类目数据，为该类型时必须通过 data 设置类目数据。
    # 'time': 时间轴，适用于连续的时序数据，与数值轴相比时间轴带有时间的格式化，在刻度计算上也有所不同
    # 例如会根据跨度的范围来决定使用月，星期，日还是小时范围的刻度。
    # 'log' 对数轴。适用于对数数据。
    type_: Optional[str] = None,

    # 坐标轴刻度最小值。
    # 可以设置成特殊值 'dataMin'，此时取数据在该轴上的最小值作为最小刻度。
    # 不设置时会自动计算最小值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'
    # 也可以设置为负数，如 -3）。
    min_: Union[str, Numeric, None] = None,

    # 坐标轴刻度最大值。
    # 可以设置成特殊值 'dataMax'，此时取数据在该轴上的最大值作为最大刻度。
    # 不设置时会自动计算最大值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'
    # 也可以设置为负数，如 -3）。
    max_: Union[str, Numeric, None] = None,

    # 只在数值轴中（type: 'value'）有效。
    # 是否是脱离 0 值比例。设置成 true 后坐标刻度不会强制包含零刻度。在双数值轴的散点图中比较有用。
    # 在设置 min 和 max 之后该配置项无效。
    is_scale: bool = False,
)
```

### ParallelItem：平行坐标系数据项

```python
class ParallelItem(
    # 数据项名称。
    name: Optional[str] = None,

    # 数据项值。
    value: Optional[Sequence] = None,

    # 线条样式。
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,

    # 线的颜色。
    color: Union[str, dict] = "#000",

    # 线宽。
    width: Numeric = 2,

    # 线的类型。可选'solid'，'dashed'，'dotted'
    type_: str = "solid",

    # 图形透明度。支持从 0 到 1 的数字，为 0 时不绘制该图形。
    opacity: Numeric = 0.45,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Parallel/README)


## Pie：饼图

> *class pyecharts.charts.Pie*

```python
class Pie(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Pie.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据项，格式为 [(key1, value1), (key2, value2)]
    data_pair: types.Sequence[types.Union[types.Sequence, opts.PieItem, dict]],

    # 系列 label 颜色
    color: Optional[str] = None,

    # 饼图的半径，数组的第一项是内半径，第二项是外半径
    # 默认设置成百分比，相对于容器高宽中较小的一项的一半
    radius: Optional[Sequence] = None,

    # 饼图的中心（圆心）坐标，数组的第一项是横坐标，第二项是纵坐标
    # 默认设置成百分比，设置成百分比时第一项是相对于容器宽度，第二项是相对于容器高度
    center: Optional[Sequence] = None,

    # 是否展示成南丁格尔图，通过半径区分数据大小，有'radius'和'area'两种模式。
    # radius：扇区圆心角展现数据的百分比，半径展现数据的大小
    # area：所有扇区圆心角相同，仅通过半径展现数据大小
    rosetype: Optional[str] = None,
    
    # 饼图的扇区是否是顺时针排布。
    is_clockwise: bool = True,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # 可以定义 data 的哪个维度被编码成什么。
    encode: types.Union[types.JSFunc, dict, None] = None,
)
```

### PieItem：饼图数据项

```python
class PieItem(
    # 数据项名称。
    name: Optional[str] = None,

    # 数据值。
    value: Optional[Numeric] = None,

    # 该数据项是否被选中。
    is_selected: bool = False,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Pie/README)


## Polar：极坐标系

> *class pyecharts.charts.Polar*

```python
class Polar(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Polar.add_schema*

```python
 def add_schema(
    radiusaxis_opts: Union[opts.RadiusAxisOpts, dict] = opts.RadiusAxisOpts(),
    angleaxis_opts: Union[opts.AngleAxisOpts, dict] = opts.AngleAxisOpts(),
)
```

> *func pyecharts.charts.Polar.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据项
    data: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 图表类型，支持
    # ChartType.SCATTER, ChartType.LINE, ChartType.BAR，ChartType.EFFECT_SCATTER
    type_: str = "line",

    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Numeric = 4,

    # 数据堆叠，同个类目轴上系列配置相同的　stack　值可以堆叠放置。
    stack: Optional[str] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 区域填充样式配置项，参考 `series_options.AreaStyleOpts`
    areastyle_opts: Union[opts.AreaStyleOpts, dict] = opts.AreaStyleOpts(),

    # 坐标轴刻度配置项，参考 `global_options.AxisTickOpts`
    axistick_opts: Union[AxisTickOpts, dict, None] = None,

    # 涟漪特效配置项，参考 `series_options.EffectOpts`
    effect_opts: Union[opts.EffectOpts, dict] = opts.EffectOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### RadiusAxisItem：极坐标系径向轴数据项

> *class pyecharts.options.RadiusAxisItem*

```python
class RadiusAxisItem(
    value: Optional[str] = None,
    textstyle_opts: Optional[TextStyleOpts] = None,
)
```

### RadiusAxisOpts：极坐标系径向轴配置项

> *class pyecharts.options.RadiusAxisOpts*

```python
class RadiusAxisOpts(
    # 径向轴所在的极坐标系的索引，默认使用第一个极坐标系。
    polar_index: Optional[int] = None,

    # 数据项，参考 `global_options.RadiusAxisItem`
    data: Optional[Sequence[Union[RadiusAxisItem, dict, str]]] = None,

    # 坐标轴两边留白策略，类目轴和非类目轴的设置和表现不一样。
    # 类目轴中 boundaryGap 可以配置为 true 和 false。默认为 true，这时候刻度只是作为分隔线，
    # 标签和数据点都会在两个刻度之间的带(band)中间。
    # 非类目轴，包括时间，数值，对数轴，boundaryGap是一个两个值的数组，分别表示数据最小值和最大值的延伸范围
    # 可以直接设置数值或者相对的百分比，在设置 min 和 max 后无效。 示例：boundaryGap: ['20%', '20%']
    boundary_gap: Union[bool, Sequence] = None,

    # 坐标轴类型。可选：
    # 'value': 数值轴，适用于连续数据。
    # 'category': 类目轴，适用于离散的类目数据，为该类型时必须通过 data 设置类目数据。
    # 'time': 时间轴，适用于连续的时序数据，与数值轴相比时间轴带有时间的格式化，在刻度计算上也有所不同
    # 例如会根据跨度的范围来决定使用月，星期，日还是小时范围的刻度。
    # 'log' 对数轴。适用于对数数据。
    type_: Optional[str] = None,

    # 坐标轴名称。
    name: Optional[str] = None,

    # 坐标轴名称显示位置。可选：
    # 'start', 'middle' 或者 'center','end
    name_location: Optional[str] = None,

    # 坐标轴刻度最小值。
    # 可以设置成特殊值 'dataMin'，此时取数据在该轴上的最小值作为最小刻度。
    # 不设置时会自动计算最小值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'
    # 也可以设置为负数，如 -3）。
    min_: Union[str, Numeric, None] = None,

    # 坐标轴刻度最大值。
    # 可以设置成特殊值 'dataMax'，此时取数据在该轴上的最大值作为最大刻度。
    # 不设置时会自动计算最大值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'
    # 也可以设置为负数，如 -3）。
    max_: Union[str, Numeric, None] = None,

    # 只在数值轴中（type: 'value'）有效。
    # 是否是脱离 0 值比例。设置成 true 后坐标刻度不会强制包含零刻度。在双数值轴的散点图中比较有用。
    # 在设置 min 和 max 之后该配置项无效。
    is_scale: bool = False,
    
    # 强制设置坐标轴分割间隔。
    interval: Optional[Numeric] = None,

    # 分割线配置项，参考 `series_options.SplitLineOpts`
    splitline_opts: Union[SplitLineOpts, dict, None] = None,

    # 坐标轴在 grid 区域中的分隔区域，默认不显示。参考 `series_options.SplitAreaOpts`
    splitarea_opts: Union[SplitAreaOpts, dict, None] = None,

    # 坐标轴线风格配置项，参考 `series_options.AxisLineOpts`
    axisline_opts: Union[AxisLineOpts, dict, None] = None,

    # 坐标轴线标签配置项，参考 `series_options.LabelOpts`
    axislabel_opts: Union[LabelOpts, dict, None] = None,

    # 半径轴组件的所有图形的 z 值。控制图形的前后顺序。z 值 小的图形会被 z 值大的图形覆盖
    z: Optional[int] = None,
)
```

### AngleAxisItem：极坐标系角度轴数据项

> *class pyecharts.options.AngleAxisItem*

```python
class AngleAxisItem(
    value: Optional[str] = None,
    textstyle_opts: Optional[TextStyleOpts] = None,
)
```

### AngleAxisOpts：极坐标系角度轴配置项

> *class pyecharts.options.AngleAxisOpts*

```python
class AngleAxisOpts(
    # 径向轴所在的极坐标系的索引，默认使用第一个极坐标系。
    polar_index: Optional[int] = None,
    data: Optional[Sequence[Union[AngleAxisItem, dict, str]]] = None,
    start_angle: Optional[Numeric] = None,
    is_clockwise: bool = False,

    # 坐标轴两边留白策略，类目轴和非类目轴的设置和表现不一样。
    # 类目轴中 boundaryGap 可以配置为 true 和 false。默认为 true，这时候刻度只是作为分隔线，
    # 标签和数据点都会在两个刻度之间的带(band)中间。
    # 非类目轴，包括时间，数值，对数轴，boundaryGap是一个两个值的数组，分别表示数据最小值和最大值的延伸范围
    # 可以直接设置数值或者相对的百分比，在设置 min 和 max 后无效。 示例：boundaryGap: ['20%', '20%']
    boundary_gap: Union[bool, Sequence] = None,

    # 坐标轴类型。可选：
    # 'value': 数值轴，适用于连续数据。
    # 'category': 类目轴，适用于离散的类目数据，为该类型时必须通过 data 设置类目数据。
    # 'time': 时间轴，适用于连续的时序数据，与数值轴相比时间轴带有时间的格式化，在刻度计算上也有所不同
    # 例如会根据跨度的范围来决定使用月，星期，日还是小时范围的刻度。
    # 'log' 对数轴。适用于对数数据。
    type_: Optional[str] = None,

    # 坐标轴刻度最小值。
    # 可以设置成特殊值 'dataMin'，此时取数据在该轴上的最小值作为最小刻度。
    # 不设置时会自动计算最小值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'
    # 也可以设置为负数，如 -3）。
    min_: Union[str, Numeric, None] = None,

    # 坐标轴刻度最大值。
    # 可以设置成特殊值 'dataMax'，此时取数据在该轴上的最大值作为最大刻度。
    # 不设置时会自动计算最大值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'
    # 也可以设置为负数，如 -3）。
    max_: Union[str, Numeric, None] = None,

    # 只在数值轴中（type: 'value'）有效。
    # 是否是脱离 0 值比例。设置成 true 后坐标刻度不会强制包含零刻度。在双数值轴的散点图中比较有用。
    # 在设置 min 和 max 之后该配置项无效。
    is_scale: bool = False,

    # 坐标轴的分割段数，需要注意的是这个分割段数只是个预估值，最后实际显示的段数会在这个基础上根据分割后坐标轴刻度显示的易读程度作调整。
    # 在类目轴中无效。
    split_number: Numeric = 5,

    # 强制设置坐标轴分割间隔。
    interval: Optional[Numeric] = None,

    # 分割线风格配置项，参考 `series_options.SplitLineOpts`
    splitline_opts: Union[SplitLineOpts, dict, None] = None,

    # 坐标轴线风格配置项，参考 `series_options.AxisLineOpts`
    axisline_opts: Union[AxisLineOpts, dict, None] = None,

    # 坐标轴标签风格配置项，参考 `series_options.LabelOpts`
    axislabel_opts: Union[LabelOpts, dict, None] = None,

    # 半径轴组件的所有图形的 z 值。控制图形的前后顺序。z 值 小的图形会被 z 值大的图形覆盖
    z: Optional[int] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Polar/README)


## Radar：雷达图

> *class pyecharts.charts.Radar*

```python
class Radar(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Radar.add_schema*

```python
def add_schema(
    # 雷达指示器配置项列表，参考 `RadarIndicatorItem`
    schema: Sequence[Union[opts.RadarIndicatorItem, dict]],

    # 雷达图绘制类型，可选 'polygon' 和 'circle'
    shape: Optional[str] = None,

    # 雷达的中心（圆心）坐标，数组的第一项是横坐标，第二项是纵坐标。
    # 支持设置成百分比，设置成百分比时第一项是相对于容器宽度，第二项是相对于容器高度。
    center: Optional[types.Sequence] = None,

    # 文字样式配置项，参考 `series_options.TextStyleOpts`
    textstyle_opts: Union[opts.TextStyleOpts, dict] = opts.TextStyleOpts(),

    # 分割线配置项，参考 `series_options.SplitLineOpts`
    splitline_opt: Union[opts.SplitLineOpts, dict] = opts.SplitLineOpts(is_show=True),

    # 分隔区域配置项，参考 `series_options.SplitAreaOpts`
    splitarea_opt: Union[opts.SplitAreaOpts, dict] = opts.SplitAreaOpts(),

    # 坐标轴轴线配置项，参考 `global_options.AxisLineOpts`
    axisline_opt: Union[opts.AxisLineOpts, dict] = opts.AxisLineOpts(),

    # 极坐标系的径向轴。参考 `basic_charts.RadiusAxisOpts`
    radiusaxis_opts: types.RadiusAxis = None,
    
    # 极坐标系的角度轴。参考 `basic_charts.AngleAxisOpts`
    angleaxis_opts: types.AngleAxis = None,

    # 极坐标系配置，参考 `global_options.PolorOpts`
    polar_opts: types.Polar = None,
)
```

> *func pyecharts.charts.Radar.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据项
    data: types.Sequence[types.Union[opts.RadarItem, dict]],

    # 是否选中图例
    is_selected: bool = True,

    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: opts.LabelOpts = opts.LabelOpts(),

    # 线样式配置项，参考 `series_options.LineStyleOpts`
    linestyle_opts: opts.LineStyleOpts = opts.LineStyleOpts(),

    # 区域填充样式配置项，参考 `series_options.AreaStyleOpts`
    areastyle_opts: opts.AreaStyleOpts = opts.AreaStyleOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### RadarIndicatorItem

> *class pyecharts.options.RadarIndicatorItem*

```python
class RadarIndicatorItem(
    # 指示器名称。
    name: Optional[str] = None,

    # 指示器的最大值，可选，建议设置
    min_: Optional[Numeric] = None,

    # 指示器的最小值，可选，默认为 0。
    max_: Optional[Numeric] = None,

    # 标签特定的颜色。
    color: Optional[str] = None,
)
```

### RadarItem：雷达图数据项

```python
class RadarItem(
    # 数据项名称
    name: Optional[str] = None,

    # 单个数据项的数值。
    value: Optional[Numeric] = None,

    # 单个数据标记的图形。
    symbol: Optional[str] = None,

    # 单个数据标记的大小
    symbol_size: Union[Sequence[Numeric], Numeric] = None,

    # 单个数据标记的旋转角度（而非弧度）。
    symbol_rotate: Optional[Numeric] = None,

    # 如果 symbol 是 path:// 的形式，是否在缩放时保持该图形的长宽比。
    symbol_keep_aspect: bool = False,

    # 单个数据标记相对于原本位置的偏移。
    symbol_offset: Optional[Sequence] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,

    # 线样式配置项，参考 `series_options.LineStyleOpts`
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,

    # 区域填充样式配置项，参考 `series_options.AreaStyleOpts`
    areastyle_opts: Union[AreaStyleOpts, dict, None] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Radar/README)


## Sankey：桑基图

> *class pyecharts.charts.Sankey*

```python
class Sankey(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *class pyechart.options.SankeyLevelsOpts*

```python
class SankeyLevelsOpts(
    # 指定设置的是桑基图哪一层，取值从 0 开始。
    depth: Numeric = None,

    # 桑基图指定层节点的样式。参考 `global_opts.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # 桑基图指定层出边的样式。
    # 其中 lineStyle.color 支持设置为'source'或者'target'特殊值，此时出边会自动取源节点或目标节点的颜色作为自己的颜色。
    # 参考 `global_opts.LineStyleOpts`
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,
)
```

> *func pyecharts.charts.Sankey.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,
    nodes: Sequence,
    links: Sequence,

    # 是否选中图例
    is_selected: bool = True,
    
    # Sankey 组件离容器左侧的距离。
    pos_left: types.Union[str, types.Numeric] = "5%",

    # Sankey 组件离容器上侧的距离。
    pos_top: types.Union[str, types.Numeric] = "5%",

    # Sankey 组件离容器右侧的距离。
    pos_right: types.Union[str, types.Numeric] = "20%",
    
    # Sankey 组件离容器下侧的距离。
    pos_bottom: types.Union[str, types.Numeric] = "5%",

    # 桑基图中每个矩形节点的宽度。
    node_width: Numeric = 20,

    # 桑基图中每一列任意两个矩形节点之间的间隔。
    node_gap: Numeric = 8,
    
    # 桑基图中节点的对齐方式，默认是双端对齐，可以设置为左对齐或右对齐，对应的值分别是：
    # justify: 节点双端对齐。
    # left: 节点左对齐。
    # right: 节点右对齐。
    node_align: str = "justify",
    
    # 布局的迭代次数，用来不断优化图中节点的位置，以减少节点和边之间的相互遮盖。
    # 默认布局迭代次数：32。
    # 注: 布局迭代次数不要低于默认值。
    layout_iterations: types.Numeric = 32,

    # 桑基图中节点的布局方向，可以是水平的从左往右，也可以是垂直的从上往下。
    # 对应的参数值分别是 horizontal, vertical。
    orient: str = "horizontal",

    # 控制节点拖拽的交互，默认开启。开启后，用户可以将图中任意节点拖拽到任意位置。若想关闭此交互，只需将值设为 false 就行了。
    is_draggable: bool = True,
    
    # 鼠标 hover 到节点或边上，相邻接的节点和边高亮的交互，默认关闭，可手动开启。
    # false：hover 到节点或边时，只有被 hover 的节点或边高亮。
    # true：同 'allEdges'。
    # 'allEdges'：hover 到节点时，与节点邻接的所有边以及边对应的节点全部高亮。hover 到边时，边和相邻节点高亮。
    # 'outEdges'：hover 的节点、节点的出边、出边邻接的另一节点 会被高亮。hover 到边时，边和相邻节点高亮。
    # 'inEdges'：hover 的节点、节点的入边、入边邻接的另一节点 会被高亮。hover 到边时，边和相邻节点高亮。
    focus_node_adjacency: types.Union[bool, str] = False,
    
    # 桑基图每一层的设置。可以逐层设置
    levels: types.SankeyLevel = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 线条样式配置项，参考 `series_options.LineStyleOpts`
    linestyle_opt: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Sankey/README)


## Sunburst：旭日图

> *class pyecharts.charts.Sunburst*

```python
class Sunburst(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Sunburst.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,
    
    # 数据项。
    data_pair: Sequence,
    
    # 旭日图的中心（圆心）坐标，数组的第一项是横坐标，第二项是纵坐标。
    # 支持设置成百分比，设置成百分比时第一项是相对于容器宽度，第二项是相对于容器高度。
    center: Optional[Sequence] = None,
    
    # 旭日图的半径。可以为如下类型：
    # Sequence.<int|str>：数组的第一项是内半径，第二项是外半径。
    radius: Optional[Sequence] = None,
    
    # 当鼠标移动到一个扇形块时，可以高亮相关的扇形块。
    # 'descendant'：高亮该扇形块和后代元素，其他元素将被淡化；
    # 'ancestor'：高亮该扇形块和祖先元素；
    # 'self'：只高亮自身；
    # 'none'：不会淡化其他元素。
    highlight_policy: str = "descendant",
    
    # 点击节点后的行为。可取值为：false：节点点击无反应。
    # 'rootToNode'：点击节点后以该节点为根结点。
    # 'link'：如果节点数据中有 link 点击节点后会进行超链接跳转。
    node_click: str = "rootToNode",
    
    # 扇形块根据数据 value 的排序方式，如果未指定 value，则其值为子元素 value 之和。
    # 'desc'：降序排序；
    # 'asc'：升序排序；
    # 'null'：表示不排序，使用原始数据的顺序；
    # 使用 javascript 回调函数进行排列：
    sort_: Optional[JSFunc] = "desc",
    
    # 旭日图多层级配置
    # 目前配置方式可以参考: https://www.echartsjs.com/option.html#series-sunburst.levels
    levels: Optional[Sequence] = None,
    
    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),
    
    # 数据项的配置，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### SunburstItem: 旭日图的数据项

> *class pyecharts.options.SunburstItem*

```python
class SunburstItem(
    # 数据值，如果包含 children，则可以不写 value 值。
    # 这时，将使用子元素的 value 之和作为父元素的 value。
    # 如果 value 大于子元素之和，可以用来表示还有其他子元素未显示。
    value: Optional[Numeric] = None,
    
    # 显示在扇形块中的描述文字。
    name: Optional[str] = None,
    
    # 点击此节点可跳转的超链接。须 Sunburst.add.node_click 值为 'link' 时才生效
    link: Optional[str] = None,
    
    # 意义同 HTML <a> 标签中的 target，跳转方式的不同
    # blank 是在新窗口或者新的标签页中打开
    # self 则在当前页面或者当前标签页打开
    target: Optional[str] = "blank",
    
    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,
    
    # 数据项配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
    
    # 子节点数据项配置配置(和 SunburstItem 一致, 递归下去)
    children: Optional[Sequence] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Sunburst/README)


## ThemeRiver：主题河流图

> *class pyecharts.charts.ThemeRiver*

```python
class ThemeRiver(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.ThemeRiver.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: Sequence,

    # 系列数据项
    data: types.Sequence[types.Union[opts.ThemeRiverItem, dict]],

    # 是否选中图例
    is_selected: bool = True,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 单轴组件配置项，参考 `global_options.SingleAxisOpts`
    singleaxis_opts: Union[opts.SingleAxisOpts, dict] = opts.SingleAxisOpts(),
):
```

### ThemeRiverItem：主题河流图数据项

```python
class ThemeRiverItem(
    # 时间或主题的时间属性。
    date: Optional[str] = None,

    # 事件或主题在某个时间点的值。
    value: Optional[Numeric] = None,

    # 事件或主题的名称。
    name: Optional[str] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/ThemeRiver/README)


## WordCloud：词云图

> *class pyecharts.charts.WordCloud*

```python
class WordCloud(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.WordCloud.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据项，[(word1, count1), (word2, count2)]
    data_pair: Sequence,

    # 词云图轮廓，有 'circle', 'cardioid', 'diamond', 'triangle-forward', 'triangle', 'pentagon', 'star' 可选
    shape: str = "circle",

    # 自定义的图片（目前支持 jpg, jpeg, png, ico 的格式，其他的图片格式待测试）
    # 该参数支持：
    # 1、 base64 （需要补充 data 头）；
    # 2、本地文件路径（相对或者绝对路径都可以）
    # 注：如果使用了 mask_image 之后第一次渲染会出现空白的情况，再刷新一次就可以了（Echarts 的问题）
    # Echarts Issue: https://github.com/ecomfe/echarts-wordcloud/issues/74
    mask_image: types.Optional[str] = None,

    # 单词间隔
    word_gap: Numeric = 20,

    # 单词字体大小范围
    word_size_range=None,

    # 旋转单词角度
    rotate_step: Numeric = 45,

    # 距离左侧的距离
    pos_left: types.Optional[str] = None,

    # 距离顶部的距离
    pos_top: types.Optional[str] = None,
    
    # 距离右侧的距离
    pos_right: types.Optional[str] = None,
    
    # 距离底部的距离
    pos_bottom: types.Optional[str] = None,

    # 词云图的宽度
    width: types.Optional[str] = None,

    # 词云图的高度
    height: types.Optional[str] = None,

    # 允许词云图的数据展示在画布范围之外
    is_draw_out_of_bound: bool = False,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 词云图文字的配置
    textstyle_opts: types.TextStyle = None,

    # 词云图文字阴影的范围
    emphasis_shadow_blur: types.Optional[types.Numeric] = None,

    # 词云图文字阴影的颜色
    emphasis_shadow_color: types.Optional[str] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/WordCloud/README)
