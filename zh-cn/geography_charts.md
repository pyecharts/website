## Geo：地理坐标系

> *class pyecharts.charts.Geo*

```python
class Geo(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.Geo.add_schema*

```python
def add_schema(
    # 地图类型，具体参考 pyecharts.datasets.map_filenames.json 文件
    maptype: str = "china",

    # 是否开启鼠标缩放和平移漫游。
    is_roam: bool = True,

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

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 涟漪特效配置项，参考 `series_options.EffectOpts`
    effect_opts: Union[opts.EffectOpts, dict] = opts.EffectOpts(),

    # 线样式配置项，参考 `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
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
) -> List
```

### Demo

> Geo-基本示例

```python
from example.commons import Faker
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
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
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

    # 标记图形形状
    symbol: Optional[str] = None,

    # 是否显示标记图形
    is_map_symbol_show: bool = True,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### Demo

> Map-基本示例

```python
from example.commons import Faker
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
