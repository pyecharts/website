The rectangular coordinate system charts inherited from `RectChart` both have the following methods

> *func RectChart.extend_axis*

Extends the X/Y axis
```python
def extend_axis(
    # extend x-axis data items
    xaxis_data: Sequence = None,
    
    # Extend X axis configuration items, see ``global_options.AxisOpts``
    xaxis: Union[opts.AxisOpts, dict, None] = None,
    
    # New Y axis configuration item, refer to `global_options.AxisOpts`
    yaxis: Union[opts.AxisOpts, dict, None] = None,
)
```

> *func RectChart.add_xaxis*

Add x-axis data
``` python
def add_xaxis(
    # X-axis data items
    xaxis_data: Sequence
)
```

> *func RectChart.reversal_axis*

Reversal of XY axis data
``` python
def reversal_axis():
```

> *func RectChart.overlap*

Cascade multiple charts
```python
def overlap(
    # chart is a rectangular coordinate system type chart
    chart: Base
)
```

> *func Chart.add_dataset*

Adds the dataset component
```python
def add_dataset(
    # Raw data. Generally, the raw data expression is a two-dimensional table.
    source: types.Union[types.Sequence, types.JSFunc] = None,
    
    # Use dimensions to define information about each dimension of series.data or dataset.source.
    dimensions: types.Optional[types.Sequence] = None,
    
    # Whether the first row/column of dataset.source is dimension name information. Optional values.
    # null/undefine (corresponding to Python's None value): default, auto-detect.
    # true: the first row/column is dimension name information.
    # false: the first row/column starts directly with the data.
    source_header: types.Optional[bool] = None,
)
```

## Bar: bar/column charts

> *class pyecharts.charts.Bar(RectChart)*

``` python
class Bar(
    # Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Bar.add_yaxis*

```python
def add_yaxis(
    # Series name for display of tooltip, legend filter for legend.
    series_name: str,

    # series data
    y_axis: Sequence[Numeric, opts.BarItem, dict],

    # Whether the legend is selected or not
    is_selected: bool = True,

    # The index of the x-axis to use, useful if there are multiple x-axes in a single chart instance.
    xaxis_index: Optional[Numeric] = None,

    # The index of the y-axis to use, useful if there are multiple y-axes in a single instance of the chart.
    yaxis_index: Optional[Numeric] = None,
    
    # The index of the polar coordinate system to use, useful when there are multiple polar coordinate systems in a single chart instance.
    polar_index: types.Optional[types.Numeric] = None,.
    
    # Whether or not to use the arc effect on both sides of the circular bar. Only valid for polar coordinate system bar charts.
    is_round_cap: types.Optional[bool] = None,.
    
    # The strategy to take the colour from the palette option.color, can take values:
    # 'series': assign colours in the palette by series, all data in the same series is in the same colour;
    # 'data': assign colours in the palette by data item, with each data item using a different colour.
    colour_by: types.Optional[str] = None,

    # Whether to enable linkage highlighting for legend hovers
    is_legend_hover_link: bool = True,

    # series label colour
    color: Optional[str] = None,
    
    # Whether to enable realtime sorting, default is False
    is_realtime_sort: bool = False,

    # Whether to display the background colour of the bar. Configure the background style via backgroundStyle.
    is_show_background: bool = False,
    
    # The background style for each bar. Requires showBackground to be set to true.
    background_style: types.Union[types.BarBackground, dict, None] = None,

    # Data stacking, where stack values with the same series configuration on the same class axis can be stacked.
    stack: Optional[str] = None,
    
    # Data stacking, where stack values with the same series configuration on the same class axis can be stacked. See stackStrategy for more information on how to customise the stacking of values.
    # Note: Currently stack is only supported on the 'value' and 'log' type category axes, not the 'time' and 'category' type category axes.
    stack_strategy: types.Optional[str] = "samesign",
    
    # Strategy for stacking values, provided the stack attribute has been set. Its value can be.
    # 'samesign' Stack only if the value to be stacked has the same positive and negative sign as the currently accumulated stacked values.
    # 'all' stacks all values, regardless of the positive and negative sign of the current or accumulated stacked values.
    # 'positive' stacks only positive values.
    # 'negative' stacks only negative values.
    sampling: types.Optional[str] = None,
    
    # What the mouse style is when hovering over a graphical element. Same as cursor for CSS.
    cursor: types.Optional[str] = "pointer",

    # The width of the bar, adaptive if not set.
    # Can be an absolute value such as 40 or a percentage such as '60%'. The percentages are based on the automatically calculated width of each category.
    # This property is shared by multiple 'bar' series in the same co-ordinate system. This property should be set on the last 'bar' series in this coordinate system to take effect, and is valid for all 'bar' series in this coordinate system.
    bar_width: types.Union[types.Numeric, str] = None,
    
    # The maximum width of the bar. Higher priority than barWidth.
    bar_max_width: types.Union[types.Numeric, str] = None,
    
    # The minimum width of the bar. Defaults to 1 in a Cartesian coordinate system. otherwise defaults to null. higher priority than barWidth.
    bar_min_width: types.Union[types.Numeric, str] = None,
    
    # The minimum height of the bar, which can be used to prevent a data item from having a value too small for interaction.
    bar_min_height: types.Numeric = 0,

    # The distance between bars in the same series, default is 20% of the category spacing, can be set to a fixed value
    category_gap: Union[Numeric, str] = "20%",

    # The distance between columns for different series, as a percentage (e.g. '30%' for 30% of the column width).
    # If you want the columns of two series to overlap, you can set the gap to '-100%'. This is useful when using the columns as a background.
    gap: Optional[str] = "30%",

    # Whether or not to turn on large data volume optimisation, which can be turned on when data graphics are particularly large and lagging.
    # When enabled, it works with largeThreshold to optimize the drawing when the data volume is greater than the specified threshold.
    # Disadvantage: you cannot customise the style of individual data items after optimisation.
    is_large: bool = False,
    
    # Threshold to turn on plotting optimization.
    large_threshold: types.Numeric = 400,
    
    # The number of graphics to draw per frame for progressive rendering, set to 0 to disable progressive rendering, supports separate configuration for each series.
    progressive: types.Optional[types.Numeric] = None,
    
    # Threshold for the number of graphics to enable progressive rendering, enable progressive rendering when the number of graphics in a single series exceeds this threshold.
    progressive_threshold: types.Optional[types.Numeric] = None, # Enable progressive rendering when the number of graphics in a single series exceeds this threshold.
    
    # The way the slices will be rendered. Optional values:
    # 'sequential': slices the data in order. The disadvantage is that the rendering process is not natural.
    # 'mod': Takes a modal chunking, i.e. the points in each fragment are spread over the entire data, allowing for visually even rendering.
    progressive_chunk_mode: types.Optional[str] = None,

    # Use dimensions to define information about each dimension of series.data or dataset.source.
    # Note: If a dataset is used, then the dimension name can be given in the first row/column of the dataset.source.
    # So there is no need to specify the dimension here.
    # However, if dimensions are specified here, then ECharts will no longer automatically get the dimension information from the first row/column of dataset.source.
    dimensions: types.Union[types.Sequence, None] = None,

    # When using a dataset, seriesLayoutBy specifies whether rows or columns in the dataset correspond to the series, i.e. whether the series is "laid out" on the rows or columns of the dataset. Possible values.
    # 'column': by default, the columns of the dataset correspond to the series, so that each column in the dataset is a dimension.
    # 'row': the row of the dataset corresponds to the series, so that each row in the dataset is a dimension.
    series_layout_by: str = "column",

    # If series.data is not specified and the dataset exists, then the dataset will be used.
    # datasetIndex specifies which dataset is used for this series.
    dataset_index: types.Numeric = 0,

    # Whether or not to crop graphs that are partly outside the coordinate system. column_plot: crop all parts that are outside the coordinate system, but still retain the width of the columns
    is_clip: bool = True,
    
    # The zlevel value for all graphs of the bar chart.
    z_level: types.Numeric = 0,

    # The z value of all graphs of the bar graph component. Controls the order of the graphs before and after.
    # Graphs with small z values are overwritten by graphs with larger z values.
    # z has lower priority than zlevel and no new Canvas is created.
    z: types.Numeric = 2,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Markpoint configuration items, see `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # Marking line configuration items, see `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,
    
    # Chart marker fields, often used to mark a range of data in a chart, see `series_options.MarkAreaOpts`
    markarea_opts: types.MarkArea = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None, # tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
    
    # The graphic style and label style when fading out. Effective when emphasis.focus is turned on.
    blur_opts: types.
    
    Blur_opts: types.Blur = None, # Graphics and label styles when data is selected. Valid when selectedMode is enabled.
    select_opts: types.
    
    # You can define which dimension of data is encoded as what.
    encode: types.Union[types.JSFunc, dict, None] = None,
)
```

### BarItem: bar chart data item

``` python
class BarItem(
    ### The name of the data item.
    name: Union[int, str, None] = None,

    ### The value of a single data item.
    value: Optional[Numeric] = None,
    
    # The group ID of this data item.
    group_id: Optional[str] = None,

    # The style of the individual bar text, see `series_options.LabelOpts`.
    label_opts: Union[LabelOpts, dict, None] = None,
    
    # Whether to show the visual guide line.
    is_show_label_line: Optional[bool] = None,.
    
    # The visual guide line configuration
    label_line_linestyle_opts: Union[LineStyleOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### BarBackgroundStyleOpts: bar chart background style configuration

```python
class BarBackgroundStyleOpts(
    ### The colour of the bar.
    color: str = "rgba(180, 180, 180, 0.2)",

    # The stroke colour of the bar.
    border_color: str = "#000",

    # Stroke width of the bar, no stroke by default.
    border_width: Numeric = 0,

    # The stroke type of the bar, defaults to solid, supports 'dashed', 'dotted'.
    border_type: str = "solid",
    
    # Radius of the rounded corners, in px, supports passing in an array of 4 radiuses.
    border_radius: Union[Numeric, Sequence] = 0,

    # The radius of the rounded corners, in px, supports passing in an array to specify each of the 4 radii. For example:
    # barBorderRadius: 5, // Set the size of the rounded corners uniformly for each of the four corners
    # barBorderRadius: [5, 5, 0, 0] // (clockwise top-left, top-right, bottom-right, bottom-left)
    bar_border_radius: Union[Numeric, Sequence] = 0,

    # The blur size of the graphical shadow.
    # This property works in conjunction with shadowColor,shadowOffsetX, shadowOffsetY to set the shadow effect of the graph.
    shadow_blur: Optional[Numeric] = None,

    # Shadow colour. The same format as color is supported.
    shadow_color: Optional[str] = None,

    # The offset distance in the horizontal direction of the shadow.
    shadow_offset_x: Numeric = 0,

    # The vertical offset of the shadow.
    shadow_offset_y: Numeric = 0,

    # Graphical transparency. Supports a number from 0 to 1, the graph is not drawn when it is 0.
    opacity: Optional[Numeric] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Bar/README)


## Boxplot: box plot

> *class pyecharts.charts.Boxplot(RectChart)*

```python
class Boxplot(
    # Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Boxplot.add_yaxis*

``` python
def add_yaxis(
    # Series name for display of tooltip, legend filter for legend.
    series_name: str,

    # series data
    y_axis: types.Sequence[types.Union[opts.BoxplotItem, dict]],

    # Whether the legend is selected or not
    is_selected: bool = True,

    # The index of the x-axis to use, useful if there are multiple x-axes in a single chart instance.
    xaxis_index: Optional[Numeric] = None,

    # The index of the y-axis to use, useful if there are multiple y-axes in a single instance of the chart.
    yaxis_index: Optional[Numeric] = None,
    
    # dataset If series.data is not specified and dataset exists, then dataset is used.
    # datasetIndex Specifies which dataset to use for this series.
    dataset_index: types.Optional[types.Numeric] = None, # dataset_index: types.Optional[types.Numeric] = None, # dataset_index.
    
    # strategy for taking colours from palette option.color, can take values:
    # 'series': assign colours in the palette by series, all data in the same series is in the same colour;
    # 'data': assign colours in the palette by data item, with each data item using a different colour.
    colour_by: types.Optional[str] = None,.
    
    # Whether to enable linkage highlighting for legend hover.
    is_legend_hover_link: bool = True, # Whether to enable hover on box.
    
    # Whether to enable hover animation on the box.
    is_hover_animation: bool = True, # Whether to enable hover animation on box.
    
    # Layout style, optional:
    # 'horizontal': arrange the boxes horizontally.
    # 'vertical': arrange the boxes vertically.
    # Default value depends on current coordinate system: horizontal if category axis is horizontal, otherwise vertical, if no category axis, then horizontal.
    layout: types.Optional[str] = None, # The upper and lower bounds of the width of the box.
    
    The upper and lower bounds of the width of the # box. Array means: [min, max].
    # Can be an absolute value, like [7, 50], or a percentage, like ['40%', '90%'].
    # Percentage means what percent of the maximum possible width (bandWidth).
    box_width: types.Optional[types.Sequence] = None,
    
    # Configuration for the check mode, indicates if multiple checks are supported, default is off, booleans and strings are supported.
    # String values can be 'single', 'multiple', and 'series' for single, multiple, and whole series respectively.
    selected_mode: types.
    
    # Use dimensions to define information about each dimension of series.data or dataset.source. Related to dataset usage
    dimensions: types.Union[types.Sequence, None] = None, # Use dimensions to define information about each dimension of series.data or dataset.source.

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Markpoint configuration items, see `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict] = opts.MarkPointOpts(), # markpoint_opts: Union[opts.MarkPointOpts, dict] = opts,

    # Mark line configuration items, see `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict] = opts.MarkLineOpts(), # markline_opts: Union[opts.MarkLineOpts, dict] = opts,

    # Chart markarea, often used to mark a range of data in a chart, see `series_options.MarkAreaOpts`.
    markarea_opts: types.MarkArea = None, # zlevel values for all graphs in the box-and-whisker plot.
    
    # zlevel values for all shapes in the box-and-whisker plot.
    # The zlevel is used for Canvas layering, where shapes with different zlevel values are placed in different Canvas, and Canvas layering is a common optimisation.
    # We can set components with frequently changing graphics (e.g. animated) to a separate zlevel.
    # Note that too many Canvas can cause memory overheads and should be used with caution on mobile to prevent crashes.
    # Canvas with a large zlevel will be placed on top of Canvas with a small zlevel.
    z_level: types.
    
    z_level: types.Numeric = 0, # z_value of all shapes in the box-and-whisker component. Controls the order of the shapes; shapes with small z-levels will be overridden by shapes with large z-levels.
    # z has a lower priority than zlevel, and no new Canvas is created.
    z: types.

    # Tipbox component configuration items, see `series_options.
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
    
    # The graphic style and label style when fading out. Valid when emphasis.focus is enabled
    blur_opts: types.
    
    # The graphical style and label style when the data is selected. Valid when selectedMode is enabled.
    select_opts: types.
    
    # Allows you to define what dimensions of the data are encoded into what.
    encode: types.Union[types.JSFunc, dict, None] = None, # You can define which dimension the data is encoded into. encode: types.
)
```

### BoxplotItem: box plot data item

```python
class BoxplotItem(
    ### Name of the data item.
    name: Optional[str] = None,

    ### The value of a single data item.
    value: Optional[Numeric] = None,

    # The style of the text, see `series_options.LabelOpts`.
    label_opts: Union[LabelOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Boxplot/README)

## EffectScatter: Ripple Effect Scatter

> *class pyecharts.charts.EffectScatter(RectChart)*

```python
class EffectScatter(
    # Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.EffectScatter.add_yaxis*

``` python
def add_yaxis(
    # Series name for display of tooltip, legend filtering for legend.
    series_name: str,

    # series data
    y_axis: types.Sequence[types.Union[opts.BoxplotItem, dict]],

    # The index of the x-axis to use, useful if there are multiple x-axes in a single chart instance.
    xaxis_index: Optional[Numeric] = None,

    # The index of the y-axis to use, useful if there are multiple y-axes in a single instance of the chart.
    yaxis_index: Optional[Numeric] = None,
    
    # The index of the polar coordinate system to use, useful when there are multiple polar coordinate systems in a single chart instance.
    polar_index: types.Optional[types.Numeric] = None,
    
    # The index of the geographic coordinate system to use, useful if there are multiple geographic coordinate systems in a single chart instance.
    geo_index: types.Optional[types.Numeric] = None, # The index of the calendar coordinate system used, useful when there are multiple geographic coordinate systems in a single chart instance.
    
    # The index of the calendar coordinate system used, useful when there are multiple calendar coordinate systems in a single chart instance.
    calendar_index: types.Optional[types.Numeric] = None, # The index of the calendar coordinate system used.
    
    # If series.data is not specified and dataset exists, then dataset is used. datasetIndex specifies which dataset is used for this series.
    dataset_index: types.Optional[types.Numeric] = None,

    # The series label colour
    color: Optional[str] = None,
    
    # The strategy for taking colours from the palette option.color, can take values:
    # 'series': assign colours in the palette by series, all data in the same series is in the same colour;
    # 'data': assign colours in the palette by data item, with each data item using a different colour.
    colour_by: types.Optional[str] = None,.
    
    # Whether to enable linkage highlighting for legend hover.
    is_legend_hover_link: bool = True, # Configure when the effect is displayed.
    
    # Configure when to show the effect.
    # Optional: 'render' Show effect after drawing is complete.' emphasis' Show effect on highlight.
    show_effect_on: str = "render", # The coordinate system used by the series.
    
    # The coordinate system used by the series, optional:
    # 'cartesian2d': use a 2D Cartesian coordinate system (also known as Cartesian coordinate system), specify the corresponding axis components via xAxisIndex, yAxisIndex.
    # 'polar': use the polar coordinate system, specify the corresponding polar component by polarIndex
    # 'geo': use a geographic coordinate system, specify the corresponding geographic component via geoIndex.
    # 'calendar': use the calendar coordinate system, specify the corresponding calendar component via calendarIndex.
    coordinate_system: str = "cartesian2d",

    # The shape of the labeled graph
    symbol: Optional[str] = None,

    # The size of the marker
    symbol_size: Numeric = 10,

    # The angle of rotation of the marker. Note that symbolRotate is ignored in markLine when symbol is 'arrow' and is forced to be set to the angle of the tangent.
    symbol_rotate: types.Optional[types.Numeric] = None,
    
    # The configuration of the check mode, it indicates whether to support multiple selections or not, default is off, support boolean value and string.
    # String value can be 'single', 'multiple', 'series' for single selection, multiple selection and whole series selection respectively.
    selected_mode: types.Union[bool, str] = False,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Ripple effect configuration items, see `series_options.EffectOpts`
    effect_opts: Union[opts.EffectOpts, dict] = opts.EffectOpts(), # effect_opts: Union[opts.EffectOpts, dict] = opts,

    # Tipbox component configuration items, see `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
    
    # Markpoint configuration items, refer to `series_options.MarkPointOpts`.
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None, `series_options.MarkLineOpts`, refer to `series_options.

    # Marker line configuration items, refer to `series_options.MarkLineOpts`.
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None, # Chart marking fields, refer to `series_options.MarkLineOpts`.
    
    # Chart marking area, often used to mark a range of data in a chart, see `series_options.MarkAreaOpts`.
    markarea_opts: types.MarkArea = None, # The zlevel value of all graphs.
    
    # zlevel values for all graphs.
    z_level: types.Numeric = 0, # zlevel value for all graphs of the component.

    # The z-value of all graphics of the component. Controls the order of graphics before and after.
    # Graphics with small z-values are overwritten by graphics with large z-values.
    # z has a lower priority than zlevel and no new Canvas is created.
    z: types.Numeric = 2,
    
    # You can define which dimension of data is encoded as what.
    encode: types.Union[types.JSFunc, dict, None] = None,
)
```

### EffectScatterItem: ripple effects scatter plot data item

```python
class EffectScatterItem(
    ### Name of the data item.
    name: Union[str, Numeric] = None,

    # The value of the data item
    value: Union[str, Numeric] = None,

    # The graph of a single data token.
    symbol: Optional[str] = None,

    # The size of a single data token
    symbol_size: Union[Sequence[Numeric], Numeric] = None,

    # The rotation angle (not radians) of a single data token.
    symbol_rotate: Optional[Numeric] = None,

    # If the symbol is of the form path://, whether to keep the aspect ratio of the graph when scaling.
    symbol_keep_aspect: bool = False,

    # The offset of a single data marker relative to its original position.
    symbol_offset: Optional[Sequence] = None,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/EffectScatter/README)


## HeatMap: Heat map

> *class pyecharts.charts.HeatMap(RectChart)*

```python
class HeatMap(
    # Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.HeatMap.add_yaxis*

``` python
def add_yaxis(
    # Series name for tooltip display, legend filtering for legends.
    series_name: str,

    # Y-coordinate axis data
    yaxis_data: types.Sequence[types.Union[opts.HeatMapItem, dict]],

    # Series data items
    value: types.Sequence[types.Union[opts.HeatMapItem, dict]],
    
    # The coordinate system used by the series, optional:
    # 'cartesian2d': use a 2D Cartesian coordinate system (also known as Cartesian coordinate system), specify the corresponding axis components via xAxisIndex, yAxisIndex.
    # 'geo': Use a geographic coordinate system, specify the geographic component by geoIndex.
    # 'calendar': use the calendar coordinate system, specify the corresponding calendar component by calendarIndex.
    coordinate_system: str = "cartesian2d",

    # The index of the x-axis to use, useful if there are multiple x-axes in a single chart instance.
    xaxis_index: Optional[Numeric] = None,

    # The index of the y-axis to use, useful if there are multiple y-axes in a single instance of the chart.
    yaxis_index: Optional[Numeric] = None,
    
    # The index of the geographic coordinate system to use, useful when there are multiple geographic coordinate systems in a single chart instance.
    geo_index: types.Optional[types.Numeric] = None,
    
    # The index of the calendar coordinate system used, useful when there are multiple calendar coordinate systems in a single chart instance.
    calendar_index: types.Optional[types.Numeric] = None, # The index of the calendar coordinate system used.
    
    # If series.data is not specified and dataset exists, then dataset is used.
    # datasetIndex Specifies which dataset to use for this series.
    dataset_index: types.Optional[types.Numeric] = None, # dataset_index: types.
    
    # point_size The size of each point, valid on the geographic coordinate system (coordinateSystem: 'geo').
    point_size: types.Optional[types.Numeric] = None, # The size of each point blur, valid on the geographic coordinate system (coordinateSystem: 'geo').
    
    # The size of each point blur, valid on the geographic coordinate system (coordinateSystem: 'geo').
    blur_size: types.Optional[types.Numeric] = None,.
    
    # Minimum transparency, valid on geographic coordinate system (coordinateSystem: 'geo').
    min_opacity: types.Optional[types.Numeric] = None, # The minimum transparency, valid on the geographic coordinate system (coordinateSystem: 'geo').
    
    # Maximum transparency, valid on the geographic coordinate system (coordinateSystem: 'geo').
    max_opacity: types.Optional[types.Numeric] = None, # Maximum transparency, valid on geographic coordinate system (coordinateSystem: 'geo').

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Markpoint configuration items, see `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # Marking line configuration items, see `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,
    
    # Chart markarea, often used to mark a range of data in a chart, see `series_options.MarkAreaOpts`.
    markarea_opts: types.MarkArea = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
    
    # The configuration of the check mode, it indicates whether to support multiple selections or not, default is off, support boolean value and string.
    # String value can be 'single', 'multiple', 'series' for single selection, multiple selection and whole series selection respectively.
    selected_mode: types.
    
    # The zlevel value of all graphs in the heatmap.
    z_level: types.Numeric = 0, # The zlevel value for all graphs of the heatmap component. z_level: types.
    
    # zlevel value for all graphs of the heat map component. Controls the order of the graphs before and after. graphs with a small z-value are overwritten by graphs with a large z-value.
    z: types.Numeric = 2, # The z value of the heatmap component.
    
    # Allows you to define which dimension of data is encoded as what.
    encode: types.Union[types.JSFunc, dict, None] = None, # You can define which dimension the data is encoded into.
)
```

### HeatMapItem: heat map data item

``` python
class HeatMapItem(
    ### Name of the data item.
    name: Optional[str] = None,
    
    ### The value of the data item.
    value: Optional[Sequence] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Heatmap/README)

## Kline/Candlestick: K-line charts

> *class pyecharts.charts.Kline(RectChart)*

```python
class Kline(
    # Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Kline.add_yaxis*

```python
def add_yaxis(
    # Series name for display of tooltip, legend filter for legend.
    series_name: str,

    # series data
    y_axis: types.Sequence[types.Union[opts.CandleStickItem, dict]],
    
    # The coordinate system used by the series, optional:
    # 'cartesian2d': use a 2D Cartesian coordinate system (also known as Cartesian coordinate system), specify the corresponding axis components via xAxisIndex, yAxisIndex.
    coordinate_system: str = "cartesian2d",

    # The strategy for taking colours from the palette option.colour, which can take the values.
    # 'series': assign the colours in the palette according to series, all data in the same series are in the same colour.
    # 'data': assigns the colours in the palette by data item, with each data item using a different colour.
    color_by: types.Optional[str] = "series",
    
    # Specifies the column width. Either an absolute value (e.g. 10) or a percentage (e.g. '20%' for what percent of the band width) can be used. 
    # The default is adaptive.
    bar_width: types.Optional[types.Numeric] = None,
    
    # Specifies the minimum width of the column. Either an absolute value (e.g. 10) or a percentage (e.g. '20%' for what percent of the band width) can be used. Default is adaptive.
    bar_min_width: types.Optional[types.Numeric] = None,
    
    # Specifies the maximum width of the bar. Can be used as an absolute value (e.g. 10) or as a percentage (e.g. '20%' for what percent of the band width). Default is adaptive.
    bar_max_width: types.Optional[types.Numeric] = None, # Specify the bar maximum width.
    
    # Layout style, optional values.
    # 'horizontal': horizontal layout of individual boxes.
    # 'vertical': vertical layout of the boxes.
    # The default value is determined by the current coordinate system: if the category axis is horizontal, then horizontal.
    # otherwise vertical; if there is no category axis then horizontal.
    layout: types.Optional[str] = None,

    # The index of the x-axis to use, useful if there are multiple x-axes in a single chart instance.
    xaxis_index: Optional[Numeric] = None,

    # The index of the y-axis to use, useful if there are multiple y-axes in a single instance of the chart.
    yaxis_index: Optional[Numeric] = None,
    
    # Whether or not to enable linkage highlighting for legend hover.
    is_legend_hover_link: bool = True,
    
    # Whether to enable hover animation on the box.
    is_hover_animation: bool = True, # Whether to enable hover animation on box.

    # Mark line configuration items, see `series_options.MarkLineOpts`
    markline_opts: types.MarkLine = None,

    # Markpoint configuration items, see `series_options.MarkPointOpts`
    markpoint_opts: types.MarkPoint = None, 
    
    # Chart markarea, often used to mark a range of data in a chart, see `series_options.MarkAreaOpts`.
    markarea_opts: types.MarkArea = None,
    
    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
    
    # The configuration of the check mode, it indicates whether to support multiple selections or not, default is off, support boolean value and string.
    # String value can be 'single', 'multiple', 'series' for single selection, multiple selection and whole series selection respectively.
    selected_mode: types.Union[bool, str] = False,
    
    # Whether or not to enable large data volume optimisation, can be enabled when the data graph is particularly large and lags.
    is_large: bool = False, # Whether to enable large data volume optimisation.
    
    # Define what dimension of the data is encoded into what.
    encode: types.Union[types.JSFunc, dict, None] = None, # Whether to crop beyond the coordinate system.
    
    # Whether or not to crop the graph beyond the coordinate system, depending on the series:
    # K-Line: ignore graphs that are out of the coordinate system as a whole, but do not clip individual graphs.
    is_clip: bool = True, # If or not all graphs in the K-chart are out of the coordinate system, but not individual graphs.
    
    # The zlevel value of all shapes in the K-line chart.
    z_level: types.Numeric = 0, # The zlevel of all graphs of the K-line chart component.
    
    # The zlevel value for all graphs of the K-Line Chart component. Controls the order of the graphs before and after each other. graphs with small z-values will be overwritten by graphs with large z-values.
    z: types.Numeric = 2, # The z value of all graphs in the K-Line Chart component.
)
```

### CandleStickItem: K line chart data item

```python
class CandleStickItem(
    ### Name of the data item.
    name: Optional[str] = None,
    
    # The value of the data item.
    value: Optional[Sequence] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Candlestick/README)


## Line: fold/area chart

> *class pyecharts.charts.Line(RectChart)*

```python
class Line(
    ## Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Line.add_yaxis*

``` python
def add_yaxis(
    # Series name for tooltip display, legend filtering for legends.
    series_name: str,

    # series data
    y_axis: types.Sequence[types.Union[opts.LineItem, dict]],

    # Whether to connect to empty data, use `None` to fill in the empty data
    is_connect_nones: bool = False,

    # The index of the x-axis to use, useful if there are multiple x-axes in a single chart instance.
    xaxis_index: Optional[Numeric] = None,

    # The index of the y-axis to use, useful if there are multiple y-axes in a single instance of the chart.
    yaxis_index: Optional[Numeric] = None,
    
    # The index of the polar coordinate system to use, useful when there are multiple polar coordinate systems in a single chart instance.
    polar_index: types.Optional[types.Numeric] = None,.
    
    # The coordinate system to use for the series, optional:
    # 'cartesian2d': use a 2D Cartesian coordinate system (also known as Cartesian coordinate system), specify the corresponding axis components via xAxisIndex, yAxisIndex.
    # 'polar': use the polar coordinate system, specify the corresponding polar component by polarIndex
    coordinate_system: types.Optional[str] = None,
    
    # The strategy for taking colours from the palette option.color, can take values:
    # 'series': assign colours in the palette by series, all data in the same series is in the same colour;
    # 'data': assign colours in the palette by data item, with each data item using a different colour.
    color_by: types.Optional[str] = None,

    # The series label colour
    color: Optional[str] = None,

    # Whether to show symbol, if false it will only be shown when tooltip hover.
    is_symbol_show: bool = True,

    # The symbol's graphic.
    # The symbol types provided by ECharts are 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # The size of the marker, either as a single number such as 10, or as an array of separate widths and heights.
    # For example [20, 10] means that the symbol is 20 wide and 10 high.
    symbol_size: Union[Numeric, Sequence] = 4,

    # Data stacking, where stack values with the same series configuration on the same class axis can be stacked.
    stack: Optional[str] = None,
    
    # The strategy for stacking values, provided the stack attribute has been set. Its value can be:
    # 'samesign' Stack only if the value to be stacked has the same positive or negative sign as the current accumulated stacked value.
    # 'all' Stack all values, regardless of the positive or negative sign of the current or accumulated stacked values.
    # 'positive' Stack only positive values.
    # 'negative' Stack only negative values.
    stack_strategy: types.Optional[str] = "samesign",

    # Whether to smooth the curve
    is_smooth: bool = False,
    
    # Whether to crop the graphs that are outside the coordinate system. fold: crop out all folded parts that are outside the coordinate system, the logic of the inflection point graph is treated as a scatter plot
    is_clip: bool = True,

    # Whether to display as a step diagram
    is_step: bool = False,
    
    # Whether to turn on hover's hint animation on the inflection marker
    is_hover_animation: bool = True,
    
    # The zlevel value for all shapes of the line graph.
    # zlevel is used for Canvas layering, where shapes with different zlevel values are placed in different Canvas, and Canvas layering is a common optimization tool.
    # Canvas with larger zlevels are placed on top of Canvas with smaller zlevels.
    z_level: types.Numeric = 0,
    
    # The z value of all the shapes of the Line Chart component. Controls the order of the shapes before and after them. zLesser shapes will be overwritten by larger ones.
    # z has lower priority than zlevel and no new Canvas is created.
    z: types.Numeric = 0,
    
    # A downsampling strategy for line charts when the amount of data is much larger than the number of pixel points. Turned on to optimise the efficiency of the chart, off by default, i.e. all plotted without filtering data points.
    # Optional.
    # 'lttb' Takes the Largest-Triangle-Three-Bucket algorithm, which maximises the trend, shape and extreme values of the sampled lines.
    # 'average' takes the average of the filtered points
    # 'max' takes the maximum value of the filter points
    # 'min' takes the minimum value of the filter points
    # 'sum' takes the sum of the filter points
    sampling: types.Optional[str] = None,
    
    # Use dimensions to define information about each dimension of series.data or dataset.source.
    # Note: If a dataset is used, then the dimension name can be given in the first row/column of the dataset.source.
    # So there is no need to specify the dimension here.
    # However, if dimensions are specified here, then ECharts will no longer automatically get the dimension information from the first row/column of dataset.source.
    dimensions: types.Union[types.Sequence, None] = None,

    # When using a dataset, seriesLayoutBy specifies whether rows or columns in the dataset correspond to the series, i.e. whether the series is "laid out" on the rows or columns of the dataset. Possible values.
    # 'column': by default, the columns of the dataset correspond to the series, so that each column in the dataset is a dimension.
    # 'row': the row of the dataset corresponds to the series, so that each row in the dataset is a dimension.
    series_layout_by: str = "column",

    # Markpoint configuration items, see `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # Marking line configuration items, see `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,
    
    # Chart markarea, often used to mark a range of data in a chart, see `series_options.MarkAreaOpts`.
    markarea_opts: types.MarkArea = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Line style configuration items, see `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(),

    # Fill area configuration items, see `series_options.AreaStyleOpts`
    areastyle_opts: Union[opts.AreaStyleOpts, dict] = opts,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # You can define which dimension of data is encoded as what.
    encode: types.Union[types.JSFunc, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### LineItem: line graph data item

```python
class LineItem(
    ### Name of the data item.
    name: Union[str, Numeric] = None,

    ### The value of the data item
    value: Union[str, Numeric] = None,

    # The graph of a single data marker.
    symbol: Optional[str] = None,

    # The size of a single data token
    symbol_size: Union[Sequence[Numeric], Numeric] = None,

    # The rotation angle (not radians) of a single data token.
    symbol_rotate: Optional[Numeric] = None,

    # If the symbol is of the form path://, whether to keep the aspect ratio of the graph when scaling.
    symbol_keep_aspect: bool = False,

    # The offset of a single data marker relative to its original position.
    symbol_offset: Optional[Sequence] = None,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Line/README)


## PictorialBar: pictorial bar

> *class pyecharts.charts.PictorialBar(RectChart)*

```python
class PictorialBar(
    # Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.PictorialBar.add_yaxis*

``` python
def add_yaxis(
    # Series name for tooltip display, legend filtering for legends.
    series_name: str,

    # series data
    y_axis: Sequence,

    # The graph type.
    # The marker types provided by ECharts are 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url' where URL is the link to the image, or dataURI.
    # URL is a link to the image e.g. 'image://http://xxx.xxx.xxx/a/b.png'
    # URL is the dataURI e.g. 'image://data:image/gif;base64,R0lGODlhEAAQAMQAAORHHOVSKudfO...'
    # Icons can be set to an arbitrary vector path using 'path://'. This way you don't have to worry about jaggedness or blurring due to scaling, compared to using images.
    # And it can be set to any colour. The path graphic adapts itself to the right size. See SVG PathData for the format of paths.
    # Can be edited and exported from tools such as Adobe Illustrator. For example.
    # 'path://M30.9,53.2C16.8,53.2,5.3,41.7,5.3,27.6S16.8,2,30.9,2C45,2,56.4,13.5,56.4,2...'
    symbol: Optional[str] = None,

    # The size of the graph.
    # The width and height can be separated by an array, e.g. [20, 10] means the symbol is 20 wide and
    # Height is 10, or can be set to a single number such as 10 for [10, 10].
    # can be set to an absolute value (e.g. 10) or to a percentage (e.g. '120%', ['55%', 23]).
    symbol_size: Union[Numeric, Sequence, None] = None,

    # Position of the graph. Possible values.
    # 'start': inner tangent of the edge of the graph to the start of the column.
    # 'end': graph edge tangent to where the column ends.
    # 'centre': the graph is centred within the column.
    symbol_pos: Optional[str] = None,

    # The offset of the graph relative to its original position. symbolOffset is the last calculated step in the positioning of the graph.
    # The calculated position of the graph can be fine-tuned.
    # Can be set to an absolute value (e.g. 10) or to a percentage (e.g. '120%', ['55%', 23]).
    # When set to a percentage, indicates the percentage relative to its own size symbolSize.
    # For example [0, '-50%'] is moving the graphic up by half of its own size.
    symbol_offset: Optional[Sequence] = None,

    # The rotation angle of the graph.
    # Note that symbolRotate does not affect the positioning of the graph (even beyond the boundary of the reference column), but simply rotates it around its own centre.
    # This property can be set at the root of the series, indicating that it is valid for all data in the series.
    # It can also be set to each data item in the data, meaning that it only takes effect for this data item.
    symbol_rotate: Optional[Numeric] = None,

    # Specifies whether the graphical element is repeated. Values can be.
    # false/null/undefined: does not repeat, i.e. each data value is represented by one graphical element.
    # true: makes the graphical elements repetitive, i.e. each data value is represented by a set of repeated graphical elements. The number of repetitions is calculated from the data.
    # a number: makes the graphical element repeat, i.e. each data value is represented by a set of repeated graphical elements. The number of repetitions is given as a fixed value.
    # 'fixed': Repeats the graphical elements, i.e. each data value is represented by a set of repeated graphical elements.
    # The number of repetitions is calculated based on symbolBoundingData, i.e. independent of data. This is useful when the graph is used as a background.
    symbol_repeat: Optional[str] = None,

    # Specifies the order in which graphic elements are drawn when they are repeated. This property is useful in two cases.
    # When symbolMargin is set to a negative value, duplicate graphics will overwrite each other, this is where you can use symbolRepeatDirection to specify the order of overwriting.
    # When animationDelay or animationDelayUpdate is used, symbolRepeatDirection specifies the index order.
    # The value of this attribute can be: 'start' or 'end'.
    symbol_repeat_direction: Optional[str] = None,

    # The distance between the sides of the graph ('sides' means both sides of the direction of its numeric axis). This can be an absolute value (e.g. 20), or a percentage value (e.g. '-30%').
    # indicates the percentage relative to its own size symbolSize. Only meaningful if symbolRepeat is used.
    # can be a positive value, indicating a large interval, or a negative number. When symbolRepeat is used, a negative number overlaps the graph.
    # Can have a "!" at the end of its value , e.g. "30%!" or 25! to indicate that the beginning of the first figure and the end of the last figure are left blank.
    # Does not fit snugly on the border. The default will be tightly bounded.
    symbol_margin: Union[Numeric, str, None] = None,

    # Whether or not to trim the figure.
    # false/null/undefined: the graph itself represents the size of the value.
    # true: The remaining part of the graph after it has been clipped represents the numeric size.
    # symbolClip is often used in this scenario: to express both 'total value' and 'current value'. In this scenario, two series can be used.
    # One series is the complete figure, used as a 'background' to express the total value, and the other series is the figure cropped using symbolClip to express the current value.
    is_symbol_clip: bool = False,

    # Whether the legend is selected or not
    is_selected: bool = True,

    # The index of the x-axis to use, useful if there are multiple x-axes in a single chart instance.
    xaxis_index: Optional[Numeric] = None,

    # The index of the y-axis to use, useful if there are multiple y-axes in a single instance of the chart.
    yaxis_index: Optional[Numeric] = None,

    # The series label colour
    color: Optional[str] = None,

    # The distance between columns in the same series, default is 20% of the category spacing, can be set to a fixed value
    category_gap: Union[Numeric, str] = "20%",

    # The distance between columns for different series, as a percentage (e.g. '30%' for 30% of the column width).
    # If you want the columns of two series to overlap, you can set the gap to '-100%'. This is useful when using the columns as a background.
    gap: Optional[str] = None,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Markpoint configuration items, see `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # Marking line configuration items, see `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None, # tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # You can define which dimension of data is encoded as what.
    encode: types.Union[types.JsCode, dict] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```


### Demo

[gallery example](http://gallery.pyecharts.org/#/PictorialBar/README)


## Scatter: scatter plot

> *class pyecharts.charts.Scatter(RectChart)*

```python
class Scatter(
    ## Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Scatter.add_yaxis*

``` python
def add_yaxis(
    # Series name for display of tooltip, legend filter for legend.
    series_name: str,

    # series data
    y_axis: Sequence,

    # whether the legend is selected or not
    is_selected: bool = True,

    # The index of the x-axis to use, useful if there are multiple x-axes in a single chart instance.
    xaxis_index: Optional[Numeric] = None,

    # The index of the y-axis to use, useful if there are multiple y-axes in a single instance of the chart.
    yaxis_index: Optional[Numeric] = None,

    # The series label colour
    color: Optional[str] = None,

    # The graph of the label.
    # The types of labels provided by ECharts include 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # The size of the marker, either as a single number such as 10, or as an array of separate widths and heights.
    # For example [20, 10] means that the symbol is 20 wide and 10 high.
    symbol_size: Numeric = 10,
    
    # The rotation angle of the marker. Note that symbolRotate is ignored in markLine when symbol is 'arrow' and is forced to be set to the angle of the tangent.
    symbol_rotate: types.Optional[types.Numeric] = None,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(position="right"),

    # Markpoint configuration items, see `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # Marking line configuration items, see `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # Chart marker fields, often used to mark a range of data in a chart, see `series_options.MarkAreaOpts`
    markarea_opts: types.MarkArea = None,

    # Tipbox component configuration items, see `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # You can define which dimension of data is encoded as what.
    encode: types.Union[types.JSFunc, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### ScatterItem: scatter plot data item

``` python
class ScatterItem(
    ### Name of the data item.
    name: Union[str, Numeric] = None,

    # The value of the data item.
    value: Union[str, Numeric] = None,

    # The graph of a single data token.
    # The types of markers provided by ECharts include 
    # 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    # The icon can be set to any vector path via 'path://'.
    symbol: Optional[str] = None,

    # The size of a single data token, which can be set to a single number such as 10
    # The width and height can also be separated by an array, e.g. [20, 10] means the marker is 20 wide and 10 high.
    symbol_size: Union[Sequence[Numeric], Numeric] = None,

    # The rotation angle (not radians) of a single data token. Positive
    symbol_rotate: Optional[Numeric] = None,

    # If the symbol is of the form path://, whether to keep the aspect ratio of the figure when scaling.
    symbol_keep_aspect: bool = False,

    # The offset of a single data marker relative to its original position.
    symbol_offset: Optional[Sequence] = None,

    # Label configuration items, refer to `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Scatter/README)

## Overlap: cascading multiple images

### Demo

[gallery example](http://gallery.pyecharts.org/#/Overlap/README)
