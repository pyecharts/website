> **Note: The section on configuration items should be read in conjunction with the example in the section on chart types. **Note: The configuration item section should be read in conjunction with the example section.

## ItemStyleOpts: Item style configuration items
> *class pyecharts.options.ItemStyleOpts*

```python
class ItemStyleOpts(
    # The colour of the graph.
    # The colour can be represented using RGB, e.g. 'rgb(128, 128, 128)', and if you want to add an alpha channel for opacity
    # You can use RGBA, e.g. 'rgba(128, 128, 128, 0.5)', or you can use hexadecimal format, e.g. '#ccc'.
    # Gradient colours and texture fills are also supported in addition to solid colours
    # 
    # Linear gradients, with the first four parameters x0, y0, x2, y2, ranging from 0 - 1, are equivalent to percentages in a graphical wraparound box.
    # If globalCoord is `true`, then the four values are absolute pixel positions
    # color: {
    # type: `linear',
    # x: 0,
    # y: 0,
    # x2: 0,
    # y2: 1,
    # colorStops: [{
    # offset: 0, color: 'red' // colour at 0%
    # }, {
    # offset: 1, color: 'blue' // colour at 100%
    # }],
    # global: false // default is false
    # }
    # 
    # radial gradient, the first three parameters are the center x, y and radius, which are the same as the linear gradient
    # color: {
    # type: 'radial',
    # x: 0.5,
    # y: 0.5,
    # r: 0.5,
    # colorStops: [{
    # offset: 0, color: 'red' // colour at 0%
    # }, {
    # offset: 1, color: 'blue' // colour at 100%
    # }],
    # global: false // default is false
    # }
    # 
    # texture fill
    # color: {
    # image: imageDom, // supported as HTMLImageElement, HTMLCanvasElement, path string not supported
    # repeat: 'repeat' // whether to tile, can be 'repeat-x', 'repeat-y', 'no-repeat'
    # }
    color: Optional[str] = None,
    
    # The colour of the shaded graph.
    color0: Optional[str] = None,

    # The stroke colour of the graph. Supports the same colour format as color, no callback functions are supported.
    border_color: Optional[str] = None,
    
    # The stroke colour of the shaded line.
    border_color0: Optional[str] = None,

    # The width of the stroke, the default is no stroke.
    border_width: Optional[Numeric] = None,

    # Supports 'dashed', 'dotted'.
    border_type: Optional[str] = None,
    
    # Graphical transparency. Supports a number from 0 to 1, with 0 not drawing the graph.
    opacity: Optional[Numeric] = None,

    # The colour of the area.    
    area_color: Optional[str] = None,
)
``.

## TextStyleOpts: text style configuration items
> *class pyecharts.options.TextStyleOpts*

``` python
class TextStyleOpts(
    # Text colour.
    color: Optional[str] = None,

    # The style of the text font.
    # Optional: 'normal', 'italic', 'oblique'
    font_style: Optional[str] = None,

    # The thickness of the main heading text font, Optional.
    # 'normal', 'bold', 'bolder', 'lighter'
    font_weight: Optional[str] = None,

    # The font family of the text
    # Can also be 'serif' , 'monospace', 'Arial', 'Courier New', 'Microsoft YaHei', ...
    font_family: Optional[str] = None,

    # The font size of the text
    font_size: Optional[Numeric] = None,
    
    # Horizontal alignment of the text, default auto
    align: Optional[str] = None,
    
    # Vertical alignment of the text, default auto
    vertical_align: Optional[str] = None,
    
    # Line height
    line_height: Optional[str] = None,
    
    # The background colour of the text block. Can be a direct colour value, e.g. '#123234', 'red', 'rgba(0,23,11,0.3)'
    background_color: Optional[str] = None,
    
    # Text block border colour
    border_color: Optional[str] = None,
    
    # The width of the text block border
    border_width: Optional[Numeric] = None,
    
    # The rounded corners of the text block
    border_radius: Union[Numeric, Sequence, None] = None,
    
    # The inner margin of the text block 
    # e.g. padding: [3, 4, 5, 6]: for [top, right, bottom, left] margins
    # e.g. padding: 4: means padding: [4, 4, 4, 4]
    # e.g. padding: [3, 4]: means padding: [3, 4, 3, 4]
    padding: Union[Numeric, Sequence, None] = None,
    
    # The background shadow colour of the text block
    shadow_color: Optional[str] = None,
    
    # The background shadow length of the text block
    shadow_blur: Optional[Numeric] = None,
    
    # The width of the text block
    width: Optional[str] = None,
    
    # The height of the text block
    height: Optional[str] = None,
    
    # Inside rich, you can customise the rich text style. Rich text styles can be used to create very rich effects in tags
    # See https://www.echartsjs.com/tutorial.html#%E5%AF%8C%E6%96%87%E6%9C%AC%E6%A0%87%E7%AD%BE for configuration details
    rich: Optional[dict] = None,
)
```

## LabelOpts: Label configuration items
> *class pyecharts.options.LabelOpts*

```python
class LabelOpts(
    ## Whether to show labels.
    is_show: bool = True,

    # The position of the label. Optional.
    # 'top', 'left', 'right', 'bottom', 'inside', 'insideLeft', 'insideRight'
    # 'insideTop', 'insideBottom', 'insideTopLeft', 'insideBottomLeft'
    # 'insideTopRight', 'insideBottomRight'
    position: Union[str, Sequence] = "top",

    # The colour of the text.
    # If set to 'auto', the colour obtained by visual mapping, e.g. series colour.
    color: Optional[str] = None,

    # The distance from the graphic element. Valid when position is a character description value (e.g. 'top', 'insideRight').
    distance: Union[Numeric, Sequence, None] = None,

    # The font size of the text
    font_size: Numeric = 12,

    # The style of the text font, optionally.
    # 'normal', 'italic', 'oblique'
    font_style: Optional[str] = None,

    # The thickness of the text font, optional.
    # 'normal', 'bold', 'bolder', 'lighter'
    font_weight: Optional[str] = None,

    # The font family of the text
    # Can also be 'serif' , 'monospace', 'Arial', 'Courier New', 'Microsoft YaHei', ...
    font_family: Optional[str] = None,

    # Label rotation. From -90 degrees to 90 degrees. Positive values are counterclockwise.
    rotate: Optional[Numeric] = None,
    
    # Scale the distance between the label and the axis.
    margin: Optional[Numeric] = 8,

    # The interval at which coordinate axis scale labels are displayed, valid in the class axis.
    # By default the labels will be displayed using a policy interval where labels do not overlap.
    # Can be set to 0 to force all labels to be displayed.
    # If set to 1, this means 'show one label every other label', if the value is 2, this means show one label every two labels, and so on.
    # The data for the interval can be expressed as a value or controlled by a callback function. The callback function format is as follows.
    # (index:number, value: string) => boolean
    # The first argument is the index of the class, the second value is the name of the class and returns false if skipped.
    interval: Union[Numeric, str, None] = None,

    # Horizontal alignment of the text, default auto. Optional.
    # 'left', 'center', 'right'
    horizontal_align: Optional[str] = None,

    # The text is aligned vertically, default is auto. Optional.
    # 'top', 'middle', 'bottom'
    vertical_align: Optional[str] = None,

    # Formatter for tag content, supports both string templates and callback functions, both string templates and callback functions return strings with \n line breaks.
    # The template variables are {a}, {b}, {c}, {d}, {e}, representing the series name, data name, data value, etc. 
    # When the trigger is 'axis', there will be more than one series of data, so the index of the series can be represented by {a0}, {a1}, {a2} followed by an index. 
    # The meaning of {a}, {b}, {c}, {d} differs between chart types. Where the variables {a}, {b}, {c}, {d} represent data under different chart types as.

    # Collapsed (area) charts, bar (bar) charts, K-line charts : {a} (series name), {b} (class value), {c} (value), {d} (none)
    # Scatter (bubble) charts : {a}(series name), {b}(data name), {c}(array of values), {d}(none)
    # Map : {a} (series name), {b} (area name), {c} (merged values), {d} (none)
    # Pie charts, dashboards, funnel charts: {a}(series name), {b}(data item name), {c}(value), {d}(percentage)
    # Example: formatter: '{b}: {@score}'
    # 
    # Callback function, callback function format.
    # (params: Object|Array) => string
    # The parameter params is the single data set required by the formatter. The format is as follows.
    # {
    # componentType: 'series',
    # // Series type
    # seriesType: string,
    # // index of the series in the option.series passed in
    # seriesIndex: number,
    # // Series name
    # seriesName: string,
    # // Data name, class name
    # name: string,
    # // index of the data in the incoming data array
    # dataIndex: number,
    # // The original data item passed in
    # data: Object,
    # // the value of the incoming data
    # value: number|Array,
    # // The colour of the data graph
    # color: string,
    # }
    formatter: Optional[str] = None,
    
    # The text block background colour.
    # Can use colour values, e.g. '#123234', 'red', 'rgba(0,23,11,0.3)'.
    background_color: Optional[str] = None,.
    
    # The text block border colour. If set to 'inherit', it is the colour obtained by visual mapping, e.g. series colour.
    border_color: Optional[str] = None, # Text block border width.
    
    # The border width of the text block.
    border_width: Optional[Numeric] = None, # The rounded corner of the text block.
    
    # The rounded corner of the text block.
    border_radius: Optional[Numeric] = None, # The inner margin of the text block.
    
    # The inner margin of the text block. Example:
    # padding: [3, 4, 5, 6]: means [top, right, bottom, left] margin.
    # padding: 4: means padding: [4, 4, 4, 4, 4].
    # padding: [3, 4]: means padding: [3, 4, 3, 4].
    # padding: [3, 4]: means padding: [3, 4, 3, 4]. # Note that the width and height of the text block specify the height and width of the content, not the padding.
    padding: Union[Numeric, Sequence[Numeric], None] = None, # Text display width.
    
    # Text display width.
    text_width: Optional[Numeric] = None, # text_width.
    
    # The height of the text.
    text_height: Optional[Numeric] = None, # Text height.
    
    # If or not the text will be truncated or linefeed if it exceeds the width. Valid when width is configured.
    # 'truncate' truncates and displays ellipsis-configured text at the end, defaults to...
    # 'break' line feed
    # 'breakAll' breaks the line, unlike 'break', which in Latin languages such as English also forces a line break within the word.
    overflow: Optional[str] = None,
    
    # In rich, you can customize the rich text style. Rich text styles can be used to create very rich effects in tags
    # See https://www.echartsjs.com/tutorial.html#%E5%AF%8C%E6%96%87%E6%9C%AC%E6%A0%87%E7%AD%BE for configuration details
    rich: Optional[dict] = None,
)
```

## LineStyleOpts: line style configuration items
> *class pyecharts.options.LineStyleOpts*

``` python
class LineStyleOpts(
    # whether to show or not
    is_show: bool = True,
    
    # Line width.
    width: Numeric = 1,

    # The transparency of the graph. Supports a number from 0 to 1, with 0 not drawing the graph.
    opacity: Numeric = 1,

    # The curvature of the line, 0 means no curvature at all
    curve: Numeric = 0,

    # The type of line. Optional.
    # 'solid', 'dashed', 'dotted'
    type_: str = "solid",

    # The colour of the line.
    # The colour can be represented using RGB, e.g. 'rgb(128, 128, 128)', and if you want to add an alpha channel for opacity
    # You can use RGBA, e.g. 'rgba(128, 128, 128, 0.5)', or you can use hexadecimal format, e.g. '#ccc'.
    # Gradient colours and texture fills are also supported in addition to solid colours
    # 
    # Linear gradients, with the first four parameters x0, y0, x2, y2, ranging from 0 - 1, are equivalent to percentages in a graphical wraparound box.
    # If globalCoord is `true`, then the four values are absolute pixel positions
    # color: {
    # type: `linear',
    # x: 0,
    # y: 0,
    # x2: 0,
    # y2: 1,
    # colorStops: [{
    # offset: 0, color: 'red' // colour at 0%
    # }, {
    # offset: 1, color: 'blue' // colour at 100%
    # }],
    # global: false // default is false
    # }
    # 
    # radial gradient, the first three parameters are the center x, y and radius, which are the same as the linear gradient
    # color: {
    # type: 'radial',
    # x: 0.5,
    # y: 0.5,
    # r: 0.5,
    # colorStops: [{
    # offset: 0, color: 'red' // colour at 0%
    # }, {
    # offset: 1, color: 'blue' // colour at 100%
    # }],
    # global: false // default is false
    # }
    # 
    # texture fill
    # color: {
    # image: imageDom, // supported as HTMLImageElement, HTMLCanvasElement, path string not supported
    # repeat: 'repeat' // whether to tile, can be 'repeat-x', 'repeat-y', 'no-repeat'
    # }
    color: Union[str, Sequence, None] = None,
)
```

## Lines3DEffectOpts: 3D line style configuration items
> *class pyecharts.options.Lines3DEffectOpts*

```python
class Line3DEffectOpts(
    # Whether to show trailing effects or not, not by default.
    is_show: bool = True,

    # The period of the trailing effect.
    period: Numeric = 4,

    # Whether the trailing effect's movement animation is at a fixed speed, in units of the dimensions of the 3D space
    # The period configuration is ignored when set to a value other than null.
    constant_speed: Optional[Numeric] = None,

    # The width of the trail.
    trail_width: Numeric = 4,

    # The length of the trail, ranging from 0 to 1, as a percentage of the line length.
    trail_length: Numeric = 0.1,

    # The colour of the trail, the default is the same as the line colour.
    trail_color: Optional[str] = None,

    # The opacity of the trail, defaults to the same as the line opacity.
    trail_opacity: Optional[Numeric] = None,
)
```

## SplitLineOpts: split line configuration items
> *class pyecharts.options.SplitLineOpts*

``` python
class SplitLineOpts(
    # Whether to show the split line or not
    is_show: bool = False,

    # Line style configuration item, see ``series_options.SplitLineOpts`''
    linestyle_opts: LineStyleOpts = LineStyleOpts()
)
```

## MarkPointItem: markpoint data item
> *class pyecharts.options.MarkPointItem*

``` python
class MarkPointItem(
    ## Marker name.
    name: Optional[str] = None,

    # Special marker type for marking max-min values, etc. Optional:
    # 'min' The maximum value.
    # 'max' The maximum value.
    # 'average' The average value.
    type_: Optional[str] = None,

    # Valid when using type, to specify the dimension in which the maximum and minimum values are specified, could be 
    # 0 (xAxis, radiusAxis), # 0 (xAxis, radiusAxis), # 0 (xAxis, radiusAxis)
    # 1 (yAxis, angleAxis), the default is to use the dimension where the first value axis is located.
    value_index: Optional[Numeric] = None,

    # Valid when using type, to specify in which dimension to specify the maximum and minimum values. This can be the direct name of the dimension.
    # For example x, angle, etc. for line graphs, or open, close, etc. for candlestick graphs.
    value_dim: Optional[str] = None,

    # The coordinates of the marker. The format of the coordinates depends on the coordinate system of the series, and can be x, y, etc. in a Cartesian coordinate system.
    # It can also be radius, angle in polar coordinates. e.g. [121, 2323], ['aa', 998].
    coord: Optional[Sequence] = None,

    # The x-coordinate of the screen relative to the container, in pixels.
    x: Optional[Numeric] = None,

    # The y-coordinate of the screen relative to the container, in pixels.
    y: Optional[Numeric] = None,

    # The value of the marker, which can be left out.
    value: Optional[Numeric] = None,

    # The graph of the marker.
    # The marker types provided by ECharts are 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # The size of the marker, either as a single number such as 10, or as an array of separate widths and heights.
    # For example [20, 10] means that the symbol is 20 wide and 10 high.
    symbol_size: Union[Numeric, Sequence] = None,

    # The marker point style configuration item, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
)
```

## MarkPointOpts: MarkPoint configuration items
> *class pyecharts.options.MarkPointOpts*

```python
class MarkPointOpts(
    # MarkPoint data, referenced in ``series_options.MarkPointItem`''
    data: Sequence[Union[MarkPointItem, dict]] = None,

    # Marked graphs.
    # The marker types provided by ECharts are 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # The size of the marker, either as a single number such as 10, or as an array of separate widths and heights.
    # For example [20, 10] means that the marker is 20 wide and 10 high.
    # If you need the graph size to be different for each piece of data, you can set the callback function to the following format.
    # (value: Array|number, params: Object) => number|Array
    # Where the first parameter value is the value of the data in data. The second parameter, params, is the other data item parameter.
    symbol_size: Union[None, Numeric] = None,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: LabelOpts = LabelOpts(position="inside", color="#fff"),
)
```

## MarkLineItem: mark line data item
> *class pyecharts.options.MarkLineItem*

```python
class MarkLineItem(
    ## Marker name.
    name: Optional[str] = None,

    # Special markup type for marking max-min values, etc. Optional:
    # 'min' Maximum value.
    # 'max' The maximum value.
    # 'average' The average value.
    type_: Optional[str] = None,

    # The screen x-coordinate relative to the container, in pixels.
    x: Union[str, Numeric, None] = None,

    # The x-coordinate of the data.
    xcoord: Union[str, Numeric, None] = None,

    # The y-coordinate of the screen relative to the container, in pixels.
    y: Union[str, Numeric, None] = None,

    # The y-coordinate of the data.
    ycoord: Union[str, Numeric, None] = None,

    # Valid when using type, to specify the dimension in which the maximum minimum value is specified, which can be 
    # 0 (xAxis, radiusAxis), # 0 (xAxis, radiusAxis), # 0 (xAxis, radiusAxis)
    # 1 (yAxis, angleAxis), the default is to use the dimension where the first value axis is located.
    value_index: Optional[Numeric] = None,

    # Valid when using type, to specify the dimension in which to specify the maximum and minimum values. This can be the direct name of the dimension.
    # For example x, angle, etc. for line graphs, or open, close, etc. for candlestick graphs.
    value_dim: Optional[str] = None,

    # The coordinates of the start or end point. The format of the coordinates depends on the coordinate system of the series, and can be x, y, or y in the Cartesian coordinate system.
    # Or radius, angle on a polar coordinate system.
    coord: Optional[Sequence] = None,

    # The graph of the endpoint marker.
    # The marker types provided by ECharts include 'circle', 'rect', 'roundRect', 'triangle',
    # 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # The size of the marker, either as a single number such as 10, or as an array of separate widths and heights.
    # For example [20, 10] means that the symbol is 20 wide and 10 high.
    symbol_size: Optional[Numeric] = None,
)
```

## MarkLineOpts: mark line configuration items
> *class pyecharts.options.MarkLineOpts*

```python
class MarkLineOpts(
    # Whether the graph does not respond to and trigger mouse events, defaults to false, i.e. responds to and triggers mouse events.
    is_silent: bool = False,

    # Mark line data, see `series_options.MarkLineItem`
    data: Sequence[Union[MarkLineItem, dict]] = None,

    # The type of marker at each end of the line, either an array specifying each end, or a single unified one, see data.symbol for details.
    symbol: Optional[str] = None,

    # The size of the symbols at each end of the line, either as an array or individually.
    symbol_size: Union[None, Numeric] = None,
    
    # The precision of the line value, useful when displaying the mean line.
    precision: int = 2,
    
    # Label configuration items, see `series_options.LabelOpts`
    label_opts: LabelOpts = LabelOpts(),

    # Label line style configuration items, see `series_options.LineStyleOpts`
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,
)
```

## MarkAreaItem: Mark area data item
> *class pyecharts.options.MarkAreaItem*

```python
class MarkAreaItem(
    # The name of the area, which is just a name
    name: Optional[str] = None,
    
    # Special markup type, for marking max min values etc.
    # 'min' The maximum value.
    # 'max' The maximum value.
    # 'average' The average value.
    type_: Sequence[Optional[str], Optional[str]] = (None, None),
    
    # Valid when using type to specify the dimension in which to specify the maximum and minimum values, either 0 (xAxis, radiusAxis), 1 (yAxis, angleAxis).
    # The default is to use the dimension in which the first value axis is located.
    value_index: Sequence[Optional[Numeric], Optional[Numeric]] = (None, None),
    
    # Valid when using type, to specify the dimension on which to specify the maximum minimum value.
    # This can be the direct name of a dimension, e.g. x, angle, etc. for line graphs, open, close, etc. for candlestick graphs.
    value_dim: Sequence[Optional[str], Optional[str]] = (None, None),
    
    # The screen x-coordinate relative to the container, in pixels, supports percentage forms, e.g. '20%'. Requires an axis type of value.
    x: Sequence[Union[str, Numeric, None], Union[str, Numeric, None]] = (None, None),
    
    # The y-coordinate of the screen relative to the container, in pixels, supporting a percentage form, e.g. '20%'.
    y: Sequence[Union[str, Numeric, None], Union[str, Numeric, None]] = (None, None),
    
    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,
    
    # The style of this data item area, the itemStyle of the start and end items will be merged together. See `series_options.ItemStyleOpts` for reference
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
)
```

## MarkAreaOpts: Mark area configuration items
> *class pyecharts.options.MarkAreaOpts*

```python
class MarkAreaOpts(
    # Whether the graph does not respond and trigger mouse events, default is False, i.e. responds and triggers mouse events.
    is_silent: bool = False,
    
    # Label configuration items, see `series_options.LabelOpts`
    label_opts: LabelOpts = LabelOpts(),
    
    # Mark area data, see `series_options.MarkAreaItem`
    data: Sequence[Union[MarkAreaItem, Sequence, dict]] = None,

    # The style of this data item area. References `series_options.ItemStyleOpts`
    itemstyle_opts: ItemStyleOpts = None,
)
```

## EffectOpts: ripple effect configuration items
> *class pyecharts.EffectOpts.

``` python
class EffectOpts(
    # Whether to show the effect.
    is_show: bool = True,

    # How the ripples are drawn, optionally 'stroke' and 'fill', valid for Scatter type.
    brush_type: str = "stroke",

    # The maximum scale of the ripple in the animation, valid for the Scatter type.
    scale: Numeric = 2.5,

    # The period of the animation, in seconds, valid for Scatter type.
    period: Numeric = 4,

    # The colour of the special effect marker
    color: Optional[str] = None,

    # The marker for the special effects graphic.
    # The marker types provided by ECharts are 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # The size of the special effects marker, which can be set to a single number such as 10, or an array of separate height and widths.
    # For example, [20, 10] means the token is 20 wide and 10 high.
    symbol_size: Optional[Numeric] = None,

    # The length of the special trailing. Takes a value from 0 to 1, the larger the value the longer the trail, valid if the Geo chart is set to Lines type.
    trail_length: Optional[Numeric] = None,
)
```

## AreaStyleOpts: Area fill style configuration items
> *class pyecharts.options.AreaStyleOpts*

```python
class AreaStyleOpts(
    # Graph transparency. Supports a number from 0 to 1, and does not draw the graph when it is 0.
    opacity: Optional[Numeric] = 0,
    # The colour of the fill.
    # The colour can be represented by RGB, e.g. 'rgb(128, 128, 128)', if you want to add an alpha channel for opacity.
    # You can use RGBA, e.g. 'rgba(128, 128, 128, 0.5)', or you can use hexadecimal format, e.g. '#ccc'.
    # Gradient colours and texture fills are also supported in addition to solid colours
    # 
    # Linear gradients, with the first four parameters x0, y0, x2, y2, ranging from 0 - 1, are equivalent to percentages in a graphical wraparound box.
    # If globalCoord is `true`, then the four values are absolute pixel positions
    # color: {
    # type: `linear',
    # x: 0,
    # y: 0,
    # x2: 0,
    # y2: 1,
    # colorStops: [{
    # offset: 0, color: 'red' // colour at 0%
    # }, {
    # offset: 1, color: 'blue' // colour at 100%
    # }],
    # global: false // default is false
    # }
    # 
    # radial gradient, the first three parameters are the center x, y and radius, which are the same as the linear gradient
    # color: {
    # type: 'radial',
    # x: 0.5,
    # y: 0.5,
    # r: 0.5,
    # colorStops: [{
    # offset: 0, color: 'red' // colour at 0%
    # }, {
    # offset: 1, color: 'blue' // colour at 100%
    # }],
    # global: false // default is false
    # }
    # 
    # texture fill
    # color: {
    # image: imageDom, // supported as HTMLImageElement, HTMLCanvasElement, path string not supported
    # repeat: 'repeat' // whether to tile, can be 'repeat-x', 'repeat-y', 'no-repeat'
    # }
    color: Optional[str] = None
)
```

## SplitAreaOpts: split area configuration items
> *class pyecharts.options.SplitAreaOpts*

``` python
class SplitAreaOpts(
    # Whether to show the split area.
    is_show=True, 
    # Style configuration item for split areas, see ``series_options.AreaStyleOpts`''
    areastyle_opts: AreaStyleOpts = AreaStyleOpts()
)
```

## MinorTickOpts: secondary scale configuration items
> *class pyecharts.options.MinorTickOpts*

``` python
class MinorTickOpts(
    # Whether or not to show subscales.
    is_show: bool = False,

    # The number of subscripts to split, by default it will split into 5 segments
    split_number: Numeric = 5,

    # The length of the subscale.
    length: Numeric = 3,

    # The style of the subscale
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,
)
```

## MinorSplitLineOpts: secondary split line configuration item
> *class pyecharts.options.MinorSplitLineOpts*

```python
class MinorSplitLineOpts(
    # Whether to show minor split lines. Not shown by default.
    is_show: bool = False,

    # The width of the subseparator line.
    width: Numeric = 1,

    # The type of separator line. Optional: 'solid', 'dashed', 'dotted'
    type_: str = "solid",

    # Graphical transparency. Supports numbers from 0 to 1, with 0 not drawing the graph.
    opacity: Union[Numeric, None] = None,

    # The style of the line
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,
)
```


## GraphGLForceAtlas2Opts: GraphGL Atlas2 algorithm configuration items
> *class pyecharts.options.GraphGLForceAtlas2Opts*

```python
class GraphGLForceAtlas2Opts(
    # Whether to enable GPU layouts.
    is_gpu: bool = True,
    
    # The number of iterations for one update. Because force-guided algorithms usually plot the results of each iteration.
    # but because the drawing time will often be greater than the layout time, it will result in a less efficient layout.
    # At this point we can set a larger steps parameter to ensure that the layout and drawing times are balanced and speed up the layout.
    steps: Numeric = 1,
    
    # The threshold to stop the layout when the global speed factor of the layout is less than this threshold. Set to 0 to never stop.
    stop_threshold: Numeric = 1,
    
    # Whether to enable Barnes Hut optimization, valid when forceAtlas2.GPU is false.
    # Default is on when node count > 1000.
    is_barnes_hut_optimize: Optional[bool] = None,
    
    # Whether to calculate the repulsion factor of nodes based on the number of node edges, recommended to turn on.
    is_repulsion_by_degree: bool = True,
    
    # Whether to be lin-log mode. lin-log mode will make the clustering of nodes more compact.
    is_lin_log_mode: bool = False,
    
    # The centripetal force on the node. This force will make the nodes move closer to the center.
    gravity: Numeric = 1,
    
    # The position of the center of the centripetal force. Default goes to the middle of the initial position.
    gravity_center: Optional[Sequence] = None,
    
    # The scaling factor of the layout, the higher the value the higher the repulsion between the nodes.
    scaling: Optional[Numeric] = None,
    
    # The influence factor of the edge weight. The larger the value, the greater the influence of the edge weights on the gravitational force.
    # Note: This factor is exponential, so it is not valid for edge weights of 0 and 1.
    edge_weight_influence: Numeric = 1,
    
    # The weight distribution of the edges. Mapped from links.value.
    # Supports setting to a single number, which is then the uniform weight value.
    edge_weight: Union[Sequence, Numeric] = None,
    
    # The weight distribution of the node. Mapped from nodes.value.
    # Supports setting to a single number, which is then the uniform weight value.
    node_weight: Union[Sequence, Numeric] = None,
    
    # Whether to turn on preventing nodes from overlapping.
    is_prevent_overlap: bool = False,
)
```
