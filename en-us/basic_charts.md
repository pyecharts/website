## Calendar: calendar chart

> *class pyecharts.charts.Calendar*

```python
class Calendar(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyeachrts.charts.Calendar.add*

``` python
def add(
    # Series name for display of tooltip, legend filter for legend.
    series_name: str,

    # Series data in the format [(date1, value1), (date2, value2), ...]
    yaxis_data: Sequence,
    
    # ChartType composite type, default `ChartType.HEATMAP`
    type_: types.Union[str, ChartType]
    
    # Whether the legend is selected
    is_selected: bool = True,
    
    # Calendar chart index
    calendar_index: types.Optional[types.Numeric] = None,

    # Label configuration items, see `series_options.
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Calendar coordinate system component configuration items, see `CalendarOpts`
    calendar_opts: Union[opts.CalendarOpts, dict, None] = None,

    # Tipbox component configuration items, see `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Data mapping configuration items, see `global_options.VisualMapOpts`
    visualmap_opts: types.VisualMap = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### CalendarOpts: calendar coordinate system component configuration item

> *class pyecharts.options.CalendarOpts*

``` python
class CalendarOpts(
    # The distance of the calendar component from the left side of the container.
    # The value of left can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'left', 'center', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: Optional[str] = None,

    # The distance of the calendar component from the top side of the container.
    # The value of top can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Optional[str] = None,

    # The distance of the calendar component from the right side of the container.
    # The value of right can be a specific pixel value like 20, and can be a percentage relative to the container height and width like '20%'.
    # Adaptive by default.
    pos_right: Optional[str] = None,

    # The distance of the calendar component from the lower side of the container.
    # The value of bottom can be a specific pixel value like 20, or a percentage relative to the container's height and width like '20%'.
    # Adaptive by default.
    pos_bottom: Optional[str] = None,

    # The layout orientation of the calendar coordinates. Optional.
    # 'horizontal', 'vertical'
    orient: Optional[str] = None,
    # Mandatory, range of calendar coordinates Multiple formats are supported, usage examples.
    # A year range: 2017
    # A month range: '2017-02'
    # Some interval range: ['2017-01-02', '2017-02-23']
    # Note This writeup will be recognized as ['2017-01-01', '2017-02-01']
    # range: ['2017-01', '2017-02']
    range_: Union[str, Sequence, int] = None,

    # Style of week axis, see `series_options.LabelOpts`
    daylabel_opts: Union[LabelOpts, dict, None] = None,

    # Styles for the month axis, see `series_options.LabelOpts`
    monthlabel_opts: Union[LabelOpts, dict, None] = None,

    # The style of the year, see `series_options.LabelOpts`
    yearlabel_opts: Union[LabelOpts, dict, None] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Calendar/README)


## Funnel: funnel chart

> *class pyecharts.charts.Funnel*

```python
class Funnel(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Funnel.add*

``` python
def add(
    # Series name for tooltip display, legend filtering for legends.
    series_name: str,

    # Series data items in the format [(key1, value1), (key2, value2)]
    data_pair: Sequence,

    # Whether the legend is selected or not
    is_selected: bool = True,

    # series label colour
    color: Optional[str] = None,

    # data sorting, can take 'ascending', 'descending', 'none' (means in order of data)
    sort_: str = "descending",

    # Data graph spacing
    gap: Numeric = 0,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Tipbox component configuration items, see `series_options.
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Funnel/README)


## Gauge: gauges

> *class pyecharts.charts.Gauge*

```python
class Gauge(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Gauge.add*

``` python
def add(
    # Series name for display of tooltip, legend filter for legend.
    series_name: str,

    # Series data items in the format [(key1, value1), (key2, value2)]
    data_pair: Sequence,

    # Whether the legend is selected or not
    is_selected: bool = True,

    # The smallest data value
    min_: Numeric = 0,

    # The maximum data value
    max_: Numeric = 100,

    # Average number of segments to split in the dashboard
    split_number: Numeric = 10,
    
    # The coordinates of the centre (centre of the circle) of the dashboard, the first item of the array is the horizontal coordinate and the second is the vertical coordinate.
    # Supports setting as a percentage, when setting the percentage the first term is relative to the container width and the second term is relative to the container height.
    centre: types.Sequence = None,

    # The radius of the dashboard, either as a percentage relative to the smaller half of the container height and width, or as an absolute value.
    radius: types.Union[types.Numeric, str] = "75%",

    # The starting angle of the dashboard. The centre of the circle is 0 degrees on the positive right-hand side, 90 degrees on the positive upper side and 180 degrees on the positive left-hand side.
    start_angle: Numeric = 225,

    # The end angle of the dashboard.
    end_angle: Numeric = -45,

    # Whether the dial scale is increasing clockwise.
    is_clock_wise: bool = True,
    
    # Configuration item for the title text item label within the wheel, see `chart_options.GaugeTitleOpts`
    title_label_opts: types.GaugeTitle = opts.GaugeTitleOpts(offset_center=["0%", "20%"]),
    
    # Data item label configuration items within the wheel, see `chart_options.GaugeDetailOpts`
    detail_label_opts: types.GaugeDetail = opts.GaugeDetailOpts(formatter="{value}%", offset_center=["0%", "40%"]),

    # Gauge progress configuration items, see `chart_options.GaugeProgressOpts`
    progress: types.GaugeProgress = opts.GaugeProgressOpts(),

    # Gauge pointer configuration items, see `chart_options.GaugePointerOpts`
    pointer: types.GaugePointer = opts.GaugePointerOpts(),
    
    # The anchor point of the pointer in the dashboard dial, see `chart_options.GaugeAnchorOpts`
    anchor: types.GaugeAnchor = opts.GaugeAnchorOpts(),

    # Tipbox component configuration items, see `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
    
    # Coordinate axis line configuration items, see `global_options.AxisLineOpts`
    axisline_opts: types.AxisLine = None,
    
    # Axis tick pointer style configuration items, see `global_options.AxisTickOpts`
    axistick_opts: types.AxisTick = None,
    
    # Axis tick label style configuration items, see `global_options.LabelOpts`
    axislabel_opts: types.AxisLabel = None,
    
    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### GaugeTitleOpts: dashboard data title configuration item

```python
class GaugeTitleOpts(
    ### Whether to show titles.
    is_show: bool = True,
       
    # The position of the offset relative to the centre of the gauge, the first item in the array is the horizontal offset, the second is the vertical offset.
    # Can be an absolute value or a percentage relative to the radius of the dashboard.
    offset_center: Sequence = None,
    
    # The colour of the text.
    colour: str = "#333",
    
    # The style of the text font.
    # Optional: 'normal', 'italic', 'oblique'
    font_style: str = "normal",
    
    # The thickness of the text font.
    # Optional: 'normal', 'bold', 'bolder', 'lighter', 100 | 200 | 300 | 400...
    font_weight: str = "normal",
    
    # The font family of the text.
    # Can be 'serif' , 'monospace', 'Arial', 'Courier New', 'Microsoft YaHei', ...
    font_family: str = "sans-serif",
    
    # The font size of the text.
    font_size: Numeric = 15,
    
    # The background colour of the text block.
    # Colour values can be used, e.g. '#123234', 'red', 'rgba(0,23,11,0.3)'.
    background_color: str = "transparent",
    
    # Text block border colour.
    border_color: str = "transparent",
    
    # The width of the text block border.
    border_width: Numeric = 0,
    
    # The rounded corners of the text block.
    border_radius: Numeric = 0,
    
    # The inner margin of the text block. Example.
    # padding: [3, 4, 5, 6]: indicates [top, right, bottom, left] margins.
    # padding: 4: means padding: [4, 4, 4, 4].
    # padding: [3, 4]: means padding: [3, 4, 3, 4].
    # Note that the width and height of the text block specify the content height and width, not the padding.
    padding: Numeric = 0,
    
    # The background shadow colour of the text block.
    shadow_color: Optional[str] = "transparent",
    
    # The length of the text block's background shadow.
    shadow_blur: Optional[Numeric] = 0,
    
    # The background shading x offset of the text block.
    shadow_offset_x: Numeric = 0,
    
    # The background shadow y offset of the text block.
    shadow_offset_y: Numeric = 0,
    
    # Whether to truncate or line break text out of width. Valid when width is configured
    # 'truncate' truncate and display ellipsis configured text at the end, default is...
    # 'break' line break
    # 'breakAll' line break, unlike 'break', 'breakAll' also forces an in-word line break in Latin languages such as English
    overflow: Optional[str] = "none",
    
    # Inside rich, rich text styles can be customised. With rich text styles, you can make very rich effects in your tags.
    rich: Optional[dict] = None,
    
    # Whether to enable numeric animation of the label.
    is_value_animation: bool = True,
)
```

### GaugeDetailOpts: dashboard data content configuration items

```python
class GaugeDetailOpts(
    ### Whether to display details.
    is_show: bool = True,

    # The text block background colour.
    # Can be a direct colour value, e.g. '#123234', 'red', 'rgba(0,23,11,0.3)'.
    background_color: str = "transparent",

    # The width of the text block border.
    border_width: Numeric = 0,

    # The colour of the text block border.
    border_color: str = "transparent",

    # The offset position relative to the centre of the dashboard, the first item in the array is the horizontal offset and the second is the vertical offset.
    # Can be an absolute value or a percentage relative to the radius of the dashboard.
    offset_center: Sequence = [0, "-40%"],

    # Formatting function or string
    formatter: Optional[JSFunc] = None,

    # The colour of the text.
    color: str = "auto",

    # The style of the text font. Optional: 'normal', 'italic', 'oblique'
    font_style: str = "normal",

    # The thickness of the text font. Optional: 'normal', 'bold', 'bolder', 'lighter', 100 | 200 | 300 | 400...
    font_weight: str = "normal",
    
    # The font family of the text. Can also be 'serif' , 'monospace', 'Arial', 'Courier New', 'Microsoft YaHei', ...
    font_family: str = "sans-serif",

    # The font size of the text
    font_size: Numeric = 15,

    # The rounded corners of the text block.
    border_radius: Numeric = 0,

    # The inner margin of the text block. Example.
    # padding: [3, 4, 5, 6]: indicates [top, right, bottom, left] margins.
    # padding: 4: means padding: [4, 4, 4, 4].
    # padding: [3, 4]: means padding: [3, 4, 3, 4].
    # Note that the width and height of the text block specify the content height and width, not the padding.
    padding: Numeric = 0,

    # The background shadow colour of the text block.
    shadow_color: Optional[str] = "transparent",

    # The length of the text block's background shadow.
    shadow_blur: Optional[Numeric] = 0,

    # The background shading x offset of the text block.
    shadow_offset_x: Numeric = 0,

    # The background shadow y offset of the text block.
    shadow_offset_y: Numeric = 0,
    
    # Whether to truncate or line break text out of width. Valid when width is configured
    # 'truncate' truncate and display ellipsis configured text at the end, default is...
    # 'break' line break
    # 'breakAll' line break, unlike 'break', 'breakAll' also forces an in-word line break in Latin languages such as English
    overflow: Optional[str] = "none",
    
    # Inside rich, rich text styles can be customised. With rich text styles, you can make very rich effects in your tags.
    rich: Optional[dict] = None,
    
    # Whether to enable numeric animation of the label.
    is_value_animation: bool = True,
)
```

### GaugeProgressOpts: dashboard progress configuration item

```python
class GaugeProgressOpts(
    ### Whether to show progress.
    is_show: bool = False,
    
    # Whether progress bars overlap when multiple sets of data are available.
    is_overlap: bool = True,
    
    # The width of the progress bar.
    width: Numeric = 10,
    
    # If or not the progress bar will be rounded at both ends.
    is_round_cap: bool = False,
    
    # Whether to crop out the excess.
    is_clip: bool = False,
    
    # The style of the progress bar.
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
)
```

### GaugePointerOpts: dashboard pointer configuration items

```python
class GaugePointerOpts(
    ### Whether to display the pointer.
    is_show: bool = True,
    
    # The length of the pointer, either as an absolute value or as a half-ratio relative to the radius.
    length: Union[str, Numeric] = "80%",

    # The width of the pointer.
    width: Numeric = 8,
)
```

### GaugeAnchorOpts: Gauge pointer fixed point configuration item

```python
class GaugeAnchorOpts(
    ### Show or not show fixed points.
    is_show: bool = True,
    
    # Whether or not the fixed point is shown above the pointer.
    is_show_above: bool = False,
    
    # The size of the fixed point.
    size: Numeric = 6,
    
    # ECharts provides marker types such as 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    # Icons can be set to any vector path via 'path://'.
    icon: str = "circle",
    
    # The offset position relative to the centre of the dashboard, the first item in the array is the horizontal offset and the second is the vertical offset. Can be an absolute value or a percentage relative to the radius of the dashboard.
    offset_center: Optional[Sequence] = None,
    
    # If the icon is of the form path://, whether to keep the aspect ratio of the graphic when scaling.
    is_keep_aspect: bool = False,
    
    # Pointer to keep the point style.
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
)
```


### Demo

[gallery example](http://gallery.pyecharts.org/#/Gauge/README)


## Graph: relational graphs

> *class pyecharts.charts.Graph*

```python
class Graph(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *class pyecharts.charts.Graph.add*

``` python
def add(
    # Series name for display of tooltip, legend filtering for legends.
    series_name: str,

    # List of data items for relational graph nodes, referencing ``opts.GraphNode`''
    nodes: Sequence[Union[opts.GraphNode, dict]],

    # List of relational data items between graph nodes, see `opts.GraphLink`
    links: Sequence[Union[opts.GraphLink, dict]],

    # A list of categories of relational graph node categories, see `opts.GraphCategory`
    categories: Union[Sequence[Union[opts.GraphCategory, dict]], None] = None,

    # Whether or not the legend is selected.
    is_selected: bool = True,

    # Whether to highlight nodes and their edges and neighbours when mousing over them.
    is_focusnode: bool = True,

    # Whether to enable mouse zoom and pan roaming.
    is_roam: bool = True,
    
    # Whether the node is draggable, only useful when using force-guided layout.
    is_draggable: bool = False,

    # Whether to rotate the label, not by default.
    is_rotate_label: bool = False,

    # The layout of the diagram. Optional.
    # 'none' uses no layout, using the x, y provided in the node as the position of the node.
    # 'circular' uses a circular layout.
    # 'force' uses a force-led layout.
    layout: str = "force",

    # The graphical representation of the relationship diagram node markup.
    # The markup types provided by ECharts include 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,
    
    # The size of the relational graph node symbols
    # Can be set to a single number such as 10
    # You can also use an array to separate the width and height, e.g. [20, 10] means the token is 20 wide and 10 high.
    symbol_size: types.Numeric = 10,

    # The distance between two nodes of an edge, this distance is also subject to repulsion.
    # Supports setting to an array to express the range of edge lengths, where values of different sizes are linearly mapped to different lengths. The smaller the value the longer the length.
    edge_length: Numeric = 50,

    # The gravitational factor towards the centre to which the node is subjected. The larger the value the closer the node is to the centre.
    gravity: Numeric = 0.2,
    
    # This parameter slows down the movement of the node. The range of values is 0 to 1.
    friction: Numeric = 0.6,
    
    # Because the force-guided layout will stabilise after several iterations, this parameter determines whether to show the iterative animation of the layout
    # It is not recommended to turn it off when there is a lot of node data on the browser side (>100), the layout process can cause a false browser death.
    is_layout_animation: bool = True,

    # The repulsion factor between nodes.
    # Supports setting to an array to express the range of repulsive forces, where different values of different sizes will map linearly to different repulsive forces. The larger the value the greater the repulsion
    repulsion: Numeric = 50,

     # Label configuration for Graph graph node edges (i.e. configuration to display data or labels on edges)
    edge_label: types.Label = None,

    # The type of label for each end of the edge, either an array specifying each end, or a single unified one.
    # No markers are displayed by default, common ones can be set to arrows as follows: edgeSymbol: ['circle', 'arrow']
    edge_symbol: Optional[str] = None,
    
    # The size of the tokens at each end of the edge, either an array specifying each end separately or a single uniform one.
    edge_symbol_size: Numeric = 10,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # The common line style for the relationship edge.
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### GraphNode: node data items for relational graphs

> *class pyecharts.options.GraphNode*

``` python
class GraphNode(
    ### The name of the data item.
    name: Optional[str] = None,

    # The initial x-value of the node. When not specified, the layout attribute needs to be specified to select the layout method.
    x: Optional[Numeric] = None,

    # The initial y value of the node. When not specified, the layout attribute needs to be specified to select the layout method.
    y: Optional[Numeric] = None,

    # Whether the node is fixed in the force-guided layout.
    is_fixed: bool = False,

    # The value of the data item.
    value: Union[str, Sequence, None] = None,

    # The index of the category in which the data item is located.
    category: Optional[int] = None,

    # The graph that the node in this category is tagged with.
    # The types of markers provided by ECharts include 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # The size of the node marker for this category, either as a single number such as 10, or as an array of separate widths and heights.
    # For example, [20, 10] means the marker is 20 wide and 10 high.
    symbol_size: Union[Numeric, Sequence, None] = None,
    
    # The rotation angle (not radians) of the node marker. Positive values indicate counterclockwise rotation.
    # Note that symbolRotate is ignored in markLine when symbol is 'arrow' forcing the angle to be tangent.
    symbol_rotate: Optional[int] = None, # symbol_rotate: Optional[int] = None, # symbol_rotate.
    
    # Item style opts, see `series_options.ItemStyleOpts`.
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None, # Item style configuration item, refer to `series_options.ItemStyleOpts`.

    # Label configuration items, refer to `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,
    
    # Whether to turn off the highlighting state.
    # Turn off highlighting to stop it being triggered when the mouse is over the graph, when the tooltip is triggered, or when the legend is linked.
    # Turn it off when there are a lot of graphics to improve the smoothness of the interaction.
    is_disabled_emphasis: Optional[bool] = None, # The style of the highlighted element.
    
    # Item style options for highlighting, see `series_options.ItemStyleOpts`.
    emphasis_itemstyle_opts: Union[ItemStyleOpts, dict, None] = None, # Highlighted label configuration items, refer to `series_options.ItemStyleOpts`.
    
    # Highlighted label options, see `series_options.LabelOpts`.
    emphasis_label_opts: Union[LabelOpts, dict, None] = None, # highlighted label configuration items, refer to `series_options.LabelOpts`, refer to `series_options.
    
    # Faded item style options, see `series_options.ItemStyleOpts`.
    blur_itemstyle_opts: Union[ItemStyleOpts, dict, None] = None, # Faded item style configuration items, refer to `series_options.ItemStyleOpts`.
    
    # Faded label options, see `series_options.LabelOpts`.
    blur_label_opts: Union[LabelOpts, dict, None] = None,.
    
    # Whether or not it can be selected. Valid when selectedMode is turned on and can be used to turn off some data.
    is_disabled_select: Optional[bool] = None, # The selected data can be used to turn off some of the data.
    
    # The selected item style options, see `series_options.ItemStyleOpts`.
    select_itemstyle_opts: Union[ItemStyleOpts, dict, None] = None, # Selected item style configuration items, refer to `series_options.ItemStyleOpts`.
    
    # Selected label options, see `series_options.LabelOpts`.
    select_label_opts: Union[LabelOpts, dict, None] = None, # Selected label configuration items, refer to `series_options.LabelOpts`.
    
    # Tip box component configuration item, see `series_options.TooltipOpts`.
    tooltip_opts: Union[TooltipOpts, dict, None] = None, # The configuration item for the tip box component, see `series_options.TooltipOpts`.
)
```

### GraphLink: relational data between nodes

> *class pyecharts.options.GraphLink*

``` python
class GraphLink(
    ### String for the name of the source node of the edge, also supports using numbers for the index of the source node.
    source: Union[str, int, None] = None,

    # String of the name of the target node of the edge, also supports using numbers for the index of the source node.
    target: Union[str, int, None] = None,

    # The value of the edge, which can be used to map to the length of the edge in a force-guided layout.
    value: Optional[Numeric] = None,

    # The type of token at each end of the edge, either an array specifying each end separately, or a single unified one.
    symbol: Union[str, Sequence, None] = None,

    # The size of the tokens at each end of the side, either as an array specifying each end, or as a single unified token.
    symbol_size: Union[Numeric, Sequence, None] = None,

    # The line style of the relationship edge, see `series_options.LineStyleOpts`
    linestyle_opts: Optional[LineStyleOpts] = None,

    # Label styles, refer to `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,
    
    # Whether to turn off the highlighting state.
    # Turn off highlighting to stop it being triggered when the mouse is over the graph, when the tooltip is triggered, or when the legend is linked.
    # Turn it off when there are a lot of graphics to improve the smoothness of the interaction.
    is_disabled_emphasis: Optional[bool] = None, # The style of the highlighted element.
    
    # Line style options for highlighting, see `series_options.LineStyleOpts`.
    emphasis_linestyle_opts: Union[LineStyleOpts, dict, None] = None, # Line style configuration items for highlighting, refer to `series_options.LineStyleOpts`.
    
    # Highlighted label opts, see `series_options.LabelOpts`.
    emphasis_label_opts: Union[LabelOpts, dict, None] = None, # The line style configuration item for fading, refer to `series_options.LabelOpts`.
    
    # Faded line style options, see `series_options.LineStyleOpts`.
    blur_linestyle_opts: Union[LineStyleOpts, dict, None] = None, # Fading line style configuration items, refer to `series_options.LineStyleOpts`.
    
    # Faded label opts, see `series_options.LabelOpts`.
    blur_label_opts: Union[LabelOpts, dict, None] = None, # The blur label configuration item.
    
    # Whether or not it can be selected. Valid when selectedMode is turned on and can be used to turn off some data.
    is_disabled_select: Optional[bool] = None,.
    
    # Selected line style options, see `series_options.LineStyleOpts`.
    select_linestyle_opts: union[LineStyleOpts, dict, None] = None, # Selected line configuration items, ref.
    
    # Selected label options, see `series_options.LabelOpts`.
    select_label_opts: Union[LabelOpts, dict, None] = None, # select_label_opts: Union[LabelOpts, dict, None] = None, # select_label_opts.
    
    # Make this edge not perform force guide layout calculations.
    is_ignore_force_layout: bool = False,
)
```

### GraphCategory: class of node categories

> *class pyecharts.options.GraphCategory*

``` python
class GraphCategory(
    ## Category name, used to correspond to legend and to format the content of tooltip.
    name: Optional[str] = None,

    # The graph tagged by this category node.
    # The types of markers provided by ECharts are 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # The size of the node marker for this category, either as a single number such as 10, or as an array of separate widths and heights.
    # For example, [20, 10] means the marker is 20 wide and 10 high.
    symbol_size: Union[Numeric, Sequence, None] = None,

    # # Label styles, see `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Graph/README)

## Liquid: water balloon chart

> *class pyecharts.charts.Liquid*

```python
class Liquid(
    ## Initialize configuration items, refer to ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Liquid.add*

``` python
def add(
    # series name for tooltip display, legend filtering for legends.
    series_name: str,

    # series data, in the format [value1, value2, ....]
    data: Sequence,

    # The shape of the water sphere, with 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow' options.
    # Default 'circle'. Can also be a custom SVG path.
    shape: str = "circle",

    # The color of the wave.
    color: Optional[Sequence[str]] = None,

    # Background color
    background_color: types.Union[str, dict, None] = None,

    # If or not show the wave animation.
    is_animation: bool = True,

    # If or not show the border.
    is_outline_show: bool = True,

    # The width of the outline border.
    outline_border_distance: types.Numeric = 8,

    # outline border style
    outline_itemstyle_opts: types.ItemStyle = None,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(font_size=50, position="inside"),

    # Tipbox component configuration items, refer to `series_options.
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Liquid/README)


## Parallel: parallel coordinate system

> *class pyecharts.charts.Parallel*

```python
class Parallel(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Parallel.add_schema*

``` python
def add_schema(
    schema: Sequence[Union[opts.ParallelAxisOpts, dict]],
    parallel_opts: Union[opts.ParallelOpts, dict, None] = None,
)
```

> *func pyecharts.charts.Parallel.add*

``` python
def add(
    # series name for tooltip display, legend filtering for legends.
    series_name: str,

    # series data
    data: types.Sequence[types.Union[opts.ParallelItem, dict]],

    # Whether or not the legend is selected.
    is_selected: bool = True,

    # Whether to smooth the curve
    is_smooth: bool = False,

    # Line styles, refer to `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(),

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### ParallelOpts: parallel coordinate system configuration items

> *class pyecharts.options.ParallelOpts*

```python
class ParallelOpts(
    # The distance of the parallel component from the left side of the container.
    # The value of left can be a specific pixel value like 20, which can be a percentage relative to the container height and width like '20%'.
    # It can also be 'left', 'center', 'right'.
    # If the value of left is 'left', 'center', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: str = "5%",

    # parallel The distance of the component from the right side of the container.
    The value of # right can be a specific pixel value like 20, or a percentage relative to the container height and width like '20%'.
    pos_right: str = "13%",

    # The distance of the parallel component from the bottom side of the container.
    The value of # bottom can be a specific pixel value like 20, or a percentage relative to the container's height and width like '20%'.
    pos_bottom: str = "10%",

    # The distance of the parallel component from the top side of the container.
    # top can be a specific pixel value like 20, or a percentage relative to the container's height and width like '20%'.
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: str = "20%",

    # Layout mode, optional values are.
    # 'horizontal': align each axis horizontally.
    # 'vertical': vertical alignment of the axes.
    layout: Optional[str] = None,
    
    # If there are more dimensions, for example 50+ dimensions, then there will be 50+ axes. Then the page may not fit.
    # You can improve the display by using parallel.axisExpandable.
    # Whether to allow clickable collapsed axes.
    is_axis_expandable: bool = False,
    
    # Initially, which axis to expand, here the index of the axis is given. there is no default value, you need to specify it manually.
    axis_expand_center: Optional[Numeric] = None,
    
    # The number of axes that will be expanded at the beginning. It is recommended to specify this manually depending on the number of dimensions you have.
    axis_expand_count: Numeric = 0,
    
    # How many axes are spaced in the expanded state, in pixels.
    axis_expand_width: Numeric = 50,
    
    # Possible values.
    # 'click': expand when mouse clicked.
    # 'mousemove': expand when mouse hover.
    axis_expand_trigger_on: str = "click",
)
```

### ParallelAxisOpts: parallel coordinate system axes configuration items

> *class pyecharts.options.ParallelAxisOpts*

```python
class ParallelAxisOpts(
    # The dimensional ordinal number of the coordinate axes.
    dim: Numeric,

    # The name of the coordinate axis.
    name: str,
    
    # If or not the view will be refreshed in real time when the axis is swiped. If set to false, the view will be refreshed only at the end of the swipe action.
    # It is recommended to set to false for large data volume to avoid lag.
    is_realtime: bool = True,

    # Coordinate axis data items
    data: Sequence = None,

    # The type of the coordinate axis. Optional.
    # 'value': numeric axis, for continuous data.
    # 'category': category axis, for discrete category data, for this type the category data must be set by data.
    # 'time': time axis, for continuous temporal data, compared to numeric axis with time formatting and different scale calculation
    # 'time': time axis for continuous time series data.
    # 'log' logarithmic axis. Applies to logarithmic data.
    type_: Optional[str] = None,
    
    # Coordinate axis name to show position.
    # Optional: 'start', 'middle' or 'center', 'end'
    name_location: str = "end",
    
    # The distance between the coordinate axis name and the axis line.
    name_gap: Numeric = 15,
    
    # The name of the axis to rotate, the angle value.
    name_rotate: Optional[int] = None,
    
    is_inverse: bool = False,
    # The minimum value of the coordinate axis scale.
    # Can be set to the special value 'dataMin', which takes the minimum value of the data on that axis as the minimum scale.
    # The minimum value will be calculated automatically when not set to ensure the uniform distribution of the axis scale.
    # In the category axis, it can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C')
    # can also be set to a negative number, e.g. -3).
    min_: Union[str, Numeric, None] = None,

    # The maximum value of the coordinate axis scale.
    # Can be set to a special value 'dataMax', when the maximum value of the data on that axis is taken as the maximum scale.
    # The maximum value is automatically calculated when not set to ensure even distribution of axis scales.
    # In the category axis, it can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C')
    # can also be set to a negative number, e.g. -3).
    max_: Union[str, Numeric, None] = None,

    # Valid only in the numeric axis (type: 'value').
    # Whether or not the scale is off the 0 value. When set to true, the coordinate scale is not forced to contain a zero scale. Useful in scatter plots with dual numeric axes.
    # This option is invalid after setting min and max.
    is_scale: bool = False,
    
    # The base of the logarithmic axis, valid only in the logarithmic axis (type: 'log').
    log_base: Numeric = 10,
    
    # Whether the coordinate axis is static or not cannot be interacted with.
    is_silent: bool = False,
    
    # If or not the label of the coordinate axis responds and triggers mouse events, default is not.
    is_trigger_event: bool = False,
    
    # Axis line configuration items, refer to `global_options.AxisLineOpts`.
    axisline_opts: Union[AxisLineOpts, dict, None] = None,
    
    # Axis scale configuration items, refer to `global_options.AxisTickOpts`
    axistick_opts: Union[AxisTickOpts, dict, None] = None,
    
    # Axis label configuration items, refer to `series_options.LabelOpts`
    axislabel_opts: Union[LabelOpts, dict, None] = None,
    
    # The settings related to the coordinate axis subscale, refer to `series_options.MinorTickOpts`
    minor_tick_opts: Union[MinorTickOpts, dict, None] = None,
)
```

### ParallelItem: parallel coordinate system data item

```python
class ParallelItem(
    ### Name of the data item.
    name: Optional[str] = None,

    ### The value of the data item.
    value: Optional[Sequence] = None,

    # The style of the line.
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,

    # The color of the line.
    color: Union[str, dict] = "#000",

    # The width of the line.
    width: Numeric = 2,

    # The type of the line. Options are 'solid', 'dashed', 'dotted'
    type_: str = "solid",

    # The transparency of the graph. Supports numbers from 0 to 1, and does not draw the graph when it is 0.
    opacity: Numeric = 0.45,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Parallel/README)


## Pie: pie chart

> *class pyecharts.charts.Pie*

```python
class Pie(
    ## Initialize configuration items, refer to ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Pie.add*

``` python
def add(
    # Series name for tooltip display, legend filter for legend.
    series_name: str,

    # series data items in the format [(key1, value1), (key2, value2)]
    data_pair: types.Sequence[types.Union[types.Sequence, opts.PieItem, dict]],

    # series label color
    color: Optional[str] = None,
    
    # The strategy for taking the color from the palette option.color, which can take the following values.
    # 'series': assign colors in the palette by series, all data in the same series are in the same color.
    # 'data': assigns the colors in the palette by data item, each data item uses a different color.
    color_by: types.Optional[str] = "data",
    
    # Whether to enable linkage highlighting on legend hover.
    is_legend_hover_link: bool = True,
    
    # Configuration of the selection mode, indicating whether multiple selections are supported, off by default, supports boolean and string.
    # String values can be selected as 'single', 'multiple', 'series' for single, multiple and entire series respectively.
    selected_mode: types.Union[str, bool] = False,
    
    # The offset distance of the selected sector.
    selected_offset: types.Numeric = 10,

    # The radius of the pie chart, the first item of the array is the inner radius, the second is the outer radius
    # default set to a percentage, half of the smaller one relative to the container height and width
    radius: Optional[Sequence] = None,

    # The coordinates of the center (center of the circle) of the pie chart, the first item of the array is the horizontal coordinate, the second item is the vertical coordinate
    # default is set to percentage, when set to percentage the first item is relative to the container width, the second item is relative to the container height
    center: Optional[Sequence] = None,

    # Whether to display as Nightingale chart, distinguish data size by radius, there are two modes of 'radius' and 'area'.
    # radius: the percentage of data displayed by sector centroid, the size of data displayed by radius
    # area: all sectors have the same centroid, only the data size is shown by radius
    rosetype: Optional[str] = None,
    
    # Whether the sectors of the pie chart are arranged clockwise.
    is_clockwise: bool = True,
    
    # Start angle, supports range [0, 360]
    start_angle: types.Numeric = 90,
    
    # The minimum sector angle (0 ~ 360), used to prevent a value too small to make the sector too small for interaction.
    min_angle: types.Numeric = 0,
    
    # Sectors smaller than this angle (0 ~ 360) are not displayed (label and labelLine).
    min_show_label_angle: types.Numeric = 0,
    
    # Whether to enable the policy of preventing label overlap. The default is on, which will move the position of each label to prevent overlap between labels in case of crowded overlap.
    # If you don't need to enable this policy, for example, if you need to force all labels to be centered in the circle diagram example, you can set this value to false.
    is_avoid_label_overlap: bool = True,
    
    # Whether to show sectors even when the data sum is 0 (usually all data is 0).
    is_still_show_zero_sum: bool = True,
    
    # The precision of the pie chart percentage value, with two decimal places by default.
    percent_precision: types.Numeric = 2,
    
    # Whether to show a placeholder circle when no data is available.
    is_show_empty_circle: bool = True,
    
    # The style of the empty circle.
    empty_circle_style_opts: types.PieEmptyCircle = opts.PieEmptyCircleStyle(),
    
    # Label configuration items, refer to `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # You can define which dimension of data is encoded as what.
    encode: types.Union[types.JSFunc, dict, None] = None,
    
    # Pie chart guide line configuration, see `chart_options.PieLabelLineOpts`
    label_line_opts: types.PieLabelLine = opts,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### PieItem: pie chart data item

```python
class PieItem(
    ### The name of the data item.
    name: Optional[str] = None,

    ### Data value.
    value: Optional[Numeric] = None,

    # Whether the data item is selected or not.
    is_selected: bool = False,

    # Label configuration items, refer to `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,

    # Item style configuration items, refer to `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### PieLabelLineOpts: visual guide line style for pie chart labels

```python
class PieLabelLineOpts(
    ### Show or not show visual guide lines.
    is_show: bool = True,
    
    # Whether or not to show above the graph
    is_show_above: bool = False,
    
    # The length of the first section of the visual guide line.
    length: Numeric = None,

    # The length of the second segment of the visual guide.
    length_2: Numeric = None,

    # If or not to smooth the visual guide, the default is not smooth, you can set it to true to smooth the display.
    # Can also be set to a value from 0 to 1, indicating the degree of smoothing.
    smooth: Union[bool, Numeric] = False,
    
    # Limit the minimum angle between the ends of the guide line by adjusting the length of the second line segment
    # to prevent unsightly display due to too small an angle.
    # Can be set to 0 - 180 degrees.
    min_turn_angle: Numeric = 90,
    
    # Line styles, see `LineStyleOpts`
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,
    
    # Limit the maximum angle between the guide line and the sector normals by adjusting the length of the second line segment
    # Set to a value less than 90 degrees to ensure that the guide line does not cross the sector.
    # Can be set to 0 - 180 degrees.
    max_surface_angle: Numeric = 90,
)
```

### PieEmptyCircleStyle: pie chart placeholder circle style

```python
class PieEmptyCircleStyle(
    ### The color of the graph.
    color: str = "lightgray",
    
    # The stroke color of the graph. Supported color formats are the same as color, no callback functions are supported.
    border_color: str = "#000",
    
    # The width of the stroke. No stroke when 0.
    border_width: Numeric = 0,
    
    # The type of the stroke. Optional: 'solid', 'dashed', 'dotted'
    border_type: str = "solid",
    
    # Used to set the offset of the dashed line, can be used with borderType to specify the dash array to achieve a flexible dashed effect.
    border_dash_offset: Numeric = 0,
    
    # Used to specify how the end of the line segment is drawn, can be.
    # 'butt': the line segment ends in a square.
    # 'round': The end of the line segment ends in a circle.
    # 'square': the end of the line segment ends in a square, but adds a rectangular area with the same width as the line segment and half the height of the segment's thickness.
    border_cap: str = "butt",
    
    # Attribute used to set how 2 connected sections (line segment, arc, curve) of non-zero length are joined together (deformed sections of length 0, whose specified end is at the same location as the control point, are ignored).
    # Can be.
    # 'bevel': fills an additional triangle-based area at the end of the connected sections, each with its own separate rectangular corner.
    # 'round': Draws the shape of the corners by filling an additional sector with the center of the circle at the end of the connected section. The radius of the rounded corner is the width of the line segment.
    # 'miter': Creates an additional diamond-shaped area by extending the outer edges of the connected sections so that they intersect at a point. The effect of this setting can be seen with the borderMiterLimit property.
    border_join: str = "bevel",
    
    # Used to set the miter limit scale. borderMiterLimit is only valid if borderJoin is miter.
    # The default value is 10. negative numbers, 0, Infinity and NaN are ignored.
    border_miter_limit: Numeric = 10,
    
    # Graphical transparency. Supports numbers from 0 to 1. 0 does not draw the graph.
    opacity: Numeric = 1,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Pie/README)


## Polar: Polar coordinate system

> *class pyecharts.charts.Polar*

```python
class Polar(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Polar.add_schema*

``` python
 def add_schema(
    radiusaxis_opts: Union[opts.RadiusAxisOpts, dict] = opts.RadiusAxisOpts(),
    angleaxis_opts: Union[opts.AngleAxisOpts, dict] = opts,
)
```

> *func pyecharts.charts.Polar.add*

``` python
def add(
    # series name for tooltip display, legend filtering for legends.
    series_name: str,

    # Series data items
    data: Sequence,

    # whether the legend is selected or not
    is_selected: bool = True,

    # Chart type, supports
    # ChartType.SCATTER, ChartType.LINE, ChartType.BAR, ChartType.EFFECT_SCATTER
    type_: str = "line",
    
    # The center (center of circle) coordinate of the polar coordinate system, the first item of the array is the horizontal coordinate, the second item is the vertical coordinate.
    # Supports setting to percentage, when set to percentage the first term is relative to the container width, the second term is relative to the container height.
    center: types.Optional[types.Sequence] = ["50%", "50%"],

    # The marker types provided by ECharts include 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # can be set to an image by 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # The size of the marker, either as a single number like 10, or as an array of separate widths and heights.
    # For example, [20, 10] means the symbol is 20 wide and 10 high.
    symbol_size: Numeric = 4,

    # Data stacking, where stack values with the same series configuration on the same class axis can be stacked.
    stack: Optional[str] = None,

    # Label configuration items, refer to `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Area padding style configuration items, see `series_options.AreaStyleOpts`
    areastyle_opts: Union[opts.AreaStyleOpts, dict] = opts,

    # Axis scale configuration items, see `global_options.AxisTickOpts`
    axistick_opts: Union[AxisTickOpts, dict, None] = None,

    # Ripple effect configuration items, refer to `series_options.EffectOpts`
    effect_opts: Union[opts.EffectOpts, dict] = opts,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### RadiusAxisItem: radial axis data item for polar coordinate system

> *class pyecharts.options.RadiusAxisItem*

```python
class RadiusAxisItem(
    value: Optional[str] = None,
    textstyle_opts: Optional[TextStyleOpts] = None,
)
```

### RadiusAxisOpts: Radial axis configuration items for polar coordinate system

> *class pyecharts.options.RadiusAxisOpts*

```python
class RadiusAxisOpts(
    # The index of the polar coordinate system in which the radius axis is located, the first polar coordinate system is used by default.
    polar_index: Optional[int] = None,

    # Data item, see `global_options.RadiusAxisItem`.
    data: Optional[Sequence[Union[RadiusAxisItem, dict, str]] = None, # data: Optional[Sequence[Union[RadiusAxisItem, dict, str]] = None,

    # The strategy of leaving white space on both sides of the coordinate axis is set and behaved differently for the item-like and non-item-like axes.
    # The boundaryGap can be configured to true and false in the category axis. the default is true, when the scale is just used as a separator line.
    # The labels and data points will be in the middle of the band between the two scales.
    # For non-category axes, including time, numeric, and logarithmic axes, boundaryGap is an array of two values that represent the extension of the minimum and maximum values of the data, respectively
    # Can be set directly as a numeric value or as a relative percentage, not valid after setting min and max. Example: boundaryGap: ['20%', '20%']
    boundary_gap: Union[bool, Sequence] = None,

    # Coordinate axis type. Optional.
    # 'value': numeric axis, for continuous data.
    # 'category': category axis, for discrete category data, the category data must be set by data for this type.
    # 'time': time axis, for continuous temporal data, compared to numeric axis with time formatting and different scale calculation
    # 'time': time axis for continuous time series data.
    # 'log' logarithmic axis. Applies to logarithmic data.
    type_: Optional[str] = None,

    # The name of the coordinate axis.
    name: Optional[str] = None,

    # The name of the coordinate axis to display the position. Optional.
    # 'start', 'middle' or 'center', 'end
    name_location: Optional[str] = None,

    # The minimum value of the coordinate axis scale.
    # Can be set to the special value 'dataMin', which takes the smallest value of the data on that axis as the minimum scale.
    # The minimum value will be calculated automatically when not set to ensure even distribution of axis scales.
    # In the category axis, it can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C')
    # can also be set to a negative number, e.g. -3).
    min_: Union[str, Numeric, None] = None,

    # The maximum value of the coordinate axis scale.
    # Can be set to a special value 'dataMax', when the maximum value of the data on that axis is taken as the maximum scale.
    # The maximum value is automatically calculated when not set to ensure even distribution of axis scales.
    # In the category axis, it can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C')
    # can also be set to a negative number, e.g. -3).
    max_: Union[str, Numeric, None] = None,

    # Valid only in the numeric axis (type: 'value').
    # Whether or not the scale is off the 0 value. When set to true, the coordinate scale is not forced to contain a zero scale. Useful in scatter plots with dual numeric axes.
    # This option is invalid after setting min and max.
    is_scale: bool = False,
    
    # Force the axis scale interval.
    interval: Optional[Numeric] = None,

    # Split line options, see `series_options.SplitLineOpts`.
    splitline_opts: Union[SplitLineOpts, dict, None] = None,

    # The separating area of the coordinate axes in the grid area, not shown by default. See `series_options.SplitAreaOpts` for reference
    splitarea_opts: Union[SplitAreaOpts, dict, None] = None,

    # Axis line style configuration items, see `series_options.
    axisline_opts: Union[AxisLineOpts, dict, None] = None,

    # Axis label configuration items, refer to `series_options.LabelOpts`
    axislabel_opts: Union[LabelOpts, dict, None] = None,

    # z-values for all graphics of the radius axis component. This controls the order of the shapes. shapes with small z values will be overwritten by shapes with large z values
    z: Optional[int] = None,
)
```

### AngleAxisItem: polar coordinate system angle axis data item

> *class pyecharts.options.AngleAxisItem*

```python
class AngleAxisItem(
    value: Optional[str] = None,
    textstyle_opts: Optional[TextStyleOpts] = None,
)
```

### AngleAxisOpts: polar coordinate system angle axis configuration item

> *class pyecharts.options.AngleAxisOpts*

```python
class AngleAxisOpts(
    # The index of the polar coordinate system in which the radial axis is located, the first polar coordinate system is used by default.
    polar_index: Optional[int] = None,
    data: Optional[Sequence[Union[AngleAxisItem, dict, str]] = None,
    start_angle: Optional[Numeric] = None,
    is_clockwise: bool = False,

    # The strategy of leaving white space on both sides of the coordinate axes is set and behaves differently for the item-like and non-item-like axes.
    # The borderGap can be configured to true and false in the category axis. the default is true, when the scale is just used as a separator line.
    # The labels and data points will be in the middle of the band between the two scales.
    # For non-category axes, including time, numeric, and logarithmic axes, boundaryGap is an array of two values that represent the extension of the minimum and maximum values of the data, respectively
    # Can be set directly as a numeric value or as a relative percentage, not valid after setting min and max. Example: boundaryGap: ['20%', '20%']
    boundary_gap: Union[bool, Sequence] = None,

    # Coordinate axis type. Optional.
    # 'value': numeric axis, for continuous data.
    # 'category': category axis, for discrete category data, the category data must be set by data for this type.
    # 'time': time axis, for continuous temporal data, compared to numeric axis with time formatting and different scale calculation
    # 'time': time axis for continuous time series data.
    # 'log' logarithmic axis. Applies to logarithmic data.
    type_: Optional[str] = None,

    # The minimum value of the coordinate axis scale.
    # Can be set to the special value 'dataMin', which takes the smallest value of the data on that axis as the minimum scale.
    # The minimum value will be calculated automatically when not set to ensure even distribution of axis scales.
    # In the category axis, it can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C')
    # can also be set to a negative number, e.g. -3).
    min_: Union[str, Numeric, None] = None,

    # The maximum value of the coordinate axis scale.
    # Can be set to a special value 'dataMax', when the maximum value of the data on that axis is taken as the maximum scale.
    # The maximum value is automatically calculated when not set to ensure even distribution of axis scales.
    # In the category axis, it can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C')
    # can also be set to a negative number, e.g. -3).
    max_: Union[str, Numeric, None] = None,

    # Valid only in the numeric axis (type: 'value').
    # Whether or not the scale is off the 0 value. When set to true, the coordinate scale is not forced to contain a zero scale. Useful in scatter plots with dual numeric axes.
    # This option is invalid after setting min and max.
    is_scale: bool = False,

    # The number of segments of the coordinate axis. Note that the number of segments is only an estimate, and the actual number of segments displayed will be adjusted based on how easy it is to read the segmented axis scale.
    # Not valid in the category axis.
    split_number: Numeric = 5,

    # Force the axis splitting interval.
    interval: Optional[Numeric] = None,

    # Split line style configuration item, refer to `series_options.SplitLineOpts`.
    splitline_opts: Union[SplitLineOpts, dict, None] = None,

    # Axis line style configuration items, refer to `series_options.
    axisline_opts: Union[AxisLineOpts, dict, None] = None,

    # Axis label style configuration items, refer to `series_options.LabelOpts`
    axislabel_opts: Union[LabelOpts, dict, None] = None,

    # z-values for all graphics of the radius axis component. This controls the order of the shapes. shapes with small z values will be overwritten by shapes with large z values
    z: Optional[int] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Polar/README)

## Radar: Radar Chart

> *class pyecharts.charts.Radar*

```python
class Radar(
    ## Initialize configuration items, refer to ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Radar.add_schema*

``` python
def add_schema(
    # Radar indicator configuration item list, refer to `RadarIndicatorItem`
    schema: Sequence[Union[opts.RadarIndicatorItem, dict]],

    # Radar plotting type, optionally 'polygon' and 'circle'
    shape: Optional[str] = None,

    # The coordinates of the radar's center (circle), the first item of the array is the horizontal coordinate, the second is the vertical coordinate.
    # Support set to percentage, when set to percentage the first term is relative to the container width, the second term is relative to the container height.
    center: Optional[types.Sequence] = None,
    
    # Radius of the radar. Can be of the following type.
    # number: specifies the outer radius value directly.
    # string: for example, '20%', means that the outer radius is 20% of the length of the visible area size (the smaller of the container height and width).
    # Array.<number|string>: The first item of the array is the inner radius and the second item is the outer radius. Each item follows the description of the number string above.
    radius: types.Optional[types.Union[types.Sequence, str]] = None,
    
    # The angle at which the coordinate system starts, i.e. the angle of the first indicator axis.
    start_angle: types.Numeric = 90,

    # Text style configuration items, refer to `series_options.TextStyleOpts`
    textstyle_opts: Union[opts.TextStyleOpts, dict] = opts,

    # Splitline configuration items, refer to `series_options.SplitLineOpts`
    splitline_opt: Union[opts.SplitLineOpts, dict] = opts.SplitLineOpts(is_show=True),

    # Split area configuration items, see `series_options.SplitAreaOpts`
    splitarea_opt: Union[opts.SplitAreaOpts, dict] = opts.SplitAreaOpts(),

    # Axis line configuration items, see `global_options.AxisLineOpts`
    axisline_opt: Union[opts.AxisLineOpts, dict] = opts.AxisLineOpts(),
    
    # Axis tick settings, see `global_options.AxisTickOpts`.
    axisTick_opt: types.AxisTick = None,

    # Axis tick labels, see `global_options.LabelOpts`.
    axislabel_opt: types.Label = None,

    # The radial axis of the polar coordinate system. References `basic_charts.RadiusAxisOpts`
    radiusaxis_opts: types.RadiusAxis = None,
    
    # The angle axis of the polar coordinate system. References `basic_charts.AngleAxisOpts`
    angleaxis_opts: types.AngleAxis = None,

    # polar coordinate system configuration, refer to `global_options.PolorOpts`
    polar_opts: types.Polar = None,
)
```

> *func pyecharts.charts.Radar.add*

``` python
def add(
    # series name for tooltip display, legend filtering for legends.
    series_name: str,

    # series data items
    data: types.Sequence[types.Union[opts.RadarItem, dict]],

    # Whether the legend is selected or not
    is_selected: bool = True,

    # ECharts provides markers of types 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # can be set to an image by 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # Series label color
    color: Optional[str] = None,

    # Label configuration items, refer to `series_options.LabelOpts`
    label_opts: opts.LabelOpts = opts,

    # Line style configuration items, see `series_options.LineStyleOpts`
    linestyle_opts: opts.LineStyleOpts = opts,

    # Area fill style configuration items, refer to `series_options.AreaStyleOpts`
    areastyle_opts: opts.AreaStyleOpts = opts,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### RadarIndicatorItem: radar chart indicator data item

> *class pyecharts.options.RadarIndicatorItem*

```python
class RadarIndicatorItem(
    # The name of the indicator.
    name: Optional[str] = None,

    # The maximum value of the indicator, optional, recommended
    min_: Optional[Numeric] = None,

    # The minimum value of the indicator, optional, default is 0.
    max_: Optional[Numeric] = None,

    # The label specific color.
    color: Optional[str] = None,
)
```

### RadarItem: radar graph data item

``` python
class RadarItem(
    ### Data item name
    name: Optional[str] = None,

    ### The value of a single data item.
    value: Optional[Numeric] = None,

    # The graph of the single data item.
    symbol: Optional[str] = None,

    # The size of a single data token
    symbol_size: Union[Sequence[Numeric], Numeric] = None,

    # The rotation angle (not radians) of a single data token.
    symbol_rotate: Optional[Numeric] = None,

    # If the symbol is of the form path://, whether to keep the aspect ratio of the graph when scaling.
    symbol_keep_aspect: bool = False,

    # The offset of a single data marker relative to its original position.
    symbol_offset: Optional[Sequence] = None,

    # Label configuration items, refer to `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,

    # Item style configuration items, refer to `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,

    # Line style configuration items, see `series_options.LineStyleOpts`
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,

    # Area padding style configuration items, refer to `series_options.AreaStyleOpts`
    areastyle_opts: Union[AreaStyleOpts, dict, None] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Radar/README)


## Sankey: Sankey chart

> *class pyecharts.charts.Sankey*

```python
class Sankey(
    ## Initialize configuration items, refer to ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

### SankeyLevelsOpts: sankey chart level configuration
> *class pyechart.options.SankeyLevelsOpts*

```python
class SankeyLevelsOpts(
    # Specifies which level of the sankey map is set, taking values starting from 0.
    depth: Numeric = None,

    # The style of the nodes of the specified layer of the Sankey map. References `global_opts.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # The style of the layer-out edge specified by the sankey map.
    # Where lineStyle.color supports setting to 'source' or 'target' special value, then the outgoing edge will automatically take the color of the source or target node as its own color.
    # Reference `global_opts.LineStyleOpts`
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,
)
```

> *func pyecharts.charts.Sankey.add*

```python
def add(
    # series name for tooltip display, legend filter for legend.
    series_name: str,
    nodes: Sequence,
    links: Sequence,

    # The distance of the Sankey component from the left side of the container.
    pos_left: types.Union[str, types.Numeric] = "5%",

    # The distance of the Sankey component from the top side of the container.
    pos_top: types.Union[str, types.Numeric] = "5%",

    # The distance of the Sankey component from the right side of the container.
    pos_right: types.Union[str, types.Numeric] = "20%",
    
    # The distance of the Sankey component from the lower side of the container.
    pos_bottom: types.Union[str, types.Numeric] = "5%",

    # The width of each rectangular node in the Sankey diagram.
    node_width: Numeric = 20,

    # The spacing between any two rectangular nodes in each column of the Sankey diagram.
    node_gap: Numeric = 8,
    
    # The alignment of the nodes in the sankey diagram. The default is double-ended alignment, which can be set to left-aligned or right-aligned, and the corresponding values are.
    # justify: The node is bipartite aligned.
    # left: The node is left-aligned.
    # right: The node is right-aligned.
    node_align: str = "justify",
    
    # Layout iteration count to continuously optimize the position of nodes in the graph to reduce mutual occlusion between nodes and edges.
    # Default number of layout iterations: 32.
    # Note: The number of layout iterations should not be lower than the default value.
    layout_iterations: types.Optional[types.Numeric] = None,

    # The layout orientation of the nodes in the san base map, either horizontally from left to right, or vertically from top to bottom.
    # The corresponding parameter values are horizontal, vertical respectively.
    orientation: str = "horizontal",

    # Control the interaction of node dragging, turned on by default. When turned on, the user can drag any node in the diagram to any position. If you want to turn off this interaction, just set the value to false.
    is_draggable: bool = True,
    
    # Configuration of Sankey's Edge Label
    edge_label_opt: types.Label = None,
    
    # When highlighting a graph, does the graph of other data fade out to achieve focus. The following configurations are supported:
    # 'none' No other graphs are faded out, this configuration is used by default.
    # 'self' Focuses (does not fade out) only the graph of the currently highlighted data.
    # 'series' Focuses all graphs in the series of the currently highlighted data.
    # 'adjacency' graph that focuses on the neighbours and edges in the relationship graph
    focus_node_mode: str = "none".

    # mouse hover to node or edge, adjacent nodes and edges highlight interaction, off by default, can be turned on manually.
    # false: When hovering to a node or edge, only the hovered node or edge is highlighted.
    # true: same as 'allEdges'.
    # 'allEdges': When hovering to a node, all edges adjacent to the node and nodes corresponding to the edge are highlighted. hovering to an edge, the edge and adjacent nodes are highlighted.
    # 'outEdges': The node hovered, the outgoing edge of the node, and the other node adjacent to the outgoing edge are highlighted. hover to the edge, the edge and the adjacent node are highlighted.
    # 'inEdges': the node hovered, the incoming edge of the node, and the other node adjacent to the incoming edge are highlighted. hovering to an edge highlights the edge and the adjacent node.
    focus_node_adjacency: types.Union[bool, str] = False,
    
    # The settings for each layer of the base map. Can be set layer by layer
    levels: types.SankeyLevel = None,

    # Label configuration items, refer to `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Line style configuration items, see `series_options.LineStyleOpts`
    linestyle_opt: Union[opts.LineStyleOpts, dict] = opts,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Sankey/README)


## Sunburst: Rising Sun Chart

> *class pyecharts.charts.Sunburst*

```python
class Sunburst(
    ## Initialize configuration items, refer to ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Sunburst.add*

``` python
def add(
    # series name, used for tooltip display, legend filtering for legend.
    series_name: str,
    
    # Data items.
    data_pair: Sequence,
    
    # The coordinates of the center (center of the circle) of the Sunburst chart, the first item of the array is the horizontal coordinate, the second is the vertical coordinate.
    # Support set to percentage, when set to percentage the first item is relative to the container width, the second item is relative to the container height.
    center: Optional[Sequence] = None,
    
    # The radius of the rising sun graph. Can be of the following type.
    # Sequence.<int|str>: The first term of the array is the inner radius, the second term is the outer radius.
    radius: Optional[Sequence] = None,
    
    # Highlight the associated sector block when the mouse moves over it.
    # 'descendant': highlight this sector block and descendant elements, other elements will be faded out.
    # 'ancestor': highlight the sector block and ancestor elements.
    # 'self': highlights only itself.
    # 'none': no other elements will be faded.
    highlight_policy: str = "descendant",
    
    # The behavior of the node after it is clicked. Can take the following values: false: node is not responsive when clicked.
    # 'rootToNode': take this node as the root node after clicking on it.
    # 'link': if there is a link in the node data a hyperlink jump will be made when the node is clicked.
    node_click: str = "rootToNode",
    
    # The way the sector block is sorted according to the data value, if value is not specified, the value is the sum of the child element values.
    # 'desc': sorting in descending order.
    # 'asc': ascending sort.
    # 'null': means no sorting, using the order of the original data.
    # Sorting using javascript callback functions.
    sort_: Optional[JSFunc] = "desc",
    
    # Sunburst chart multi-level configuration
    # The current configuration can be found at: https://www.echartsjs.com/option.html#series-sunburst.levels
    levels: Optional[Sequence] = None,
    
    # Label configuration items, refer to `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,
    
    # Configuration of data items, refer to `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
)
```

### SunburstItem: Sunburst Item

> *class pyecharts.options.SunburstItem*

```python
class SunburstItem(
    # The data value, or if it contains children, the value may be left out.
    # In this case, the sum of the values of the child elements will be used as the value of the parent element.
    # If value is greater than the sum of the children, it can be used to indicate that there are other child elements not shown.
    value: Optional[Numeric] = None,
    
    # The description text displayed in the sector block.
    name: Optional[str] = None,
    
    # A hyperlink that can be jumped to by clicking on this node. Must have a Sunburst.add.node_click value of 'link' to be effective
    link: Optional[str] = None,
    
    # Meaning is the same as target in HTML <a> tags, the difference in the jumping method
    # blank opens in a new window or tab
    # self opens in the current page or tab
    target: Optional[str] = "blank",
    
    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,
    
    # Data item configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
    
    # Child data item configuration configuration (consistent with SunburstItem, recursive down)
    children: Optional[Sequence] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Sunburst/README)


## ThemeRiver：ThemeRiver

> *class pyecharts.charts.ThemeRiver*

```python
class ThemeRiver(
    ## Initialize configuration items, refer to ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.
)
```

> *func pyecharts.charts.ThemeRiver.add*

``` python
def add(
    # Series name, used for tooltip display, legend filtering for legends.
    series_name: Sequence,

    # Series data items
    data: types.Sequence[types.Union[opts.ThemeRiverItem, dict]],

    # Whether the legend is selected or not
    is_selected: bool = True,

    # Label configuration items, refer to `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Single axis component configuration items, see `global_options.SingleAxisOpts`
    singleaxis_opts: Union[opts.SingleAxisOpts, dict] = opts,
    
    # Marker point style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: types.ItemStyle = None,
    
    # Emphasis configuration items，see `global_options.EmphasisOpts`
    emphasis_opts: types.Emphasis = None,
):
```

### ThemeRiverItem: theme river map data item

```python
class ThemeRiverItem(
    ### The time or theme's time attribute.
    date: Optional[str] = None,

    # The value of the event or theme at a point in time.
    value: Optional[Numeric] = None,

    # The name of the event or topic.
    name: Optional[str] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/ThemeRiver/README)


## WordCloud: word cloud graph

> *class pyecharts.charts.WordCloud*

```python
class WordCloud(
    ## Initialize configuration items, refer to ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.
)
```

> *func pyecharts.charts.WordCloud.add*

``` python
def add(
    # series name for tooltip display, legend filtering for legends.
    series_name: str,

    # series data items, [(word1, count1), (word2, count2)]
    data_pair: Sequence,

    # word cloud map contours, with 'circle', 'cardioid', 'diamond', 'triangle-forward', 'triangle', 'pentagon', 'star' optional
    shape: str = "circle",

    # Custom images (currently jpg, jpeg, png, ico formats are supported, other image formats to be tested)
    # This parameter supports.
    # 1, base64 (need to supplement data header).
    # 2, the local file path (relative or absolute path can be)
    # Note: If the first rendering after using mask_image is blank, refresh it again (Echarts problem)
    # Echarts Issue: https://github.com/ecomfe/echarts-wordcloud/issues/74
    mask_image: types.Optional[str] = None,

    # Word spacing
    word_gap: Numeric = 20,

    # Word font size range
    word_size_range=None,

    # Rotate the word angle
    rotate_step: Numeric = 45,

    # distance from the left side
    pos_left: types.Optional[str] = None,

    # distance to the top
    pos_top: types.Optional[str] = None,
    
    # Distance to the right
    pos_right: types.Optional[str] = None,
    
    # Distance to the bottom
    pos_bottom: types.Optional[str] = None,

    # The width of the word cloud map
    width: types.Optional[str] = None,

    # The height of the word cloud
    height: types.Optional[str] = None,

    # Allow the word cloud data to be displayed outside the canvas
    is_draw_out_of_bound: bool = False,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Configuration of the word cloud map text
    textstyle_opts: types.TextStyle = None,

    # Range of word cloud text shadows
    emphasis_shadow_blur: types.Optional[types.Numeric] = None,

    # The color of the word cloud text shadow
    emphasis_shadow_color: types.Optional[str] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/WordCloud/README)
