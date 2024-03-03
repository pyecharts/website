> A first look at the global configuration component

> **Note: The section on configuration items should be read in conjunction with the example in the section on diagram types. **Note: The configuration items section should be read in conjunction with the example section in the chart types chapter.

Global configuration items can be set via the `set_global_opts` method

![](https://user-images.githubusercontent.com/19553554/57307650-8a4d0280-7117-11e9-921f-69b8e9c5e4aa.png)
![](https://user-images.githubusercontent.com/19553554/58749659-3554a000-84bb-11e9-9421-b1905e2f3430.png)

## AnimationOpts: Echarts drawing animation configuration items
> *class pyecharts.options.Animation*

```python
class AnimationOpts(
    # Whether to turn on animation, default is True to turn it on.
    animation: bool = True,
    
    # Threshold for whether to turn on animation, which will be turned off when the number of graphics displayed in a single series is greater than this threshold. Default 2000.
    animation_threshold: Numeric = 2000,
    
    # The length of the initial animation, the default value is 1000.
    # Callback functions are supported to enable more dramatic initial animation effects by returning a different delay time for each data.
    animation_duration: Union[Numeric, JSFunc] = 1000,
    
    # The jogging effect of the initial animation.
    # Different easing effects can be found in the easing example (https://www.echartsjs.com/gallery/editor.html?c=line-easing).
    animation_easing: Union[str] = "cubicOut",
    
    # The delay of the initial animation, default value is 0.
    # Callback functions are supported to enable more dramatic initial animation effects by returning a different delay time for each data.
    animation_delay: Union[Numeric, JSFunc] = 0,
    
    # The duration of the data update animation, the default is 300.
    # Callback functions are supported to allow more dramatic update animations by returning a different delay time for each data.
    animation_duration_update: Union[Numeric, JSFunc] = 300,
    
    # The jogging effect of the data update animation.
    # Different easing effects can be found in, easing example (https://www.echartsjs.com/gallery/editor.html?c=line-easing).
    animation_easing_update: Union[Numeric] = "cubicOut",
    
    # The delay of the data update animation, default value is 0.
    # Callback functions are supported to allow for more dramatic update animations by returning a different delay time for each data.
    animation_delay_update: Union[Numeric, JSFunc] = 0,
)
```

## AriaLabelOpts: Accessible label configuration items
> *class pyecharts.options.AriaLabelOpts*

```python
class AriaLabelOpts(
    # Whether to turn on accessibility label generation. The aria-label attribute will be generated when enabled.
    is_enable: bool = True,
    
    # The algorithm is used to automatically generate the chart description by default, if the user needs to fully customize it, this value can be set to description.
    # If this is set to 'This is a chart showing the price movement'
    # then the value of the aria-label attribute of the chart DOM element will be this string.
    # This is often used when displaying a single piece of data does not show the content of the chart
    # The user displays text that specifies a general description of the chart.
    # For example, if the chart is a map with a large number of scatter plots, the default algorithm only shows the location of the data points
    # It does not convey the author's intention as a whole.
    # In this case, it is sufficient to specify description as what the author wants to say.
    description: Optional[str] = None,
    
    # An overall description of the chart.
    # If title.text exists for the chart, use withTitle.
    # This includes the template variable {title}: this will be replaced with the chart's title.text.
    general_with_title: str = "This is a chart about "{title}"." ,
    
    # If the chart does not have title.text, then use withoutTitle.
    general_without_title: str = "This is a chart on ",
    
    # The maximum number of series to appear in the description.
    series_max_count: int = 10,
    
    # For the overall description of all series, displayed before each series description. This includes the template variables.
    # {seriesCount}: will be replaced with the number of series, always 1 here.
    series_single_prefix: str = "",
    
    # If the series has a name attribute, the description is used. This includes the template variables.
    # {seriesName}: will be replaced with the name of the series.
    # {seriesType}: will be replaced with the name of the type of the series, e.g. 'bar chart', 'line chart', etc.
    series_single_with_name: str = "The chart type is {seriesType} for {seriesName}." ,
    
    # If the series does not have a name attribute, then this description is used. This includes the template variables.
    # {seriesType}: will be replaced with the name of the type of the series, e.g. 'bar chart', 'line chart', etc.
    series_single_without_name: str = "The chart type is {seriesType}." ,
    
    # For a holistic description of all series, displayed before each series description. This includes the template variables.
    # {seriesCount}: will be replaced with the number of series.
    series_multiple_prefix: str = "It consists of {seriesCount} chart series." ,
    
    # If the series has a name attribute, this description is used. This includes the template variables.
    # {seriesName}: will be replaced with the name of the series.
    # {seriesType}: will be replaced with the name of the type of series, e.g. 'bar chart', 'line chart', etc.
    series_multiple_with_name: str = "The chart type is {seriesType} for {seriesName}." ,
    
    # If the series does not have a name attribute, then this description is used. This includes the template variables.
    # {seriesType}: will be replaced with the name of the type of the series, e.g. 'bar chart', 'line chart', etc.
    series_multiple_without_name: str = "The chart type is {seriesType}." ,
    
    # The separator after the last series except for the last series.
    series_multiple_separator_middle: str = ";",
    
    # The separator after the last series.
    series_multiple_separator_end: str = "." ,
    
    # The maximum number of data that can appear in each series in the description.
    data_max_count: int = 10,
    
    # The description to be used when all data is displayed. This configuration item will not cause the data to be displayed in its entirety.
    # This can be achieved by setting aria.data.maxCount to Number.MAX_VALUE.
    data_all_data: str = "The data is --",
    
    # The description used when only some of the data is displayed. This includes the template variables.
    # {displayCnt}: the number of pieces of data that will be replaced with the display.
    data_partial_data: str = "where the first {displayCnt} item is --",
    
    # If the data has a name attribute, that description is used. This includes the template variables.
    # {name}: will be replaced with the name of the data.
    # {value}: will be replaced with the value of the data.
    data_with_name: str = "The data for {name} is {value}",
    
    # If the data does not have a name attribute, this description is used. This includes the template variables.
    # {value}: the value that will be replaced with the data.
    data_without_name: str = "{value}",
    
    # The separator character after the last piece of data except.
    data_separator_middle: str = ",",
    
    # The separator after the last piece of data.
    # Note that usually the last data is followed by the series separator.end
    # So data.separator.end is the empty string in most cases.
    data_separator_end: str = "",
)
```

## AriaLabelOpts: Accessible Label Configuration Items
> *class pyecharts.options.AriaLabelOpts*

```python
class AriaLabelOpts(
    # Whether to turn on accessibility label generation. The aria-label attribute will be generated when enabled.
    is_enable: bool = True,
    
    # The algorithm is used to automatically generate the chart description by default, if the user needs to fully customize it, this value can be set to description.
    # If this is set to 'This is a chart showing the price movement'
    # then the value of the aria-label attribute of the chart DOM element will be this string.
    # This is often used when displaying a single piece of data does not show the content of the chart
    # The user displays text that specifies a general description of the chart.
    # For example, if the chart is a map with a large number of scatter plots, the default algorithm only shows the location of the data points
    # It does not convey the author's intention as a whole.
    # In this case, it is sufficient to specify description as what the author wants to say.
    description: Optional[str] = None,
    
    # An overall description of the chart.
    # If title.text exists for the chart, use withTitle.
    # This includes the template variable {title}: this will be replaced with the chart's title.text.
    general_with_title: str = "This is a chart about "{title}"." ,
    
    # If the chart does not have title.text, then use withoutTitle.
    general_without_title: str = "This is a chart on ",
    
    # The maximum number of series to appear in the description.
    series_max_count: int = 10,
    
    # For the overall description of all series, displayed before each series description. This includes the template variables.
    # {seriesCount}: will be replaced with the number of series, always 1 here.
    series_single_prefix: str = "",
    
    # If the series has a name attribute, the description is used. This includes the template variables.
    # {seriesName}: will be replaced with the name of the series.
    # {seriesType}: will be replaced with the name of the type of the series, e.g. 'bar chart', 'line chart', etc.
    series_single_with_name: str = "The chart type is {seriesType} for {seriesName}." ,
    
    # If the series does not have a name attribute, then this description is used. This includes the template variables.
    # {seriesType}: will be replaced with the name of the type of the series, e.g. 'bar chart', 'line chart', etc.
    series_single_without_name: str = "The chart type is {seriesType}." ,
    
    # For a holistic description of all series, displayed before each series description. This includes the template variables.
    # {seriesCount}: will be replaced with the number of series.
    series_multiple_prefix: str = "It consists of {seriesCount} chart series." ,
    
    # If the series has a name attribute, this description is used. This includes the template variables.
    # {seriesName}: will be replaced with the name of the series.
    # {seriesType}: will be replaced with the name of the type of series, e.g. 'bar chart', 'line chart', etc.
    series_multiple_with_name: str = "The chart type is {seriesType} for {seriesName}." ,
    
    # If the series does not have a name attribute, then this description is used. This includes the template variables.
    # {seriesType}: will be replaced with the name of the type of the series, e.g. 'bar chart', 'line chart', etc.
    series_multiple_without_name: str = "The chart type is {seriesType}." ,
    
    # The separator after the last series except for the last series.
    series_multiple_separator_middle: str = ";",
    
    # The separator after the last series.
    series_multiple_separator_end: str = "." ,
    
    # The maximum number of data that can appear in each series in the description.
    data_max_count: int = 10,
    
    # The description to be used when all data is displayed. This configuration item will not cause the data to be displayed in its entirety.
    # This can be achieved by setting aria.data.maxCount to Number.MAX_VALUE.
    data_all_data: str = "The data is --",
    
    # The description used when only some of the data is displayed. This includes the template variables.
    # {displayCnt}: the number of pieces of data that will be replaced with the display.
    data_partial_data: str = "where the first {displayCnt} item is --",
    
    # If the data has a name attribute, that description is used. This includes the template variables.
    # {name}: will be replaced with the name of the data.
    # {value}: will be replaced with the value of the data.
    data_with_name: str = "The data for {name} is {value}",
    
    # If the data does not have a name attribute, this description is used. This includes the template variables.
    # {value}: the value that will be replaced with the data.
    data_without_name: str = "{value}",
    
    # The separator character after the last piece of data except.
    data_separator_middle: str = ",",
    
    # The separator after the last piece of data.
    # Note that usually the last data is followed by the series separator.end
    # So data.separator.end is the empty string in most cases.
    data_separator_end: str = "",
)
```

## AriaDecalOpts: accessibility decal configuration item
> *class pyecharts.options.AriaDecalOpts*

```python
class AriaDecalOpts(
    # Whether or not to show decal patterns, the default is not to show them. If you want to show decals.
    # You need to ensure that aria.enabled and aria.decal.show are both true.
    is_show: bool = False,
    
    # The decal pattern
    # The types of markers provided by ECharts include
    # 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow', 'none'
    # Can also be a URL or SVG path
    decals_symbol: Union[str, Sequence] = "rect",
    
    # The range of values: 0 to 1, indicating the percentage of the pattern area.
    decals_symbol_size: Numeric = 1,
    
    # Whether to keep the aspect ratio of the pattern.
    decals_symbol_keep_aspect: bool = True,
    
    # The colour of the decal pattern, a semi-transparent colour is recommended so that it can be superimposed on the colour of the collection itself.
    decals_color: str = "rgba(0, 0, 0, 0, 0.2)",
    
    # The background colour of the decal, which will be overlaid on top of the colour of the collection itself and underneath the decal pattern.
    decals_background_color: Optional[str] = None,
    
    # The horizontal configuration of the decal pattern
    decals_dash_array_x: Union[Numeric, Sequence] = 5,
    
    # Vertical configuration of the applique pattern
    decals_dash_array_y: Union[Numeric, Sequence] = 5,
    
    # The overall angle of rotation of the pattern (in radians), from -Math.PI to Math.
    decals_rotation: Numeric = 0,
    
    # The upper limit of the width of the generated pattern before it is repeated.
    # Usually not needed to set this value, try increasing it when you find that the pattern has discontinuous seams when it repeats.
    decals_max_tile_width: Numeric = 512,
    
    # The maximum height of the generated pattern before it is repeated.
    # Usually not needed, try increasing this value when you find that the pattern has discontinuous seams when it repeats.
    decals_max_tile_height: Numeric = 512,
)
```

## InitOpts: initialise configuration items
> *class pyecharts.options.InitOpts*

``` python
class InitOpts(
    ## Chart canvas width, css length units.
    width: str = "900px",

    # The height of the chart canvas, in css units of length.
    height: str = "500px",

    # Chart ID, the unique identifier of the chart, used to distinguish it in case of multiple charts.
    chart_id: Optional[str] = None,

    # Rendering style, optional "canvas", "svg"
    # Refer to the `global variables` section
    renderer: str = RenderType.CANVAS,

    # Page title
    page_title: str = "Awesome-pyecharts",

    # Chart theme
    theme: str = "white",

    # Chart background colour
    bg_color: Optional[str] = None,

    # Remote js host, defaults to https://assets.pyecharts.org/assets/ if not set"
    # Refer to the `Global Variables` section
    js_host: str = "",
    
    # Draw animation initialization configuration, refer to `global_options.AnimationOpts`
    animation_opts: Union[AnimationOpts, dict] = AnimationOpts(),
)
```

## RenderOpts: Render configuration items
> *class pyecharts.options.RenderOpts*

```python
class RenderOpts(
    # Whether to embed JS files when rendering HTML
    is_embed_js: bool = False
)
```

## ToolBoxFeatureSaveAsImagesOpts: toolbox save image configuration items
> *class pyecharts.options.ToolBoxFeatureSaveAsImagesOpts*

```python
class ToolBoxFeatureSaveAsImageOpts(
    # The format of the saved images. Supports 'png' and 'jpeg'.
    type_: str = "png",
    
    # The name of the saved file, the default is to use title.text as the name.
    name: Optional[str] = None,
    
    # The background colour of the saved image, the default is backgroundColor, if backgroundColor does not exist it will take white.
    background_color: str = "auto",
    
    # If the chart uses echarts.connect to link multiple charts, the linked charts will be exported when the image is exported. This configuration item determines the fill colour for the gaps between charts.
    connected_background_color: str = "#fff",
    
    # List of components to ignore when saving as an image, toolbars are ignored by default.
    exclude_components: Optional[Sequence[str]] = None,
    
    # Whether to show the tool.
    is_show: bool = True,
    
    # Prompt
    title: str = "Save as image",
    
    # Can be set to an image by 'image://url', where URL is the link to the image, or dataURI.
    icon: Optional[JSFunc] = None,
    
    # The resolution ratio of the saved image, the default is the same size as the container, if you need to save a higher resolution, you can set it to a value greater than 1, e.g. 2.
    pixel_ratio: Numeric = 1,
):
```

## ToolBoxFeatureRestoreOpts: toolbox restore configuration items
> *class pyecharts.options.ToolBoxFeatureRestoreOpts*

```python
class ToolBoxFeatureRestoreOpts(
    # Whether to show this tool.
    is_show: bool = True, 
    
    # Prompt
    title: str = "restore", 
    
    # Can be set to an image by 'image://url', where URL is the link to the image, or dataURI.
    icon: Optional[JSFunc] = None
):
```

## ToolBoxFeatureDataViewOpts: toolbox data view tools
> *class pyecharts.options.ToolBoxFeatureDataViewOpts*

```python
class ToolBoxFeatureDataViewOpts(
    # Whether to show this tool.
    is_show: bool = True, 
        
    # Prompt
    title: str = "restore", 
        
    # Can be set to an image by 'image://url', where URL is the link to the image, or dataURI.
    icon: Optional[JSFunc] = None
    
    # Whether to be non-editable (read-only). Default is False
    is_read_only: bool = False,

    # Custom dataView presentation function to replace the default textarea for richer data editing. Can return dom objects or html strings.
    option_to_content: Optional[JSFunc] = None,
    
    # In the case of optionToContent, if it supports refreshing after data editing, you will need to implement the logic for assembling the option yourself with this function.
    content_to_option: Optional[JSFunc] = None,
    
    # There are three words on the data view, the default is ['data_view', 'close', 'refresh'].
    lang: Optional[Sequence[str]] = None,
    
    # The floating background colour of the data view.
    background_color: str = "#fff",
    
    # The background colour of the floating text input area of the data view.
    text_area_color: str = "#fff",
    
    # The border colour of the floating text input area of the data view.
    text_area_border_color: str = "#333",
    
    # Text colour.
    text_color: str = "#000",
    
    # The button colour.
    button_color: str = "#c23531",
    
    # The button text colour.
    button_text_color: str = "#fff",
):
```

## ToolBoxFeatureDataZoomOpts: toolbox area zoom configuration items
> *class pyecharts.options.ToolBoxFeatureDataZoomOpts*

```python
class ToolBoxFeatureDataZoomOpts(
    # Whether to show this tool.
    is_show: bool = True,
    
    # Prompt
    zoom_title: str = "Zone zoom",
    
    # Prompt
    back_title: str = "Area zoom restore",
    
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    zoom_icon: Optional[JSFunc] = None,
    
    # Can be set to an image with 'image://url', where the URL is a link to the image, or a dataURI.
    back_icon: Optional[JSFunc] = None,
    
    # Specifies which xAxis are to be controlled. If default then all x-axes are controlled.
    # If set to false does not control any x-axis. If set to 3 then the x-axis with axisIndex 3 is controlled.
    # If set to [0, 3] then controls the x-axis with axisIndex of 0 and 3.
    xaxis_index: Union[Numeric, Sequence, bool] = None,
    
    # Specifies which yAxis are to be controlled. If default, all y-axes are controlled.
    # If set to false does not control any y-axis. If set to 3 controls the y-axis with axisIndex 3.
    # If set to [0, 3] then controls the y-axis with axisIndex of 0 and 3.
    yaxis_index: Union[Numeric, Sequence, bool] = None,

    # dataZoom works by filtering the data and setting the display window of the axis internally to achieve the effect of scaling the data window.
    # 'filter': data outside the current data window, is filtered out. i.e. it affects the data range of the other axes.
    # For each data item, as long as one dimension is outside the data window, the whole data item is filtered out.
    # 'weakFilter': data outside the current data window, is filtered out. I.e. it affects the data range of the other axes.
    # Each data item, the whole data item is filtered out only if all dimensions are outside the same side of the data window.
    # 'empty': data outside the current data window, is set to empty. I.e. it does not affect the data range of the other axes.
    # 'none': No data is filtered, only the range of the number axis is changed.
    filter_mode: str = "filter",
):
```

## ToolBoxFeatureMagicTypeOpts: toolbox dynamic type switching configuration item
> *class pyecharts.options.ToolBoxFeatureMagicTypeOpts*

```python
class ToolBoxFeatureMagicTypeOpts(
    # Whether to show this tool.
    is_show: bool = True,
    
    # Dynamic types enabled
    # Includes 'line' (switch to line chart), 'bar' (switch to bar chart),
    # 'stack' (switch to stack mode), 'tiled' (switch to tiled mode)
    type_: Optional[Sequence] = None,    

    # The text of each type of title, which can be configured separately.
    line_title: str = "Switch to tiled mode",
    
    # The text of the title for each type, which can be configured separately.
    bar_title: str = "Switch to bar chart",
    
    # The text of the title for each type, which can be configured separately.
    stack_title: str = "Switch to stack",
    
    # The text of each type of title, which can be configured separately.
    tiled_title: str = "Toggle to tiled",
    
    # The icon path for each type, which can be configured separately.
    line_icon: Optional[JSFunc] = None,
    
    # The icon path for each type, which can be configured separately.
    bar_icon: Optional[JSFunc] = None,
    
    # The icon path for each type, can be configured separately.
    stack_icon: Optional[JSFunc] = None,
    
    # The icon path for each type, can be configured separately.
    tiled_icon: Optional[JSFunc] = None,
):
```

## ToolBoxFeatureBrushOpts: toolbox checkbox component configuration items
> *class pyecharts.options.ToolBoxFeatureBrushOpts*

```python
class ToolBoxFeatureBrushOpts(
    # The button to use, taking the following values.
    # 'rect': turns on rectangular checkbox selection.
    # 'polygon': turns on arbitrary shape checkbox selection.
    # 'lineX': enables horizontal selection.
    # 'lineY': enables vertical selection.
    # 'keep': toggles between 'single' and 'multiple' selection. The latter allows multiple checkboxes to be drawn at the same time. The former supports clearing all checkboxes with a single click.
    # 'clear': clears all checkboxes.
    type_: Optional[str] = None,

    # The icon path for each button.
    rect_icon: Optional[JSFunc] = None,
    
    # The icon path for each button.
    polygon_icon: Optional[JSFunc] = None,
    
    # The icon path for each button.
    line_x_icon: Optional[JSFunc] = None,
    
    # The icon path for each button.
    line_y_icon: Optional[JSFunc] = None,
    
    # The icon path for each button.
    keep_icon: Optional[JSFunc] = None,
    
    # The icon path for each button.
    clear_icon: Optional[JSFunc] = None,
    
    # The title text.
    rect_title: str = "Rectangle Selection",
    
    # The title text.
    polygon_title: str = "Circle Selection",
    
    # Title text.
    line_x_title: str = "Horizontal selection",
    
    # Title text.
    line_y_title: str = "Portrait selection",
    
    # The text of the title.
    keep_title: str = "Keep Selection",
    
    # The text of the title.
    clear_title: str = "Clear selection",
):
```

## ToolBoxFeatureOpts: Toolbox tool configuration items
> *class pyecharts.options.ToolBoxFeatureOpts*

```python
class ToolBoxFeatureOpts(
    # Save as image
    save_as_image: Union[ToolBoxFeatureSaveAsImageOpts, dict] = ToolBoxFeatureSaveAsImageOpts(),
    
    # Configuration item restore    
    restore: Union[ToolBoxFeatureRestoreOpts, dict] = ToolBoxFeatureRestoreOpts(),
    
    # Data view tool that shows the data used in the current chart and can be dynamically updated after editing
    data_view: Union[ToolBoxFeatureDataViewOpts, dict] = ToolBoxFeatureDataViewOpts(),
    
    # Data area scaling. (currently only supports scaling in right-angle coordinate system)
    data_zoom: Union[ToolBoxFeatureDataZoomOpts, dict] = ToolBoxFeatureDataZoomOpts(),
    
    # Dynamic type switching.
    magic_type: Union[ToolBoxFeatureMagicTypeOpts, dict] = ToolBoxFeatureMagicTypeOpts(),
    
    # The control button for the checkbox component.
    brush: Union[ToolBoxFeatureBrushOpts, dict] = ToolBoxFeatureBrushOpts(),
)
```

## ToolboxOpts: Toolbox configuration items
> *class pyecharts.options.ToolboxOpts*

```python
class ToolboxOpts(
    # Whether to show the toolbox components
    is_show: bool = True,

    # The layout orientation of the toolbar icon.
    # Optional: 'horizontal', 'vertical'
    orient: str = "horizontal",

    # The distance of the toolbar component from the left side of the container.
    # The value of left can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'left', 'centre', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position
    pos_left: str = "80%",

    # The distance of the toolbar component from the right side of the container.
    The value of # right can be a specific pixel value like 20, or a percentage relative to the container height and width like '20%'.
    pos_right: Optional[str] = None,

    # The distance of the toolbar component from the top side of the container.
    # The value of top can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'.
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Optional[str] = None,

    # The distance of the toolbar component from the lower side of the container.
    The value of # bottom can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'.
    pos_bottom: Optional[str] = None,

    # Configuration items for each tool, see `global_options.ToolBoxFeatureOpts`
    feature: Union[ToolBoxFeatureOpts, dict] = ToolBoxFeatureOpts(),
)
```

## BrushOpts: Area selection component configuration item
> *class pyecharts.options.BrushOpts*

```python
class BrushOpts(
    # The button to use in the toolbox. Default values are ["rect", "polygon", "keep", "clear"]
    # The brush-related toolbox buttons are.
    # "rect": Enables rectangular checkbox selection.
    # "polygon": Enables the selection of arbitrary shape checkboxes.
    # "lineX": Enables horizontal selection.
    # "lineY"': enables vertical selection.
    # "keep": toggles between "single" and "multiple" selection. The latter supports drawing multiple checkboxes at the same time. The former supports clearing all checkboxes with a single click.
    # "clear": Clears all checkboxes.
    tool_box: Optional[Sequence] = None,
    
    # The selected items can be linked between different series.
    # The brush_link configuration item is a list with seriesIndex specifying which series can be linked.
    # For example it could be.
    # [3, 4, 5] means that series with seriesIndex 3, 4, 5 can be linked.
    # "all" means that all series are brushLinked.
    # None means brush_link is not enabled.
    brush_link: Union[Sequence, str] = None,
    
    # Specifies which series can be brushed, and can take the following values.
    # "all": all series
    # A list of series indexes, e.g. [0, 4, 2], specifying the coordinate system to which these indexes correspond.
    # A series index, e.g. 0, indicates the coordinate system to which this index corresponds.
    series_index: Union[Sequence, Numeric, str] = None,
    
    # Specifies which geo's can be brushed. You can set whether the brush is global or part of a coordinate system.
    # Global brush
    # Brush anywhere in the echarts instance. This is the default. If not specified as a coordinate system brush, it is a global brush.
    # Coordinate system brush
    # Brush in the specified coordinate system. The checkbox can follow the zoom and translation (roam and dataZoom) of the coordinate system.
    # The coordinate system brush is actually more commonly used, especially in geo.
    # Specify which coordinate systems can be brushed in by specifying brush.geoIndex or brush.xAxisIndex or brush.yAxisIndex.
    # Specify which series can be brushed, which can take the following values.
    # "all": means all series
    # A list of series indexes, e.g. [0, 4, 2], specifying the coordinate systems to which these indexes correspond.
    # A series index, e.g. 0, indicates the coordinate system to which this index corresponds.
    geo_index: Union[Sequence, Numeric, str] = None,
    
    # Specifies which xAxisIndexes can be brushed. You can set whether the brush is global or belongs to the coordinate system.
    # Global brush
    # Brush anywhere in the echarts instance. This is the default. If brush is not specified as a coordinate system, it is a global brush.
    # Coordinate system brush
    # Brush in the specified coordinate system. The checkbox can follow the zoom and translation (roam and dataZoom) of the coordinate system.
    # The coordinate system brush is actually more commonly used, especially in geo.
    # Specify which coordinate systems can be brushed in by specifying brush.geoIndex or brush.xAxisIndex or brush.yAxisIndex.
    # Specify which series can be brushed, which can take the following values.
    # "all": means all series
    # A list of series indexes, e.g. [0, 4, 2], specifying the coordinate systems to which these indexes correspond.
    # A series index, e.g. 0, indicates the coordinate system to which this index corresponds.
    x_axis_index: Union[Sequence, Numeric, str] = None,
    
    # Specifies which yAxisIndexes can be brushed. You can set whether the brush is global or belongs to the coordinate system.
    # Global brush
    # Brush anywhere in the echarts instance. This is the default. If brush is not specified as a coordinate system, it is a global brush.
    # Coordinate system brush
    # Brush in the specified coordinate system. The checkbox can follow the zoom and translation (roam and dataZoom) of the coordinate system.
    # The coordinate system brush is actually more commonly used, especially in geo.
    # Specify which coordinate systems can be brushed in by specifying brush.geoIndex or brush.xAxisIndex or brush.yAxisIndex.
    # Specify which series can be brushed, which can take the following values.
    # "all": means all series
    # A list of series indexes, e.g. [0, 4, 2], specifying the coordinate systems to which these indexes correspond.
    # A series index, e.g. 0, indicates the coordinate system to which this index corresponds.
    y_axis_index: Union[Sequence, Numeric, str] = None,
    
    # The default brush type. The default value is rect.
    # The optional parameters are as follows.
    # "rect": rectangular checkbox.
    # "polygon": arbitrary shape checkbox.
    # "lineX": horizontal selection.
    # "lineY": vertical selection.
    brush_type: str = "rect",
    
    # The default mode of the brush. Can take the following values.
    # The default is single
    # "single": single selection.
    # "multiple": multiple selection.
    brush_mode: str = "single",
    
    # Whether already selected boxes can be reshaped or panned. The default value is True
    transformable: bool = True,
    
    # The default style of the checkbox, with a value of
    # {
    # "borderWidth": 1,
    # "color": "rgba(120,140,180,0.3)",
    # "borderColor": "rgba(120,140,180,0.8)"
    # },
    brush_style: Optional[dict] = None,
    
    # By default, the brushSelected event is fired constantly when the selection is swiped or moved, thus telling the outside world what is selected.
    # But frequent events can lead to performance problems or poor animation.
    # So the brush component provides brush.throttleType, brush.throttleDelay to solve this problem.
    # throttleType can take values such as.
    # "debounce": indicates that the event will only be triggered if the action has stopped (i.e. no action has been performed for a while). The time threshold is specified by brush.throttleDelay.
    # "fixRate": indicates that the event is triggered at a certain frequency, the time interval is specified by brush.throttleDelay.
    throttle_type: str = "fixRate",
    
    # The default is 0, which means throttle is not enabled.
    throttle_delay: Numeric = 0,
    
    # If brush_mode is "single", whether one click is supported to clear all checkboxes.
    remove_on_click: bool = True,
    
    # Defines the visual elements that are outside the selected range. The final parameters are configured in the form of a dictionary
    # The visual elements that can be selected are.
    # symbol: The graphical category of the graphic element.
    # symbolSize: The size of the graphic element.
    # color: The colour of the element.
    # colorAlpha: Transparency of the colour of the element.
    # opacity: the transparency of the element and of its appendages (e.g. text labels).
    # colorLightness: The lightness or darkness of the colour, see https://en.wikipedia.org/wiki/HSL_and_HSV.
    # colorSaturation: The saturation of the colour, see https://en.wikipedia.org/wiki/HSL_and_HSV.
    # colorHue: The hue of the colour, see https://en.wikipedia.org/wiki/HSL_and_HSV.
    out_of_brush: dict = None,
)
```

## TitleOpts: Title configuration items
> *class pyecharts.options.TitleOpts*

```python
class TitleOpts(
    # If or not to display the title component.
    is_show: bool = True,

    ## Main title text, supports line breaks with \n.
    title: Optional[str] = None,
    
    # main title jump URL link
    title_link: Optional[str] = None,
    
    # The main title jump link method
    # The default value is: blank
    # Optional arguments: 'self', 'blank'
    # 'self' current window open; 'blank' new window open
    title_target: Optional[str] = None,

    # Subtitle text, supports line breaks with \n.
    subtitle: Optional[str] = None,
    
    # subtitle jump URL link
    subtitle_link: Optional[str] = None,
    
    # Subtitle jump link method
    # The default value is: blank
    # Optional arguments: 'self', 'blank'
    # 'self' current window open; 'blank' new window open
    subtitle_target: Optional[str] = None,

    # The distance of the title component from the left side of the container.
    # The value of left can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'
    # It can also be 'left', 'centre', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: Optional[str] = None,

    # The distance of the title component from the right side of the container.
    The value of # right can be a specific pixel value like 20, or it can be a percentage relative to the container height and width like '20%'.
    pos_right: Optional[str] = None,

    # The distance of the title component from the top side of the container.
    # The value of top can be a specific pixel value like 20, or a percentage of the container's height and width like '20%'.
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Optional[str] = None,

    # The distance of the title component from the lower side of the container.
    The value of # bottom can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'.
    pos_bottom: Optional[str] = None,

    # Header inner margins in px, default inner margins are 5 in each direction, accepts an array to set the top right and bottom left margins respectively.
    # // Set the inner margin to 5
    # padding: 5
    # // set the top and bottom inner margins to 5 and the left and right inner margins to 10
    # padding: [5, 10]
    # // Set the inner margins in each of the four directions
    # padding: [
    # 5, // top
    # 10, // right
    # 5, // bottom
    # 10, // left
    # ]
    padding: Union[Sequence, Numeric] = 5,

    # Spacing between main and subheadings.
    item_gap: Numeric = 10,
    
    # Horizontal alignment of the whole (including text and subtext).
    # Optional values: 'auto', 'left', 'right', 'center'.
    text_align: str = "auto",
    
    # Vertical alignment of the whole (including text and subtext).
    # Optional values: 'auto', 'left', 'right', 'center'.
    text_vertical_align: str = "auto",
    
    # Whether or not to trigger the event.
    is_trigger_event: bool = False,

    # Main title text style configuration items, refer to `series_options.TextStyleOpts`
    title_textstyle_opts: Union[TextStyleOpts, dict, None] = None,

    # subtitle_textstyle_opts, see `series_options.TextStyleOpts`
    subtitle_textstyle_opts: Union[TextStyleOpts, dict, None] = None,
)
```

## DataZoomOpts: zone zoom configuration items
> *class pyecharts.options.DataZoomOpts*

```python
class DataZoomOpts(
    # Whether to display the component. If set to false, it will not be shown, but the data filtering is still present.
    is_show: bool = True,

    # component type, optionally "slider", "inside"
    type_: str = "slider",
    
    # Whether to update the view of the series in real time when dragging. If set to false, updates only at the end of the drag.
    is_realtime: bool = True,

    # The starting percentage of the data window range. The range is: 0 ~ 100. means 0% ~ 100%.
    range_start: Union[Numeric, None] = 20,

    # The percentage of the end of the data window range. The range is: 0 ~ 100
    range_end: Union[Numeric, None] = 80,
    
    # The start value of the data window range. If start is set then startValue is invalidated.
    start_value: Union[int, str, None] = None,
    
    # The end value of the data window range. If end is set then endValue is invalid.
    end_value: Union[int, str, None] = None,

    # Whether the layout is horizontal or vertical. Not only the layout method, but also for the Cartesian coordinate system, determines, by default, whether the horizontal or vertical number axis is controlled
    # The optional values are: 'horizontal', 'vertical'
    orient: str = "horizontal",

    # Sets the x-axis controlled by the dataZoom-inside component (i.e. xAxis, a concept in the Cartesian coordinate system, see grid).
    # When not specified, when dataZoom-inside.orient is 'horizontal', the first xAxis parallel to the dataZoom is controlled by default
    # If number means control one axis, if Array means control multiple axes.
    xaxis_index: Union[int, Sequence[int], None] = None,

    # Sets the y-axis controlled by the dataZoom-inside component (i.e. yAxis, a concept in the Cartesian coordinate system, see grid).
    # When not specified, when dataZoom-inside.orient is 'horizontal', the first yAxis parallel to the dataZoom is controlled by default
    # If number means control one axis, if Array means control multiple axes.
    yaxis_index: Union[int, Sequence[int], None] = None,
    
    # Whether to lock the size of the selection area (or data window as it is called).
    # If set to true then the selection area is locked in size, i.e. it can only be panned, not zoomed.
    is_zoom_lock: bool = False,

    # The distance of the dataZoom-slider component from the left side of the container.
    # The value of left can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'left', 'centre', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: Optional[str] = None,

    # The distance of the dataZoom-slider component from the top side of the container.
    # The value of top can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Optional[str] = None,

    # The distance of the dataZoom-slider component from the right side of the container.
    The value of # right can be a specific pixel value like 20, or a percentage relative to the container height and width like '20%'.
    # Adaptive by default.
    pos_right: Optional[str] = None,

    # The distance of the dataZoom-slider component from the lower side of the container.
    # The value of bottom can be a specific pixel value like 20, or a percentage relative to the container's height and width like '20%'.
    # Adaptive by default.
    pos_bottom: Optional[str] = None,

    # dataZoom works by filtering the data and setting the display window of the axis internally to achieve the data window scaling effect.
    # 'filter': Data outside the current data window, is filtered out. i.e. it affects the data range of the other axes.
    # For each data item, as long as one dimension is outside the data window, the whole data item is filtered out.
    # 'weakFilter': data outside the current data window, is filtered out. I.e. it affects the data range of the other axes.
    # Each data item, the whole data item is filtered out only if all dimensions are outside the same side of the data window.
    # 'empty': data outside the current data window, is set to empty. I.e. it does not affect the data range of the other axes.
    # 'none': No data is filtered, only the range of the number axis is changed.
    filter_mode: str = "filter"
)
```

## LegendOpts: legend configuration items
> *class pyecharts.options.LegendOpts*

```python
class LegendOpts(
    ## The type of legend. Optional values.
    # 'plain': plain legend. The default is the plain legend.
    # 'scroll': scrollable legend. Can be used when the number of legends is high.
    type_: Optional[str] = None,
    
    # The legend selection mode, controls whether the series can be changed by clicking on the legend. Legend selection is enabled by default, and can be set to false to turn it off
    # This can also be set to 'single' or 'multiple' to use single or multiple selection mode.
    selected_mode: Union[str, bool, None] = None,

    # Whether to display the legend component
    is_show: bool = True,

    # The distance of the legend component from the left side of the container.
    # The value of left can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'.
    # It can also be 'left', 'centre', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: Union[str, Numeric, None] = None,

    # The distance of the legend component from the right side of the container.
    The value of # right can be a specific pixel value like 20, and can be a percentage relative to the container height and width like '20%'.
    pos_right: Union[str, Numeric, None] = None,

    # The distance of the legend component from the top side of the container.
    # The value of top can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Union[str, Numeric, None] = None,

    # The distance of the legend component from the lower side of the container.
    # The value of bottom can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'.
    pos_bottom: Union[str, Numeric, None] = None,

    # The layout orientation of the legend list. Optional: 'horizontal', 'vertical'
    orient: Optional[str] = None,
    
    # The alignment of the legend markers and text. Default automatic (auto)
    # Determined by the position and orientation of the component
    # Right-aligned when the component's left value is 'right' and when the vertical layout (orient is 'vertical') is 'right'.
    # Optional parameters: `auto`, `left`, `right`
    align: Optional[str] = None,
    
    # Legend inner margin in px, default inner margin is 5 in all directions
    padding: int = 5,

    # The spacing between each item in the legend. Horizontal spacing for horizontal layouts, vertical spacing for vertical layouts.
    # The default spacing is 10
    item_gap: int = 10,
    
    # The graphical width of the legend marker. Default width is 25
    item_width: int = 25,
    
    # The height of the legend marker graphic. The default height is 14
    item_height: int = 14,

    # The colour of the legend when it is closed. Default is #ccc
    inactive_color: Optional[str] = None,

    # Legend component font styles, see `series_options.TextStyleOpts`
    textstyle_opts: Union[TextStyleOpts, dict, None] = None,
    
    # The icon for the legend item.
    # ECharts provides markup types such as 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow', 'none'
    # Can be set to an image with 'image://url', where URL is the link to the image, or dataURI.
    # Can be set to an arbitrary vector path with 'path://'.
    legend_icon: Optional[str] = None,
    
    # The background color of the legend, transparent by default.
    background_color: Optional[str] = "transparent",
    
    # The border color of the legend. The supported color format is the same as backgroundColor.
    border_color: Optional[str] = "#ccc",
    
    # The border line width of the legend.
    border_width: int = 1,
    
    # The radius of the rounded corners, in px, support passing in an array to specify 4 radii each. For example:
    border_radius: Union[int, Sequence] = 0,
    
    # valid when legend.type is 'scroll'. The spacing between buttons and page information in the legend control block.
    page_button_item_gap: int = 5,
    
    # valid when legend.type is 'scroll'. The gap between the legend control block and the legend item.
    page_button_gap: Optional[int] = None,
    
    # Valid if legend.type is 'scroll'. The position of the legend control block. Optional values are.
    # 'start': the control block is on the left or top.
    # 'end': right or bottom of the legend.
    page_button_position: str = "end",
    
    # valid when legend.type is 'scroll'.
    # The format of the page information to be displayed in the legend control block. Default is '{current}/{total}', where {current} is the current page number (counting from 1) and {total} is the total number of pages.
    # If pageFormatter uses a function, it shall return a string with the following parameters.
    # {
    # current: number
    # total: number
    # total: number # }
    page_formatter: JSFunc = "{current}/{total}",
    
    # valid when legend.type is 'scroll'. Icon for the legend control block.
    page_icon: Optional[str] = None,
    
    # Valid if legend.type is 'scroll'. The color of the page flip button.
    page_icon_color: str = "#2f4554",
    
    # valid when legend.type is 'scroll'. The color of the page flip button when it is not active (i.e. when the page is turned to the top).
    page_icon_inactive_color: str = "#aaa",
    
    # valid when legend.type is 'scroll'.
    # The size of the page flip button. Can be a number or an array, e.g. [10, 3] for [width, height].
    page_icon_size: Union[int, Sequence] = 15,
    
    # If or not the legend page flip uses animation.
    is_page_animation: Optional[bool] = None,
    
    # The duration of the animation when the legend turns the page.
    page_animation_duration_update: int = 800,
    
    # The selector button in the legend component, currently includes both select all and deselect functions.
    # Not shown by default, user can turn it on manually or configure the title of each button manually.
    selector: Union[bool, Sequence] = False,
    
    # The position of the selector, it can be placed at the end or the head of the legend, the corresponding values are 'end' and 'start' respectively.
    # By default, when the legend is laid out horizontally, the selector is placed at the end of the legend; when the legend is laid out vertically, the selector is placed at the head of the legend.
    selector_position: str = "auto",
    
    # The spacing between selector buttons.
    selector_item_gap: int = 7,
    
    # The spacing between the selector button and the legend component.
    selector_button_gap: int = 10,
)
```

## VisualMapOpts: visual mapping configuration items
> *class pyecharts.options.VisualMapOpts*

```python
class VisualMapOpts(
    # Whether to show the visual mapping configuration
    is_show: bool = True,
    
    # Mapping transition type, optional, "color", "size"
    type_: str = "color",

    # Specifies the minimum value for the visualMapPiecewise component.
    min_: union[int, float] = 0,

    # Specifies the maximum value of the visualMapPiecewise component.
    max_: Union[int, float] = 100,

    # The text at each end, e.g. ['High', 'Low'].
    range_text: Union[list, tuple] = None,

    # visualMap component transition colour
    range_color: Union[Sequence[str]] = None,

    # visualMap component transition symbol size
    range_size: Union[Sequence[int]] = None,
    
    # The transparency of the visualMap element and its dependencies (e.g. text labels).
    range_opacity: Optional[Numeric] = None,

    # How to place the visualMap component, horizontally ('horizontal') or vertically ('vertical').
    orient: str = "vertical",

    # The distance of the visualMap component from the left side of the container.
    # The value of left can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'left', 'center', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: Optional[str] = None,

    # The distance of the visualMap component from the right side of the container.
    The value of # right can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'.
    pos_right: Optional[str] = None,

    # The distance of the visualMap component from the top side of the container.
    # The value of top can be a specific pixel value like 20, or a percentage of the container's height and width like '20%'.
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Optional[str] = None,

    # The distance of the visualMap component from the lower side of the container.
    The value of # bottom can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'.
    pos_bottom: Optional[str] = None,

    # For continuous data, automatically cut into equal segments. The default is 5 segments. The range of continuous data needs to be specified by max and min
    split_number: int = 5,
    
    # Specifies which series of data to take, defaults to all series.
    series_index: Union[Numeric, Sequence, None] = None,

    # The component mapping dimension
    dimension: Optional[Numeric] = None,

    # Whether to show the handle for dragging (the handle can be dragged to adjust the selection range).
    is_calculable: bool = True,

    # Whether to be segmented or not
    is_piecewise: bool = False,
    
    # Whether to invert the visualMap component
    is_inverse: bool = False,

    # The decimal precision of the data display.
    # Average segmentation of continuous data, with precision automatically adapted to the data.
    # Custom segmentation for continuous data or segmentation mode for discrete data based on category, precision defaults to 0 (no decimals).
    precision: Optional[int] = None,

    # Custom range for each segment, and text for each segment, and special style for each segment. For example.
    # pieces: [
    # {"min": 1500}, // Do not specify max, indicating that max is infinity.
    # {"min": 900, "max": 1500},
    # {"min": 310, "max": 1000},
    # {"min": 200, "max": 300},
    # {"min": 10, "max": 200, "label": '10 to 200 (custom label)'},
    # {"value": 123, "label": '123 (custom special colour)', "colour": 'grey'}, // indicates a value equal to 123
    # {"max": 5} // no min is specified, indicating that min is infinity (-Infinity)
    # ]
    pieces: Optional[Sequence] = None,
    
    # {"max": 5} // Do not specify min to indicate that min is infinity (-Infinity). (The user can interact with the visualMap component to select the range with the mouse or touch)
    # The optional visual elements are.
    # symbol: The graphical category of the element.
    # symbolSize: The size of the symbol.
    # color: The colour of the element.
    # colorAlpha: Transparency of the colour of the symbol.
    # opacity: the transparency of the element and of its appendages (e.g. text labels).
    # colorLightness: The lightness or darkness of the colour, see HSL.
    # colorSaturation: The saturation of the colour, see HSL.
    # colorHue: The hue of the colour, see HSL.
    out_of_range: Optional[dict] = None,
    
    # The width of the graphic, i.e. the width of the long bar.
    item_width: int = 0,

    # The height of the graphic, i.e. the height of the bar.
    item_height: int = 0,
    
    # The background colour of the visualMap component.
    background_color: Optional[str] = None,
    
    # The border colour of the visualMap component.
    border_color: Optional[str] = None,
    
    # The border width of the visualMap component, in px.
    border_width: int = 0,
    
    # Text style options, refer to `series_options.TextStyleOpts`.
    textstyle_opts: Union[TextStyleOpts, dict, None] = None,
)
```

## TooltipOpts: prompt box configuration items
> *class pyecharts.options.TooltipOpts*

```python
class TooltipOpts(
    # Whether to show the prompt box component, including the prompt box float and axisPointer.
    is_show: bool = True,

    # Trigger type. Optional.
    # 'item': data item graph trigger, mainly used in scatter charts, pie charts and other charts without classed axes.
    # 'axis': trigger for coordinate axes, mainly used in bar charts, line charts, etc. that use classed axes.
    # 'none': Triggers nothing
    trigger: str = "item",

    # The condition for the prompt box to trigger, optionally.
    # 'mousemove': trigger on mouse movement.
    # 'click': Triggered on mouse click.
    # 'mousemove|click': triggered by both mouse movement and click.
    # 'none': does not trigger on 'mousemove' or 'click'.
    trigger_on: str = "mousemove|click",

    # Indicator type. Optional
    # 'line': straight line indicator
    # 'shadow': shadow indicator
    # 'none': no indicator
    # 'cross': crosshair indicator. is actually kind of shorthand for an axisPointer that enables two orthogonal axes.
    axis_pointer_type: str = "line",

    # Whether or not to show the pointer box float, default is shown.
    # Configure this to false if you only need the tooltip to trigger an event or to show the axisPointer but not the content.
    is_show_content: bool = True,

    # Whether to always display the content of the prompt box.
    # By default the content is hidden after a certain amount of time after moving out of the triggerable area, set to true to ensure that the content is always shown.
    is_always_show_content: bool = False,

    # The delay of the floating layer in ms, there is no delay by default and it is not recommended to set it.
    show_delay: Numeric = 0,
    
    # Delay for floating layer hiding, in ms, not valid when alwaysShowContent is true.
    hide_delay: Numeric = 100,

    # The position of the floating layer of the hint box, the default position will follow the mouse position if not set.
    # 1, configured via array.
    # Absolute position, relative to container left 10px, top 10 px ===> position: [10, 10]
    # Relative position, placed right in the middle of the container ===> position: ['50%', '50%']
    # 2, configured by callback function
    # 3, configured with fixed parameters: 'inside', 'top', 'left', 'right', 'bottom'
    position: Union[str, Sequence, JSFunc] = None,

    # Label content formatter, supports both string templates and callback functions, both string templates and callback functions return strings with \n line breaks.
    # String templates The template variables are.
    # {a}: series name.
    # {b}: data name.
    # {c}: data value.
    # {@xxx}: the value of the dimension named 'xxx' in the data, e.g. {@product} indicates the value of the dimension named 'product'`.
    # {@[n]}: The value of dimension n in the data, e.g. {@[3]}` indicates the value of dimension 3, counting from 0.
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

    # The background colour of the prompt box floating layer.
    background_color: Optional[str] = None,

    # The border colour of the prompt box floating layer.
    border_color: Optional[str] = None,

    # The width of the border for the prompt box.
    border_width: Numeric = 0,

    # Text style options, see `series_options.TextStyleOpts`
    textstyle_opts: TextStyleOpts = TextStyleOpts(font_size=14),
)
```

## AxisLineOpts: Coordinate axis configuration items
> *class pyecharts.option.AxisLineOpts*

```python
class AxisLineOpts(
    # Whether to show axis lines.
    is_show: bool = True,
    
    # Whether the axis of the X or Y axis is on the 0 scale of the other axis, only valid if the other axis is a numeric axis and contains a 0 scale.
    is_on_zero: bool = True,
    
    # This property can be used to specify manually, when there are two axes, on which axis is at 0 degrees.
    on_zero_axis_index: int = 0,
    
    # The arrows on either side of the axis. This can be a string indicating that the same arrow is used at both ends, or an array of strings of length 2, indicating the arrows at each end.
    # No arrows are shown by default, i.e. 'none'.
    # Show arrows at both ends can be set to 'arrow'.
    # Show arrows only at the ends can be set to ['none', 'arrow'].
    symbol: Optional[str] = None,
    
    # Coordinate axis style configuration items, see `series_optionsLineStyleOpts`
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,
)
```

## AxisTickOpts: Coordinate axis scale configuration items
> *class pyecharts.options.AxisTickOpts*

```python
class AxisTickOpts(
    # Whether to show the axis scales.
    is_show: bool = True,
    
    # Valid in the class Axis when boundaryGap is true, to ensure that the ticks and labels are aligned.
    is_align_with_label: bool = False,
    
    # Whether or not the coordinate axis scale faces inwards, the default is outwards.
    is_inside: bool = False,
    
    # The length of the scale.
    length: Optional[Numeric] = None,
    
    # The axis style configuration item, see `series_optionsLineStyleOpts`.
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,
)
```

## AxisPointerOpts: Coordinate axis indicator configuration items
> *class pyecharts.options.AxisPointerOpts*

```python
class AxisPointerOpts(
    # Show the axis indicator by default
    is_show: bool = True,
    
    # The axisPointer for different axes can be linked, set here. Linking means that the axes can move together in sync.
    # Axes are linked according to the current value of their axisPointer.
    # link is an array where each item represents a link group and the axes in a group are linked to each other.
    # See https://www.echartsjs.com/option.html#axisPointer.link for details on how to use this.
    link: Sequence[dict] = None,
    
    # Indicator type.
    # The optional parameters are as follows, the default is 'line'
    # 'line' Straight line indicator
    # 'shadow' shadow indicator
    # 'none' no indicator
    type_: str = "line",
    
    # Text labels for axis indicators, axis label configuration items, see `series_options.LabelOpts`
    label: Union[LabelOpts, dict, None] = None,
    
    # Coordinate axis line style configuration items, see `series_optionsLineStyleOpts`
    linestyle_opts: Union[LineStyleOpts, dict, None] = None,
)
```

## AxisOpts: Axis configuration items
> *class pyecharts.options.AxisOpts*

```python
class AxisOpts(
    ## Axis type. Optional.
    # 'value': numeric axis, for continuous data.
    # 'category': category axis, applies to discrete category data, for this type the category data must be set via data.
    # 'time': time axis, for continuous temporal data, compared to the numeric axis the time axis is formatted with time and has a different scale calculation.
    # 'log': The time axis, for continuous temporal data, has a formatting of time compared to the numeric axis and differs in the scale calculation, e.g. whether to use a month, week, day or hour scale depending on the span.
    # 'log' logarithmic axis. Applies to logarithmic data.
    type_: Optional[str] = None,
    
    # The name of the coordinate axis.
    name: Optional[str] = None,

    # Whether to display the x-axis.
    is_show: bool = True,

    # Valid only in numeric axes (type: 'value').
    # Whether to scale off the 0 value. When set to true the coordinate scale is not forced to contain a zero scale. Useful in scatter plots with dual numeric axes.
    # This is not valid after min and max are set.
    is_scale: bool = False,

    # Whether to reverse the axis.
    is_inverse: bool = False,

    # The position of the axis name display. Optional.
    # 'start', 'middle' or 'center', 'end'
    name_location: str = "end",

    # The distance between the name of the coordinate axis and the axis line.
    name_gap: Numeric = 15,
    
    # The axis name rotation, the angle value.
    name_rotate: Optional[Numeric] = None,

    # Force the axis splitting interval.
    # Because splitNumber is a predicted value, the actual scale calculated according to the strategy may not have the desired effect.
    # This is where interval can be used in conjunction with min and max to force the scale divisions, which is generally not recommended.
    # Cannot be used in the category axis. In the time axis (type: 'time') you need to pass the timestamp, in the logarithmic axis (type: 'log') you need to pass the exponent.
    interval: Optional[Numeric] = None,

    # The index of the grid where the x-axis is located, the default is the first grid.
    grid_index: Numeric = 0,

    # The position of the x-axis. Optional.
    # 'top', 'bottom'
    # The first x-axis in the default grid is below the grid ('bottom'), the second x-axis is on the other side depending on the position of the first x-axis.
    position: Optional[str] = None,
    
    # The offset of the Y-axis relative to the default position, useful if there are multiple Y-axes on the same position.
    offset: Numeric = 0,
    
    # The number of segments of the axis, note that this is only an estimate and the actual number of segments displayed will be adjusted based on the legibility of the segmented axis scale. 
    # The default value is 5
    split_number: Numeric = 5,

    # The strategy of leaving white space on both sides of the coordinate axis is set and behaves differently for the category and non-category axes.
    # The boundaryGap can be configured as true and false in the category axis. the default is true, when the scale is just used as a separator.
    # The labels and data points will be in the middle of the band between the two scales.
    # For non-categorical axes, including time, numeric, and logarithmic axes, boundaryGap is an array of two values that represent the extension of the minimum and maximum values of the data respectively
    # Can be set directly as a value or as a relative percentage, not valid after setting min and max. Example: boundaryGap: ['20%', '20%']
    boundary_gap: Union[str, bool, None] = None,

    # The minimum value of the coordinate axis scale.
    # Can be set to the special value 'dataMin', which takes the smallest value of the data on that axis as the minimum scale.
    # The minimum value is automatically calculated when not set to ensure an even distribution of axis scales.
    # In the category axis, this can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C'.
    (# can also be set to a negative number, e.g. -3).
    min_: Union[Numeric, str, None] = None,

    # The maximum value of the coordinate axis scale.
    # Can be set to the special value 'dataMax', when the maximum value of the data on that axis is taken as the maximum scale.
    # The maximum value is automatically calculated when not set to ensure an even distribution of the axis scales.
    # In the category axis, this can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C'.
    (# can also be set to a negative number, e.g. -3).
    max_: Union[Numeric, str, None] = None,
    
    # The minimum interval size of the axes calculated automatically.
    # This can be set to 1 for example to ensure that the axis division scale is displayed as an integer.
    # The default value is 0
    min_interval: Numeric = 0,
    
    # The maximum interval size of the axes to be calculated automatically.
    # For example, on the time axis ((type: 'time')) this could be set to 3600 * 24 * 1000 to ensure that the axis division scale is a maximum of one day.
    max_interval: Optional[Numeric] = None,

    # Axis line configuration items, see `global_options.AxisLineOpts`
    axisline_opts: Union[AxisLineOpts, dict, None] = None,
    
    # Coordinate axis scale configuration items, see `global_options.AxisTickOpts`
    axistick_opts: Union[AxisTickOpts, dict, None] = None,

    # Coordinate axis label configuration items, see `series_options.LabelOpts`
    axislabel_opts: Union[LabelOpts, dict, None] = None,
    
    # Axis indicator configuration items, see `global_options.AxisPointerOpts`
    axispointer_opts: Union[AxisPointerOpts, dict, None] = None,

    # Text style for coordinate axis names, see `series_options.TextStyleOpts`
    name_textstyle_opts: Union[TextStyleOpts, dict, None] = None,

    # Split area configuration items, see `series_options.SplitAreaOpts`
    splitarea_opts: Union[SplitAreaOpts, dict, None] = None,

    # Split line configuration items, see `series_options.SplitLineOpts`
    splitline_opts: Union[SplitLineOpts, dict] = SplitLineOpts(),

    # For settings related to coordinate axis subscripts, see `series_options.MinorTickOpts`
    minor_tick_opts: Union[MinorTickOpts, dict, None] = None,

    # The subdivisions of the coordinate axes in the grid area. The minor split line aligns to the minorTick line, see `series_options.MinorSplitLineOpts`
    minor_split_line_opts: Union[MinorSplitLineOpts, dict, None] = None,
)
```

## SingleAxisOpts: single axis configuration items
> *class pyecharts.SingleAxisOpts*

```python
class SingleAxisOpts(
    # Coordinate axis names.
    name: Optional[str] = None,

    # The maximum value of the coordinate axis scale.
    # Can be set to the special value 'dataMax', which takes the maximum value of the data on that axis as the maximum scale.
    # The maximum value is automatically calculated when not set to ensure an even distribution of axis scales.
    # In the category axis, this can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C'.
    (# can also be set to a negative number, e.g. -3).
    max_: Union[str, Numeric, None] = None,

    # The minimum value of the coordinate axis scale.
    # Can be set to the special value 'dataMin', which takes the smallest value of the data on that axis as the minimum scale.
    # The minimum value is automatically calculated when not set to ensure an even distribution of axis scales.
    # In the category axis, this can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C'.
    (# can also be set to a negative number, e.g. -3).
    min_: Union[str, Numeric, None] = None,

    # The distance of the single component from the left side of the container.
    # The value of left can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'left', 'centre', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: Optional[str] = None,

    # The distance of the single component from the right side of the container.
    The value of # right can be a specific pixel value like 20, and can be a percentage relative to the container height and width like '20%'.
    pos_right: Optional[str] = None,

    # The distance of the single component from the top side of the container.
    # The value of top can be a specific pixel value like 20, or a percentage of the container's height and width like '20%'.
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Optional[str] = None,

    # The distance of the single component from the lower side of the container.
    The value of # bottom can be a specific pixel value like 20, or it can be a percentage relative to the container height and width like '20%'.
    pos_bottom: Optional[str] = None,

    # The width of the single component. Adaptive by default.
    width: Optional[str] = None,

    # The height of the single component. Adaptive by default.
    height: Optional[str] = None,

    # The orientation of the axis, the default is horizontal, can be set to 'vertical'.
    orient: Optional[str] = None,

    # The coordinate axis type. Optional.
    # 'value': The numeric axis, for continuous data.
    # 'category': category axis, for discrete category data, the category data must be set via data for this type.
    # 'time': time axis, for continuous temporal data, compared to the numeric axis the time axis is formatted with time and has a different scale calculation.
    # 'log': The time axis, for continuous temporal data, has a formatting of time compared to the numeric axis and differs in the scale calculation, e.g. whether to use a month, week, day or hour scale depending on the span.
    # 'log' logarithmic axis. Applies to logarithmic data.
    type_: Optional[str] = None,
    
    # Axis line options, see `global_options.AxisLineOpts`.
    axisline_opts: Union[AxisLineOpts, dict, None] = None,
    
    # Axis tick options, refer to `global_options.AxisTickOpts`.
    axistick_opts: union[AxisTickOpts, dict, None] = None, # Axis tick label configuration item, refer to `global_options.AxisTickOpts`.
    
    # Axis label options, refer to `series_options.LabelOpts`.
    axislabel_opts: Union[LabelOpts, dict, None] = None, # Axis axis label configuration item ref.
    
    # Axis pointer options, see `global_options.AxisPointerOpts`.
    axispointer_opts: Union[AxisPointerOpts, dict, None] = None, # Axis pointer configuration items in the grid area, refer to `global_options.AxisPointerOpts`.
    
    # Axis separators in the grid area, not shown by default. References `series_options.SplitAreaOpts`.
    splitarea_opts: union[SplitAreaOpts, dict, None] = None, # Split area configuration items, cf.
    
    # Split line opts, see `series_options.SplitLineOpts`.
    splitline_opts: Union[SplitLineOpts, dict] = SplitLineOpts(is_show=True),
    
    # Settings related to the minor ticks of the axes, see `series_options.MinorTickOpts`.
    minor_tick_opts: Union[MinorTickOpts, dict, None] = None, # Axes in grid area.
    
    # The minor ticks for the axes in the grid area. Minor split lines align to minor ticks, see `series_options.MinorSplitLineOpts`.
    minor_split_line_opts: Union[MinorSplitLineOpts, dict, None] = None, `series_options.
    
    # Configuration items for the tipbox component, see `series_options.TooltipOpts`.
    tooltip_opts: Union[TooltipOpts, dict, None] = None, # Tip box component configuration item, see `series_options.TooltipOpts`.
)
```


## GraphicGroup: native graphic element component
> *class pyecharts.GraphicGroup*

``` python
class GraphicGroup(
    ## Configuration items for graphics
    graphic_item: Union[GraphicItem, dict, None] = None,
    
    # Redraws based on the name attribute of each graphic element in its children
    is_diff_children_by_name: bool = False,
    
    # A list of children, where each item is a graphic element definition.
    # Currently GraphicText, GraphicImage, GraphicRect can be selected
    children: Optional[Sequence[BaseGraphic]] = None,
)
```

### GraphicItem: native graphic configuration item
> *class pyecharts.GraphicItem*

```python
class GraphicItem(
    ### id is used to specify which graphic element to update when updating or deleting a graphic element, and can be ignored if it is not needed.
    id_: Optional[str] = None,
    
    # setOption when specifying the behavior of this operation on this graphic element. Optional.
    # 'merge': If the element already exists, the new configuration item is merged with the existing setting. if not, a new one is created.
    # 'replace': if there is already an element, delete it and replace it with a new element.
    # 'remove': delete the element.
    action: str = "merge",
    
    # panning (position): default is [0, 0]. Indicates [distance of horizontal translation, distance of vertical translation]. Right and bottom are positive values.
    position: [Sequence, Numeric, None] = None,
    
    # Rotation: The default value is 0. This is the radian value of the rotation. Positive values indicate counterclockwise rotation.
    rotation: Union[Numeric, JSFunc, None] = 0,
    
    # scale: The default value is [1, 1]. Indicates [multiple of horizontal scaling, multiple of vertical scaling].
    scale: Union[Sequence, Numeric, None] = None,
    
    # origin specifies the centre point for rotation and scaling, the default is [0, 0].
    origin: Union[Numeric, Sequence, None] = None,
    
    # Describes how to position the element according to its parent.
    # The parent element is: if it is a top-level element, the parent element is the echarts chart container. If it is a child element of a group, the parent element is the group element.
    # The type of value can be.
    # Numeric value: represents a pixel value.
    # Percentage value: e.g. '33%', using the height of the parent element and this percentage to calculate the final value.
    # Position: e.g. 'center': indicates auto-centre.
    # Note: only one of left and right can take effect. If left or right is specified, the x, cx, etc. positioning attributes in shape no longer take effect.
    left: Union[Numeric, str, None] = None,
    
    # Same as above
    right: Union[Numeric, str, None] = None,
    
    # Same configuration as left and right, note: only one of top and bottom can take effect.
    top: Union[Numeric, str, None] = None,
    
    # Same as above
    bottom: Union[Numeric, str, None] = None,
    
    # Determines how this graphic element's bounding box is calculated for itself when positioned. Optional.
    # 'all': (default) Indicates that the transformed wraparound box of itself and the child nodes as a whole is used for positioning. This makes it easy to keep the whole within the parent element.
    # 'raw': indicates that only the untranformed enclosing box of itself (excluding children) is used for positioning. This is an easy way to position content outside the scope of the parent element.
    bounding: str = "all",
    
    # The height in the z-direction, which determines the cascading relationship.
    z: Numeric = 0,
    
    # Determines which canvas layer this element is drawn in. Note that more canvas layers will take up more resources.
    z_level: Numeric = 0,
    
    # Whether to not respond to mouse and touch events.
    is_silent: bool = False,
    
    # If or not the node is visible.
    is_invisible: bool = False,
    
    # Whether the node is completely ignored (neither rendered nor responsive to events).
    is_ignore: bool = False,
    
    # What the mouse style is when it is over a graphical element on hover. Same as CSS for cursor.
    cursor: str = "pointer",
    
    # Whether the graphical element can be dragged or not.
    is_draggable: bool = False,
    
    # Whether to render progressively. Used when there are too many graphical elements.
    is_progressive: bool = False,
    
    # Used to describe the width of this group. This width is only used to position the child nodes.
    # Child nodes can be centred horizontally relative to the parent node using left: 'centre' even when the width is zero.
    width: Numeric = 0,
    
    # Used to describe the height of this group. This height is only used to position the child node.
    # Even when the height is zero, the child node can be vertically centred with respect to the parent using top: 'middle'.
    height: Numeric = 0,
)
```

### GraphicBasicStyleOpts: native graphic base configuration items
> *class pyecharts.GraphicBasicStyleOpts*

```python
class GraphicBasicStyleOpts(
    # Fill colour.
    fill: str = "#000",
    
    # Stroke colour.
    stroke: Optional[str] = None,
    
    # The width of the stroke.
    line_width: Numeric = 0,
    
    # The width of the shadow.
    shadow_blur: Optional[Numeric] = None,
    
    # The shadow x-direction offset.
    shadow_offset_x: Optional[Numeric] = None,
    
    # Offset in the y-direction of the shadow.
    shadow_offset_y: Optional[Numeric] = None,
    
    # The colour of the shadow.
    shadow_color: Optional[str] = None,
)
```

### GraphicShapeOpts: native graphic shape configuration items
> *class pyecharts.GraphicShapeOpts*

```python
class GraphicShapeOpts(
    # The value of the upper-left corner of the graphic element's horizontal coordinate in the parent node's coordinate system (with the parent's upper-left corner as the origin).
    pos_x: Numeric = 0,
    
    # The value of the upper-left corner of the graphic element in the parent's coordinate system (with the parent's upper-left corner as the origin).
    pos_y: Numeric = 0,
    
    # The width of the graphical element.
    width: Numeric = 0,
    
    # The height of the graphical element.
    height: Numeric = 0,
    
    # Can be used to set rounded rectangles. r: [r1, r2, r3, r4], The radii of the top left, top right, bottom right and bottom left corners are r1, r2, r3 and r4 in that order.
    # can be abbreviated, for example.
    # r abbreviated to 1 equivalent to [1, 1, 1, 1]
    # r abbreviated to [1] Equivalent to [1, 1, 1, 1]
    # r abbreviated to [1, 2] equivalent to [1, 2, 1, 2]
    # r abbreviated to [1, 2, 3]1 equivalent to [1, 2, 3, 2]`
    r: Union[Sequence, Numeric, None] = None,
)
```

### GraphicImage: native graphic image configuration item
> *class pyecharts.GraphicImage*

``` python
class GraphicImage(
    ### Configuration item for graphics, referenced by GraphicItem
    graphic_item: Union[GraphicItem, dict, None] = None,
    
    # Configuration items for graphic image styles
    graphic_imagestyle_opts: Union[GraphicImageStyleOpts, dict, None] = None,
)
```

### GraphicImageStyleOpts: native graphic image style configuration item
> *class pyecharts.GraphicImageStyleOpts*

``` python
class GraphicImageStyleOpts(
    # The content of the image, which can be the URL of the image.
    image: Optional[str] = None,
    
    # The value of the upper-left corner of the graphic element's horizontal coordinate in the parent node's coordinate system (with the parent's upper-left corner as the origin).
    pos_x: Numeric = 0,
        
    # The value of the vertical coordinate of the upper left corner of the graphic element in the parent's coordinate system (with the parent's upper left corner as the origin).
    pos_y: Numeric = 0,
    
    # The width of the graphical element.
    width: Numeric = 0,
    
    # The height of the graphical element.
    height: Numeric = 0,
    
    # Transparency 0 to 1. 1 for full display
    opacity: Numeric = 1,
    
    # Graphic basic configuration items, see GraphicBasicStyleOpts
    graphic_basicstyle_opts: Union[GraphicBasicStyleOpts, dict, None] = None,
)
```


### GraphicText: native graphic text configuration item
> *class pyecharts.GraphicText*

``` python
class GraphText(
    ### Configuration item for graphics, referenced by GraphicItem
    graphic_item: Union[GraphicItem, dict, None] = None,
    
    # Configuration items for graph text styles
    graphic_textstyle_opts: Union[GraphicTextStyleOpts, dict, None] = None,
)
```

### GraphicTextStyleOpts: native graphic text style configuration item
> *class pyecharts.GraphicTextStyleOpts*

``` python
class GraphicTextStyleOpts(
    # Text block text. Can use \n for line breaks.
    text: Optional[JSFunc] = None,
    
    # The value of the upper-left corner of the graphic element's horizontal coordinate in the parent node's coordinate system (with the parent's upper-left corner as the origin).
    pos_x: Numeric = 0,
    
    # The value of the vertical coordinate of the upper left corner of the graphic element in the parent's coordinate system (with the parent's upper left corner as the origin).
    pos_y: Numeric = 0,
    
    # Font size, font type, thickness, font style.
    # For example.
    # // size | family
    # font: '2em "STHeiti", sans-serif'
    # // style | weight | size | family
    # font: 'italic bolder 16px cursive'
    # // weight | size | family
    # font: 'bolder 2em "Microsoft YaHei", sans-serif'
    font: Optional[str] = None,
    
    # Horizontal alignment, take values: 'left', 'center', 'right'. Default value is: 'left'
    # If 'left', the leftmost end of the text is at the x value. If 'right', it means that the rightmost end of the text is on the x value.
    text_align: str = "left",
    
    # Vertical alignment, takes values: 'top', 'middle', 'bottom'. Default value is: 'None'
    text_vertical_align: Optional[str] = None,
    
    # Graphic basic configuration items, see GraphicBasicStyleOpts
    graphic_basicstyle_opts: Union[GraphicBasicStyleOpts, dict, None] = None,
)
```

### GraphicRect: native graphic rectangle configuration item
> *class pyecharts.GraphicRect*

```python
class GraphicRect(
    ### Configuration item for graphics, referenced by GraphicItem
    graphic_item: Union[GraphicItem, dict, None] = None,
    
    # Configuration items for the shape of the graphic, see GraphicShapeOpts
    graphic_shape_opts: Union[GraphicShapeOpts, dict, None] = None,
    
    # Basic configuration items for graphics, see GraphicBasicStyleOpts
    graphic_basicstyle_opts: Union[GraphicBasicStyleOpts, dict, None] = None,
)
```


### PolarOpts: polar coordinate system configuration
> *class pyecharts.PolarOpts*

```python
class PolarOpts(
    ### Polar coordinate system centre (center of circle) coordinates, the first item of the array is the horizontal coordinate, the second is the vertical coordinate.
    # Supports setting to a percentage, when set to a percentage the first term is relative to the container width, the second term is relative to the container height.
    center: Optional[Sequence] = None,
    
    # The radius of the polar coordinate system. Can be of the following type.
    # number: specifies the outer radius value directly.
    # string: e.g. '20%', means that the outer radius is 20% of the length of the visible area dimension (the smaller of the container height and width).
    # Array.<number|string>: The first item of the array is the inner radius and the second item is the outer radius. Each item follows the description of the number string above.
    radius: Optional[Union[Sequence, str]] = None,
    
    # Tooltip settings specific to this coordinate system. See `global_options.TooltipOpts`
    tooltip_opts: TooltipOpts = None,
)
```

### DatasetTransformOpts: dataset transformation configuration items
> *class pyecharts.options.DatasetTransformOpts*

```python
class DatasetTransformOpts(
    # Transform types
    # filter, sort, Echarts functions
    type_: str = "filter",
    
    # specific transform configuration items
    config: Optional[dict] = None,
    
    # debug mode will be printed via browser console.
    is_print: bool = False,
)
```

### EmphasisOpts: polygon and label styles for highlighting.
> *class pyecharts.EmphasisOpts*.

```python
class EmphasisOpts(
    # Whether to turn off highlighting.
    # Turning off highlighting can stop the highlighting effect from being triggered when the mouse is over the graph, the tooltip is triggered, or the legend is linked.
    # Can be turned off when there are a lot of graphics to improve the smoothness of the interaction.
    is_disabled: bool = False, # If or not hover is enabled at inflection points.
    
    # Whether or not to enable hover's zoom effect on corner markers.
    is_scale: bool = True, # Whether to turn on hover's zoom effect on the inflection markers.
    
    # Whether or not to fade out the graph of other data to achieve the focus effect when highlighting the graph. The following configurations are supported:
    # 'none' Do not fade out other graphs, this configuration is used by default.
    # 'self' Focus only on the graph of the currently highlighted data (without fading out).
    # 'series' Focus on all graphs in the series of the currently highlighted data.
    
    
    # When focus is turned on, you can configure the scope of the fadeout via blurScope. The following configurations are supported
    # 'coordinateSystem' The fade scope is the coordinate system, which is used by default.
    # 'series' Fade out to series.
    # 'global' Fadeout scope is global.
    blur_scope: str = "coordinateSystem", # 'series' Fadeout scope is global.
    
    # Label configuration items, refer to `series_options.LabelOpts`.
    label_opts: union[LabelOpts, dict, None] = None, # label_opts.
    
    # Whether to show visual guide lines.
    is_show_label_line: bool = False, # whether to show the visual guide line.
    
    # The configuration item for the guide line, see `series_options.LineStyleOpts`.
    label_linestyle_opts: union[LineStyleOpts, dict, None] = None, # The label style configuration item, refer to `series_options.LineStyleOpts`.
    
    # Item style options, see `series_options.ItemStyleOpts`.
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None, # Item style options, refer to `series_options.ItemStyleOpts`.
    
    # Highlight line style items, see `series_options.LineStyleOpts`.
    linestyle_opts: Union[LineStyleOpts, dict, None] = None, # Highlight line style options, refer to `series_options.LineStyleOpts`.
    
    # Highlight area style options, see `series_options.AreaStyleOpts`.
    areastyle_opts: Union[AreaStyleOpts, dict, None] = None, # End label configuration item, refer to `series_options.AreaStyleOpts`.
    
    # end_label_opts, see `series_options.LabelOpts`.
    end_label_opts: Union[LabelOpts, dict, None] = None, # end_label_opts: Union[LabelOpts, dict, None] = None, # end_label_opts.
)
```