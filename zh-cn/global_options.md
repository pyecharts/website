## InitOpts
> 初始化配置项 *class pyecharts.options.InitOpts*

```python
class InitOpts(
    # 图表画布宽度
    width: str = "900px",

    # 图表画布高度
    height: str = "500px",

    # 图表 ID
    chart_id: Optional[str] = None,
    renderer: str = RenderType.CANVAS,
    page_title: str = "Awesome-pyecharts",
    theme: str = "white",
    bg_color: Optional[str] = None,
    js_host: str = "",
)
```

## ToolBoxFeatureOpts
> *class pyecharts.options.ToolBoxFeatureOpts*

```python
class ToolBoxFeatureOpts(
    # 保存为图片
    save_as_image: Optional[dict] = None,

    # 配置项还原
    restore: Optional[dict] = None,

    # 数据视图工具，可以展现当前图表所用的数据，编辑后可以动态更新
    data_view: Optional[dict] = None,
    
    # 数据区域缩放。目前只支持直角坐标系的缩放
    data_zoom: Optional[dict] = None,
)
```

## ToolboxOpts
> 工具箱配置项 *class pyecharts.options.ToolboxOpts*

```python
class ToolboxOpts(
    # 是否显示工具栏组件
    is_show: bool = True,

    # 工具栏 icon 的布局朝向。
    # 可选：'horizontal', 'vertical'
    orient: str = "horizontal",

    # 工具栏组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐
    pos_left: str = "80%",

    # 工具栏组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_right: Optional[str] = None,

    # 工具栏组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Optional[str] = None,

    # 工具栏组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_bottom: Optional[str] = None,

    # 各工具配置项
    feature: Union[ToolBoxFeatureOpts, dict] = ToolBoxFeatureOpts(),
)
```

## TitleOpts
> 标题配置项 *class pyecharts.options.TitleOpts*

```python
class TitleOpts(
    # 主标题文本，支持使用 \n 换行。
    title: Optional[str] = None,

    # 副标题文本，支持使用 \n 换行。
    subtitle: Optional[str] = None,

    # title 组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: Optional[str] = None,

    # title 组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_right: Optional[str] = None,

    # title 组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Optional[str] = None,

    # title 组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_bottom: Optional[str] = None,

    # 主标题字体样式配置项
    title_textstyle_opts: Union[TextStyleOpts, dict, None] = None,

    # 副标题字体样式配置项
    subtitle_textstyle_opts: Union[TextStyleOpts, dict, None] = None,
)
```

## DataZoomOpts
> *class pyecharts.options.DataZoomOpts*

```python
class DataZoomOpts(
    # 是否显示 组件。如果设置为 false，不会显示，但是数据过滤的功能还存在。
    is_show: bool = True,

    # 组件类型，可选 "slider", "inside"
    type_: str = "slider",

    # 数据窗口范围的起始百分比。范围是：0 ~ 100。表示 0% ~ 100%。
    range_start: Numeric = 20,

    # 数据窗口范围的结束百分比。范围是：0 ~ 100
    range_end: Numeric = 80,

    # 布局方式是横还是竖。不仅是布局方式，对于直角坐标系而言，也决定了，缺省情况控制横向数轴还是纵向数轴
    # 可选值为：'horizontal', 'vertical'
    orient: str = "horizontal",

    # 设置 dataZoom-inside 组件控制的 x 轴（即 xAxis，是直角坐标系中的概念，参见 grid）。
    # 不指定时，当 dataZoom-inside.orient 为 'horizontal'时，默认控制和 dataZoom 平行的第一个 xAxis
    # 如果是 number 表示控制一个轴，如果是 Array 表示控制多个轴。
    xaxis_index: int = 0,

    # 设置 dataZoom-inside 组件控制的 y 轴（即 yAxis，是直角坐标系中的概念，参见 grid）。
    # 不指定时，当 dataZoom-inside.orient 为 'horizontal'时，默认控制和 dataZoom 平行的第一个 yAxis
    # 如果是 number 表示控制一个轴，如果是 Array 表示控制多个轴。
    yaxis_index: int = 0,
)
```

## LegendOpts
> *class pyecharts.options.LegendOpts*

```python
class LegendOpts(
    # 图例选择的模式，控制是否可以通过点击图例改变系列的显示状态。默认开启图例选择，可以设成 false 关闭
    # 除此之外也可以设成 'single' 或者 'multiple' 使用单选或者多选模式。
    selected_mode: Union[str, bool, None] = None,

    # 是否显示图例组件
    is_show: bool = True,

    # 图例组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: Optional[str] = None,

    # 图例组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_right: Optional[str] = None,

    # 图例组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Optional[str] = None,

    # 图例组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_bottom: Optional[str] = None,

    # 图例列表的布局朝向。可选：'horizontal', 'vertical'
    orient: Optional[str] = None,

    # 图例组件字体样式，参考 `global_options.TextStyleOpts`
    textstyle_opts: Union[TextStyleOpts, dict, None] = None,
)
```

## VisualMapOpts
> *class pyecharts.options.VisualMapOpts*

```python
class VisualMapOpts(
    type_: str = "color",
    min_: Union[int, float] = 0,
    max_: Union[int, float] = 100,
    range_text: Union[list, tuple] = None,
    range_color: Union[List[str]] = None,
    range_size: Union[List[int]] = None,
    orient: str = "vertical",
    pos_left: str = "left",
    pos_top: str = "bottom",
    split_number: int = 5,
    dimension: Optional[Numeric] = None,
    is_calculable: bool = True,
    is_piecewise: bool = False,
    pieces: Optional[Sequence] = None,
    textstyle_opts: Union[TextStyleOpts, dict, None] = None,
)
```

## TooltipOpts
> *class pyecharts.options.TooltipOpts*

```python
class TooltipOpts(
    # 触发类型。可选：
    # 'item': 数据项图形触发，主要在散点图，饼图等无类目轴的图表中使用。
    # 'axis': 坐标轴触发，主要在柱状图，折线图等会使用类目轴的图表中使用。
    # 'none': 什么都不触发
    trigger: str = "item",

    # 提示框触发的条件，可选：
    # 'mousemove': 鼠标移动时触发。
    # 'click': 鼠标点击时触发。
    # 'mousemove|click': 同时鼠标移动和点击时触发。
    # 'none': 不在 'mousemove' 或 'click' 时触发，
    trigger_on: str = "mousemove|click",


    axis_pointer_type: str = "line",

    # 
    formatter: Optional[str] = None,

    # 提示框浮层的背景颜色。
    background_color: Optional[str] = None,

    # 提示框浮层的边框颜色。
    border_color: Optional[str] = None,

    # 提示框浮层的边框宽。
    border_width: Numeric = 0,
    textstyle_opts: TextStyleOpts = TextStyleOpts(font_size=14),
)
```

## AxisOpts
> *class pyecharts.options.AxisOpts*

```python
class AxisOpts(
    # 坐标轴名称。
    name: Optional[str] = None,

    # 是否显示 x 轴。
    is_show: bool = True,

    # 只在数值轴中（type: 'value'）有效。
    # 是否是脱离 0 值比例。设置成 true 后坐标刻度不会强制包含零刻度。在双数值轴的散点图中比较有用。
    # 在设置 min 和 max 之后该配置项无效。
    is_scale: bool = False,

    # 坐标轴名称显示位置。可选：
    # 'start', 'middle' 或者 'center','end'
    name_location: str = "end",

    # 坐标轴名称与轴线之间的距离。
    name_gap: Numeric = 15,

    # 强制设置坐标轴分割间隔。
    # 因为 splitNumber 是预估的值，实际根据策略计算出来的刻度可能无法达到想要的效果，
    # 这时候可以使用 interval 配合 min、max 强制设定刻度划分，一般不建议使用。
    # 无法在类目轴中使用。在时间轴（type: 'time'）中需要传时间戳，在对数轴（type: 'log'）中需要传指数值。
    interval: Optional[Numeric] = None,

    # x 轴所在的 grid 的索引，默认位于第一个 grid。
    grid_index: Numeric = 0,

    # x 轴的位置。可选：
    # 'top', 'bottom'
    # 默认 grid 中的第一个 x 轴在 grid 的下方（'bottom'），第二个 x 轴视第一个 x 轴的位置放在另一侧。
    position: Optional[str] = None,

    # 坐标轴两边留白策略，类目轴和非类目轴的设置和表现不一样。
    # 类目轴中 boundaryGap 可以配置为 true 和 false。默认为 true，这时候刻度只是作为分隔线，
    # 标签和数据点都会在两个刻度之间的带(band)中间。
    # 非类目轴，包括时间，数值，对数轴，boundaryGap是一个两个值的数组，分别表示数据最小值和最大值的延伸范围
    # 可以直接设置数值或者相对的百分比，在设置 min 和 max 后无效。 示例：boundaryGap: ['20%', '20%']
    boundary_gap: Union[str, bool, None] = None,

    label_alignment: Optional[str] = None,

    formatter: Optional[str] = None,

    inverse: Optional[str] = None,

    # 坐标轴刻度最小值。
    # 可以设置成特殊值 'dataMin'，此时取数据在该轴上的最小值作为最小刻度。
    # 不设置时会自动计算最小值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'。
    # 也可以设置为负数，如 -3）。
    min_: Union[Numeric, str, None] = None,

    # 坐标轴刻度最大值。
    # 可以设置成特殊值 'dataMax'，此时取数据在该轴上的最大值作为最大刻度。
    # 不设置时会自动计算最大值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'。
    # 也可以设置为负数，如 -3）。
    max_: Union[Numeric, str, None] = None,

    # 坐标轴类型。可选：
    # 'value': 数值轴，适用于连续数据。
    # 'category': 类目轴，适用于离散的类目数据，为该类型时必须通过 data 设置类目数据。
    # 'time': 时间轴，适用于连续的时序数据，与数值轴相比时间轴带有时间的格式化，在刻度计算上也有所不同，
    # 例如会根据跨度的范围来决定使用月，星期，日还是小时范围的刻度。
    # 'log' 对数轴。适用于对数数据。
    type_: Optional[str] = None,

    name_textstyle_opts: Union[TextStyleOpts, dict, None] = None,

    splitarea_opts: Union[SplitAreaOpts, dict, None] = None,

    splitline_opts: Union[SplitLineOpts, dict] = SplitLineOpts(),

    linestyle_opts: Union[LineStyleOpts, dict] = LineStyleOpts(),
)
```

## GridOpts
> *class pyecharts.options.GridOpts*

```python
class GridOpts(
    # grid 组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: Optional[str] = None,

    # grid 组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Optional[str] = None,

    # grid 组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_right: Optional[str] = None,

    # grid 组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_bottom: Optional[str] = None,

    # grid 组件的宽度。默认自适应。
    width: Optional[Numeric] = None,

    # grid 组件的高度。默认自适应。
    height: Optional[Numeric] = None,
)
```

## Grid3DOpts
> *class pyecahrts.options.Grid3DOpts*

```python
class Grid3DOpts(
    width: Numeric = 200,
    height: Numeric = 100,
    depth: Numeric = 80,
    is_rotate: bool = False,
    rotate_speed: Numeric = 10,
    rotate_sensitivity: Numeric = 1,
)
```

## Axis3DOpts
> *class pyecharts.options.Axis3DOpts*

```python
class Axis3DOpts(
    data: Optional[Sequence] = None,
    type_: Optional[str] = None,
    name: Optional[str] = None,
    name_size: Numeric = 16,
    name_gap: Numeric = 20,
    min_: Union[str, Numeric, None] = None,
    max_: Union[str, Numeric, None] = None,
    interval: Optional[str] = None,
    margin: Numeric = 8,
)
```

## CalendarOpts
> *class pyecahrts.options.CalendarOpts*

```python
class CalendarOpts(
    pos_left: Optional[str] = None,
    pos_top: Optional[str] = None,
    pos_right: Optional[str] = None,
    pos_bottom: Optional[str] = None,
    orient: Optional[str] = None,
    range_: Union[str, Sequence, int] = None,
    daylabel_opts: Union[LabelOpts, dict, None] = None,
    monthlabel_opts: Union[LabelOpts, dict, None] = None,
    yearlabel_opts: Union[LabelOpts, dict, None] = None,
)
```

## SingleAxisOpts
> *class pyecharts.SingleAxisOpts*

```python
class SingleAxisOpts(
    name: Optional[str] = None,
    max_: Union[str, Numeric, None] = None,
    min_: Union[str, Numeric, None] = None,
    pos_left: Optional[str] = None,
    pos_right: Optional[str] = None,
    pos_top: Optional[str] = None,
    pos_bottom: Optional[str] = None,
    width: Optional[str] = None,
    height: Optional[str] = None,
    orient: Optional[str] = None,
    type_: Optional[str] = None,
)
```

## RadiusAxisItem
> *class pyecahrts.options.RadiusAxisItem*

```python
class RadiusAxisItem(
    value: Optional[str] = None,
    textstyle_opts: Optional[TextStyleOpts] = None,
)
```

## AngleAxisItem
> *class pyecharts.options.AngleAxisItem*

```python
class AngleAxisItem(
    value: Optional[str] = None,
    textstyle_opts: Optional[TextStyleOpts] = None,
)
```

## RadiusAxisOpts
> *class pyecharts.optiones.RadiusAxisOpts*

```python
class RadiusAxisOpts(
    # 径向轴所在的极坐标系的索引，默认使用第一个极坐标系。
    polar_index: Optional[int] = None,


    data: Optional[List[Union[RadiusAxisItem, dict, str]]] = None,

    # 坐标轴两边留白策略，类目轴和非类目轴的设置和表现不一样。
    # 类目轴中 boundaryGap 可以配置为 true 和 false。默认为 true，这时候刻度只是作为分隔线，
    # 标签和数据点都会在两个刻度之间的带(band)中间。
    # 非类目轴，包括时间，数值，对数轴，boundaryGap是一个两个值的数组，分别表示数据最小值和最大值的延伸范围
    # 可以直接设置数值或者相对的百分比，在设置 min 和 max 后无效。 示例：boundaryGap: ['20%', '20%']
    boundary_gap: Union[bool, List] = None,

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

    # 分割线配置项，参考 `series_options.SplitLineOpts`
    splitline_opts: Union[SplitLineOpts, dict, None] = None,
    axisline_opts: Union[AxisLineOpts, dict, None] = None,
    axislabel_opts: Union[LabelOpts, dict, None] = None,
    z: Optional[int] = None,
)
```

## AngleAxisOpts
> *class pyecharts.options.AngleAxisOpts*

```python
class AngleAxisOpts(
    polar_index: Optional[int] = None,
    data: Optional[List[Union[AngleAxisItem, dict, str]]] = None,
    start_angle: Optional[Numeric] = None,
    is_clockwise: bool = False,
    boundary_gap: Union[bool, List] = None,
    type_: Optional[str] = None,
    min_: Union[str, Numeric, None] = None,
    max_: Union[str, Numeric, None] = None,
    splitline_opts: Union[SplitLineOpts, dict, None] = None,
    axisline_opts: Union[AxisLineOpts, dict, None] = None,
    axislabel_opts: Union[LabelOpts, dict, None] = None,
    z: Optional[int] = None,
)
```
