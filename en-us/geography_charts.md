## Geo: Geographical coordinate system

> *class pyecharts.charts.Geo*

```python
class Geo(
    ## Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()

    # Whether to ignore non-existent coordinates, default is False, i.e. not to ignore
    is_ignore_nonexistent_coord: bool = False
)
```

> *func pyecharts.charts.Geo.add_schema*

``` python
def add_schema(
    # map type, see pyecharts.datasets.map_filenames.json file for details
    maptype: str = "china",

    # Whether to enable mouse zoom and pan roaming.
    is_roam: bool = True,

    # The scale of the current view. Default is 1
    zoom: Optional[Numeric] = None,

    # The center of the current view, expressed in latitude and longitude. Example: center: [115.97, 29.71]
    center: Optional[Sequence] = None,

    # The parameter to scale the aspect ratio of the map.
    aspect_scale: types.Numeric = 0.75,

    # Two-dimensional array defining the latitude and longitude of the top left and bottom right corners of the location.
    bounding_coords: types.Optional[types.Sequence[types.Numeric]] = None,

    # The minimum scaling value.
    min_scale_limit: types.Optional[types.Numeric] = None,

    # The maximum scale value.
    max_scale_limit: types.Optional[types.Numeric] = None, # max_scale_limit: types.Optional[types.Numeric] = None,

    # Default is 'name', a custom property name for the GeoJSON element, used as the primary key to associate data points with GeoJSON geographic elements.
    name_property: str = "name",

    # Checked mode, indicates if multiple checks are supported, default off, supports boolean and string.
    # String value can be selected as 'single' for single selection or 'multiple' for multiple selection.
    selected_mode: types.Union[bool, str] = False,

    # pyecharts does not provide a left/top/right/bottom configuration at the moment
    # layoutCenter and layoutSize provide a means of layout other than left/right/top/bottom/width/height.
    # When using left/right/top/bottom/width/height
    # It may be difficult to place the map right in the middle of a boxed area while maintaining its aspect ratio and keeping it within the box.
    # In this case, the layoutCenter property defines the position of the map centre on the screen and the layoutSize defines the size of the map.
    # The following example
    # layoutCenter: ['30%', '30%'],
    # // if the aspect ratio is greater than 1 then the width is 100, if less than 1 then the height is 100, ensuring no more than a 100x100 area
    # layoutSize: 100
    layout_center: types.Optional[types.Sequence[str]] = None,

    # The size of the map, see layoutCenter. supports a percentage or absolute pixel size relative to the screen width and height.
    layout_size: types.Union[str, types.Numeric] = None,

    # # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict, None] = None,

    # Polygons for the map area Graphical style.
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # The polygon style for the highlighted state
    emphasis_itemstyle_opts: Union[opts.ItemStyleOpts, dict,None] = None,

    # The label style in the highlighted state.
    emphasis_label_opts: Union[opts.LabelOpts, dict, None] = None,
    
    # Configure styles for specific regions in the map. Refer to `charts_options.GeoRegionsOpts` for specific configurations
    regions_opts: types.Union[types.Sequence[types.GeoRegions], types.Sequence[dict]] = None,
):
```

> *func pyecharts.charts.Geo.add*

``` python
def add(
    # Series name for display of tooltip, legend filter for legends.
    series_name: str,

    # Data items (coordinate point names, coordinate point values)
    data_pair: Sequence,

    # Geo plot types, 9 types
    # from pyecharts.globals import GeoType
    # ChartType.SCATTER
    # ChartType.SCATTERGL
    # ChartType.EFFECT_SCATTER
    # ChartType.FLOWGL
    # ChartType.HEATMAP
    # ChartType.LINES
    # ChartType.LINESGL
    # ChartType.CUSTOM
    # ChartType.PIE
    type_: str = "scatter",

    # Whether the legend is selected or not
    is_selected: bool = True,

    # Mark the shape of the graphic
    symbol: Optional[str] = None,

    # The size of the marker
    symbol_size: Numeric = 12,

    # The size of each point, valid on the geographic coordinate system (coordinateSystem: 'geo').
    blur_size: types.Numeric = 20,
    
    # The size of each point blur, valid on the geographic coordinate system (coordinateSystem: 'geo').
    point_size: types.Numeric = 20,

    # Radius of the pie chart, valid when type_ is ChartType.
    radius: types.Optional[types.Sequence] = None,

    # series label colour
    color: Optional[str] = None,
    
    # Whether it is a polyline, in the case of drawing lines
    is_polyline: bool = False,
    
    # Whether to enable optimization of large scale line graphs, in case of particularly large data graphs (>=5k)
    is_large: bool = False,
    
    # The length of the special trails. Takes a value from 0 to 1, the larger the value the longer the trail. Default value 0.2
    trail_length: Numeric = 0.2,
    
    # Threshold to turn on draw optimization.
    large_threshold: Numeric = 2000,
    
    # Configure the number of graphics rendered per frame for the series
    progressive: types.Numeric = 400,
    
    # Threshold for the number of graphics to enable progressive rendering, which is enabled when the number of graphics in a single series exceeds this threshold.
    progressive_threshold: types.Numeric = 3000,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Ripple effect configuration items, see `series_options.EffectOpts`
    effect_opts: Union[opts.EffectOpts, dict] = opts.EffectOpts(),

    # Line style configuration items, see `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(), # linestyle_opts: Union[opts.LineStyleOpts, dict] = opts,

    # Tipbox component configuration items, see `series_options.
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # This configuration is relatively complex (refer to https://www.echartsjs.com/zh/option.html#series-custom.renderItem)
    render_item: types.JsCode = None,
    
    # This is a relatively complex configuration (see https://www.echartsjs.com/zh/option.html#series-custom.encode)
    encode: types.Union[types.JsCode, dict] = None,
)
```

> *func pyecharts.charts.Geo.add_coordinate*

Add a coordinate point
``` python
def add_coordinate(
    # The name of the coordinate location
    name: str,

    # Longitude
    longitude: Numeric,

    # Latitude
    latitude: Numeric,
)
```

> *func pyecharts.charts.Geo.add_coordinate_json*

Add multiple coordinate points in JOSN file format
``` python
def add_coordinate_json(
    # Coordinate data in json file format
    # The format is as follows
    # {
    # "Acheng": [126.58, 45.32],
    # "Aksu": [80.19, 41.09]
    # }
  ],
    json_file: str
)
```

> *func pyecharts.charts.Geo.get_coordinate*

Query the coordinates of a specified location
``` python
def get_coordinate(
    # the name of the location
    name: str
) -> Sequence
```

The coordinates of the Geo chart are referenced from `pyecharts.datasets.COORDINATES`, `COORDINATES` is a dictionary class that supports fuzzy matching. Matching thresholds can be set.
```python
from pyecharts.datasets import COORDINATES
# cutoff is the matching threshold, the higher the threshold the higher the similarity, 1 is identical. The default is 0.6
COORDINATES.cutoff = 0.75
```

> *func pyecharts.options.GeoRegionsOpts*

```python
class GeoRegionsOpts(
    # The name of the map region, e.g. 'Guangdong', 'Zhejiang'.
    name: Optional[str] = None,
    
    # Whether the region is selected or not.
    is_selected: bool = False,
    
    # The polygon style setting for the region.
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
    
    # Text labels on the graph that can be used to describe some data information about the graph, such as values, names, etc.
    label_opts: Union[LabelOpts, dict, None] = None,
    
    # Style settings for the highlighted state.
    emphasis_itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
    
    # The label settings for the highlighted state.
    emphasis_label_opts: Union[LabelOpts, dict, None] = None,
    
    # The style settings for the selected state.
    select_itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
    
    # The label settings of the selected state.
    select_label_opts: Union[LabelOpts, dict, None] = None,
    
    # The style settings of the fade state.
    blur_itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
    
    # The label settings for the fadeout state.
    blur_label_opts: Union[LabelOpts, dict, None] = None,
    
    # The specific tooltip settings in this region.
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
    
    # Whether the graph does not respond and trigger mouse events, default is false, i.e. responds and triggers mouse events.
    is_silent: bool = False,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Geo/README)


## Map: Map

> *class pyecharts.charts.Map*

```python
class Map(
    ## Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Map.add*

``` python
def add(
    # Series name for display of tooltip, legend filter for legend.
    series_name: str,

    # Data items (coordinate point names, coordinate point values)
    data_pair: types.Sequence[types.Union[types.Sequence, opts.MapItem, dict]],

    # Map types, see pyecharts.datasets.map_filenames.json file for details
    maptype: str = "china",

    # Whether the legend is selected or not
    is_selected: bool = True,

    # Whether to enable mouse zoom and pan roaming.
    is_roam: bool = True,
    
    # The centre of the current view, expressed in latitude and longitude
    center: Optional[Sequence] = None,

    # The parameter to scale the aspect ratio of the map.
    aspect_scale: types.Numeric = 0.75,

    # Two-dimensional array defining the latitude and longitude of the top left and bottom right corners of the location.
    bounding_coords: types.Optional[types.Sequence[types.Numeric]] = None,

    # The minimum scaling value.
    min_scale_limit: types.Optional[types.Numeric] = None,

    # The maximum scale value.
    max_scale_limit: types.Optional[types.Numeric] = None, # max_scale_limit: types.Optional[types.Numeric] = None,

    # Default is 'name', a custom property name for the GeoJSON element, used as the primary key to associate data points with GeoJSON geographic elements.
    name_property: str = "name",

    # Checked mode, indicates if multiple checks are supported, default off, supports boolean and string.
    # String value can be selected as 'single' for single selection or 'multiple' for multiple selection.
    selected_mode: types.Union[bool, str] = False,
    
    # The scale of the current view.
    zoom: Optional[Numeric] = 1,
    
    # Name map for the custom region
    name_map: Optional[dict] = None,
    
    # The shape of the marker graphic
    symbol: Optional[str] = None,
    
    # Multiple series with the same map type will use the same map presentation.
    # If multiple series all have values in the same area, ECharts will count these values to get a single figure.
    # This configuration item is what is used to configure how the statistics will be presented, currently there are.
    # 'sum' Takes the sum.
    # 'average' takes the average value.
    # 'max' takes the maximum value.
    # 'min' takes the minimum value.
    map_value_calculation: str = "sum",

    # Whether to display the marker graph
    is_map_symbol_show: bool = True,
    
    # The zlevel value of all shapes.
    # Canvas with a larger zlevel is placed on top of Canvas with a smaller zlevel.
    z_level: types.Numeric = 0.
    
    # The z-level of all graphics of the component. Controls the order of the shapes before and after them. shapes with small z values are overwritten by shapes with large z values.
    # z has lower priority than zlevel and no new Canvas is created.
    z: types.Numeric = 2.
    
    # The distance of the component from the left side of the container.
    # The value of left can be a specific pixel value like 20, or a percentage relative to the container height and width like '20%'
    # It can also be 'left', 'centre', 'right'.
    pos_left: types.Union[str, types.Numeric] = "auto".
    
    # The distance of the component from the top side of the container.
    # The value of top can be a specific pixel value like 20, it can be a percentage relative to the height and width of the container like '20%'
    # It can also be 'top', 'middle', 'bottom'.
    pos_top: types.Union[str, types.Numeric] = "auto".
    
    # The distance of the component from the right side of the container.
    The value of # right can be a specific pixel value like 20, and can be a percentage relative to the container height and width like '20%'. Adaptive by default.
    pos_right: types.Union[str, types.Numeric] = "auto".
    
    # The distance of the component from the lower side of the container.
    # The value of bottom can be a specific pixel value like 20, or a percentage relative to the container height and width like '20%'. Adaptive by default.
    pos_bottom: types.Union[str, types.Numeric] = "auto".
    
    # By default, map series generates its own internal dedicated geo component. But it is possible to specify a geo component with this geoIndex.
    geo_index: types.Optional[types.Numeric] = None.
    
    # When using a dataset, seriesLayoutBy specifies whether the dataset has rows or columns corresponding to the series
    # That is, whether the series is "laid out" on the dataset's rows or columns. Possible values:
    # 'column': by default, the columns of the dataset correspond to the series, so that each column in the dataset is a dimension.
    # 'row': the row of the dataset corresponds to the series, so that each row in the dataset is a dimension.
    series_layout_by: str = "column".
    
    # If series.data is not specified and a dataset exists, then the dataset will be used. datasetIndex specifies which dataset is used for this series.
    dataset_index: types.Optional[types.Numeric] = 0.

    # pyecharts does not provide a left/top/right/bottom configuration at the moment
    # layoutCenter and layoutSize provide a means of layout other than left/right/top/bottom/width/height.
    # When using left/right/top/bottom/width/height
    # It may be difficult to place the map right in the middle of a boxed area while maintaining its aspect ratio and staying within the box.
    # In this case, the layoutCenter property defines the position of the map centre on the screen and the layoutSize defines the size of the map.
    # The following example
    # layoutCenter: ['30%', '30%'],
    # // if the aspect ratio is greater than 1 then the width is 100, if less than 1 then the height is 100, ensuring no more than a 100x100 area
    # layoutSize: 100
    layout_center: types.Optional[types.Sequence[str]] = None,

    # The size of the map, see layoutCenter. supports a percentage or absolute pixel size relative to the screen width and height.
    layout_size: types.Union[str, types.Numeric] = None,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Tipbox component configuration items, see `series_options.
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # Highlight label configuration items, see `series_options.LabelOpts`
    emphasis_label_opts: Union[opts.LabelOpts, dict, None] = None,

    # Highlight the item style configuration, see `series_options.ItemStyleOpts`
    emphasis_itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### MapItem: map data item

``` python
class MapItem(
    ### The name of the map area to which the data corresponds, e.g. 'Guangdong', 'Zhejiang'.
    name: Optional[str] = None,

    # The value of the data for the region.
    value: Optional[Numeric] = None,

    # Whether the field is selected or not.
    is_selected: bool = False,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Map/README)

## BMap: Baidu Maps

Baidu Maps requires a Developer AK application, [official website application](https://lbsyun.baidu.com/).

> *class pyecharts.charts.BMap*

```python
class BMap(
    # Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()

    # Whether to ignore non-existent coordinates, default is False, i.e. not to ignore
    is_ignore_nonexistent_coord: bool = False
)
```

> *func pyecharts.charts.BMap.add_schema*

``` python
def add_schema(
    # Baidu map development application appkey, please use to Baidu map developers themselves to Baidu map developer centre
    # Register Baidu ak.
    baidu_ak: str,
    
    # The centre point of the current view, expressed in latitude and longitude
    center: Optional[Sequence] = None,
    
    # The zoom scale of the current view.
    zoom: Optional[Numeric] = None,
    
    # Whether to enable mouse zoom and pan roaming.
    is_roam: bool = True,
    
    # The map style configuration item
    map_style: Optional[dict] = None,
)
```

> *func pyecharts.charts.bmap.add*

``` python
def add(
    # Series name for display of tooltip, legend filter for legend.
    series_name: str,

    # Data items (coordinate point names, coordinate point values)
    data_pair: Sequence,

    # Geo plot types, 4 types: scatter, effectScatter, heatmap, lines, recommended
    # from pyecharts.globals import GeoType
    # GeoType.GeoType.EFFECT_SCATTER, GeoType.HEATMAP, GeoType.LINES
    type_: str = "scatter",

    # Whether the legend is selected or not
    is_selected: bool = True,

    # Mark the shape of the graphic
    symbol: Optional[str] = None,

    # The size of the marker
    symbol_size: Numeric = 12,

    # series label colour
    color: Optional[str] = None,
    
    # Whether it is a polyline, in the case of a lines diagram
    is_polyline: bool = False,
    
    # Whether to enable optimization of large scale line graphs, in case of particularly large data graphs (>=5k)
    is_large: bool = False,
    
    # Threshold to enable plotting optimization.
    large_threshold: Numeric = 2000,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Ripple effect configuration items, see `series_options.EffectOpts`
    effect_opts: Union[opts.EffectOpts, dict] = opts.EffectOpts(),

    # Line style configuration items, see `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(), # linestyle_opts: Union[opts.LineStyleOpts, dict] = opts,

    # Tipbox component configuration items, see `series_options.
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Item style configuration items, see `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

> *func pyecharts.charts.BMap.add_control_panel*

``` python
def add_control_panel(
    # The map's pan and zoom control
    navigation_control_opts: Union[opts.BMapNavigationControlOpts, dict, None] = None,
    
    # Thumbnail map control
    overview_map_opts: Union[opts.BMapOverviewMapControlOpts, dict, None] = None, # overview_map_opts: Union[opts.BMapOverviewMapControlOpts, dict, None] = None
    
    # Scale control
    scale_control_opts: Union[opts.BMapScaleControlOpts, dict, None] = None,
    
    # Controls for switching map types
    maptype_control_opts: Union[opts.BMapTypeControlOpts, dict, None] = None,
    
    # A copyright control where you can add your own copyright information to the map.
    # Each copyright message needs to contain the following: a unique identifier for the copyright, the content of the copyright and the area range to which it applies.
    copyright_control_opts: Union[opts.BMapCopyrightTypeOpts, dict, None] = None,
    
    # Controls for map positioning, using HTML5 browser positioning
    geo_location_control_opts: Union[opts.BMapGeoLocationControlOpts, dict, None] = None,
)
```

### BMapNavigationControlOpts: panning and zooming control for maps

> *class pyecharts.options.BMapNavigationControlOpts*

```python
class BMapNavigationControlOpts(
    # The docking position of the control
    # ANCHOR_TOP_LEFT, the control will be positioned to the top left corner of the map, value is 0
    # ANCHOR_TOP_RIGHT, the control will be positioned to the top right corner of the map, the value is 1
    # ANCHOR_BOTTOM_LEFT, the control will be positioned to the bottom left corner of the map, the value is 2
    # ANCHOR_BOTTOM_RIGHT, the control will be positioned to the bottom right corner of the map, the value is 3
    position: Numeric = BMapType.ANCHOR_TOP_LEFT,
    
    # The horizontal offset value of the control
    offset_width: Numeric = 10,
    
    # The vertical offset of the control
    offset_height: Numeric = 10,
    
    # The type of the pan and zoom control
    # NAVIGATION_CONTROL_LARGE, the standard pan and zoom control (including pan and zoom buttons and sliders, value 0)
    # NAVIGATION_CONTROL_SMALL, contains only pan and zoom buttons, value is 1
    # NAVIGATION_CONTROL_PAN, contains only the pan button, value 2
    # NAVIGATION_CONTROL_ZOOM, contains only the zoom button, value 3
    type_: Numeric = BMapType.NAVIGATION_CONTROL_LARGE,

    # Whether to show the level prompt message
    is_show_zoom_info: bool = False,

    # Whether the control has integrated positioning functionality
    is_enable_geo_location: bool = False,
)
```

### BMapOverviewMapControlOpts: thumbnail map control

> *class pyecharts.options.BMapOverviewMapControlOpts*

```python
class BMapOverviewMapControlOpts(
    # The dock position of the control
    # ANCHOR_TOP_LEFT, the control will be positioned to the top left corner of the map, value is 0
    # ANCHOR_TOP_RIGHT, the control will be positioned to the top right corner of the map, the value is 1
    # ANCHOR_BOTTOM_LEFT, the control will be positioned to the bottom left corner of the map, the value is 2
    # ANCHOR_BOTTOM_RIGHT, the control will be positioned to the bottom right corner of the map with a value of 3
    position: Numeric = BMapType.ANCHOR_BOTTOM_RIGHT,

    # The horizontal offset value of the control
    offset_width: Numeric = 10,

    # The vertical offset of the control
    offset_height: Numeric = 50,

    # The open/close state of the thumbnail map after it has been added to the map, default is False Close
    is_open: bool = False,
)
```

### BMapScaleControlOpts: Scale control

> *class pyecharts.options.BMapScaleControlOpts*

```python
class BMapScaleControlOpts(
    # The dock position of the control
    # ANCHOR_TOP_LEFT, the control will be positioned to the top left corner of the map, value is 0
    # ANCHOR_TOP_RIGHT, the control will be positioned to the top right corner of the map, the value is 1
    # ANCHOR_BOTTOM_LEFT, the control will be positioned to the bottom left corner of the map, the value is 2
    # ANCHOR_BOTTOM_RIGHT, the control will be positioned to the bottom right corner of the map with a value of 3
    position: Numeric = BMapType.ANCHOR_BOTTOM_RIGHT,

    # The horizontal offset value of the control
    offset_width: Numeric = 10,

    # The vertical offset of the control
    offset_height: Numeric = 50,
)
```

### BMapTypeControl: control for switching map types

> *class pyecharts.options.BMapTypeControl*

```python
class BMapTypeControl(
    # The dock position of the control
    # ANCHOR_TOP_LEFT, the control will be positioned to the top left corner of the map, value is 0
    # ANCHOR_TOP_RIGHT, the control will be positioned to the top right corner of the map, the value is 1
    # ANCHOR_BOTTOM_LEFT, the control will be positioned to the bottom left corner of the map, the value is 2
    # ANCHOR_BOTTOM_RIGHT, the control will be positioned to the bottom right corner of the map with a value of 3
    position: Numeric = BMapType.ANCHOR_TOP_RIGHT,

    # Map type property
    # MAPTYPE_CONTROL_HORIZONTAL, the button is displayed horizontally, the default is displayed with this type. The value is 0.
    # MAPTYPE_CONTROL_DROPDOWN, the button is displayed as a drop-down list, the value is 1
    # MAPTYPE_CONTROL_MAP to display the type control as a picture, the maptypes property cannot be specified when this type is set, the value is 2
    type_: Numeric = BMapType.MAPTYPE_CONTROL_HORIZONTAL,
)
```

### BMapCopyrightType: copyright control

> *class pyecharts.options.BMapCopyrightType*

``` python
class BMapCopyrightType(
    # The dock position of the control
    # ANCHOR_TOP_LEFT, the control will be positioned to the top left corner of the map, value is 0
    # ANCHOR_TOP_RIGHT, the control will be positioned to the top right corner of the map, the value is 1
    # ANCHOR_BOTTOM_LEFT, the control will be positioned to the bottom left corner of the map, the value is 2
    # ANCHOR_BOTTOM_RIGHT, the control will be positioned to the bottom right corner of the map, the value is 3
    position: Numeric = BMapType.ANCHOR_BOTTOM_RIGHT,

    # The horizontal offset value of the control
    offset_width: Numeric = 10,

    # The vertical offset of the control
    offset_height: Numeric = 50,

    # The text content of the copyright, which can be placed in HTML tags
    copyright_: str = "",
)
```

### BMapGeoLocationControlOpts: controls for map positioning

> *class pyecharts.options.BMapGeoLocationControlOpts*

```python
class BMapGeoLocationControlOpts(
    # The docking position of the control
    # ANCHOR_TOP_LEFT, the control will be positioned to the top left corner of the map, value is 0
    # ANCHOR_TOP_RIGHT, the control will be positioned to the top right corner of the map, the value is 1
    # ANCHOR_BOTTOM_LEFT, the control will be positioned to the bottom left corner of the map, the value is 2
    # ANCHOR_BOTTOM_RIGHT, the control will be positioned to the bottom right corner of the map, the value is 3
    position: Numeric = BMapType.ANCHOR_BOTTOM_RIGHT,

    # The horizontal offset value of the control
    offset_width: Numeric = 10,

    # The vertical offset of the control
    offset_height: Numeric = 50,

    # Whether to display the positioning information panel. Default is to show the location information panel
    is_show_address_bar: bool = True,

    # Whether or not to position the control when adding it. The default is to add the control without positioning
    is_enable_auto_location: bool = False,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/BMap/README)
