直角坐标系图表继承自 `RectChart` 都拥有以下方法

> *func RectChart.extend_axis*

扩展 X/Y 轴
```python
def extend_axis(
    # 扩展 X 坐标轴数据项
    xaxis_data: Sequence = None,
    
    # 扩展 X 坐标轴配置项，参考 `global_options.AxisOpts`
    xaxis: Union[opts.AxisOpts, dict, None] = None,
    
    # 新增 Y 坐标轴配置项，参考 `global_options.AxisOpts`
    yaxis: Union[opts.AxisOpts, dict, None] = None,
)
```

> *func RectChart.add_xaxis*

新增 X 轴数据
```python
def add_xaxis(
    # X 轴数据项
    xaxis_data: Sequence
)
```

> *func RectChart.reversal_axis*

翻转 XY 轴数据
```python
def reversal_axis():
```

> *func RectChart.overlap*

层叠多图
```python
def overlap(
    # chart 为直角坐标系类型图表
    chart: Base
)
```

> *func Chart.add_dataset*

添加 dataset 组件
```python
def add_dataset(
    # 原始数据。一般来说，原始数据表达的是二维表。
    source: types.Union[types.Sequence, types.JSFunc] = None,
    
    # 使用 dimensions 定义 series.data 或者 dataset.source 的每个维度的信息。
    dimensions: types.Optional[types.Sequence] = None,
    
    # dataset.source 第一行/列是否是 维度名 信息。可选值：
    # null/undefine（对应 Python 的 None 值）：默认，自动探测。
    # true：第一行/列是维度名信息。
    # false：第一行/列直接开始是数据。
    source_header: types.Optional[bool] = None,
)
```

## Bar：柱状图/条形图

> *class pyecharts.charts.Bar(RectChart)*

```python
class Bar(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Bar.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: Sequence[Numeric, opts.BarItem, dict],

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 是否启用图例 hover 时的联动高亮
    is_legend_hover_link: bool = True,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 是否显示柱条的背景色。通过 backgroundStyle 配置背景样式。
    is_show_background: bool = False,
    
    # 每一个柱条的背景样式。需要将 showBackground 设置为 true 时才有效。
    background_style: types.Union[types.BarBackground, dict, None] = None,

    # 数据堆叠，同个类目轴上系列配置相同的　stack　值可以堆叠放置。
    stack: Optional[str] = None,

    # 柱条的宽度，不设时自适应。
    # 可以是绝对值例如 40 或者百分数例如 '60%'。百分数基于自动计算出的每一类目的宽度。
    # 在同一坐标系上，此属性会被多个 'bar' 系列共享。此属性应设置于此坐标系中最后一个 'bar' 系列上才会生效，并且是对此坐标系中所有 'bar' 系列生效。
    bar_width: types.Union[types.Numeric, str] = None,
    
    # 柱条的最大宽度。比 barWidth 优先级高。
    bar_max_width: types.Union[types.Numeric, str] = None,
    
    # 柱条的最小宽度。在直角坐标系中，默认值是 1。否则默认值是 null。比 barWidth 优先级高。
    bar_min_width: types.Union[types.Numeric, str] = None,
    
    # 柱条最小高度，可用于防止某数据项的值过小而影响交互。
    bar_min_height: types.Numeric = 0,

    # 同一系列的柱间距离，默认为类目间距的 20%，可设固定值
    category_gap: Union[Numeric, str] = "20%",

    # 不同系列的柱间距离，为百分比（如 '30%'，表示柱子宽度的 30%）。
    # 如果想要两个系列的柱子重叠，可以设置 gap 为 '-100%'。这在用柱子做背景的时候有用。
    gap: Optional[str] = "30%",

    # 是否开启大数据量优化，在数据图形特别多而出现卡顿时候可以开启。
    # 开启后配合 largeThreshold 在数据量大于指定阈值的时候对绘制进行优化。
    # 缺点：优化后不能自定义设置单个数据项的样式。
    is_large: bool = False,
    
    # 开启绘制优化的阈值。
    large_threshold: types.Numeric = 400,

    # 使用 dimensions 定义 series.data 或者 dataset.source 的每个维度的信息。
    # 注意：如果使用了 dataset，那么可以在 dataset.source 的第一行/列中给出 dimension 名称。
    # 于是就不用在这里指定 dimension。
    # 但是，如果在这里指定了 dimensions，那么 ECharts 不再会自动从 dataset.source 的第一行/列中获取维度信息。
    dimensions: types.Union[types.Sequence, None] = None,

    # 当使用 dataset 时，seriesLayoutBy 指定了 dataset 中用行还是列对应到系列上，也就是说，系列“排布”到 dataset 的行还是列上。可取值：
    # 'column'：默认，dataset 的列对应于系列，从而 dataset 中每一列是一个维度（dimension）。
    # 'row'：dataset 的行对应于系列，从而 dataset 中每一行是一个维度（dimension）。
    series_layout_by: str = "column",

    # 如果 series.data 没有指定，并且 dataset 存在，那么就会使用 dataset。
    # datasetIndex 指定本系列使用那个 dataset。
    dataset_index: types.Numeric = 0,

    # 是否裁剪超出坐标系部分的图形。柱状图：裁掉所有超出坐标系的部分，但是依然保留柱子的宽度
    is_clip: bool = True,
    
    # 柱状图所有图形的 zlevel 值。
    z_level: types.Numeric = 0,

    # 柱状图组件的所有图形的z值。控制图形的前后顺序。
    # z值小的图形会被z值大的图形覆盖。
    # z相比zlevel优先级更低，而且不会创建新的 Canvas。
    z: types.Numeric = 2,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # 可以定义 data 的哪个维度被编码成什么。
    encode: types.Union[types.JSFunc, dict, None] = None,
)
```

### BarItem：柱状图数据项

```python
class BarItem(
    # 数据项名称。
    name: Optional[str] = None,

    # 单个数据项的数值。
    value: Optional[Numeric] = None,

    # 单个柱条文本的样式设置，参考 `series_options.LabelOpts`。
    label_opts: Union[LabelOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### BarBackgroundStyleOpts：柱状图背景样式配置

```python
class BarBackgroundStyleOpts(
    # 柱条的颜色。
    color: str = "rgba(180, 180, 180, 0.2)",

    # 柱条的描边颜色。
    border_color: str = "#000",

    # 柱条的描边宽度，默认不描边。
    border_width: Numeric = 0,

    # 柱条的描边类型，默认为实线，支持 'dashed', 'dotted'。
    border_type: str = "solid",

    # 圆角半径，单位px，支持传入数组分别指定 4 个圆角半径。 如:
    # barBorderRadius: 5, // 统一设置四个角的圆角大小
    # barBorderRadius: [5, 5, 0, 0] //（顺时针左上，右上，右下，左下）
    bar_border_radius: Union[Numeric, Sequence] = 0,

    # 图形阴影的模糊大小。
    # 该属性配合 shadowColor,shadowOffsetX, shadowOffsetY 一起设置图形的阴影效果。
    shadow_blur: Optional[Numeric] = None,

    # 阴影颜色。支持的格式同color。
    shadow_color: Optional[str] = None,

    # 阴影水平方向上的偏移距离。
    shadow_offset_x: Numeric = 0,

    # 阴影垂直方向上的偏移距离。
    shadow_offset_y: Numeric = 0,

    # 图形透明度。支持从 0 到 1 的数字，为 0 时不绘制该图形。
    opacity: Optional[Numeric] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Bar/README)


## Boxplot：箱形图

> *class pyecharts.charts.Boxplot(RectChart)*

```python
class Boxplot(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Boxplot.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: types.Sequence[types.Union[opts.BoxplotItem, dict]],

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict] = opts.MarkPointOpts(),

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict] = opts.MarkLineOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### BoxplotItem：箱形图数据项

```python
class BoxplotItem(
    # 数据项名称。
    name: Optional[str] = None,

    # 单个数据项的数值。
    value: Optional[Numeric] = None,

    # 文本的样式设置，参考 `series_options.LabelOpts`。
    label_opts: Union[LabelOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Boxplot/README)


## EffectScatter：涟漪特效散点图

> *class pyecharts.charts.EffectScatter(RectChart)*

```python
class EffectScatter(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.EffectScatter.add_yaxis*

```python
 def add_yaxis(
     # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: types.Sequence[types.Union[opts.BoxplotItem, dict]],

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 标记图形形状
    symbol: Optional[str] = None,

    # 标记的大小
    symbol_size: Numeric = 10,

    # 标记的旋转角度。注意在 markLine 中当 symbol 为 'arrow' 时会忽略 symbolRotate 强制设置为切线的角度。
    symbol_rotate: types.Optional[types.Numeric] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 涟漪特效配置项，参考 `series_options.EffectOpts`
    effect_opts: Union[opts.EffectOpts, dict] = opts.EffectOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### EffectScatterItem：涟漪特效散点图数据项

```python
class EffectScatterItem(
    # 数据项名称。
    name: Union[str, Numeric] = None,

    # 数据项的值
    value: Union[str, Numeric] = None,

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
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/EffectScatter/README)


## HeatMap：热力图

> *class pyecharts.charts.HeatMap(RectChart)*

```python
class HeatMap(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.HeatMap.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # Y 坐标轴数据
    yaxis_data: types.Sequence[types.Union[opts.HeatMapItem, dict]],

    # 系列数据项
    value: types.Sequence[types.Union[opts.HeatMapItem, dict]],

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### HeatMapItem：热力图数据项

```python
class HeatMapItem(
    # 数据项名称。
    name: Optional[str] = None,
    
    # 数据项的值。
    value: Optional[Sequence] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Heatmap/README)


## Kline/Candlestick：K线图

> *class pyecharts.charts.Kline(RectChart)*

```python
class Kline(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Kline.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: types.Sequence[types.Union[opts.CandleStickItem, dict]],

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### CandleStickItem：K 线图数据项

```python
class CandleStickItem(
    # 数据项名称。
    name: Optional[str] = None,
    
    # 数据项的值。
    value: Optional[Sequence] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Candlestick/README)


## Line：折线/面积图

> *class pyecharts.charts.Line(RectChart)*

```python
class Line(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Line.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: types.Sequence[types.Union[opts.LineItem, dict]],

    # 是否选中图例
    is_selected: bool = True,

    # 是否连接空数据，空数据使用 `None` 填充
    is_connect_nones: bool = False,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 是否显示 symbol, 如果 false 则只有在 tooltip hover 的时候显示。
    is_symbol_show: bool = True,

    # 标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Union[Numeric, Sequence] = 4,

    # 数据堆叠，同个类目轴上系列配置相同的　stack　值可以堆叠放置。
    stack: Optional[str] = None,

    # 是否平滑曲线
    is_smooth: bool = False,
    
    # 是否裁剪超出坐标系部分的图形。折线图：裁掉所有超出坐标系的折线部分，拐点图形的逻辑按照散点图处理
    is_clip: bool = True,

    # 是否显示成阶梯图
    is_step: bool = False,
    
    # 是否开启 hover 在拐点标志上的提示动画效果。
    is_hover_animation: bool = True,
    
    # 折线图所有图形的 zlevel 值。
    # zlevel用于 Canvas 分层，不同zlevel值的图形会放置在不同的 Canvas 中，Canvas 分层是一种常见的优化手段。
    # zlevel 大的 Canvas 会放在 zlevel 小的 Canvas 的上面。
    z_level: types.Numeric = 0,
    
    # 折线图组件的所有图形的z值。控制图形的前后顺序。z值小的图形会被z值大的图形覆盖。
    # z 相比 zlevel 优先级更低，而且不会创建新的 Canvas。
    z: types.Numeric = 0,

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 线样式配置项，参考 `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(),

    # 填充区域配置项，参考 `series_options.AreaStyleOpts`
    areastyle_opts: Union[opts.AreaStyleOpts, dict] = opts.AreaStyleOpts(),

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### LineItem：折线图数据项

```python
class LineItem(
    # 数据项名称。
    name: Union[str, Numeric] = None,

    # 数据项的值
    value: Union[str, Numeric] = None,

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
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Line/README)


## PictorialBar：象形柱状图

> *class pyecharts.charts.PictorialBar(RectChart)*

```python
class PictorialBar(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.PictorialBar.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: Sequence,

    # 图形类型。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    # URL 为图片链接例如：'image://http://xxx.xxx.xxx/a/b.png'
    # URL 为 dataURI 例如：'image://data:image/gif;base64,R0lGODlhEAAQAMQAAORHHOVSKudfO...
    # 可以通过 'path://' 将图标设置为任意的矢量路径。这种方式相比于使用图片的方式，不用担心因为缩放而产生锯齿或模糊，
    # 而且可以设置为任意颜色。路径图形会自适应调整为合适的大小。路径的格式参见 SVG PathData。
    # 可以从 Adobe Illustrator 等工具编辑导出。例如：
    # 'path://M30.9,53.2C16.8,53.2,5.3,41.7,5.3,27.6S16.8,2,30.9,2C45,2,56.4,13.5,56.4,2...'
    symbol: Optional[str] = None,

    # 图形的大小。
    # 可以用数组分开表示宽和高，例如 [20, 10] 表示标记宽为20，
    # 高为 10，也可以设置成诸如 10 这样单一的数字，表示 [10, 10]。
    # 可以设置成绝对值（如 10），也可以设置成百分比（如 '120%'、['55%', 23]）。
    symbol_size: Union[Numeric, Sequence, None] = None,

    # 图形的定位位置。可取值：
    # 'start'：图形边缘与柱子开始的地方内切。
    # 'end'：图形边缘与柱子结束的地方内切。
    # 'center'：图形在柱子里居中。
    symbol_pos: Optional[str] = None,

    # 图形相对于原本位置的偏移。symbolOffset 是图形定位中最后计算的一个步骤，
    # 可以对图形计算出来的位置进行微调。
    # 可以设置成绝对值（如 10），也可以设置成百分比（如 '120%'、['55%', 23]）。
    # 当设置为百分比时，表示相对于自身尺寸 symbolSize 的百分比。
    # 例如 [0, '-50%'] 就是把图形向上移动了自身尺寸的一半的位置。
    symbol_offset: Optional[Sequence] = None,

    # 图形的旋转角度。
    # 注意，symbolRotate 并不会影响图形的定位（哪怕超出基准柱的边界），而只是单纯得绕自身中心旋转。
    # 此属性可以被设置在系列的 根部，表示对此系列中所有数据都生效；
    # 也可以被设置在 data 中的 每个数据项中，表示只对此数据项生效。
    symbol_rotate: Optional[Numeric] = None,

    # 指定图形元素是否重复。值可为：
    # false/null/undefined：不重复，即每个数据值用一个图形元素表示。
    # true：使图形元素重复，即每个数据值用一组重复的图形元素表示。重复的次数依据 data 计算得到。
    # a number：使图形元素重复，即每个数据值用一组重复的图形元素表示。重复的次数是给定的定值。
    # 'fixed'：使图形元素重复，即每个数据值用一组重复的图形元素表示。
    # 重复的次数依据 symbolBoundingData 计算得到，即与 data 无关。这在此图形被用于做背景时有用。
    symbol_repeat: Optional[str] = None,

    # 指定图形元素重复时，绘制的顺序。这个属性在两种情况下有用处：
    # 当 symbolMargin 设置为负值时，重复的图形会互相覆盖，这是可以使用 symbolRepeatDirection 来指定覆盖顺序。
    # 当 animationDelay 或 animationDelayUpdate 被使用时，symbolRepeatDirection 指定了 index 顺序。
    # 这个属性的值可以是：'start' 或 'end'。
    symbol_repeat_direction: Optional[str] = None,

    # 图形的两边间隔（『两边』是指其数值轴方向的两边）。可以是绝对数值（如 20），或者百分比值（如 '-30%'），
    # 表示相对于自身尺寸 symbolSize 的百分比。只有当 symbolRepeat 被使用时有意义。
    # 可以是正值，表示间隔大；也可以是负数。当 symbolRepeat 被使用时，负数时能使图形重叠。
    # 可以在其值结尾处加一个 "!"，如 "30%!" 或 25!，表示第一个图形的开始和最后一个图形结尾留白，
    # 不紧贴边界。默认会紧贴边界。
    symbol_margin: Union[Numeric, str, None] = None,

    # 是否剪裁图形。
    # false/null/undefined：图形本身表示数值大小。
    # true：图形被剪裁后剩余的部分表示数值大小。
    # symbolClip 常在这种场景下使用：同时表达『总值』和『当前数值』。在这种场景下，可以使用两个系列，
    # 一个系列是完整的图形，当做『背景』来表达总数值，另一个系列是使用 symbolClip 进行剪裁过的图形，表达当前数值。
    is_symbol_clip: bool = False,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 同一系列的柱间距离，默认为类目间距的 20%，可设固定值
    category_gap: Union[Numeric, str] = "20%",

    # 不同系列的柱间距离，为百分比（如 '30%'，表示柱子宽度的 30%）。
    # 如果想要两个系列的柱子重叠，可以设置 gap 为 '-100%'。这在用柱子做背景的时候有用。
    gap: Optional[str] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # 可以定义 data 的哪个维度被编码成什么。
    encode: types.Union[types.JsCode, dict] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/PictorialBar/README)


## Scatter：散点图

> *class pyecharts.charts.Scatter(RectChart)*

```python
class Scatter(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Scatter.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Numeric = 10,
    
    # 标记的旋转角度。注意在 markLine 中当 symbol 为 'arrow' 时会忽略 symbolRotate 强制设置为切线的角度。
    symbol_rotate: types.Optional[types.Numeric] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(position="right"),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 图表标域，常用于标记图表中某个范围的数据，参考 `series_options.MarkAreaOpts`
    markarea_opts: types.MarkArea = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # 可以定义 data 的哪个维度被编码成什么。
    encode: types.Union[types.JSFunc, dict, None] = None,
)
```

### ScatterItem：散点图数据项

```python
class ScatterItem(
    # 数据项名称。
    name: Union[str, Numeric] = None,

    # 数据项值。
    value: Union[str, Numeric] = None,

    # 单个数据标记的图形。
    # ECharts 提供的标记类型包括 
    # 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    # 可以通过 'path://' 将图标设置为任意的矢量路径。
    symbol: Optional[str] = None,

    # 单个数据标记的大小，可以设置成诸如 10 这样单一的数字
    # 也可以用数组分开表示宽和高，例如 [20, 10] 表示标记宽为20，高为10。
    symbol_size: Union[Sequence[Numeric], Numeric] = None,

    # 单个数据标记的旋转角度（而非弧度）。正
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
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Scatter/README)


## Overlap：层叠多图

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Overlap/README)