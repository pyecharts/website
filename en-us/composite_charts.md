## Grid: parallel multiple charts

> *class pyecharts.charts.Grid(Base)*

```python
class Grid(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Grid.add*

``` python
def add(
    # Chart instances, only class `Chart` or its subclasses
    chart: Chart,

    # Cartesian grid configuration items, see `GridOpts`
    grid_opts: Union[opts.GridOpts, dict],

    # Cartesian grid index
    grid_index: int = 0,

    # Whether to control the Axis index by itself
    is_control_axis_index: bool = False,
)
```

### GridOpts: right-angle coordinate system grid configuration items
> *class pyecharts.options.GridOpts*

```python
class GridOpts(
    # Whether or not to show right-angle coordinate system grids.
    is_show: bool = False,

    # The zlevel value of all graphs.
    z_level: Numeric = 0,

    # The z value of all graphs of the component.
    z: Numeric = 2,
    
    # The distance of the grid component from the left side of the container.
    # The value of left can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'.
    # It can also be 'left', 'centre', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: Union[Numeric, str, None] = None,

    # The distance of the grid component from the top side of the container.
    # The value of top can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Union[Numeric, str, None] = None,

    # The distance of the grid component from the right side of the container.
    The value of # right can be a specific pixel value like 20, or it can be a percentage relative to the container height and width like '20%'.
    pos_right: Union[Numeric, str, None] = None,

    # The distance of the grid component from the lower side of the container.
    The value of # bottom can be a specific pixel value like 20, or a percentage of the container's height and width like '20%'.
    pos_bottom: Union[Numeric, str, None] = None,

    # The width of the grid component. Adaptive by default.
    width: Union[Numeric, str, None] = None,

    # The height of the grid component. Adaptive by default.
    height: Union[Numeric, str, None] = None,

    # Whether or not the grid area contains a scale label for the axes.
    is_contain_label: bool = False,

    # The background colour of the grid, transparent by default.
    background_color: str = "transparent",
    
    # The border colour of the grid. Supported colours are in the same format as backgroundColor.
    border_color: str = "#ccc",

    # The border line width of the grid.
    border_width: Numeric = 1,
    
    # The blur size of the graph's shadow
    shadow_blur: Optional[Numeric] = None,
    
    # Shadow colour
    shadow_color: Optional[str] = None,
    
    # The horizontal offset distance of the shadow
    shadow_offset_x: Numeric = 0,
    
    # The offset distance of the shadow vertically
    shadow_offset_y: Numeric = 0,

    # A tooltip setting specific to this coordinate system.
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Grid/README)


## Page: sequential multimap

> *class pyecharts.charts.Page*

```python
class Page(
    ## HTML title
    page_title: str = "Awesome-pyecharts",

    # Remote HOST, defaults to "https://assets.pyecharts.org/assets/"
    js_host: str = "",

    # The interval between each legend
    interval: int = 1,

    # Layout configuration items, see `PageLayoutOpts`
    layout: Union[PageLayoutOpts, dict] = PageLayoutOpts()
)
```

> *func pyecharts.charts.Page.add*

``` python
def add(*charts) # charts: any chart instance
```

> *class pyecharts.options.PageLayoutOpts*

``` python
class PageLayoutOpts(
    # Configure all native CSS styles
    justify_content: Optional[str] = None,
    margin: Optional[str] = None,
    display: Optional[str] = None,
    flex_wrap: Optional[str] = None,
)
```

> *func pyecharts.charts.Page.save_resize_html*

For DraggablePageLayout layout re-rendering charts
``` python
def save_resize_html(
    # The html file after the first rendering of the Page
    source: str = "render.html",
    *,
    # Layout configuration file
    cfg_file: types.Optional[str] = None,

    # Layout configuration dict
    cfg_dict: types.Optional[list] = None,

    # path to re-generated .html storage
    dest: str = "resize_render.html",
) -> str
```

Page has the following layouts built in

* SimplePageLayout
* DraggablePageLayout

### Demo

[gallery example](http://gallery.pyecharts.org/#/Page/README)

**Default layout**
```python
page = Page()
page.add(bar_datazoom_slider(), line_markpoint(), pie_rosetype(), grid_mutil_yaxis())
page.render()
```

**SimplePageLayout layout**
```python
page = Page(layout=Page.SimplePageLayout)
# You need to adjust the height/width of each chart yourself, the display may be different on different monitors
page.add(bar_datazoom_slider(), line_markpoint(), pie_rosetype(), grid_mutil_yaxis())
page.render()
```
![](https://user-images.githubusercontent.com/19553554/58749778-c8420a00-84bc-11e9-87e5-2aeab78a8eef.png)

**DraggablePageLayout layout**
```python
page = Page(layout=Page.DraggablePageLayout)
page.add(bar_datazoom_slider(), line_markpoint(), pie_rosetype(), grid_mutil_yaxis())
page.render()
```

Note: DraggablePageLayout requires pyecharts version v.1.4.0+
```python
# DraggablePageLayout makes use of Jquery and Echarts' own resize feature to implement a draggable layout. The steps are as follows
# 1. Specify the Page layout
page = Page(layout=Page.DraggablePageLayout)

# Normal render chart
page.add(bar_datazoom_slider(), line_markpoint(), pie_rosetype(), grid_mutil_yaxis())
page.render()

# Use your browser to open the rendered .html file, which defaults to render.html. drag/resize the chart, and when it is resized to a suitable
# Click on the `Save Config` button at the top left to download the chart_config.json configuration file, assuming the location is
# Render the chart again and specify its layout configuration

# Warning: Please comment out all the rendering code above, which is the following three lines. As the html is already generated, there is no need to render it again.
# page = Page(layout=Page.DraggablePageLayout)
# page.add(bar_datazoom_slider(), line_markpoint(), pie_rosetype(), grid_mutil_yaxis())
# page.render()

# render.html: the original html file generated in the first step
# chart_config.json: the configuration file downloaded in step 2
# my_new_charts.html: path to the new html file
Page.save_resize_html("render.html", cfg_file="~/chart_config.json", dest="my_new_charts.html")

# Or you can use json data
# cfg_dict is the contents of the json file
Page.save_resize_html("render.html", cfg_dict=cfg_dict, dest="my_new_charts.html")

# Question: Can I reuse rendering templates?
# Answer: Yes, the rendering configuration json data uses the chart_id as the unique identifier for a graph, so you only need to specify the chart_id in the
# The first time you render a chart, you can specify the chart_id.
# example:
# bar = bar_datazoom_slider()
# bar.chart_id = "chenjiandongx_is_an_awesome_boy"
# line = line_markpoint()
# line.chart_id = "chenjiandongx_is_an_amazing_boy"
# pie = pie_rosetype()
# pie.chart_id = "chenjiandongx_is_an_adorable_boy"
# pie = pie_rosetype() # pie.chart_id = "chenjiandongx_is_an_adorable_boy" # pie.chart_id = "chenjiandongx_is_an_adorable_boy
# cat chart_config.json, you will see that the chart_id is fixed.
page.add(bar_datazoom_slider(), line_markpoint(), pie_rosetype()))
```

Demo video
* [Oil Tube Video](https://www.youtube.com/watch?v=gizMMGkUt80&feature=youtu.be)
* [Tencent Video](https://v.qq.com/x/page/u0914vsm901.html)


## Tab: tab multimap

> * class pyecharts.charts.Tab*

```python
class Tab(
    ## HTML title
    page_title: str = "Awesome-pyecharts",

    # Remote HOST, defaults to "https://assets.pyecharts.org/assets/"
    js_host: str = ""
)
```

> *func pyecharts.charts.Tab.add*

``` python
def add(
    # arbitrary chart types
    chart,

    # the name of the tab
    tab_name
):
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Tab/README)

## Timeline: Timeline rotating multiple images

> *class pyecharts.charts.Timeline*

```python
class Timeline(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Timeline.add_schema*

``` python
def add_schema(
    # Coordinate axis type. Optional.
    # 'value': numeric axis, for continuous data.
    # 'category': category axis, for discrete category data, for this type the category data must be set via data.
    # 'time': time axis, for continuous temporal data, compared to the numeric axis the time axis is formatted with time and has a different scale calculation.
    # 'log': The time axis, for continuous temporal data, has a formatting of time compared to the numeric axis and differs in the scale calculation, e.g. whether to use a month, week, day or hour scale depending on the span.
    # 'log' logarithmic axis. Applies to logarithmic data.
    axis_type: str = "category",
    
    # The type of the time axis. Optional:
    # 'horizontal': horizontal
    # 'vertical': vertical
    orient: str = "horizontal",

    # The graph of the timeline marker.
    # The types of markers provided by ECharts include 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 
    # 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    symbol: Optional[str] = None,

    # The size of the timeline marker, which can be set to a single number such as 10, or an array of separate widths and heights.
    # For example, [20, 10] means the marker is 20 wide and 10 high.
    symbol_size: Optional[Numeric] = None,

    # Indicates the speed of play (the interval between beats) in milliseconds (ms).
    play_interval: Optional[Numeric] = None,

    # Indicates the position of the play button. Optional values: 'left', 'right'.
    control_position: str = "left",

    # Whether to play automatically.
    is_auto_play: bool = False,

    # Whether to loop play.
    is_loop_play: bool = True,

    # Whether to play in reverse.
    is_rewind_play: bool = False,

    # Whether or not to display the timeline component. If set to false, it will not be shown, but the function will still exist.
    is_timeline_show: bool = True,
    
    # Whether to put the timeline in reverse, if so the first one will be reversed
    is_inverse: bool = False,

    # The distance of the timeline component from the left side of the container.
    # The value of left can be a specific pixel value like 20, or a percentage of the container's height and width like '20%'.
    # It can also be 'left', 'centre', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position
    pos_left: Optional[str] = None,

    # The distance of the timeline component from the right side of the container.
    The value of # right can be a specific pixel value like 20, or a percentage relative to the container's height and width like '20%'.
    pos_right: Optional[str] = None,

    # The distance of the timeline component from the top side of the container.
    # The value of left can be a specific pixel value like 20, or a percentage of the container's height and width like '20%'.
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of left is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position
    pos_top: Optional[str] = None,

    # The distance of the timeline component from the lower side of the container.
    The value of # bottom can be a specific pixel value like 20, or a percentage relative to the container height and width like '20%'.
    pos_bottom: Optional[str] = "-5px",
    
    # The width of the timeline area, affecting the distance between the timeline's axis labels and the axis when vertical
    width: Optional[str] = None,
    
    # The height of the timeline area
    height: Optional[str] = None,
    
    # The axis configuration for the timeline, see `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict, None] = None,
    
    # Axis labels for the timeline, refer to `series_options.LabelOpts`
    label_opts: Optional[opts.LabelOpts] = None,
    
    # The graphical style of the timeline, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # Graphic styles
    graphic_opts: types.Graphic = None,

    # The graphic style of the 'current item' (checkpoint).
    checkpointstyle_opts: types.TimeLinkCheckPoint = None,

    # The style of the 'control button'. "The 'control buttons' include: 'play button', 'forward button', 'back button'.
    controlstyle_opts: types.TimeLineControl = None,
    
    # Line styles in the progress bar
    progress_linestyle_opts: types.LineStyle = None,
    
    # The style of the inflection point in the progress bar.
    progress_itemstyle_opts: types.ItemStyle = None,
    
    # The style of the label in the progress bar.
    progress_label_opts: types.Label = None,
)
```

> *func pyecharts.charts.Timeline.add*

``` python
def add(
    # chart instance
    chart: Base, 

    # time_point
    time_point: str
)
```

### TimeLinkCheckPoint: Timeline checkpoint style configuration

```python
class TimelineCheckPointerStyle(
    # ECharts provides marker types such as 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    # The icon can be set to an arbitrary vector path by 'path://'.
    # This way you don't have to worry about jaggies or blurring due to scaling compared to using images, and can be set to any colour.
    # The path graphic adapts itself to the right size. See SVG PathData for the format of paths.
    # Can be edited and exported from tools such as Adobe Illustrator.
    symbol: str = "circle",

    # The size of the marker.
    symbol_size: Union[Numeric, Sequence[Numeric]] = 13,

    # The angle of rotation (not radians) of the marker. A positive value indicates a counterclockwise rotation.
    symbol_rotate: Optional[Numeric] = None,

    # If symbol is of the form path://, whether to keep the aspect ratio of the figure when scaling.
    symbol_keep_aspect: bool = False,

    # The offset of the symbol relative to its original position.
    symbol_offset: Optional[Sequence[Union[str, Numeric]]] = None,
    
    # The colour of the 'current item' (checkpoint).
    color: str = "#c23531",

    # The border width of the 'current item' (checkpoint).
    border_width: Numeric = 5,

    # The border colour of the 'current item' (checkpoint).
    border_color: str = "rgba(194,53,49,0.5)",

    # Whether the movement of the checkpoint in the timeline play switch is animated.
    is_animation: bool = True,

    # The duration of the checkpoint's animation.
    animation_duration: Numeric = 300,

    # The easing effect of the checkpoint's animation.
    animation_easing: str = "quinticInOut",
)
```

### TimelineControlStyle: Timeline control button style

```python
class TimelineControlStyle(
    ### Show or not show 'control buttons'. Set to false to show none.
    is_show: bool = True,

    # Whether or not to show the 'play button'.
    is_show_play_button: bool = True,

    # Whether to show the 'back button' or not.
    is_show_prev_button: bool = True,

    # Whether to show the 'forward button'.
    is_show_next_button: bool = True,

    # The size of the 'control button', in pixels (px).
    item_size: Numeric = 22,

    # The spacing of the 'control button' in pixels (px).
    item_gap: Numeric = 12,

    # The position of the 'control button'.
    # When timeline.orient is 'horizontal', 'left' and 'right' are valid.
    # When timeline.orient is 'vertical', 'top' and 'bottom' are valid.
    position: str = 'left',

    # The graphical representation of the 'playable state' of the 'play button'.
    # Can be set to an image via 'image://url', where URL is the link to the image, or dataURI.
    # The icon can be set to an arbitrary vector path via 'path://'.
    # This way you don't have to worry about jaggedness or blurring due to scaling compared to using images, and can be set to any colour.
    # The path graphic adapts itself to the right size. See SVG PathData for the format of paths.
    # Can be edited and exported from tools such as Adobe Illustrator.
    play_icon: Optional[str] = None,

    # Same as above
    stop_icon: Optional[str] = None,

    # Same as above
    prev_icon: Optional[str] = None,

    # ditto
    next_icon: Optional[str] = None,

    # The button colour.
    color: str = "#304654",

    # The button border colour.
    border_color: str = "#304654",

    # The width of the button border line.
    border_width: Numeric = 1,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Timeline/README)
