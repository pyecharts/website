## Geo：地理坐标系

> *class pyecharts.charts.Geo*

```python
class Geo(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()

    # 是否忽略不存在的坐标，默认值为 False，即不忽略
    is_ignore_nonexistent_coord: bool = False
)
```

> *func pyecharts.charts.Geo.add_schema*

```python
def add_schema(
    # 地图类型，具体参考 pyecharts.datasets.map_filenames.json 文件
    maptype: str = "china",

    # 是否开启鼠标缩放和平移漫游。
    is_roam: bool = True,

    # 当前视角的缩放比例。默认为 1
    zoom: Optional[Numeric] = None,

    # 当前视角的中心点，用经纬度表示。例如：center: [115.97, 29.71]
    center: Optional[Sequence] = None,

    # # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict, None] = None,

    # 地图区域的多边形 图形样式。
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] =None,

    # 高亮状态下的多边形样式
    emphasis_itemstyle_opts: Union[opts.ItemStyleOpts, dict,None] = None,

    # 高亮状态下的标签样式。
    emphasis_label_opts: Union[opts.LabelOpts, dict, None] =None,
):
```

> *func pyecharts.charts.Geo.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 数据项 (坐标点名称，坐标点值)
    data_pair: Sequence,

    # Geo 图类型，有 scatter, effectScatter, heatmap, lines 4 种，建议使用
    # from pyecharts.globals import GeoType
    # GeoType.GeoType.EFFECT_SCATTER，GeoType.HEATMAP，GeoType.LINES
    type_: str = "scatter",

    # 是否选中图例
    is_selected: bool = True,

    # 标记图形形状
    symbol: Optional[str] = None,

    # 标记的大小
    symbol_size: Numeric = 12,

    # 每个点的大小，在地理坐标系(coordinateSystem: 'geo')上有效。
    blur_size: types.Numeric = 20,
    
    # 每个点模糊的大小，在地理坐标系(coordinateSystem: 'geo')上有效。
    point_size: types.Numeric = 20,

    # 系列 label 颜色
    color: Optional[str] = None,
    
    # 是否是多段线，在画 lines 图情况下
    is_polyline: bool = False,
    
    # 是否启用大规模线图的优化，在数据图形特别多的时候（>=5k）可以开启
    is_large: bool = False,
    
    # 特效尾迹的长度。取从 0 到 1 的值，数值越大尾迹越长。默认值 0.2
    trail_length: Numeric = 0.2,
    
    # 开启绘制优化的阈值。
    large_threshold: Numeric = 2000,
    
    # 配置该系列每一帧渲染的图形数
    progressive: types.Numeric = 400,
    
    # 启用渐进式渲染的图形数量阈值，在单个系列的图形数量超过该阈值时启用渐进式渲染。
    progressive_threshold: types.Numeric = 3000,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 涟漪特效配置项，参考 `series_options.EffectOpts`
    effect_opts: Union[opts.EffectOpts, dict] = opts.EffectOpts(),

    # 线样式配置项，参考 `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # 这个配置相对非常复杂（参照地址: https://www.echartsjs.com/zh/option.html#series-custom.renderItem）
    render_item: types.JsCode = None,
    
    # 这个配置相对非常复杂（参照地址: https://www.echartsjs.com/zh/option.html#series-custom.encode）
    encode: types.Union[types.JsCode, dict] = None,
)
```

> *func pyecharts.charts.Geo.add_coordinate*

新增一个坐标点
```python
def add_coordinate(
    # 坐标地点名称
    name: str,

    # 经度
    longitude: Numeric,

    # 纬度
    latitude: Numeric,
)
```

> *func pyecharts.charts.Geo.add_coordinate_json*

以 JOSN 文件格式新增多个坐标点
```python
def add_coordinate_json(
    # json 文件格式的坐标数据
    # 格式如下
    # {
    #   "阿城": [126.58, 45.32],
    #   "阿克苏": [80.19, 41.09]
    # }
  ],
    json_file: str
)
```

> *func pyecharts.charts.Geo.get_coordinate*

查询指定地点的坐标
```python
def get_coordinate(
    # 地点名称
    name: str
) -> Sequence
```

Geo 图的坐标引用自 `pyecharts.datasets.COORDINATES`，`COORDINATES` 是一个支持模糊匹配的字典类。可设置匹配的阈值。
```python
from pyecharts.datasets import COORDINATES
# cutoff 为匹配阈值，阈值越高相似性越高，1 为完全相同。默认为 0.6
COORDINATES.cutoff = 0.75
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Geo/README)


## Map：地图

> *class pyecharts.charts.Map*

```python
class Map(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Map.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 数据项 (坐标点名称，坐标点值)
    data_pair: types.Sequence[types.Union[types.Sequence, opts.MapItem, dict]],

    # 地图类型，具体参考 pyecharts.datasets.map_filenames.json 文件
    maptype: str = "china",

    # 是否选中图例
    is_selected: bool = True,

    # 是否开启鼠标缩放和平移漫游。
    is_roam: bool = True,
    
    # 当前视角的中心点，用经纬度表示
    center: Optional[Sequence] = None,
    
    # 当前视角的缩放比例。
    zoom: Optional[Numeric] = 1,
    
    # 自定义地区的名称映射
    name_map: Optional[dict] = None,
    
    # 标记图形形状
    symbol: Optional[str] = None,

    # 是否显示标记图形
    is_map_symbol_show: bool = True,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,

    # 高亮标签配置项，参考 `series_options.LabelOpts`
    emphasis_label_opts: Union[opts.LabelOpts, dict, None] = None,

    # 高亮图元样式配置项，参考 `series_options.ItemStyleOpts`
    emphasis_itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### MapItem：地图数据项

```python
class MapItem(
    # 数据所对应的地图区域的名称，例如 '广东'，'浙江'。
    name: Optional[str] = None,

    # 该区域的数据值。
    value: Optional[Numeric] = None,

    # 该区域是否选中。
    is_selected: bool = False,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Map/README)


## BMap：百度地图

百度地图需要申请开发者 AK，[官网申请](https://lbsyun.baidu.com/)。

> *class pyecharts.charts.BMap*

```python
class BMap(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()

    # 是否忽略不存在的坐标，默认值为 False，即不忽略
    is_ignore_nonexistent_coord: bool = False
)
```

> *func pyecharts.charts.BMap.add_schema*

```python
def add_schema(
    # 百度地图开发应用 appkey，请使用到百度地图的开发者自行到百度地图开发者中心
    # 注册百度 ak。
    baidu_ak: str,
    
    # 当前视角的中心点，用经纬度表示
    center: Optional[Sequence] = None,
    
    # 当前视角的缩放比例。
    zoom: Optional[Numeric] = None,
    
    # 是否开启鼠标缩放和平移漫游。
    is_roam: bool = True,
    
    # 地图样式配置项
    map_style: Optional[dict] = None,
)
```

> *func pyecharts.charts.BMap.add*

```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 数据项 (坐标点名称，坐标点值)
    data_pair: Sequence,

    # Geo 图类型，有 scatter, effectScatter, heatmap, lines 4 种，建议使用
    # from pyecharts.globals import GeoType
    # GeoType.GeoType.EFFECT_SCATTER，GeoType.HEATMAP，GeoType.LINES
    type_: str = "scatter",

    # 是否选中图例
    is_selected: bool = True,

    # 标记图形形状
    symbol: Optional[str] = None,

    # 标记的大小
    symbol_size: Numeric = 12,

    # 系列 label 颜色
    color: Optional[str] = None,
    
    # 是否是多段线，在画 lines 图情况下
    is_polyline: bool = False,
    
    # 是否启用大规模线图的优化，在数据图形特别多的时候（>=5k）可以开启
    is_large: bool = False,
    
    # 开启绘制优化的阈值。
    large_threshold: Numeric = 2000,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 涟漪特效配置项，参考 `series_options.EffectOpts`
    effect_opts: Union[opts.EffectOpts, dict] = opts.EffectOpts(),

    # 线样式配置项，参考 `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

> *func pyecharts.charts.BMap.add_control_panel*

```python
def add_control_panel(
    # 地图的平移缩放控件
    navigation_control_opts: Union[opts.BMapNavigationControlOpts, dict, None] = None,
    
    # 缩略地图控件
    overview_map_opts: Union[opts.BMapOverviewMapControlOpts, dict, None] = None,
    
    # 比例尺控件
    scale_control_opts: Union[opts.BMapScaleControlOpts, dict, None] = None,
    
    # 切换地图类型的控件
    maptype_control_opts: Union[opts.BMapTypeControlOpts, dict, None] = None,
    
    # 版权控件，您可以在地图上添加自己的版权信息。
    # 每一个版权信息需要包含如下内容：版权的唯一标识、版权内容和其适用的区域范围。
    copyright_control_opts: Union[opts.BMapCopyrightTypeOpts, dict, None] = None,
    
    # 地图定位的控件，使用 HTML5 浏览器定位功能
    geo_location_control_opts: Union[opts.BMapGeoLocationControlOpts, dict, None] = None,
)
```

### BMapNavigationControlOpts：地图的平移缩放控件

> *class pyecharts.options.BMapNavigationControlOpts*

```python
class BMapNavigationControlOpts(
    # 控件的停靠位置
    # ANCHOR_TOP_LEFT，控件将定位到地图的左上角，值为 0
    # ANCHOR_TOP_RIGHT，控件将定位到地图的右上角，值为 1
    # ANCHOR_BOTTOM_LEFT，控件将定位到地图的左下角，值为 2
    # ANCHOR_BOTTOM_RIGHT，控件将定位到地图的右下角，值为 3
    position: Numeric = BMapType.ANCHOR_TOP_LEFT,
    
    # 控件的水平偏移值
    offset_width: Numeric = 10,
    
    # 控件的竖直偏移值
    offset_height: Numeric = 10,
    
    # 平移缩放控件的类型
    # NAVIGATION_CONTROL_LARGE，标准的平移缩放控件（包括平移、缩放按钮和滑块，值为 0
    # NAVIGATION_CONTROL_SMALL，仅包含平移和缩放按钮，值为 1
    # NAVIGATION_CONTROL_PAN，仅包含平移按钮，值为 2
    # NAVIGATION_CONTROL_ZOOM，仅包含缩放按钮，值为 3
    type_: Numeric = BMapType.NAVIGATION_CONTROL_LARGE,

    # 是否显示级别提示信息
    is_show_zoom_info: bool = False,

    # 控件是否集成定位功能
    is_enable_geo_location: bool = False,
)
```

### BMapOverviewMapControlOpts：缩略地图控件

> *class pyecharts.options.BMapOverviewMapControlOpts*

```python
class BMapOverviewMapControlOpts(
    # 控件的停靠位置
    # ANCHOR_TOP_LEFT，控件将定位到地图的左上角，值为 0
    # ANCHOR_TOP_RIGHT，控件将定位到地图的右上角，值为 1
    # ANCHOR_BOTTOM_LEFT，控件将定位到地图的左下角，值为 2
    # ANCHOR_BOTTOM_RIGHT，控件将定位到地图的右下角，值为 3
    position: Numeric = BMapType.ANCHOR_BOTTOM_RIGHT,

    # 控件的水平偏移值
    offset_width: Numeric = 10,

    # 控件的竖直偏移值
    offset_height: Numeric = 50,

    # 缩略地图添加到地图后的开合状态，默认为 False 关闭
    is_open: bool = False,
)
```

### BMapScaleControlOpts：比例尺控件

> *class pyecharts.options.BMapScaleControlOpts*

```python
class BMapScaleControlOpts(
    # 控件的停靠位置
    # ANCHOR_TOP_LEFT，控件将定位到地图的左上角，值为 0
    # ANCHOR_TOP_RIGHT，控件将定位到地图的右上角，值为 1
    # ANCHOR_BOTTOM_LEFT，控件将定位到地图的左下角，值为 2
    # ANCHOR_BOTTOM_RIGHT，控件将定位到地图的右下角，值为 3
    position: Numeric = BMapType.ANCHOR_BOTTOM_RIGHT,

    # 控件的水平偏移值
    offset_width: Numeric = 10,

    # 控件的竖直偏移值
    offset_height: Numeric = 50,
)
```

### BMapTypeControl：切换地图类型的控件

> *class pyecharts.options.BMapTypeControl*

```python
class BMapTypeControl(
    # 控件的停靠位置
    # ANCHOR_TOP_LEFT，控件将定位到地图的左上角，值为 0
    # ANCHOR_TOP_RIGHT，控件将定位到地图的右上角，值为 1
    # ANCHOR_BOTTOM_LEFT，控件将定位到地图的左下角，值为 2
    # ANCHOR_BOTTOM_RIGHT，控件将定位到地图的右下角，值为 3
    position: Numeric = BMapType.ANCHOR_TOP_RIGHT,

    # 地图类型属性
    # MAPTYPE_CONTROL_HORIZONTAL，按钮水平方式展示，默认采用此类型展示。值为 0
    # MAPTYPE_CONTROL_DROPDOWN，按钮呈下拉列表方式展示，值为 1
    # MAPTYPE_CONTROL_MAP，以图片方式展示类型控件，设置该类型后无法指定 maptypes 属性，值为 2
    type_: Numeric = BMapType.MAPTYPE_CONTROL_HORIZONTAL,
)
```

### BMapCopyrightType：版权控件

> *class pyecharts.options.BMapCopyrightType*

```python
class BMapCopyrightType(
    # 控件的停靠位置
    # ANCHOR_TOP_LEFT，控件将定位到地图的左上角，值为 0
    # ANCHOR_TOP_RIGHT，控件将定位到地图的右上角，值为 1
    # ANCHOR_BOTTOM_LEFT，控件将定位到地图的左下角，值为 2
    # ANCHOR_BOTTOM_RIGHT，控件将定位到地图的右下角，值为 3
    position: Numeric = BMapType.ANCHOR_BOTTOM_RIGHT,

    # 控件的水平偏移值
    offset_width: Numeric = 10,

    # 控件的竖直偏移值
    offset_height: Numeric = 50,

    # Copyright 的文本内容, 可以放入 HTML 标签
    copyright_: str = "",
)
```

### BMapGeoLocationControlOpts：地图定位的控件

> *class pyecharts.options.BMapGeoLocationControlOpts*

```python
class BMapGeoLocationControlOpts(
    # 控件的停靠位置
    # ANCHOR_TOP_LEFT，控件将定位到地图的左上角，值为 0
    # ANCHOR_TOP_RIGHT，控件将定位到地图的右上角，值为 1
    # ANCHOR_BOTTOM_LEFT，控件将定位到地图的左下角，值为 2
    # ANCHOR_BOTTOM_RIGHT，控件将定位到地图的右下角，值为 3
    position: Numeric = BMapType.ANCHOR_BOTTOM_RIGHT,

    # 控件的水平偏移值
    offset_width: Numeric = 10,

    # 控件的竖直偏移值
    offset_height: Numeric = 50,

    # 是否显示定位信息面板。默认显示定位信息面板
    is_show_address_bar: bool = True,

    # 添加控件时是否进行定位。默认添加控件时不进行定位
    is_enable_auto_location: bool = False,
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/BMap/README)