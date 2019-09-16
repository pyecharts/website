## Geo：地理坐标系

> *class pyecharts.charts.Geo*

```python
class Geo(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
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

> Geo-基本示例

```python
from pyecharts.faker import Faker
from pyecharts import options as opts
from pyecharts.charts import Geo
from pyecharts.globals import ChartType, SymbolType


def geo_base() -> Geo:
    c = (
        Geo()
        .add_schema(maptype="china")
        .add("geo", [list(z) for z in zip(Faker.provinces, Faker.values())])
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(
            visualmap_opts=opts.VisualMapOpts(),
            title_opts=opts.TitleOpts(title="Geo-基本示例"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55609062-62821c00-57b2-11e9-8ad0-7cfba218f189.png)

> Geo-VisualMap（分段型）

```python
def geo_visualmap_piecewise() -> Geo:
    c = (
        Geo()
        .add_schema(maptype="china")
        .add("geo", [list(z) for z in zip(Faker.provinces, Faker.values())])
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(
            visualmap_opts=opts.VisualMapOpts(is_piecewise=True),
            title_opts=opts.TitleOpts(title="Geo-VisualMap（分段型）"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55609078-69109380-57b2-11e9-8308-f7a2c993b130.png)

> Geo-EffectScatter

```python
def geo_effectscatter() -> Geo:
    c = (
        Geo()
        .add_schema(maptype="china")
        .add(
            "geo",
            [list(z) for z in zip(Faker.provinces, Faker.values())],
            type_=ChartType.EFFECT_SCATTER,
        )
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(title_opts=opts.TitleOpts(title="Geo-EffectScatter"))
    )
    return c

```
![](https://user-images.githubusercontent.com/19553554/55609084-6e6dde00-57b2-11e9-8327-5ac7bd4de6f7.png)

> Geo-HeatMap

```python
def geo_heatmap() -> Geo:
    c = (
        Geo()
        .add_schema(maptype="china")
        .add(
            "geo",
            [list(z) for z in zip(Faker.provinces, Faker.values())],
            type_=ChartType.HEATMAP,
        )
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(
            visualmap_opts=opts.VisualMapOpts(),
            title_opts=opts.TitleOpts(title="Geo-HeatMap"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55609091-7463bf00-57b2-11e9-8856-e509edb38702.png)

> Geo-广东地图

```python
def geo_guangdong() -> Geo:
    c = (
        Geo()
        .add_schema(maptype="广东")
        .add(
            "geo",
            [list(z) for z in zip(Faker.guangdong_city, Faker.values())],
            type_=ChartType.HEATMAP,
        )
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(
            visualmap_opts=opts.VisualMapOpts(),
            title_opts=opts.TitleOpts(title="Geo-广东地图"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55609103-7a59a000-57b2-11e9-82bc-fb10c0327229.png)

> Geo-Lines

```python
def geo_lines() -> Geo:
    c = (
        Geo()
        .add_schema(maptype="china")
        .add(
            "",
            [("广州", 55), ("北京", 66), ("杭州", 77), ("重庆", 88)],
            type_=ChartType.EFFECT_SCATTER,
            color="white",
        )
        .add(
            "geo",
            [("广州", "上海"), ("广州", "北京"), ("广州", "杭州"), ("广州", "重庆")],
            type_=ChartType.LINES,
            effect_opts=opts.EffectOpts(
                symbol=SymbolType.ARROW, symbol_size=6, color="blue"
            ),
            linestyle_opts=opts.LineStyleOpts(curve=0.2),
        )
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(title_opts=opts.TitleOpts(title="Geo-Lines"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55609114-85accb80-57b2-11e9-99b2-c045dc6f4c6c.png)

> Geo-Lines-background

```python
def geo_lines_background() -> Geo:
    c = (
        Geo()
        .add_schema(
            maptype="china",
            itemstyle_opts=opts.ItemStyleOpts(color="#323c48", border_color="#111"),
        )
        .add(
            "",
            [("广州", 55), ("北京", 66), ("杭州", 77), ("重庆", 88)],
            type_=ChartType.EFFECT_SCATTER,
            color="white",
        )
        .add(
            "geo",
            [("广州", "上海"), ("广州", "北京"), ("广州", "杭州"), ("广州", "重庆")],
            type_=ChartType.LINES,
            effect_opts=opts.EffectOpts(
                symbol=SymbolType.ARROW, symbol_size=6, color="blue"
            ),
            linestyle_opts=opts.LineStyleOpts(curve=0.2),
        )
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(title_opts=opts.TitleOpts(title="Geo-Lines-background"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55609133-8cd3d980-57b2-11e9-89c9-ed7e5fd15420.png)


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
    data_pair: Sequence,

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

### Demo

> Map-基本示例

```python
from pyecharts.faker import Faker
from pyecharts import options as opts
from pyecharts.charts import Map


def map_base() -> Map:
    c = (
        Map()
        .add("商家A", [list(z) for z in zip(Faker.provinces, Faker.values())], "china")
        .set_global_opts(title_opts=opts.TitleOpts(title="Map-基本示例"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55606353-07006000-57ab-11e9-9598-18b8b6c84b6a.png)

> Map-不显示Label

```python
def map_without_label() -> Map:
    c = (
        Map()
        .add("商家A", [list(z) for z in zip(Faker.provinces, Faker.values())], "china")
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(title_opts=opts.TitleOpts(title="Map-不显示Label"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55606360-0d8ed780-57ab-11e9-8bb4-2838d112fb5f.png)

> Map-VisualMap（连续型）

```python
def map_visualmap() -> Map:
    c = (
        Map()
        .add("商家A", [list(z) for z in zip(Faker.provinces, Faker.values())], "china")
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Map-VisualMap（连续型）"),
            visualmap_opts=opts.VisualMapOpts(max_=200),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55606364-12538b80-57ab-11e9-8f33-6263fcaf008e.png)

> Map-VisualMap（分段型）

```python
def map_visualmap() -> Map:
    c = (
        Map()
        .add("商家A", [list(z) for z in zip(Faker.provinces, Faker.values())], "china")
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Map-VisualMap（分段型）"),
            visualmap_opts=opts.VisualMapOpts(max_=200, is_piecewise=True),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55606366-17b0d600-57ab-11e9-881a-f0fbea89143c.png)

> Map-世界地图

```python
def map_world() -> Map:
    c = (
        Map()
        .add("商家A", [list(z) for z in zip(Faker.country, Faker.values())], "world")
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Map-世界地图"),
            visualmap_opts=opts.VisualMapOpts(max_=200),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55606372-1ed7e400-57ab-11e9-859a-65c904cda320.png)

> Map-广东地图

```python
def map_guangdong() -> Map:
    c = (
        Map()
        .add("商家A", [list(z) for z in zip(Faker.guangdong_city, Faker.values())], "广东")
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Map-广东地图"),
            visualmap_opts=opts.VisualMapOpts(),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55606380-24cdc500-57ab-11e9-816b-7b6f51e96d16.png)


## BMap：百度地图

百度地图需要申请开发者 AK，[官网申请](https://lbsyun.baidu.com/)。

> *class pyecharts.charts.BMap*

```python
class BMap(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
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
    maptype_control_opts: Union[opts.BMapTypeControl, dict, None] = None,
    
    # 版权控件，您可以在地图上添加自己的版权信息。
    # 每一个版权信息需要包含如下内容：版权的唯一标识、版权内容和其适用的区域范围。
    copyright_control_opts: Union[opts.BMapCopyrightType, dict, None] = None,
    
    # 地图定位的控件，使用 HTML5 浏览器定位功能
    geo_location_control_opts: Union[opts.BMapGeoLocationControlOpts, dict, None] = None,
)
```

### BMapNavigationControlOpts：地图的平移缩放控件

> *class pyecahrts.options.BMapNavigationControlOpts*

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

> *class pyecahrts.options.BMapOverviewMapControlOpts*

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

> *class pyecahrts.options.BMapScaleControlOpts*

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

> *class pyecahrts.options.BMapTypeControl*

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

> *class pyecahrts.options.BMapCopyrightType*

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

> *class pyecahrts.options.BMapGeoLocationControlOpts*

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

> BMap 基本示例

```python
BAIDU_AK = "your_baidu_map_ak"

def bmap_base() -> BMap:
    c = (
        BMap()
        .add_schema(
            baidu_ak=BAIDU_AK,
            center=[120.13066322374, 30.240018034923],
        )
        .add(
            "bmap",
            [list(z) for z in zip(Faker.provinces, Faker.values())],
            label_opts=opts.LabelOpts(formatter="{b}"),
        )
        .set_global_opts(title_opts=opts.TitleOpts(title="BMap-基本示例"))
    )
    return c
```

> BMap-杭州热门步行路线

```python
def bmap_lines() -> BMap:
    with open(
        os.path.join("fixtures", "hangzhou-tracks.json"), "r", encoding="utf-8"
    ) as f:
        j = json.load(f)
    c = (
        BMap()
        .add_schema(
            baidu_ak=BAIDU_MAP_AK,
            center=[120.13066322374, 30.240018034923],
            zoom=14,
            is_roam=True,
            map_style={
                "styleJson": [
                    {
                        "featureType": "water",
                        "elementType": "all",
                        "stylers": {"color": "#d1d1d1"},
                    },
                    {
                        "featureType": "land",
                        "elementType": "all",
                        "stylers": {"color": "#f3f3f3"},
                    },
                    {
                        "featureType": "railway",
                        "elementType": "all",
                        "stylers": {"visibility": "off"},
                    },
                    {
                        "featureType": "highway",
                        "elementType": "all",
                        "stylers": {"color": "#fdfdfd"},
                    },
                    {
                        "featureType": "highway",
                        "elementType": "labels",
                        "stylers": {"visibility": "off"},
                    },
                    {
                        "featureType": "arterial",
                        "elementType": "geometry",
                        "stylers": {"color": "#fefefe"},
                    },
                    {
                        "featureType": "arterial",
                        "elementType": "geometry.fill",
                        "stylers": {"color": "#fefefe"},
                    },
                    {
                        "featureType": "poi",
                        "elementType": "all",
                        "stylers": {"visibility": "off"},
                    },
                    {
                        "featureType": "green",
                        "elementType": "all",
                        "stylers": {"visibility": "off"},
                    },
                    {
                        "featureType": "subway",
                        "elementType": "all",
                        "stylers": {"visibility": "off"},
                    },
                    {
                        "featureType": "manmade",
                        "elementType": "all",
                        "stylers": {"color": "#d1d1d1"},
                    },
                    {
                        "featureType": "local",
                        "elementType": "all",
                        "stylers": {"color": "#d1d1d1"},
                    },
                    {
                        "featureType": "arterial",
                        "elementType": "labels",
                        "stylers": {"visibility": "off"},
                    },
                    {
                        "featureType": "boundary",
                        "elementType": "all",
                        "stylers": {"color": "#fefefe"},
                    },
                    {
                        "featureType": "building",
                        "elementType": "all",
                        "stylers": {"color": "#d1d1d1"},
                    },
                    {
                        "featureType": "label",
                        "elementType": "labels.text.fill",
                        "stylers": {"color": "#999999"},
                    },
                ]
            },
        )
        .add(
            "",
            type_="lines",
            data_pair=j,
            is_polyline=True,
            is_large=True,
            linestyle_opts=opts.LineStyleOpts(color="purple", opacity=0.6, width=1),
        )
        .add_control_panel(
            maptype_control_opts=opts.BMapTypeControl(
                type_=BMapType.MAPTYPE_CONTROL_DROPDOWN
            ),
            scale_control_opts=opts.BMapScaleControlOpts(),
            overview_map_opts=opts.BMapOverviewMapControlOpts(is_open=True),
        )
        .set_global_opts(title_opts=opts.TitleOpts(title="BMap-杭州热门步行路线"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/57545910-431c7700-738e-11e9-896b-e071b55115c7.png)
