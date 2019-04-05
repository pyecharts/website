## Geo：地理坐标系

> *class pyecharts.charts.Geo*

```python
class Geo(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
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
