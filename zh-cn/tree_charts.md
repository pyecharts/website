## Tree：树图

> *class pyecharts.charts.Tree*

```python
class Tree(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Tree.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据项
    data: Sequence[Union[opts.TreeItem, dict]],

    # 树图的布局，有 正交 和 径向 两种。这里的 正交布局 就是我们通常所说的水平 和 垂直 方向，
    # 对应的参数取值为 'orthogonal' 。而 径向布局 是指以根节点为圆心，每一层节点为环，
    # 一层层向外发散绘制而成的布局，对应的参数取值为 'radial'
    layout: str = "orthogonal",

    # 标记的图形。ECharts 提供的标记类型包括 'emptyCircle', 'circle', 'rect', 'roundRect', 
    # 'triangle', 'diamond', 'pin', 'arrow', 'none'。
    symbol: str = "emptyCircle",

    # 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Numeric = 7,

    # 树图中 正交布局 的方向，也就是说只有在 layout = 'orthogonal' 的时候，
    # 该配置项才生效。对应有 水平 方向的 从左到右，从右到左；以及垂直方向的从上到下，
    # 从下到上。取值分别为 'LR' , 'RL', 'TB', 'BT'。注意，之前的配置项值 'horizontal' 
    # 等同于 'LR'， 'vertical' 等同于 'TB'。
    orient: str = "LR",

    # tree组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Optional[str] = None,

    # tree 组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: Optional[str] = None,

    # tree 组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_bottom: Optional[str] = None,

    # tree 组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_right: Optional[str] = None,

    # 折叠节点间隔，当节点过多时可以解决节点显示过杂间隔。
    collapse_interval: Numeric = 0,

    # 是否开启鼠标缩放和平移漫游。默认不开启。如果只想要开启缩放或者平移。
    # 可以设置成 'scale' 或者 'move'。设置成 true 为都开启
    is_roam: bool = False,

    # 子树折叠和展开的交互，默认打开 。由于绘图区域是有限的，而通常一个树图的节点可能会比较多，
    # 这样就会出现节点之间相互遮盖的问题。为了避免这一问题，可以将暂时无关的子树折叠收起，
    # 等到需要时再将其展开。如上面径向布局树图示例，节点中心用蓝色填充的就是折叠收起的子树，可以点击将其展开。
    # 注意：如果配置自定义的图片作为节点的标记，是无法通过填充色来区分当前节点是否有折叠的子树的。
    # 而目前暂不支持，上传两张图片分别表示节点折叠和展开两种状态。所以，如果想明确地显示节点的两种状态，
    # 建议使用 ECharts 常规的标记类型，如 'emptyCircle' 等。
    is_expand_and_collapse: bool = True,

    # 树图初始展开的层级（深度）。根节点是第 0 层，然后是第 1 层、第 2 层，... ，
    # 直到叶子节点。该配置项主要和 折叠展开 交互一起使用，目的还是为了防止一次展示过多节点，
    # 节点之间发生遮盖。如果设置为 -1 或者 null 或者 undefined，所有节点都将展开。
    initial_tree_depth: Optional[Numeric] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 叶子节点标签配置项，参考 `series_options.LabelOpts`
    leaves_label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### TreeItem

> *class pyecharts.options.TreeItem*

```python
class TreeItem(
    # 树节点的名称，用来标识每一个节点。
    name: Optional[str] = None,

    # 节点的值，在 tooltip 中显示。
    value: Optional[Numeric] = None,

    # 该节点的样式，参考 `series_options.LabelOpts`
    label_opts: Optional[LabelOpts] = None,

    # 子节点，嵌套定义。
    children: Optional[Sequence] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Tree/README)


## TreeMap：矩形树图

> *class pyecharts.charts.TreeMap*

```python
class TreeMap(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *class pyecharts.options.TreeMapBreadcrumbOpts*

```python
class TreeMapBreadcrumbOpts(
    # 是否显示面包屑。
    is_show: bool = True,
    
    # 组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: Union[str, Numeric] = "center",

    # 组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    # 默认自适应。
    pos_right: Union[str, Numeric] = "auto",
    
    # 组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Union[str, Numeric] = "auto",
    
    # 组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    # 默认自适应。
    pos_bottom: Union[str, Numeric] = 0,
    
    # 面包屑的高度。
    height: Numeric = 22,
    
    # 当面包屑没有内容时候，设个最小宽度。
    empty_item_width: Numeric = 25,

    # 图形样式。参考 `global_options.ItemStyleOpts`
    item_opts: ItemStyleOpts = ItemStyleOpts(),
)
```

> *class pyecharts.options.TreeMapItemStyleOpts*

```python
class TreeMapItemStyleOpts(
    # 矩形的颜色。
    color: Optional[str] = None,

    # 矩形颜色的透明度。取值范围是 0 ~ 1 之间的浮点数。
    color_alpha: Union[Numeric, Sequence] = None,

    # 矩形颜色的饱和度。取值范围是 0 ~ 1 之间的浮点数。
    color_saturation: Union[Numeric, Sequence] = None,

    # 矩形边框 和 矩形间隔（gap）的颜色。
    border_color: Optional[str] = None,
    
    # 矩形边框线宽。为 0 时无边框。而矩形的内部子矩形（子节点）的间隔距离是由 gapWidth 指定的。
    border_width: Numeric = 0,
    
    # 矩形边框的颜色的饱和度。取值范围是 0 ~ 1 之间的浮点数。
    border_color_saturation: Union[Numeric, Sequence] = None,

    # 矩形内部子矩形（子节点）的间隔距离。
    gap_width: Numeric = 0,

    # 每个矩形的描边颜色。
    stroke_color: Optional[str] = None,

    # 每个矩形的描边宽度。
    stroke_width: Optional[Numeric] = None,
)
```

> *class pyecharts.options.TreeMapLevelsOpts*

```python
class TreeMapLevelsOpts(
    # 矩形颜色的透明度。取值范围是 0 ~ 1 之间的浮点数。
    color_alpha: Union[Numeric, Sequence] = None,

    # 矩形颜色的饱和度。取值范围是 0 ~ 1 之间的浮点数。
    color_saturation: Union[Numeric, Sequence] = None,

    # 表示同一层级节点，在颜色列表中（参见 color 属性）选择时，按照什么来选择。可选值:
    # 'value' 将节点的值（即 series-treemap.data.value）映射到颜色列表中。这样得到的颜色，反应了节点值的大小。
    # 'index' 将节点的 index（序号）映射到颜色列表中。即同一层级中，第一个节点取颜色列表中第一个颜色，第二个节点取第二个。
    # 这样得到的颜色，便于区分相邻节点。
    # 'id' 将节点的 id 映射到颜色列表中。
    # id 是用户指定的，这样能够使得，在 treemap 通过 setOption 变化数值时，同一 id 映射到同一颜色，保持一致性。
    color_mapping_by: str = "index",

    # 矩形树图的 Item 配置，参考 `class pyecharts.options.TreeMapItemStyleOpts`
    treemap_itemstyle_opts: Union[TreeMapItemStyleOpts, dict, None] = None,

    # 每个矩形中，文本标签的样式，参考 `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,
    
    # 用于显示矩形的父节点的标签。参考 `series_options.LabelOpts`
    upper_label_opts: Union[LabelOpts, dict, None] = None,
)
```

> *func pyecharts.charts.TreeMap.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据项
    data: Sequence[Union[opts.TreeItem, dict]],

    # 是否选中图例。
    is_selected: bool = True,

    # leaf_depth 表示『展示几层』，层次更深的节点则被隐藏起来。
    # 设置了 leafDepth 后，下钻（drill down）功能开启。drill down 功能即点击后才展示子层级。
    # 例如，leafDepth 设置为 1，表示展示一层节点。
    leaf_depth: Optional[Numeric] = None,

    # treemap 组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: Optional[str] = None,

    # treemap 组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_right: Optional[str] = None,

    # treemap 组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Optional[str] = None,

    # treemap 组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_bottom: Optional[str] = None,
    
    # treemap 组件的宽度。
    width: types.Union[str, types.Numeric] = "80%",
    
    # treemap 组件的高度。
    height: types.Union[str, types.Numeric] = "80%",

    # 期望矩形长宽比率。布局计算时会尽量向这个比率靠近。
    # 默认为黄金比：0.5 * (1 + Math.sqrt(5))。
    square_ratio: types.Optional[types.JSFunc] = None,

    # 当节点可以下钻时的提示符。只能是字符。
    drilldown_icon: str = "▶",

    # 是否开启拖拽漫游（移动和缩放）。可取值有：
    # false：关闭。
    # 'scale' 或 'zoom'：只能够缩放。
    # 'move' 或 'pan'：只能够平移。
    # true：缩放和平移均可。
    roam: types.Union[bool, str] = True,

    # 点击节点后的行为。可取值为
    # false：节点点击无反应。
    # 'zoomToNode'：点击节点后缩放到节点。
    # 'link'：如果节点数据中有 link 点击节点后会进行超链接跳转。
    node_click: types.Union[bool, str] = "zoomToNode",

    # 点击某个节点，会自动放大那个节点到合适的比例（节点占可视区域的面积比例），这个配置项就是这个比例。
    zoom_to_node_ratio: types.Numeric = 0.32 * 0.32,

    # treemap 中采用『三级配置』：
    #『每个节点』->『每个层级』->『每个系列』。
    # 即我们可以对每个节点进行配置，也可以对树的每个层级进行配置，也可以 series 上设置全局配置。节点上的设置，优先级最高。
    # 最常用的是『每个层级进行配置』，levels 配置项就是每个层级的配置
    levels: types.TreeMapLevel = None,

    # 当前层级的最小 value 值。如果不设置则自动统计。
    visual_min: Optional[Numeric] = None,

    # 当前层级的最大 value 值。如果不设置则自动统计。
    visual_max: Optional[Numeric] = None,

    # 本系列默认的 颜色透明度 选取范围。数值范围 0 ~ 1。
    color_alpha: types.Union[types.Numeric, types.Sequence] = None,
    
    # 本系列默认的 颜色饱和度 选取范围。数值范围 0 ~ 1。
    color_saturation: types.Union[types.Numeric, types.Sequence] = None,
    
    # 表示同一层级节点，在颜色列表中（参见 color 属性）选择时，按照什么来选择。可选值:
    # 'value' 将节点的值（即 series-treemap.data.value）映射到颜色列表中。这样得到的颜色，反应了节点值的大小。
    # 'index' 将节点的 index（序号）映射到颜色列表中。即同一层级中，第一个节点取颜色列表中第一个颜色，第二个节点取第二个。
    # 这样得到的颜色，便于区分相邻节点。
    # 'id' 将节点的 id 映射到颜色列表中。
    # id 是用户指定的，这样能够使得，在 treemap 通过 setOption 变化数值时，同一 id 映射到同一颜色，保持一致性。
    color_mapping_by: str = "index",
    
    # 如果某个节点的矩形的面积，小于这个数值（单位：px平方），这个节点就不显示。
    # 如果不加这个限制，很小的节点会影响显示效果。
    # 关于视觉设置，详见 series-treemap.levels。
    visible_min: types.Numeric = 10,
    
    # 如果某个节点的矩形面积，小于这个数值（单位：px平方），则不显示这个节点的子节点。
    # 这能够在矩形面积不足够大时候，隐藏节点的细节。当用户用鼠标缩放节点时，如果面积大于此阈值，又会显示子节点。
    # 关于视觉设置，详见 series-treemap.levels。
    children_visible_min: types.Optional[types.Numeric] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(position="inside"),

    # 父级标签配置项，参考 `series_options.LabelOpts`
    upper_label_opts: types.Label = opts.LabelOpts(position="inside"),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图形样式配置，参考 `global_options.ItemStyleOpts`
    itemstyle_opts: types.ItemStyle = None,

    # 面包屑控件配置，参考 `TreeMapBreadcrumbOpts`
    breadcrumb_opts: types.TreeMapBreadcrumb = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/TreeMap/README)
