## Grid：并行多图

> *class class pyecharts.Grid*

```python
```

### GridOpts：直角坐标系网格配置项
> *class pyecharts.options.GridOpts*

```python
class GridOpts(
    # grid 组件离容器左侧的距离。
    # left 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'left', 'center', 'right'。
    # 如果 left 的值为'left', 'center', 'right'，组件会根据相应的位置自动对齐。
    pos_left: Optional[str] = None,

    # grid 组件离容器上侧的距离。
    # top 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比，
    # 也可以是 'top', 'middle', 'bottom'。
    # 如果 top 的值为'top', 'middle', 'bottom'，组件会根据相应的位置自动对齐。
    pos_top: Optional[str] = None,

    # grid 组件离容器右侧的距离。
    # right 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_right: Optional[str] = None,

    # grid 组件离容器下侧的距离。
    # bottom 的值可以是像 20 这样的具体像素值，可以是像 '20%' 这样相对于容器高宽的百分比。
    pos_bottom: Optional[str] = None,

    # grid 组件的宽度。默认自适应。
    width: Optional[Numeric] = None,

    # grid 组件的高度。默认自适应。
    height: Optional[Numeric] = None,
)
```

### Demo

> Grid-上下布局

```python
from example.commons import Faker
from pyecharts import options as opts
from pyecharts.charts import Bar, Grid, Line,Scatter


def grid_vertical() -> Grid:
    bar = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Grid-Bar"))
    )
    line = (
        Line()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Grid-Line", pos_top="48%"),
            legend_opts=opts.LegendOpts(pos_top="48%"),
        )
    )

    grid = (
        Grid()
        .add(bar, grid_opts=opts.GridOpts(pos_bottom="60%"))
        .add(line, grid_opts=opts.GridOpts(pos_top="60%"))
    )
    return grid
```
![](https://user-images.githubusercontent.com/19553554/55605302-79bb0c80-57a6-11e9-950d-a7de622ce263.png)


> Grid-左右布局

```python
def grid_horizontal() -> Grid:
    scatter = (
        Scatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Grid-Scatter"),
            legend_opts=opts.LegendOpts(pos_left="20%"),
        )
    )
    line = (
        Line()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Grid-Line", pos_right="5%"),
            legend_opts=opts.LegendOpts(pos_right="20%"),
        )
    )

    grid = (
        Grid()
        .add(scatter, grid_opts=opts.GridOpts(pos_left="55%"))
        .add(line, grid_opts=opts.GridOpts(pos_right="55%"))
    )
    return grid
```
![](https://user-images.githubusercontent.com/19553554/55605309-7d4e9380-57a6-11e9-87be-e7b6d3193261.png)


## Overlap：层叠多图

> *class pyecharts.charts.*

```python
```


## Page：顺序多图

> *class pyecharts.charts.Page*

```python
class Page(
    page_title: str = "Awesome-pyecharts",
    js_host: str = CurrentConfig.ONLINE_HOST,
    interval: int = 1,
)
```

> *func pyecharts.charts.Page.add*

```python
def add(*charts)
```


## Timeline：时间线轮播多图

> *class pyecharts.charts.Timeline*

```python
class Timeline(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.Timeline.add_schema*

```python
def add_schema(
    axis_type: str = "category",
    symbol: Optional[str] = None,
    symbol_size: Optional[Numeric] = None,
    play_interval: Optional[Numeric] = None,
    is_auto_play: bool = False,
    is_loop_play: bool = True,
    is_rewind_play: bool = False,
    is_timeline_show: bool = True,
    pos_left: Optional[str] = None,
    pos_right: Optional[str] = None,
    pos_top: Optional[str] = None,
    pos_bottom: Optional[str] = "-5px",
)
```

> *func pyecharts.charts.Timeline.add*

```python
def add(
    chart: Base, 
    time_point: str
)
```

### Demo

> Bar 图 Timeline 效果

```python
from example.commons import Faker
from pyecharts import options as opts
from pyecharts.charts import Bar, Page, Pie, Timeline


def timeline_bar() -> Timeline:
    x = Faker.choose()
    bar0 = (
        Bar()
        .add_xaxis(x)
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts("某商店2015年营业额"))
    )
    bar1 = (
        Bar()
        .add_xaxis(x)
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts("某商店2016年营业额"))
    )
    bar2 = (
        Bar()
        .add_xaxis(x)
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts("某商店2017年营业额"))
    )
    bar3 = (
        Bar()
        .add_xaxis(x)
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts("某商店2018年营业额"))
    )
    bar4 = (
        Bar()
        .add_xaxis(x)
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts("某商店2019年营业额"))
    )

    tl = (
        Timeline()
        .add(bar0, "2015年")
        .add(bar1, "2016年")
        .add(bar2, "2017年")
        .add(bar3, "2018年")
        .add(bar4, "2019年")
    )
    return tl
```

> Pie 图 Timeline 效果

```python
def timeline_pie() -> Timeline:
    attr = Faker.choose()
    pie0 = (
        Pie()
        .add(
            "商家A",
            [list(z) for z in zip(attr, Faker.values())],
            rosetype="radius",
            radius=["30%", "55%"],
        )
        .set_global_opts(title_opts=opts.TitleOpts("某商店2015年营业额"))
    )
    pie1 = (
        Pie()
        .add(
            "商家A",
            [list(z) for z in zip(attr, Faker.values())],
            rosetype="radius",
            radius=["30%", "55%"],
        )
        .set_global_opts(title_opts=opts.TitleOpts("某商店2016年营业额"))
    )
    pie2 = (
        Pie()
        .add(
            "商家A",
            [list(z) for z in zip(attr, Faker.values())],
            rosetype="radius",
            radius=["30%", "55%"],
        )
        .set_global_opts(title_opts=opts.TitleOpts("某商店2017年营业额"))
    )
    pie3 = (
        Pie()
        .add(
            "商家A",
            [list(z) for z in zip(attr, Faker.values())],
            rosetype="radius",
            radius=["30%", "55%"],
        )
        .set_global_opts(title_opts=opts.TitleOpts("某商店2018年营业额"))
    )
    pie4 = (
        Pie()
        .add(
            "商家A",
            [list(z) for z in zip(attr, Faker.values())],
            rosetype="radius",
            radius=["30%", "55%"],
        )
        .set_global_opts(title_opts=opts.TitleOpts("某商店2019年营业额"))
    )
    tl = (
        Timeline()
        .add(pie0, "2015年")
        .add(pie1, "2016年")
        .add(pie2, "2017年")
        .add(pie3, "2018年")
        .add(pie4, "2019年")
    )
    return tl
```
