## Tree: Tree diagram

> *class pyecharts.charts.Tree*

```python
class Tree(
    ## Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Tree.add*

``` python
def add(
    # Series name for display of tooltip, legend filter for legend.
    series_name: str,

    # Series data items
    data: Sequence[Union[opts.TreeItem, dict]],

    # The layout of a tree graph, both orthogonal and radial. The orthogonal layout is what we usually call the horizontal and vertical directions.
    # The corresponding parameter takes the value 'orthogonal'. The radial layout is a ring of nodes at each level, with the root node as the centre of the circle.
    # The corresponding parameter is 'radial'
    layout: str = "orthogonal",

    # The type of marker provided by ECharts is 'emptyCircle', 'circle', 'rect', 'roundRect', 
    # 'triangle', 'diamond', 'pin', 'arrow', 'none'.
    symbol: types.JSFunc = "emptyCircle",

    # The size of the marker, which can be set to a single number such as 10, or an array of separate widths and heights.
    # For example, [20, 10] means the marker is 20 wide and 10 high.
    symbol_size: types.Union[types.JSFunc, types.Numeric, types.Sequence] = 7,

    # The direction of the orthogonal layout in the tree diagram, i.e. only if layout = 'orthogonal'.
    # This configuration item is only valid if layout = 'orthogonal'. This corresponds to left-to-right and right-to-left in the horizontal direction, and top-to-bottom and bottom-to-bottom in the vertical direction.
    # bottom to top. The values are 'LR' , 'RL', 'TB', 'BT' respectively. Note that the previous value of the configuration item 'horizontal' 
    # is equivalent to 'LR' and 'vertical' is equivalent to 'TB'.
    orient: str = "LR",

    # The distance of the tree component from the top side of the container.
    # The value of top can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Optional[str] = None,

    # The distance of the tree component from the left side of the container.
    # The value of left can be a specific pixel value like 20, a percentage relative to the height and width of the container like '20%'
    # It can also be 'left', 'centre', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: Optional[str] = None,

    # The distance of the tree component from the lower side of the container.
    The value of # bottom can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'.
    pos_bottom: Optional[str] = None,

    # The distance of the tree component from the right side of the container.
    The value of # right can be a specific pixel value like 20, or a percentage of the container's height and width like '20%'.
    pos_right: Optional[str] = None,

    # Collapse node interval, to resolve node display overspacing when there are too many nodes.
    collapse_interval: Numeric = 0,

    # The shape of the edges of the tree in an orthogonal layout. The values are curve and polyline.
    # Note: this configuration is only valid under orthogonal layout, it will be reported as an error in the development environment under warp layout.
    edge_shape: str = "curve",

    # The position of the bifurcation of a bifurcated segment in the subtree under orthogonal layout when the shape of the edge is a fold.
    # The position here refers to the distance between the fork point and the parent node of the subtree as a percentage of the height of the whole subtree.
    # The default value is '50%', which can be between ['0', '100%'].
    # Note: This configuration item is only valid if edgeShape = 'curve'.
    edge_fork_position: str = "50%",

    # Whether to turn on mouse zoom and pan roaming. Not enabled by default. If you only want to turn on scaling or panning.
    # Can be set to 'scale' or 'move'. Set to true to enable both
    is_roam: bool = False,

    # Interaction for subtree collapse and expansion, turned on by default. Since the drawing area is finite, and a tree diagram may normally have a large number of nodes.
    # This can lead to the problem of nodes covering each other. To avoid this problem, temporarily unrelated subtrees can be collapsed and put away
    # and then expand them when needed. As in the radial layout tree example above, the node centres filled in blue are collapsed subtrees that can be expanded by clicking on them.
    # Note: If a custom image is configured as the node's marker, it is not possible to distinguish whether the current node has a collapsed subtree by its fill colour.
    # And it is not currently supported to upload two images to indicate the two states of the node collapsed and expanded respectively. So, if you want to explicitly show the two states of the node.
    # It is recommended to use the regular ECharts token types, such as 'emptyCircle' etc.
    is_expand_and_collapse: bool = True,

    # The level (depth) at which the tree diagram is initially expanded. The root node is level 0, then level 1, level 2, ... , and
    # up to the leaf nodes. This configuration item is mainly used in conjunction with the collapse and expand interaction, again to prevent too many nodes from being displayed at once.
    # nodes are masked to each other. If set to -1 or null or undefined, all nodes will be expanded.
    initial_tree_depth: Optional[Numeric] = None,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts,

    # Leaf node label configuration items, see `series_options.LabelOpts`
    leaves_label_opts: Union[opts.LabelOpts, dict] = opts,

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### TreeItem

> *class pyecharts.options.TreeItem*

``` python
class TreeItem(
    ### The name of the tree node, used to identify each node.
    name: Optional[str] = None,

    # The value of the node, displayed in the tooltip.
    value: Optional[Numeric] = None,

    # The style of this node, referenced in `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,

    # Child node, nested definition.
    children: Optional[Sequence] = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Tree/README)


## TreeMap: rectangular tree map

> *class pyecharts.charts.TreeMap*

```python
class TreeMap(
    ## Initialize configuration items, see ``global_options.InitOpts``
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *class pyecharts.options.TreeMapBreadcrumbOpts*

``` python
class TreeMapBreadcrumbOpts(
    # Whether to show breadcrumbs or not.
    is_show: bool = True,
    
    # The distance of the component from the left side of the container.
    # The value of left can be a specific pixel value like 20, a percentage relative to the container's height and width like '20%', or 'left', 'center', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: Union[str, Numeric] = "center",

    # The distance of the component from the right side of the container.
    # The value of right can be a specific pixel value like 20, and can be a percentage relative to the height and width of the container like '20%'.
    # Adaptive by default.
    pos_right: Union[str, Numeric] = "auto",
    
    # The distance of the component from the top side of the container.
    # The value of top can be a specific pixel value like 20, a percentage relative to the container's height and width like '20%', or 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Union[str, Numeric] = "auto",
    
    # The distance of the component from the lower side of the container.
    # The value of bottom can be a specific pixel value like 20, and can be a percentage relative to the height and width of the container like '20%'.
    # Adaptive by default.
    pos_bottom: Union[str, Numeric] = 0,
    
    # The height of the breadcrumbs.
    height: Numeric = 22,
    
    # Set a minimum width when the breadcrumbs have no content.
    empty_item_width: Numeric = 25,

    # Graphical style. References `global_options.ItemStyleOpts`
    item_opts: ItemStyleOpts = ItemStyleOpts(),
)
```

> *class pyecharts.options.TreeMapItemStyleOpts*

```python
class TreeMapItemStyleOpts(
    # The colour of the rectangle.
    color: Optional[str] = None,

    # The transparency of the rectangle's colour. Takes a floating point number in the range 0 ~ 1.
    color_alpha: Union[Numeric, Sequence] = None,

    # The saturation of the rectangle's colour. The value is a floating point number between 0 and 1.
    color_saturation: Union[Numeric, Sequence] = None,

    # The colour of the rectangle's border and gap.
    border_color: Optional[str] = None,
    
    # The width of the rectangular border line. No border when 0. The distance between the inner sub-rectangles (child nodes) of the rectangle is specified by the gapWidth.
    border_width: Numeric = 0,
    
    # The saturation of the rectangle's border colour. The value is a floating point number between 0 and 1.
    border_color_saturation: Union[Numeric, Sequence] = None,

    # The distance between the subrectangles (child nodes) inside the rectangle.
    gap_width: Numeric = 0,

    # The stroke colour of each rectangle.
    stroke_color: Optional[str] = None,

    # The width of the stroke of each rectangle.
    stroke_width: Optional[Numeric] = None,
)
```

> *class pyecharts.options.TreeMapLevelsOpts*

``` python
class TreeMapLevelsOpts(
    # Represents a list of colour selections for nodes at the same level (see colorMappingBy for selection rules).
    # Selects the system color list when the default is empty.
    color: Union[str, Sequence] = None,

    # The transparency of the rectangle colour. The value is a floating point number between 0 and 1.
    color_alpha: Union[Numeric, Sequence] = None,

    # The saturation of the rectangle's colour. The value is a floating point number between 0 and 1.
    color_saturation: Union[Numeric, Sequence] = None,

    # Indicates what the same hierarchy node, when selected in the colour list (see color property), is selected by. Optional values:
    # 'value' maps the value of the node (i.e. series-treemap.data.value) to the colour list. The colour thus obtained reflects the size of the node's value.
    # 'index' maps the index of the node to the list of colours. This means that the first node in the same hierarchy takes the first colour in the colour list and the second node takes the second.
    # 'index' maps the node's index to the list of colours.
    # 'id' Maps the node's id to the colour list.
    The # id is user-specified, so that the same id is mapped to the same colour for consistency when the treemap changes values via setOption.
    color_mapping_by: str = "index",

    # Item configuration for the rectangular tree map, see `class pyecharts.options.
    treemap_itemstyle_opts: Union[TreeMapItemStyleOpts, dict, None] = None,

    # The style of the text labels in each rectangle, see `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,
    
    # The label used to display the parent node of the rectangle. References `series_options.LabelOpts`
    upper_label_opts: Union[LabelOpts, dict, None] = None,
)
```

> *func pyecharts.charts.TreeMap.add*

```python
def add(
    # Series name for tooltip display, legend filtering for legends.
    series_name: str,

    # Series data items
    data: Sequence[Union[opts.TreeItem, dict]],

    # Whether the legend is selected.
    is_selected: bool = True,

    # leaf_depth indicates 'how many levels to show', nodes deeper than that are hidden.
    # When leafDepth is set, drill down is enabled. drill down means that sub-levels are only shown when clicked.
    # For example, leafDepth is set to 1 to show one level of nodes.
    leaf_depth: Optional[Numeric] = None,

    # The distance of the treemap component from the left side of the container.
    # The value of left can be a specific pixel value like 20, or a percentage relative to the height and width of the container like '20%'.
    # It can also be 'left', 'center', 'right'.
    # If the value of left is 'left', 'centre', 'right', the component will be automatically aligned according to the corresponding position.
    pos_left: Optional[str] = None,

    # The distance of the treemap component from the right side of the container.
    The value of # right can be a specific pixel value like 20, or a percentage relative to the container's height and width like '20%'.
    pos_right: Optional[str] = None,

    # The distance of the treemap component from the top side of the container.
    # The value of top can be a specific pixel value like 20, or a percentage of the container's height and width like '20%'.
    # It can also be 'top', 'middle', 'bottom'.
    # If the value of top is 'top', 'middle', 'bottom', the component will be automatically aligned according to the corresponding position.
    pos_top: Optional[str] = None,

    # The distance of the treemap component from the lower side of the container.
    The value of # bottom can be a specific pixel value like 20, or a percentage relative to the container height and width like '20%'.
    pos_bottom: Optional[str] = None,
    
    # The width of the treemap component.
    width: types.Union[str, types.Numeric] = "80%",
    
    # The height of the treemap component.
    height: types.Union[str, types.Numeric] = "80%",

    # The desired rectangle aspect ratio. The layout will be calculated as close to this ratio as possible.
    # Defaults to golden ratio: 0.5 * (1 + Math.sqrt(5)).
    square_ratio: types.Optional[types.JSFunc] = None,

    # A hint when a node is drillable. Can only be characters.
    drilldown_icon: str = "▶",

    # Whether to enable drag and drop roaming (moving and zooming). Possible values are.
    # false: off.
    # 'scale' or 'zoom': only zooming is possible.
    # 'move' or 'pan': only panning is possible.
    # true: both zoom and pan are possible.
    roam: types.Union[bool, str] = True,

    # The behaviour of the node when clicked. Can take the values
    # false: node is unresponsive when clicked.
    # 'zoomToNode': zoom to the node after clicking on it.
    # 'link': if there is a link in the node data a hyperlink jump will be made when the node is clicked.
    node_click: types.Union[bool, str] = "zoomToNode",

    # Clicking on a node will automatically zoom that node to the appropriate ratio (the ratio of the node's area to the visible area), and this configuration item is that ratio.
    zoom_to_node_ratio: types.Numeric = 0.32 * 0.32,

    # treemap uses a 'three-level configuration'.
    # 'per node' -> 'per level' -> 'per series'.
    # i.e. we can configure per node, we can configure per level of the tree, and we can set global configuration on series. The settings on the nodes have the highest priority.
    # The most commonly used is 'configure per level', the levels configuration item is the configuration per level
    levels: types.TreeMapLevel = None,

    # The minimum value for the current level. If not set, it will be counted automatically.
    visual_min: Optional[Numeric] = None,

    # The maximum value for the current level. If not set, it will be counted automatically.
    visual_max: Optional[Numeric] = None,
    
    # Visual mapping of other dimensions of the data is supported in treemap.
    # First, the data format of treemap (see series-treemap.data) allows the values of each node to be arrays.
    # Each item of the array is a dimension. visualDimension specifies which item of the array is used for the additional 'visual mapping'.
    # The default is item 0.
    visual_dimension: types.Optional[types.Numeric] = None,

    # The default colour transparency selection range for this series. Numeric range 0 ~ 1.
    color_alpha: types.Union[types.Numeric, types.Sequence] = None,
    
    # The default colour saturation range for this family. Values range 0 ~ 1.
    color_saturation: types.Union[types.Numeric, types.Sequence] = None,
    
    # Indicates what the same hierarchy node, when selected in the colour list (see color property), is selected by. Optional values:
    # 'value' maps the value of the node (i.e. series-treemap.data.value) to the colour list. The colour thus obtained reflects the size of the node's value.
    # 'index' maps the index of the node to the list of colours. This means that the first node in the same hierarchy takes the first colour in the colour list and the second node takes the second.
    # 'index' maps the node's index to the list of colours.
    # 'id' Maps the node's id to the colour list.
    The # id is user-specified, so that the same id is mapped to the same colour for consistency when the treemap changes values via setOption.
    color_mapping_by: str = "index",
    
    # If the area of a node's rectangle is smaller than this value (in px squared), the node will not be displayed.
    # If this limit is not added, very small nodes will affect the display.
    # See series-treemap.levels for details on visual settings.
    visible_min: types.Numeric = 10,
    
    # If the rectangular area of a node is smaller than this value (in px squared), the node's children will not be displayed.
    # This hides the details of a node when the rectangle is not large enough. When the user zooms on the node with the mouse, if the area is larger than this threshold, the child nodes are shown again.
    # See series-treemap.levels for more details on visual settings.
    children_visible_min: types.Optional[types.Numeric] = None,

    # Label configuration items, see `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(position="inside"),

    # Parent label configuration items, see `series_options.LabelOpts`
    upper_label_opts: types.Label = opts.LabelOpts(position="inside"),

    # Tipbox component configuration items, refer to `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # Graphical style configuration, see `global_options.ItemStyleOpts`
    itemstyle_opts: types.ItemStyle = None,

    # Breadcrumb control configuration, see `TreeMapBreadcrumbOpts`
    breadcrumb_opts: types.TreeMapBreadcrumb = None,
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/TreeMap/README)
