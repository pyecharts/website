> Grid3Dopts, Axis3DOpts are required for 3D graphics

### Grid3DOpts: configuration item for 3D Cartesian coordinate system
> *class pyecharts.options.Grid3DOpts*

```python
class Grid3DOpts(
    # Whether to show the 3D Cartesian product
    show: Optional[bool] = None,
    
    # The width of the 3D Cartesian coordinate system component in the 3D scene
    width: Numeric = 200,

    # The height of the 3D Cartesian component in the 3D scene.
    height: Numeric = 100,

    # The depth of the 3D Cartesian component in the 3D scene.
    depth: Numeric = 80,

    # Whether to enable automatic rotation of the view around the object.
    is_rotate: bool = False,

    # The speed at which the object rotates. The unit is angle/sec, the default is 10, which means one rotation in 36 seconds.
    rotate_speed: Numeric = 10,

    # The sensitivity of the rotation operation, the higher the value the more sensitive it is. The rotation sensitivity can be set separately for horizontal and vertical using arrays.
    # Cannot be rotated when set to 0.
    rotate_sensitivity: Numeric = 1,
    
    # Axis line configuration items, see `global_options.AxisLineOpts`
    axisline_opts: Union[AxisLineOpts, dict, None] = None,
    
    # Coordinate axis scale configuration items, see `global_options.AxisTickOpts`
    axistick_opts: Union[AxisTickOpts, dict, None] = None,
    
    # Axis label configuration items, see `series_options.LabelOpts`
    axislabel_opts: Union[LabelOpts, dict, None] = None,
    
    # Axis indicator configuration items, see `global_options.AxisPointerOpts`
    axispointer_opts: Union[AxisPointerOpts, dict, None] = None,
    
    # The area separating the coordinate axes in the grid area, not shown by default. References `series_options.SplitAreaOpts`
    splitarea_opts: Union[SplitAreaOpts, dict, None] = None,
    
    # Split line configuration items, see `series_options.SplitLineOpts`
    splitline_opts: Union[SplitLineOpts, dict] = SplitLineOpts(is_show=True),
    
    # Environment mapping. Supports url's for solid, gradient, and panorama mapping. default is 'auto'.
    # This texture will be used as the ambient texture if light.ambientCubemap.texture is configured.
    # Otherwise, the ambient texture is not displayed.
    environment: JSFunc = "auto",
    
    # The angle of view around the x-axis, i.e. the angle of rotation up and down. Combined with beta, this controls the direction of the view.
    view_control_alpha: Numeric = 20,
    
    # The angle of view around the y-axis, i.e. the angle of rotation left and right.
    view_control_beta: Numeric = 40,
    
    # The minimum alpha value for up and down rotation. This is the angle at which the view can be rotated to the top.
    view_control_min_alpha: Numeric = -90,
    
    # The maximum alpha value for up and down rotation. This is the angle at which the view can be rotated to the bottom.
    view_control_max_alpha: Numeric = 90,
    
    # The minimum beta value for left and right rotation. This is the leftmost angle the view can be rotated to.
    view_control_min_beta: Optional[int] = None,
    
    # The maximum beta value for left and right rotation. This is the angle to the right of the view.
    view_control_max_beta: Optional[int] = None,
    
    # The level the component is on.
    z_level: Numeric = -10,
    
    # The distance of the component's view from the left side of the container.
    pos_left: Union[str, Numeric] = "auto",
    
    # The distance of the component's view from the top side of the container.
    pos_top: Union[str, Numeric] = "auto",
    
    # The distance of the component's view from the right side of the container.
    pos_right: Union[str, Numeric] = "auto",
    
    # The distance of the component's view from the right side of the container.
    pos_bottom: Union[str, Numeric] = "auto",
)
```

### Axis3DOpts: 3D coordinate axis configuration items
> *class pyecharts.options.Axis3DOpts*

``` python
class Axis3DOpts(
    data: Optional[Sequence] = None,

    # Coordinate axis type. Optional.
    # 'value': numeric axis, for continuous data.
    # 'category': category axis, for discrete category data, the category data must be set by data for this type.
    # 'time': time axis, for continuous temporal data, compared to the numeric axis the time axis is formatted with time and has a different scale calculation.
    # 'log': The time axis, for continuous temporal data, has a formatting of time compared to the numeric axis and differs in the scale calculation, e.g. whether to use a month, week, day or hour scale depending on the span.
    # 'log' logarithmic axis. Applies to logarithmic data.
    type_: Optional[str] = None,

    # The name of the coordinate axis.
    name: Optional[str] = None,
    
    # Whether to show the axis
    is_show: bool = True,
    
    # Valid for type: 'value'.
    # Whether to scale away from 0 values.
    is_scale: bool = False,
    
    # The index of the Grid3D component used for the coordinate axis. The first Grid3D component is used by default.
    grid_3d_index: Numeric = 0,

    # The distance between the name of the coordinate axis and the axis line, note that this is a distance in 3D space and not a screen pixel value.
    name_gap: Numeric = 20,

    # The minimum value of the coordinate axis scale.
    # Can be set to the special value 'dataMin', which takes the smallest value of the data on that axis as the minimum scale.
    # The minimum value is automatically calculated when not set to ensure an even distribution of axis scales.
    # In the category axis, this can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C'.
    (# can also be set to a negative number, e.g. -3).
    min_: Union[str, Numeric, None] = None,

    # The maximum value of the coordinate axis scale.
    # Can be set to the special value 'dataMax', when the maximum value of the data on that axis is taken as the maximum scale.
    # The maximum value is automatically calculated when not set to ensure an even distribution of the axis scales.
    # In the category axis, this can also be set to the ordinal number of the category (e.g. in the category axis data: ['Category A', 'Category B', 'Category C'], the ordinal number 2 means 'Category C'.
    (# can also be set to a negative number, e.g. -3).
    max_: Union[str, Numeric, None] = None,

    # The number of segments of the coordinate axis, note that this is only an estimate and the actual number of segments displayed will be based on this
    # The actual number of segments displayed will be based on this estimate, and will be adjusted according to the legibility of the segmented axis scale.
    # Not valid for class axes.
    splitnum: Optional[Numeric] = None,
    
    # The base of the logarithmic axis
    log_base: Numeric = 10,

    # Force the axis splitting interval.
    # Because splitNumber is a predicted value, the actual scale calculated according to the strategy may not be as good as desired.
    # This is where interval can be used in conjunction with min and max to force a scale division, which is not generally recommended.
    # Cannot be used in the category axis. In the time axis (type: 'time') you need to pass the timestamp, in the logarithmic axis (type: 'log') you need to pass the exponent.
    interval: Optional[Numeric] = None,
    
    # Text style configuration items, see `series_options.TextStyleOpts`
    textstyle_opts: Union[TextStyleOpts, dict, None] = None,
    
    # Coordinate axis line configuration items, see `global_options.AxisLineOpts`
    axisline_opts: Union[AxisLineOpts, dict, None] = None,
    
    # Coordinate axis scale configuration items, see `global_options.AxisTickOpts`
    axistick_opts: Union[AxisTickOpts, dict, None] = None,
    
    # Axis label configuration items, see `series_options.LabelOpts`
    axislabel_opts: Union[LabelOpts, dict, None] = None,
    
    # Axis indicator configuration items, see `global_options.AxisPointerOpts`
    axispointer_opts: Union[AxisPointerOpts, dict, None] = None,
    
    # The area separating the coordinate axes in the grid area, not shown by default. References `series_options.SplitAreaOpts`
    splitarea_opts: Union[SplitAreaOpts, dict, None] = None,
    
    # Split line configuration items, see `series_options.SplitLineOpts`
    splitline_opts: Union[SplitLineOpts, dict] = SplitLineOpts(is_show=True),
)
```

> *func pyecharts.charts.Chart3D.add*

All 3D charts have the following methods
```python
def add(
    # Series name for tooltip display, legend filtering for legends.
    series_name: str,

    # Series data
    data: Sequence,

    # The colouring effect of the 3D graphics in the 3D bar chart.
    # colour: only colour is displayed, independent of other factors such as lighting.
    # lambert: light and shade by classic lambert shading.
    # realistic: realistic rendering, used in conjunction with light.ambientCubemap and postEffect to give a qualitative improvement to the presentation and texture.
    # physically based rendering (PBR) is used in ECharts GL to represent realistic materials.
    shading: Optional[str] = None,

    # Image configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(is_show=False),

    # 3D X axis configuration items, see `Axis3DOpts`
    xaxis3d_opts: Union[opts.Axis3DOpts, dict] = opts.Axis3DOpts(type_="category"),

    # 3D Y coordinate configuration items, refer to `Axis3DOpts`
    yaxis3d_opts: Union[opts.Axis3DOpts, dict] = opts.Axis3DOpts(type_="category"),

    # 3D Z axis configuration items, see `Axis3DOpts`
    zaxis3d_opts: Union[opts.Axis3DOpts, dict] = opts.Axis3DOpts(type_="value"),

    # 3D Cartesian coordinate system configuration items, see `Grid3DOpts`
    grid3d_opts: Union[opts.Grid3DOpts, dict] = opts.Grid3DOpts(),
    
    # Whether to be a parametric surface (only available for Surface3D)
    is_parametric: types.Optional[bool] = None,
    
    # Whether to show grid lines for surface maps (only available for Surface3D)
    is_show_wire_frame: types,
    
    # Grid line style
    wire_frame_line_style_opts: types.Optional[opts.LineStyleOpts] = None,
    
    # Function expressions for curved surfaces
    equation: types.Optional[dict] = None,
    
    # The parametric equation of the surface
    parametric_equation: types.Optional[dict] = None,
)
````

## Bar3D: 3D bar chart

> *class pyecharts.charts.Bar3D(Chart3D)*

``` python
class Bar3D(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Bar3D/README)

## Line3D: 3D folding line chart

> *class pyecharts.charts.Line3D(Chart3D)*

```python
class Line3D(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Line3D/README)


## Scatter3D: 3D scatter plot

> *class pyecharts.charts.Scatter3D(Chart3D)*

```python
class Scatter3D(
    # Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Scatter3D/README)


## Surface3D: 3D surface charts

> *class pyecharts.charts.Surface3D(Chart3D)*

```python
class Surface3D(
    # Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

## Lines3D : 3D path map
> *class pyecharts.charts.Lines3D(Chart3D)*

``` python
class Surface3D(
    # Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Lines3D.add*

``` python
def add(
    # Series name for tooltip display, legend filtering for legends.
    series_name: str,
    
    # Data items (coordinate point names, coordinate point values)
    data_pair: types.Sequence,
    
    # The coordinate system used by the series, optionally.
    # 'geo3D' uses a 3D geographic coordinate system
    coordinate_system: str,
    
    # The index of the geo3D component used for the coordinate axis. The first geo3D component is used by default.
    geo_3d_index: types.Numeric = 0,
    
    # The index of the globe component used for the coordinate axis. The first globe component is used by default.
    globe_index: types.Numeric = 0,
    
    # If or not this is a polyline.
    # The default is false, which can only be used to draw lines with only two endpoints (represented as a selvedge curve).
    # If this is true, more than 2 vertices can be set in data.coords to draw polylines.
    # Useful when drawing route traces.
    is_polyline: bool = False,
    
    # Whether to show trailing effects or not, not by default.
    is_show_lines_effect: bool = False,
    
    # The period of the trailing effect.
    lines_effect_period: types.Numeric = 4,
    
    # Whether the trails effect's movement animation is at a fixed speed, in units of dimensions in 3D space.
    # The period configuration is ignored when set to a value other than null.
    lines_effect_constant_speed: types.Optional[types.Numeric] = None,
    
    # The width of the trail.
    lines_effect_trail_width: types.Numeric = 4,
    
    # The length of the trail, ranging from 0 to 1, as a percentage of the line length.
    lines_effect_trail_length: types.Numeric = 0.1,
    
    # The colour of the trail, the default is the same as the line colour.
    lines_effect_trail_color: types.Optional[str] = None,
    
    # The opacity of the trail, the default is the same as the line opacity.
    lines_effect_trail_opacity: types.Optional[types.Numeric] = None,
    
    # Blend mode, currently supports 'source-over', 'lighter'
    # The default use of 'source-over' is by alpha blending
    # and 'lighter' is the overlay mode, which allows areas of the dataset to be highlighted due to the overlay.
    blend_mode: str = "source-over",
    
    # Marker line style configuration items, see `series_options.LineStyleOpts`
    linestyle_opts: types.Optional[types.LineStyle] = None,
    
    # The level where the component is located.
    z_level: types.Numeric = -10,
    
    # Whether the graphic does not respond to and trigger mouse events, defaults to false, i.e. responds to and triggers mouse events.
    is_silent: bool = False,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Surface3D/README)


## Map3D - 3D map

> *class pyecharts.charts.Map3D(Chart3D)*

```python
class Map3D(
    ## Initialize configuration items, see ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Map3D.add*

``` python
def add(
    # Series name for display of tooltip, legend filter for legend.
    series_name: str,
    
    # Data items (coordinate point names, coordinate point values)
    data_pair: types.Sequence,

    # Type of superimposed chart (currently only Bar3D, Line3D, Lines3D, Scatter3D are supported)
    type_: ChartType = None,

    # Map type, refer to pyecharts.datasets.map_filenames.json file for details
    maptype: str = "china",

    # Whether the legend is selected or not
    is_selected: bool = True,

    # Whether to display the marker graphics
    is_map_symbol_show: bool = True,

    # The index of the grid3D component to use. The first grid3D component is used by default.
    grid_3d_index: types.Numeric = 0,

    # The index of the geo3D component used for the coordinate axis. The first geo3D component is used by default.
    geo_3d_index: types.Numeric = 0,
    
    # The index of the globe component used for the coordinate axis. The first globe component is used by default.
    globe_index: types.Numeric = 0,
    
    # Only works with bar3D
    # Set the size of the bar
    bar_size: types.Optional[types.Numeric] = None,
    
    # Only works under bar3D
    # The size of the chamfer of the bar. Supports setting to a value from 0 to 1. Default is 0, i.e. no chamfers.
    bevel_size: types.Numeric = 0,
    
    # Only works with bar3D
    # The smoothness/roundness of the bevel of the bar, the larger the value the smoother/rounder it is.
    bevel_smoothness: types.Numeric = 2,
    
    # Only works under bar3D
    # Bar stacking, where series of bars with the same stack value are stacked.
    # Note that the indexes of the data items in the array must be the same for different series to be stacked.
    stack: types.Optional[str] = None,
    
    # Only works under bar3D
    # Minimum height of the bar.
    min_height: types.Numeric = 2,
    
    # Only works under Scatter3D.
    # The shape of the scatter. Defaults to circular.
    # ECharts provides marker types including 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow', 'none'
    # Icons can be set to any vector path by using 'path://'.
    # This way you don't have to worry about jaggies or blurring due to scaling compared to using images, and can be set to any colour.
    # The path graphic adapts to the appropriate (or symbolSize in the case of symbol) size.
    symbol: str = "circle",

    # Only works in Scatter3D.
    # The size of the symbol, which can be set to a single number such as 10, or an array of separate widths and heights, e.g. [20, 10] means the symbol is 20 wide and 10 high.
    symbol_size: types.Union[types.Numeric, types.Sequence, types.JSFunc] = 10,

    # Mixed mode, currently supports 'source-over', 'lighter'.
    # The default use of 'source-over' is by alpha blending.
    # and 'lighter' is the overlay mode, which allows areas of the dataset to be highlighted due to the overlay.
    blend_mode: str = "source-over",

    # Only works in Lines3D
    # Whether to be a polyline.
    # Defaults to false and can only be used to draw line segments with only two endpoints (behaving as a selvedge curve).
    # If this is true, more than 2 vertices can be set in data.coords to draw polylines, which is useful when drawing route traces.
    is_polyline: bool = False,

    # Only works with Lines3D
    # Trailing effects for flying lines, see `series_options.Line3DEffectOpts`
    effect: types.Lines3DEffect = None,

    # Only works on Line3D, Lines3D
    # Line styles for flying lines, see `series_options.LineStyleOpts`
    linestyle_opts: types.LineStyle = opts.LineStyleOpts(),

    # Only works in Scatter3D, Bar3D, Map3D
    # Label configuration items, see `series_options.LabelOpts`
    label_opts: types.Label = opts,

    # Tipbox component configuration items, see `series_options.TooltipOpts`
    tooltip_opts: types.Tooltip = None,

    # Only works in Scatter3D, Bar3D, Map3D
    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: types.ItemStyle = None,

    # Only works in Scatter3D, Bar3D, Map3D
    # Highlight label configuration items, see `series_options.LabelOpts`
    emphasis_label_opts: types.Label = None,

    # Only works in Scatter3D, Bar3D, Map3D
    # Highlight item style configuration, see `series_options.ItemStyleOpts`
    emphasis_itemstyle_opts: types.ItemStyle = None,

    # Colouring effects for 3D graphics in 3D maps. echarts-gl supports the following three colouring methods.
    # colour: Only colours are displayed, independent of other factors such as lighting.
    # lambert: Light and shade by classic lambert shading.
    # realistic: realistic rendering, used in conjunction with light.ambientCubemap and postEffect to give a qualitatively improved look and feel.
    # physically based rendering (PBR) is used in ECharts GL to represent realistic materials.
    shading: types.Optional[str] = None,

    # Realistic material-related configuration item, valid when shading is 'realistic'.
    realistic_material_opts: types.Optional[types.Map3DRealisticMaterial] = None,

    # lambert material related configuration items, valid when shading is 'lambert'.
    lambert_material_opts: types.Optional[types.Map3DLambertMaterial] = None,

    # color Material related configuration item, valid when shading is 'color'.
    color_material_opts: types.Optional[types.Map3DColorMaterial] = None,

    # The layer the component is on.
    zlevel: types.Numeric = -10,

    # Whether the graphic does not respond to and trigger mouse events, defaults to false, i.e. responds to and triggers mouse events.
    is_silent: bool = False,

    # If or not animation is enabled.
    is_animation: bool = True,

    # The duration of the transition animation.
    animation_duration_update: types.Numeric = 100,

    # The easing effect of the transition animation.
    animation_easing_update: types.Numeric = "cubicOut",
):
```

> *func pyecharts.charts.Map3D.add_schema*

```python
def add_schema(
    # map type, see pyecharts.datasets.map_filenames.json file for details
    maptype: str = "china",

    # Name
    name: types.Optional[str] = None,

    # The width of the 3D geo-coordinate system component in the 3D scene.
    # Specifically illustrated here: https://www.echartsjs.com/zh/documents/asset/gl/img/geo-size.png
    box_width: types.Optional[types.Numeric] = 100,

    # The height of the 3D georeferencing component in the 3D scene.
    # The height of the component. This height contains the height of the histogram and scatter plot on the 3D map.
    box_height: types.Optional[types.Numeric] = 10,

    # The depth of the 3D geo-coordinate system component in the 3D scene.
    # The component depth is automatic by default, ensuring that the 3D component is displayed at the same scale as the input GeoJSON.
    box_depth: types.Optional[types.Numeric] = None,

    # The height of each area of the 3D map. This height is the height of the model and is less than boxHeight.
    # boxHeight - regionHeight This area will be used for the display of 3D bar charts, scatter plots etc.
    region_height: types.Optional[types.Numeric] = 3,

    # Environment mapping. Supports url for solid, gradient, and panorama mapping.
    # Default is 'auto', which will be used as the ambient texture if light.ambientCubemap.texture is configured.
    # Otherwise the ambient texture is not displayed.
    # Example.
    # // configured as a panorama texture
    # environment: 'asset/starfield.jpg'
    # // configured as a solid black background
    # environment: '#000'
    # // configured as a vertical gradient background
    # environment: new echarts.graphics.LinearGradient(0, 0, 0, 1, [{
    # offset: 0, color: '#00aaff' // sky colour
    # }, {
    # offset: 0.7, color: '#998866' // ground colour
    # }, {
    # offset: 1, color: '#998866' // ground colour
    # }], false)
    environment: types.Optional[types.JSFunc] = None,

    # Whether to show the ground or not.
    # The ground allows the whole component to have a place to "sit", thus making the whole scene look more realistic and model-like.
    is_show_ground: bool = False,

    # Ground colour.
    ground_color: str = "#aaa",

    # instancing will merge all the geometry in GeoJSON into one
    # This can be useful when GeoJSON has a large number of geometries (thousands).
    is_instancing: bool = False,

    # Map3D's Label setting
    map3d_label: types.Map3DLabel = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: types.ItemStyle = None,

    # Highlight label configuration items, see `series_options.LabelOpts`
    emphasis_label_opts: types.Label = None,

    # Highlight the item style configuration, see `series_options.ItemStyleOpts`
    emphasis_itemstyle_opts: types.ItemStyle = None,

    # Colouring effects for 3D graphics in 3D geo-coordinate system components. echarts-gl supports the following three colouring methods.
    # colour: Only colours are displayed, independent of other factors such as lighting.
    # lambert: light and shade by classic lambert shading.
    # realistic: realistic rendering, used in conjunction with light.ambientCubemap and postEffect to give a qualitatively improved look and feel.
    # physically based rendering (PBR) is used in ECharts GL to represent realistic materials.
    shading: types.Optional[str] = None,

    # Realistic material-related configuration item, valid when shading is 'realistic'.
    realistic_material_opts: types.Optional[types.Map3DRealisticMaterial] = None,

    # lambert material related configuration items, valid when shading is 'lambert'.
    lambert_material_opts: types.Optional[types.Map3DLambertMaterial] = None,

    # color Material related configuration item, valid when shading is 'color'.
    color_material_opts: types.Optional[types.Map3DColorMaterial] = None,

    # Illumination-related settings. Invalid when shading is 'color'.
    # The lighting setting affects the component and all charts in the component's coordinate system.
    # Proper lighting settings can make the whole scene richer and more layered.
    light_opts: types.Optional[types.Map3DLight] = None,

    # Configuration for post-processing effects. Post-processing effects can add highlights, depth of field, ambient light masking (SSAO), colour grading, etc. to the image. It can add texture to the whole image.
    post_effect_opts: types.Optional[types.Map3DPostEffect] = None,

    # Whether to enable frame-splitting oversampling. By default, this is also enabled when postEffect is enabled.
    is_enable_super_sampling: types.Union[str, bool] = "auto",

    # viewControl is used for mouse rotation, zooming and other view control.
    view_control_opts: types.Optional[types.Map3DViewControl] = None,

    # The layer where the component is located.
    zlevel: types.Optional[types.Numeric] = -10,

    # The distance of the component's view from the left side of the container.
    # The value of left can be a specific pixel value like 20, which can be a percentage relative to the container height and width like '20%'
    # It can also be 'left', 'centre', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: types.Union[types.Numeric, str] = "auto",

    # The distance of the component's view from the top side of the container.
    pos_top: types.Union[types.Numeric, str] = "auto",

    # The distance of the component's view from the right side of the container.
    pos_right: types.Union[types.Numeric, str] = "auto",

    # The distance of the component's view from the lower side of the container.
    pos_bottom: types.Union[types.Numeric, str] = "auto",

    # The width of the component's view.
    pos_width: types.Union[types.Numeric, str] = "auto",

    # The height of the component's view.
    pos_height: types.Union[types.Numeric, str] = "auto",
)
```

> *class pyecharts.options.charts_options.Map3DLabelOpts*

``` python
class Map3DLabelOpts(
    # Whether to show the labels or not.
    is_show: bool = True,

    # The distance of the label from the graph, in a 3D scatter plot this distance is the pixel value in screen space, in other plots this distance is the relative 3D distance.
    distance: Numeric = None,

    # Label content formatter, supports both string templates and callback functions, both string templates and callback functions return strings with \n line breaks.
    # Template variables are.
    # {a}: series name.
    # {b}: data name.
    # {c}: data value.
    formatter: Optional[JSFunc] = None,

    # The font style of the tag.
    text_style: Union[TextStyleOpts, dict, None] = None,
)
```

> *class pyecharts.options.charts_options.Map3DRealisticMaterialOpts*

```python
class Map3DRealisticMaterialOpts(
    # Texture maps for material details.
    detail_texture: Optional[JSFunc] = None,

    # The tiling of the material detail texture. Defaults to 1, which means stretched and filled. If greater than 1, the number indicates the number of times the texture tile will be repeated.
    # Note: Using tiling requires that the height and width of the detailTexture is the nth power of 2. For example 512x512, if the texture is 200x200, tiling is not possible.
    texture_tiling: Numeric = 1,

    # The displacement of the material's detail texture.
    texture_offset: Numeric = 0,

    # The roughness property is used to indicate the roughness of the material, with 0 being perfectly smooth, 1 being perfectly rough, and intermediate values in between.
    roughness: Numeric = 0.5,

    # The metalness property is used to indicate whether the material is metallic or non-metallic, with 0 being non-metallic and 1 being metallic, and intermediate values in between.
    # Usually a value of 0 and 1 is sufficient for most scenarios.
    metalness: Numeric = 0,

    # Roughness adjustment, useful when using roughness mapping. The overall roughness of the texture can be adjusted.
    # Defaults to 0.5, with 0 being completely smooth and 1 being completely rough.
    roughness_adjust: Numeric = 0.5,

    # Metallicity adjustment, useful when using metallic mapping. Allows adjustment of the overall metallicity of the texture.
    # Defaults to 0.5, with 0 being non-metallic and 1 being metallic.
    metalness_adjust: Numeric = 0.5,

    # Normal map for material details.
    # Use a normal texture to show the richness of the surface with fewer vertices.
    normal_texture: Optional[JSFunc] = None,
)
```

> *class pyecharts.options.charts_options.Map3DLambertMaterialOpts*

``` python
class Map3DLambertMaterialOpts(
    # Texture maps for material details.
    detail_texture: Optional[JSFunc] = None,
    
    # The tiling of the material detail texture. Defaults to 1, which means stretched and filled. If greater than 1, the number indicates the number of times the texture tile will be repeated.
    # Note: Using tiling requires that the height and width of the detailTexture is the nth power of 2. For example 512x512, if the texture is 200x200, tiling is not possible.
    texture_tiling: Numeric = 1,

    # The displacement of the material's detail texture.
    texture_offset: Numeric = 0,
)
```

> *class pyecharts.options.charts_options.Map3DColorMaterialOpts*

``` python
class Map3DColorMaterialOpts(
    # Texture maps for material details.
    detail_texture: Optional[JSFunc] = None,
    
    # The tiling of the material detail texture. Defaults to 1, which means stretched and filled. For values greater than 1, the number indicates the number of times the texture tile will be repeated.
    # Note: Using tiling requires that the height and width of the detailTexture is the nth power of 2. For example 512x512, if the texture is 200x200, tiling is not possible.
    texture_tiling: Numeric = 1,

    # The displacement of the material's detail texture.
    texture_offset: Numeric = 0,
)
```

> *class pyecharts.options.charts_options.Map3DLightOpts*

``` python
class Map3DLightOpts(
    # The colour of the main light source.
    main_color: str = "#fff",

    # The intensity of the main light source.
    main_intensity: Numeric = 1,

    # Whether or not the main light source casts shadows. Default is off.
    # Turning on shadows will give the scene a more realistic and layered lighting effect. However, it also increases the overhead of the program.
    is_main_shadow: bool = False,

    # The quality of the shadows. Can be 'low', 'medium', 'high', 'ultra'
    main_shadow_quality: str = "medium",

    # The angle of rotation of the main light source around the x-axis, i.e. up and down. Combined with beta, this controls the direction of the light source.
    # Icon: https://www.echartsjs.com/zh/documents/asset/gl/img/light-alpha-beta.png
    main_alpha: Numeric = 40,

    # The angle of rotation of the main light source around the y-axis, i.e. left and right.
    main_beta: Numeric = 40,

    # The colour of the ambient light.
    ambient_color: str = "#fff",

    # The intensity of the ambient light.
    ambient_intensity: Numeric = 0.2,

    # The url for the ambient light mapping, HDR images using the .hdr format are supported.
    # A source for .hdr can be obtained from sites such as http://www.hdrlabs.com/sibl/archive.html.
    ambient_cubemap_texture: Optional[str] = None,

    # The intensity of the diffuse reflection.
    ambient_cubemap_diffuse_intensity: Numeric = 0.5,

    # The intensity of the high light reflection.
    ambient_cubemap_specular_intensity: Numeric = 0.5,
)
```

> *class pyecharts.options.charts_options.Map3DPostEffectOpts*

``` python
class Map3DPostEffectOpts(
    # Whether to turn on post-processing effects. Off by default.
    is_enable: bool = False,

    # Whether or not to enable glow effects.
    is_bloom_enable: bool = False,

    # The intensity of the halo, default is 0.1
    bloom_intensity: Numeric = 0.1,

    # Whether to enable depth of field.
    is_depth_field_enable: bool = False,

    # The initial depth of focus, the user can click on the area to focus it automatically.
    depth_field_focal_distance: Numeric = 50,

    # The range of the fully focused area, where objects are perfectly sharp and not blurred
    depth_field_focal_range: Numeric = 20,

    # The F value of the lens, the smaller the value the shallower the depth of field.
    depth_field_fstop: Numeric = 2.8,

    # The out-of-focus blur radius
    depth_field_blur_radius: Numeric = 10,

    # Whether to turn on ambient light blurring. Not enabled by default.
    is_ssao_enable: bool = False,

    # The quality of the ambient light masking. Supports 'low', 'medium', 'high', 'ultra'.
    ssao_quality: str = "medium",

    # The sampling radius for ambient light masking. The larger the radius the more natural the effect, but a higher 'quality' setting is required.
    ssao_radius: Numeric = 2,

    # The intensity of the ambient light mask. The larger the value the darker the colour.
    ssao_intensity: Numeric = 1,

    # Whether to turn on colour correction.
    is_color_correction_enable: bool = False,

    # Refer to the official Echarts explanation.
    # Address:https://www.echartsjs.com/zh/option-gl.html#geo3D.postEffect.colorCorrection.lookupTexture
    color_correction_lookup_texture: Optional[JSFunc] = None,

    # The exposure of the screen.
    color_correction_exposure: Numeric = 0,

    # The brightness of the screen.
    color_correction_brightness: Numeric = 0,

    # The contrast of the screen.
    color_correction_contrast: Numeric = 1,

    # The saturation of the screen.
    color_correction_saturation: Numeric = 1,

    # Whether FXAA is enabled or not, the default is not.
    is_fxaa_enable: bool = False,
)
```

> *class pyecharts.options.charts_options.Map3DViewControlOpts*

```python
class Map3DViewControlOpts(
    # Projection method, defaults to perspective projection 'perspective', also supports setting to orthogonal projection 'orthographic'.
    projection: str = "perspective",
    
    # Whether to enable auto-rotate view of the perspective around the object.
    auto_rotate: bool = False,

    # The direction in which the object will rotate itself. The default is 'cw' which is clockwise from top to bottom, or you can take 'ccw' which is counterclockwise from top to bottom.
    auto_rotate_direction: str = "cw",

    # The speed at which the object rotates. The unit is angle/sec, the default is 10, which means one rotation in 36 seconds.
    auto_rotate_speed: Numeric = 10,

    # The interval at which auto-rotation resumes after a mouse standstill operation. Valid when autoRotate is enabled.
    auto_rotate_after_still: Numeric = 3,

    # Hysteresis factor for rotate, zoom, etc., where the mouse will continue to move (rotate and zoom) with some inertia even after the mouse is stopped if greater than 0.
    damping: Numeric = 0.8,

    # The sensitivity of the rotation operation, the higher the value the more sensitive it is. Supports the use of arrays to set the sensitivity of rotation in landscape and portrait orientation respectively.
    # Default is 1.
    # Can't rotate when set to 0.
    # // Cannot rotate
    # rotateSensitivity: 0
    # // Can only rotate horizontally
    # rotateSensitivity: [1, 0]
    # // Can only rotate vertically
    # rotateSensitivity: [0, 1]
    rotate_sensitivity: Union[Numeric, Sequence] = 1,

    # Sensitivity of the zoom operation, the larger the value the more sensitive it is. Default is 1.
    # Cannot be scaled when set to 0.
    zoom_sensitivity: Numeric = 1,

    # The sensitivity of the pan operation, the larger the value the more sensitive it is. Supports using arrays to set the sensitivity of horizontal and vertical panning separately
    # Default is 1.
    # Cannot be panned when set to 0.
    pan_sensitivity: Numeric = 1,

    # The mouse button used for the pan operation, supports.
    # 'left' left mouse button (default)
    # 'middle' middle mouse button
    # 'right' right mouse button
    # 'right' mouse button: If set to right mouse button this will prevent the default right click menu.
    pan_mouse_button: str = "left",

    # The mouse button used for the rotate operation, supporting.
    # 'left' left mouse button (default)
    # 'middle' middle mouse button
    # 'right' right mouse button
    # Note: if set to right mouse button it will prevent the default right click menu.
    rotate_mouse_button: str = "middle",

    # The default view distance from the subject, for globe it is the distance from the surface of the earth
    # For other components such as grid3D and geo3D this is the distance from the central origin.
    # Valid when projection is 'perspective'.
    distance: Numeric = 100,

    # The minimum distance that the view angle can be brought closer to the subject by mouse control. Valid when projection is 'perspective'.
    min_distance: Numeric = 40,

    # The maximum distance from the subject that the angle of view can be drawn away from by mouse control. Valid when projection is 'perspective'.
    max_distance: Numeric = 400,

    # The size of the orthogonal projection. Valid when projection is 'orthographic'.
    orthographic_size: Numeric = 100,

    # The maximum value of the orthographic projection scale. Valid when projection is 'orthographic'.
    min_orthographic_size: Numeric = 20,

    # Minimum value for orthographic scaling. Valid when projection is 'orthographic'.
    max_orthographic_size: Numeric = 400,

    # The angle of rotation of the view around the x-axis, i.e. up and down. Combined with beta, this controls the direction of the view.
    alpha: Numeric = 40,

    # The angle of view around the y-axis, i.e. the angle of rotation left and right.
    beta: Numeric = 0,

    # The centre of the view, around which the rotation will be based, default is [0,0,0].
    center: Optional[Sequence] = None,

    # The minimum alpha value to rotate up and down. That is, the angle at which the viewpoint can be rotated to reach the top.
    min_alpha: Numeric = 5,

    # The maximum alpha value for up and down rotation. This is the angle at which the viewpoint can be rotated to the bottom.
    max_alpha: Numeric = 90,

    # The minimum beta value for left and right rotation. This is the leftmost angle that the view can be rotated to.
    min_beta: Numeric = -80,

    # The maximum beta value for left and right rotation. This is the angle to the far right that the view can be rotated.
    max_beta: Numeric = 80,

    # If or not animation is enabled.
    animation: bool = True,

    # The length of the transition animation.
    animation_duration_update: Numeric = 1000,

    # The easing effect of the transition animation.
    animation_easing_update: str = "cubicInOut",
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Map3D/README)


## GraphGL - GL relational graphs

> *class pyecharts.charts.GraphGL(Chart3D)*

```python
class GraphGL(
    ## Initialize configuration items, refer to ``global_options.InitOpts`''
    init_opts: opts.InitOpts = opts.
)
```

> *func pyecharts.charts.GraphGL.add*

``` python
def add(
    # series name for tooltip display, legend filtering for legends.
    series_name: str,
    
    # The dataset of nodes. GraphGLNode like GraphNode
    nodes: types.Sequence[types.GraphGLNode],
    
    # Relationship data between nodes. GraphGLLink like GraphLink
    links: types.Sequence[types.GraphGLLink],
    
    # Algorithm for layout, supports layout using gephi's forceAtlas2 algorithm.
    layout: str = "forceAtlas2",
    
    # forceAtlas2 layout algorithm configuration
    force_atlas2_opts: types.GraphGLForceAtlas2 = None,
    
    # The shape of the scatter. Defaults to circular.
    # ECharts provides token types including 'circle', 'rect', 'roundRect', 'triangle',
    # 'diamond', 'pin', 'arrow', 'none'
    # You can set the icon to an arbitrary vector path by using 'path://'. This way you don't have to worry about jaggies or blur due to scaling compared to using images, and you can set it to any color.
    # The path graphic adapts to the appropriate (symbolSize in the case of symbols) size.
    # See SVG PathData for the format of the path, which can be edited and exported from tools such as Adobe Illustrator.
    symbol: types.Optional[str] = "circle",
    
    # The size of the symbol
    symbol_size: types.Numeric = 5,
    
    # The style setting for the node.
    itemstyle_opts: types.ItemStyle = None,
    
    # Style settings for relationship edges.
    linestyle_opts: types.LineStyle = opts,
    
    # The level where the component is located.
    z_level: types.Numeric = 10,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/GraphGL/README)
