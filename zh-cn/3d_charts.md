> Grid3Dopts，Axis3DOpts 为 3D 图形需要配置项

### Grid3DOpts：三维笛卡尔坐标系配置项
> *class pyecahrts.options.Grid3DOpts*

```python
class Grid3DOpts(
    # 三维笛卡尔坐标系组件在三维场景中的宽度
    width: Numeric = 200,

    # 三维笛卡尔坐标系组件在三维场景中的高度。
    height: Numeric = 100,

    # 三维笛卡尔坐标系组件在三维场景中的深度。
    depth: Numeric = 80,

    # 是否开启视角绕物体的自动旋转查看。
    is_rotate: bool = False,

    # 物体自转的速度。单位为角度 / 秒，默认为10 ，也就是 36 秒转一圈。
    rotate_speed: Numeric = 10,

    # 旋转操作的灵敏度，值越大越灵敏。支持使用数组分别设置横向和纵向的旋转灵敏度。
    # 设置为0后无法旋转。
    rotate_sensitivity: Numeric = 1,
)
```

### Axis3DOpts：三维坐标轴配置项
> *class pyecharts.options.Axis3DOpts*

```python
class Axis3DOpts(
    data: Optional[Sequence] = None,

    # 坐标轴类型。可选：
    # 'value': 数值轴，适用于连续数据。
    # 'category': 类目轴，适用于离散的类目数据，为该类型时必须通过 data 设置类目数据。
    # 'time': 时间轴，适用于连续的时序数据，与数值轴相比时间轴带有时间的格式化，在刻度计算上也有所不同，
    # 例如会根据跨度的范围来决定使用月，星期，日还是小时范围的刻度。
    # 'log' 对数轴。适用于对数数据。
    type_: Optional[str] = None,

    # 坐标轴名称。
    name: Optional[str] = None,

    # 坐标轴名称与轴线之间的距离，注意是三维空间的距离而非屏幕像素值。
    name_gap: Numeric = 20,

    # 坐标轴刻度最小值。
    # 可以设置成特殊值 'dataMin'，此时取数据在该轴上的最小值作为最小刻度。
    # 不设置时会自动计算最小值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'。
    # 也可以设置为负数，如 -3）。
    min_: Union[str, Numeric, None] = None,

    # 坐标轴刻度最大值。
    # 可以设置成特殊值 'dataMax'，此时取数据在该轴上的最大值作为最大刻度。
    # 不设置时会自动计算最大值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'。
    # 也可以设置为负数，如 -3）。
    max_: Union[str, Numeric, None] = None,

    # 坐标轴的分割段数，需要注意的是这个分割段数只是个预估值，最后实际显示的段数会在这个
    # 基础上根据分割后坐标轴刻度显示的易读程度作调整。
    # 在类目轴中无效。
    splitnum: Optional[Numeric] = None,

    # 强制设置坐标轴分割间隔。
    # 因为 splitNumber 是预估的值，实际根据策略计算出来的刻度可能无法达到想要的效果，
    # 这时候可以使用 interval 配合 min、max 强制设定刻度划分，一般不建议使用。
    # 无法在类目轴中使用。在时间轴（type: 'time'）中需要传时间戳，在对数轴（type: 'log'）中需要传指数值。
    interval: Optional[Numeric] = None,
    margin: Numeric = 8,
    textstyle_opts: Union[TextStyleOpts, dict, None] = None,
)
```

> *func pyecharts.charts.Chart3D.add*

所有 3D 图表均拥有以下方法
```python
def add(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    data: Sequence,

    # 三维柱状图中三维图形的着色效果。
    # color：只显示颜色，不受光照等其它因素的影响。
    # lambert：通过经典的 lambert 着色表现光照带来的明暗。
    # realistic：真实感渲染，配合 light.ambientCubemap 和 postEffect 使用可以让展示的画面效果和质感有质的提升。
    # ECharts GL 中使用了基于物理的渲染（PBR) 来表现真实感材质。
    shading: Optional[str] = None,

    # 图元配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(is_show=False),

    # 3D X 坐标轴配置项，参考 `Axis3DOpts`
    xaxis3d_opts: Union[opts.Axis3DOpts, dict] = opts.Axis3DOpts(type_="category"),

    # 3D Y 坐标轴配置项，参考 `Axis3DOpts`
    yaxis3d_opts: Union[opts.Axis3DOpts, dict] = opts.Axis3DOpts(type_="category"),

    # 3D Z 坐标轴配置项，参考 `Axis3DOpts`
    zaxis3d_opts: Union[opts.Axis3DOpts, dict] = opts.Axis3DOpts(type_="value"),

    # 三维笛卡尔坐标系配置项，参考 `Grid3DOpts`
    grid3d_opts: Union[opts.Grid3DOpts, dict] = opts.Grid3DOpts(),
)
```

## Bar3D：3D柱状图

> *class pyecharts.charts.Bar3D(Chart3D)*

```python
class Bar3D(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

### Demo

> Bar3D-基本示例

```python
from pyecharts.faker import Faker
from pyecharts import options as opts
from pyecharts.charts import Bar3D

def bar3d_base() -> Bar3D:
    data = [(i, j, random.randint(0, 12)) for i in range(6) for j in range(24)]
    c = (
        Bar3D()
        .add(
            "",
            [[d[1], d[0], d[2]] for d in data],
            xaxis3d_opts=opts.Axis3DOpts(Faker.clock, type_="category"),
            yaxis3d_opts=opts.Axis3DOpts(Faker.week_en, type_="category"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .set_global_opts(
            visualmap_opts=opts.VisualMapOpts(max_=20),
            title_opts=opts.TitleOpts(title="Bar3D-基本示例"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55604530-d3213c80-57a2-11e9-8a13-45289fe88d17.png)

> Bar3D-堆叠柱状图示例

```python
def bar3d_stack() -> Bar3D:
    def generate_data():
        data = []
        for j in range(10):
            for k in range(10):
                value = random.randint(0, 9)
                data.append([j, k, value * 2 + 4])
        return data

    c = (
        Bar3D()
        .add(
            "",
            generate_data(),
            shading="lambert",
            xaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .add(
            "",
            generate_data(),
            shading="lambert",
            xaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .add(
            "",
            generate_data(),
            shading="lambert",
            xaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .add(
            "",
            generate_data(),
            shading="lambert",
            xaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .add(
            "",
            generate_data(),
            shading="lambert",
            xaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .add(
            "",
            generate_data(),
            shading="lambert",
            xaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .add(
            "",
            generate_data(),
            shading="lambert",
            xaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .add(
            "",
            generate_data(),
            shading="lambert",
            xaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .add(
            "",
            generate_data(),
            shading="lambert",
            xaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .add(
            "",
            generate_data(),
            shading="lambert",
            xaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(data=list(range(10)), type_="value"),
            zaxis3d_opts=opts.Axis3DOpts(type_="value"),
        )
        .set_global_opts(title_opts=opts.TitleOpts("Bar3D-堆叠柱状图示例"))
        .set_series_opts(**{"stack": "stack"})
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/68597558-23e6d980-04d8-11ea-8342-6a36dad4ab49.png)

## Line3D：3D折线图

> *class pyecharts.charts.Line3D(Chart3D)*

```python
class Line3D(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

### Demo

> Line3D-基本示例

```python
import math

from pyecharts.faker import Faker
from pyecharts import options as opts
from pyecharts.charts import Line3D


def line3d_base() -> Line3D:
    data = []
    for t in range(0, 25000):
        _t = t / 1000
        x = (1 + 0.25 * math.cos(75 * _t)) * math.cos(_t)
        y = (1 + 0.25 * math.cos(75 * _t)) * math.sin(_t)
        z = _t + 2.0 * math.sin(75 * _t)
        data.append([x, y, z])
    c = (
        Line3D()
        .add(
            "",
            data,
            xaxis3d_opts=opts.Axis3DOpts(Faker.clock, type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(Faker.week_en, type_="value"),
            grid3d_opts=opts.Grid3DOpts(width=100, height=100, depth=100),
        )
        .set_global_opts(
            visualmap_opts=opts.VisualMapOpts(
                max_=30, min_=0, range_color=Faker.visual_color
            ),
            title_opts=opts.TitleOpts(title="Line3D-基本示例"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55604820-52634000-57a4-11e9-8f70-8914d60180dd.png)

> Line3D-旋转的弹簧

```python
def line3d_auto_rotate() -> Line3D:
    data = []
    for t in range(0, 25000):
        _t = t / 1000
        x = (1 + 0.25 * math.cos(75 * _t)) * math.cos(_t)
        y = (1 + 0.25 * math.cos(75 * _t)) * math.sin(_t)
        z = _t + 2.0 * math.sin(75 * _t)
        data.append([x, y, z])
    c = (
        Line3D()
        .add(
            "",
            data,
            xaxis3d_opts=opts.Axis3DOpts(Faker.clock, type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(Faker.week_en, type_="value"),
            grid3d_opts=opts.Grid3DOpts(
                width=100, depth=100, rotate_speed=150, is_rotate=True
            ),
        )
        .set_global_opts(
            visualmap_opts=opts.VisualMapOpts(
                max_=30, min_=0, range_color=Faker.visual_color
            ),
            title_opts=opts.TitleOpts(title="Line3D-旋转的弹簧"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55604882-9ce4bc80-57a4-11e9-8309-746a62b629a4.gif)


## Scatter3D：3D散点图

> *class pyecharts.charts.Scatter3D(Chart3D)*

```python
class Scatter3D(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

### Demo

> Scatter3D-基本示例

```python
import random

from pyecharts.faker import Faker
from pyecharts import options as opts
from pyecharts.charts import Scatter3D


def scatter3d_base() -> Scatter3D:
    data = [
        [random.randint(0, 100), random.randint(0, 100), random.randint(0, 100)]
        for _ in range(80)
    ]
    c = (
        Scatter3D()
        .add("", data)
        .set_global_opts(
            title_opts=opts.TitleOpts("Scatter3D-基本示例"),
            visualmap_opts=opts.VisualMapOpts(range_color=Faker.visual_color),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55604945-ce5d8800-57a4-11e9-9b23-f7ef7f2f8e98.png)


## Surface3D：3D曲面图

> *class pyecharts.charts.Surface3D(Chart3D)*

```python
class Surface3D(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

### Demo

> Surface3D-基本示例

```python
import math

from pyecharts.faker import Faker
from pyecharts import options as opts
from pyecharts.charts import Surface3D

def surface3d_base() -> Surface3D:
    def surface3d_data():
        for t0 in range(-60, 60, 1):
            y = t0 / 60
            for t1 in range(-60, 60, 1):
                x = t1 / 60
                if math.fabs(x) < 0.1 and math.fabs(y) < 0.1:
                    z = "-"
                else:
                    z = math.sin(x * math.pi) * math.sin(y * math.pi)
                yield [x, y, z]

    c = (
        Surface3D()
        .add(
            "",
            list(surface3d_data()),
            xaxis3d_opts=opts.Axis3DOpts(type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(type_="value"),
            grid3d_opts=opts.Grid3DOpts(width=100, height=100, depth=100),
        )
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Surface3D-基本示例"),
            visualmap_opts=opts.VisualMapOpts(
                max_=3, min_=-3, range_color=Faker.visual_color
            ),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55605014-14b2e700-57a5-11e9-9fe9-4f76a95ecb07.png)

> Surface3D-曲面波图

```python
def surface3d_flower() -> Surface3D:
    def surface3d_data():
        for t0 in range(-30, 30, 1):
            y = t0 / 10
            for t1 in range(-30, 30, 1):
                x = t1 / 10
                z = math.sin(x * x + y * y) * x / 3.14
                yield [x, y, z]

    c = (
        Surface3D()
        .add(
            "",
            list(surface3d_data()),
            xaxis3d_opts=opts.Axis3DOpts(type_="value"),
            yaxis3d_opts=opts.Axis3DOpts(type_="value"),
            grid3d_opts=opts.Grid3DOpts(width=100, height=100, depth=100),
        )
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Surface3D-曲面波图"),
            visualmap_opts=opts.VisualMapOpts(
                max_=1, min_=-1, range_color=Faker.visual_color
            ),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55605020-20061280-57a5-11e9-8813-8f8818bd524b.png)

> Map3D - 三维地图

有待加强。

```python
from pyecharts.charts import Map3D

Map3D().add_schema().render()
```

![](https://user-images.githubusercontent.com/4280312/60053207-3306ef80-96cf-11e9-96c1-adc1675894e4.png)


> Map3D - 地球地图

API 用法和 map 一样。

```python
import pyecharts.options as opts
from pyecharts.faker import POPULATION
from pyecharts.charts import MapGlobe

high = max([x for _, x in POPULATION[1:]])
low = min([x for _, x in POPULATION[1:]])

m = (
    MapGlobe()
    .add_schema()
    .add(
        maptype="world",
        series_name="World Population",
        data_pair=POPULATION[1:],
        is_map_symbol_show=False,
        label_opts=opts.LabelOpts(is_show=False),
    )
    .set_global_opts(
        visualmap_opts=opts.VisualMapOpts(
            min_=low,
            max_=high,
            range_text=["max", "min"],
            is_calculable=True,
            range_color=["lightskyblue", "yellow", "orangered"],
        )
    )
)
m.render()
```

![](https://user-images.githubusercontent.com/4280312/60053228-3dc18480-96cf-11e9-809e-c8ccf243d7dc.png)
