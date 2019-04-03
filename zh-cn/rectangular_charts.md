
直角坐标系图表继承自 `AxisChart` 都拥有以下方法

> *func AxisChart.extend_axis*

扩展 X/Y 轴
```python
def extend_axis(
    # X 坐标轴配置项，参考 `global_options.AxisOpts`
    xaxis: Union[opts.AxisOpts, dict, None] = None,
    # Y 坐标轴配置项，参考 `global_options.AxisOpts`
    yaxis: Union[opts.AxisOpts, dict, None] = None,
)
```

> *func AxisChart.add_xaxis*

新增 X 轴数据
```python
def add_xaxis(
    # X 轴数据项
    xaxis_data: Sequence
)
```

> *func AxisChart.reversal_axis*

翻转 XY 轴数据
```python
def reversal_axis():
```

> *func AxisChart.overlap*

层叠多图
```python
def overlap(
    # chart 为直角坐标系类型图表
    chart: Base
)
```

## Bar：柱状图/条形图

> *class pyecharts.charts.Bar*

```python
class Bar(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.Bar.add_yaxis*

新增及配置 Series
```python
def add_yaxis(
    # 系列名称，用于tooltip的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    yaxis_data: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 数据堆叠，同个类目轴上系列配置相同的　stack　值可以堆叠放置。
    stack: Optional[str] = None,

    # 同一系列的柱间距离，默认为类目间距的20%，可设固定值
    category_gap: Union[Numeric, str] = "20%",

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### Demo

```python
def bar_base() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values(), is_selected=False)
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-基本示例", subtitle="我是副标题"))
    )
    return c
```

```python
def bar_reversal_axis() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .reversal_axis()
        .set_series_opts(label_opts=opts.LabelOpts(position="right"))
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-翻转 XY 轴"))
    )
    return c
```

```python
def bar_stack0() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values(), stack="stack1")
        .add_yaxis("商家B", Faker.values(), stack="stack1")
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-堆叠数据（全部）"))
    )
    return c
```

```python
def bar_stack1() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values(), stack="stack1")
        .add_yaxis("商家B", Faker.values(), stack="stack1")
        .add_yaxis("商家C", Faker.values())
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-堆叠数据（部分）"))
    )
    return c
```

```python
def bar_markpoint_type() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-MarkPoint（指定类型）"))
        .set_series_opts(
            label_opts=opts.LabelOpts(is_show=False),
            markpoint_opts=opts.MarkPointOpts(
                data=[
                    opts.MarkPointItem(type_="max", name="最大值"),
                    opts.MarkPointItem(type_="min", name="最小值"),
                    opts.MarkPointItem(type_="average", name="平均值"),
                ]
            ),
        )
    )
    return c
```

```python
def bar_markpoint_custom() -> Bar:
    x, y = Faker.choose(), Faker.values()
    c = (
        Bar()
        .add_xaxis(x)
        .add_yaxis(
            "商家A",
            y,
            markpoint_opts=opts.MarkPointOpts(
                data=[opts.MarkPointItem(name="自定义标记点", coord=[x[2], y[2]], value=y[2])]
            ),
        )
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-MarkPoint（自定义）"))
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
    )
    return c
```

```python
def bar_markline_type() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-MarkLine（指定类型）"))
        .set_series_opts(
            label_opts=opts.LabelOpts(is_show=False),
            markline_opts=opts.MarkLineOpts(
                data=[
                    opts.MarkLineItem(type_="min", name="最小值"),
                    opts.MarkLineItem(type_="max", name="最大值"),
                    opts.MarkLineItem(type_="average", name="平均值"),
                ]
            ),
        )
    )
    return c
```

```python
def bar_markline_custom() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-MarkLine（自定义）"))
        .set_series_opts(
            label_opts=opts.LabelOpts(is_show=False),
            markline_opts=opts.MarkLineOpts(
                data=[opts.MarkLineItem(y=50, name="yAxis=50")]
            ),
        )
    )
    return c
```

```python
def bar_datazoom_slider() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.days_attrs)
        .add_yaxis("商家A", Faker.days_values)
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-DataZoom（slider-水平）"),
            datazoom_opts=[opts.DataZoomOpts()],
        )
    )
    return c
```

```python
def bar_datazoom_slider_vertical() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.days_attrs)
        .add_yaxis("商家A", Faker.days_values, color=Faker.rand_color())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-DataZoom（slider-垂直）"),
            datazoom_opts=[opts.DataZoomOpts(orient="vertical")],
        )
    )
    return c
```

```python
def bar_datazoom_inside() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.days_attrs)
        .add_yaxis("商家A", Faker.days_values, color=Faker.rand_color())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-DataZoom（inside）"),
            datazoom_opts=[opts.DataZoomOpts(type_="inside")],
        )
    )
    return c
```

```python
def bar_datazoom_both() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.days_attrs)
        .add_yaxis("商家A", Faker.days_values, color=Faker.rand_color())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-DataZoom（slider+inside）"),
            datazoom_opts=[opts.DataZoomOpts(), opts.DataZoomOpts(type_="inside")],
        )
    )
    return c
```

```python
def bar_histogram() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values(), category_gap=0, color=Faker.rand_color())
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-直方图"))
    )
    return c
```

## Boxplot：箱形图

> *class pyecharts.charts.Boxplot*

```python
class Boxplot(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.Boxplot.add_yaxis*

新增及配置 Series
```python
def add_yaxis(
    # 系列名称，用于tooltip的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict] = opts.MarkPointOpts(),

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict] = opts.MarkLineOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### Demo

```python
def boxpolt_base() -> Boxplot:
    v1 = [
        [850, 740, 900, 1070, 930, 850, 950, 980, 980, 880]
        + [1000, 980, 930, 650, 760, 810, 1000, 1000, 960, 960],
        [960, 940, 960, 940, 880, 800, 850, 880, 900]
        + [840, 830, 790, 810, 880, 880, 830, 800, 790, 760, 800],
    ]
    v2 = [
        [890, 810, 810, 820, 800, 770, 760, 740, 750, 760]
        + [910, 920, 890, 860, 880, 720, 840, 850, 850, 780],
        [890, 840, 780, 810, 760, 810, 790, 810, 820, 850, 870]
        + [870, 810, 740, 810, 940, 950, 800, 810, 870],
    ]
    c = Boxplot()
    c.add_xaxis(["expr1", "expr2"]).add_yaxis("A", c.prepare_data(v1)).add_yaxis(
        "B", c.prepare_data(v2)
    ).set_global_opts(title_opts=opts.TitleOpts(title="BoxPlot-基本示例"))
    return c
```

## EffectScatter：涟漪特效散点图

> *class pyecharts.charts.EffectScatter*

```python
class EffectScatter(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.EffectScatter.add_yaxis*

新增及配置 Series
```python
 def add_yaxis(
     # 系列名称，用于tooltip的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 标记图形形状
    symbol: Optional[str] = None,

    # 标记的大小
    symbol_size: Numeric = 10,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 涟漪特效配置项，参考 `series_options.EffectOpts`
    effect_opts: Union[opts.EffectOpts, dict] = opts.EffectOpts(),

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### Demo

```python
def effectscatter_base() -> EffectScatter:
    c = (
        EffectScatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="EffectScatter-基本示例"))
    )
    return c
```

```python
def effectscatter_splitline() -> EffectScatter:
    c = (
        EffectScatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="EffectScatter-显示分割线"),
            xaxis_opts=opts.AxisOpts(splitline_opts=opts.SplitLineOpts(is_show=True)),
            yaxis_opts=opts.AxisOpts(splitline_opts=opts.SplitLineOpts(is_show=True)),
        )
    )
    return c
```

```python
def effectscatter_symbol() -> EffectScatter:
    c = (
        EffectScatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("", Faker.values(), symbol=SymbolType.ARROW)
    ).set_global_opts(title_opts=opts.TitleOpts(title="EffectScatter-不同Symbol"))
    return c
```

## HeatMap：热力图

> *class pyecharts.charts.HeatMap*

```python
class HeatMap(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

```python
def add_yaxis(
    # 系列名称，用于tooltip的显示，legend 的图例筛选。
    series_name: str,

    # Y 坐标轴数据
    yaxis_data: Sequence,

    # 系列数据项
    value: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### Demo

```python
def heatmap_base() -> HeatMap:
    value = [[i, j, random.randint(0, 50)] for i in range(24) for j in range(7)]
    c = (
        HeatMap()
        .add_xaxis(Faker.clock)
        .add_yaxis("series0", Faker.week, value)
        .set_global_opts(
            title_opts=opts.TitleOpts(title="HeatMap-基本示例"),
            visualmap_opts=opts.VisualMapOpts(),
        )
    )
    return c
```

## Kline/Candlestick：K线图

> *class pyecharts.charts.Kline*

```python
class Kline(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.Kline.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于tooltip的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### Demo

```python
data = [
    [2320.26, 2320.26, 2287.3, 2362.94],
    [2300, 2291.3, 2288.26, 2308.38],
    [2295.35, 2346.5, 2295.35, 2345.92],
    [2347.22, 2358.98, 2337.35, 2363.8],
    [2360.75, 2382.48, 2347.89, 2383.76],
    [2383.43, 2385.42, 2371.23, 2391.82],
    [2377.41, 2419.02, 2369.57, 2421.15],
    [2425.92, 2428.15, 2417.58, 2440.38],
    [2411, 2433.13, 2403.3, 2437.42],
    [2432.68, 2334.48, 2427.7, 2441.73],
    [2430.69, 2418.53, 2394.22, 2433.89],
    [2416.62, 2432.4, 2414.4, 2443.03],
    [2441.91, 2421.56, 2418.43, 2444.8],
    [2420.26, 2382.91, 2373.53, 2427.07],
    [2383.49, 2397.18, 2370.61, 2397.94],
    [2378.82, 2325.95, 2309.17, 2378.82],
    [2322.94, 2314.16, 2308.76, 2330.88],
    [2320.62, 2325.82, 2315.01, 2338.78],
    [2313.74, 2293.34, 2289.89, 2340.71],
    [2297.77, 2313.22, 2292.03, 2324.63],
    [2322.32, 2365.59, 2308.92, 2366.16],
    [2364.54, 2359.51, 2330.86, 2369.65],
    [2332.08, 2273.4, 2259.25, 2333.54],
    [2274.81, 2326.31, 2270.1, 2328.14],
    [2333.61, 2347.18, 2321.6, 2351.44],
    [2340.44, 2324.29, 2304.27, 2352.02],
    [2326.42, 2318.61, 2314.59, 2333.67],
    [2314.68, 2310.59, 2296.58, 2320.96],
    [2309.16, 2286.6, 2264.83, 2333.29],
    [2282.17, 2263.97, 2253.25, 2286.33],
    [2255.77, 2270.28, 2253.31, 2276.22],
]


def kline_base() -> Kline:
    c = (
        Kline()
        .add_xaxis(["2017/7/{}".format(i + 1) for i in range(31)])
        .add_yaxis("kline", data)
        .set_global_opts(
            yaxis_opts=opts.AxisOpts(is_scale=True),
            xaxis_opts=opts.AxisOpts(is_scale=True),
            title_opts=opts.TitleOpts(title="Kline-基本示例"),
        )
    )
    return c
```

```python
def kline_splitarea() -> Kline:
    c = (
        Kline()
        .add_xaxis(["2017/7/{}".format(i + 1) for i in range(31)])
        .add_yaxis("kline", data)
        .set_global_opts(
            xaxis_opts=opts.AxisOpts(is_scale=True),
            yaxis_opts=opts.AxisOpts(
                is_scale=True,
                splitarea_opts=opts.SplitAreaOpts(
                    is_show=True, areastyle_opts=opts.AreaStyleOpts(opacity=1)
                ),
            ),
            title_opts=opts.TitleOpts(title="Kline-显示分割区域"),
        )
    )
    return c
```

```python
def kline_datazoom_slider() -> Kline:
    c = (
        Kline()
        .add_xaxis(["2017/7/{}".format(i + 1) for i in range(31)])
        .add_yaxis("kline", data)
        .set_global_opts(
            xaxis_opts=opts.AxisOpts(is_scale=True),
            yaxis_opts=opts.AxisOpts(
                is_scale=True,
                splitarea_opts=opts.SplitAreaOpts(
                    is_show=True, areastyle_opts=opts.AreaStyleOpts(opacity=1)
                ),
            ),
            datazoom_opts=[opts.DataZoomOpts()],
            title_opts=opts.TitleOpts(title="Kline-DataZoom-slider"),
        )
    )
    return c
```

```python
def kline_datazoom_inside() -> Kline:
    c = (
        Kline()
        .add_xaxis(["2017/7/{}".format(i + 1) for i in range(31)])
        .add_yaxis("kline", data)
        .set_global_opts(
            xaxis_opts=opts.AxisOpts(is_scale=True),
            yaxis_opts=opts.AxisOpts(
                is_scale=True,
                splitarea_opts=opts.SplitAreaOpts(
                    is_show=True, areastyle_opts=opts.AreaStyleOpts(opacity=1)
                ),
            ),
            datazoom_opts=[opts.DataZoomOpts(type_="inside")],
            title_opts=opts.TitleOpts(title="Kline-DataZoom-inside"),
        )
    )
    return c
```

```python
def kline_markline() -> Kline:
    c = (
        Kline()
        .add_xaxis(["2017/7/{}".format(i + 1) for i in range(31)])
        .add_yaxis(
            "kline",
            data,
            markline_opts=opts.MarkLineOpts(
                data=[opts.MarkLineItem(type_="max", value_dim="close")]
            ),
        )
        .set_global_opts(
            xaxis_opts=opts.AxisOpts(is_scale=True),
            yaxis_opts=opts.AxisOpts(
                is_scale=True,
                splitarea_opts=opts.SplitAreaOpts(
                    is_show=True, areastyle_opts=opts.AreaStyleOpts(opacity=1)
                ),
            ),
            title_opts=opts.TitleOpts(title="Kline-MarkLine"),
        )
    )
    return c
```

## Line：折线/面积图

> *class pyecharts.charts.Line*

```python
class Line(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.Line.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于tooltip的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 是否显示 symbol, 如果 false 则只有在 tooltip hover 的时候显示。
    is_symbol_show: bool = True,

    # 标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Union[Numeric, List] = 4,

    # 数据堆叠，同个类目轴上系列配置相同的　stack　值可以堆叠放置。
    stack: Optional[str] = None,

    # 是否平滑曲线
    is_smooth: bool = False,

    # 是否显示成阶梯图
    is_step: bool = False,

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 线样式配置项，参考 `series_options.LineStyleOpts`
    linestyle_opts: Union[opts.LineStyleOpts, dict] = opts.LineStyleOpts(),

    # 填充区域配置项，参考 `series_options.AreaStyleOpts`
    areastyle_opts: Union[opts.AreaStyleOpts, dict] = opts.AreaStyleOpts(),
)
```

### Demo

```python
def line_base() -> Line:
    c = (
        Line()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Line-基本示例"))
    )
    return c
```

```python
def line_smooth() -> Line:
    c = (
        Line()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values(), is_smooth=True)
        .add_yaxis("商家B", Faker.values(), is_smooth=True)
        .set_global_opts(title_opts=opts.TitleOpts(title="Line-smooth"))
    )
    return c
```

```python
def line_markpoint() -> Line:
    c = (
        Line()
        .add_xaxis(Faker.choose())
        .add_yaxis(
            "商家A",
            Faker.values(),
            markpoint_opts=opts.MarkPointOpts(data=[opts.MarkPointItem(type_="min")]),
        )
        .add_yaxis(
            "商家B",
            Faker.values(),
            markpoint_opts=opts.MarkPointOpts(data=[opts.MarkPointItem(type_="max")]),
        )
        .set_global_opts(title_opts=opts.TitleOpts(title="Line-MarkPoint"))
    )
    return c
```

```python
def line_markline() -> Line:
    c = (
        Line()
        .add_xaxis(Faker.choose())
        .add_yaxis(
            "商家A",
            Faker.values(),
            markline_opts=opts.MarkLineOpts(data=[opts.MarkLineItem(type_="average")]),
        )
        .add_yaxis(
            "商家B",
            Faker.values(),
            markline_opts=opts.MarkLineOpts(data=[opts.MarkLineItem(type_="average")]),
        )
        .set_global_opts(title_opts=opts.TitleOpts(title="Line-MarkLine"))
    )
    return c
```

```python
def line_step() -> Line:
    c = (
        Line()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values(), is_step=True)
        .set_global_opts(title_opts=opts.TitleOpts(title="Line-阶梯图"))
    )
    return c

```

## Scatter：散点图

> *class pyecharts.charts.Scatter*

```python
class Scatter(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: Union[opts.InitOpts, dict] = opts.InitOpts()
)
```

> *func pyecharts.charts.Scatter.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于tooltip的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Numeric = 10,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(position="right"),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,
)
```

### Demo

```python
def scatter_base() -> Scatter:
    c = (
        Scatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Scatter-基本示例"))
    )
    return c
```

```python
def scatter_spliteline() -> Scatter:
    c = (
        Scatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Scatter-显示分割线"))
        .set_global_opts(
            xaxis_opts=opts.AxisOpts(splitline_opts=opts.SplitLineOpts(is_show=True)),
            yaxis_opts=opts.AxisOpts(splitline_opts=opts.SplitLineOpts(is_show=True)),
        )
    )
    return c
```

```python
def scatter_visualmap_color() -> Scatter:
    c = (
        Scatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Scatter-VisualMap(Color)"),
            visualmap_opts=opts.VisualMapOpts(max_=150),
        )
    )
    return c
```

```python
def scatter_visualmap_color() -> Scatter:
    c = (
        Scatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Scatter-VisualMap(Size)"),
            visualmap_opts=opts.VisualMapOpts(type_="size", max_=150, min_=20),
        )
    )
    return c
```
