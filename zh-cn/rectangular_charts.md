直角坐标系图表继承自 `RectChart` 都拥有以下方法

> *func RectChart.extend_axis*

扩展 X/Y 轴
```python
def extend_axis(
    # 扩展 X 坐标轴数据项
    xaxis_data: Sequence = None,
    
    # 扩展 X 坐标轴配置项，参考 `global_options.AxisOpts`
    xaxis: Union[opts.AxisOpts, dict, None] = None,
    
    # 新增 Y 坐标轴配置项，参考 `global_options.AxisOpts`
    yaxis: Union[opts.AxisOpts, dict, None] = None,
)
```

> *func RectChart.add_xaxis*

新增 X 轴数据
```python
def add_xaxis(
    # X 轴数据项
    xaxis_data: Sequence
)
```

> *func RectChart.reversal_axis*

翻转 XY 轴数据
```python
def reversal_axis():
```

> *func RectChart.overlap*

层叠多图
```python
def overlap(
    # chart 为直角坐标系类型图表
    chart: Base
)
```

## Bar：柱状图/条形图

> *class pyecharts.charts.Bar(RectChart)*

```python
class Bar(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Bar.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    yaxis_data: Sequence[Numeric, opts.BarItem, dict],

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

    # 同一系列的柱间距离，默认为类目间距的 20%，可设固定值
    category_gap: Union[Numeric, str] = "20%",

    # 不同系列的柱间距离，为百分比（如 '30%'，表示柱子宽度的 30%）。
    # 如果想要两个系列的柱子重叠，可以设置 gap 为 '-100%'。这在用柱子做背景的时候有用。
    gap: Optional[str] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### BarItem：柱状图数据项

```python
class BarItem(
    # 数据项名称。
    name: Optional[str] = None,

    # 单个数据项的数值。
    value: Optional[Numeric] = None,

    # 单个柱条文本的样式设置，参考 `series_options.LabelOpts`。
    label_opts: Union[LabelOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[TooltipOpts, dict, None] = None,
)
```

### Demo

> Bar-基本示例

```python
from pyecharts.faker import Faker
from pyecharts import options as opts
from pyecharts.charts import Bar


def bar_base() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-基本示例", subtitle="我是副标题"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/56866199-32bce180-6a09-11e9-9e1c-35273a2770e5.png)

> Bar-渐变圆柱

```python
def bar_border_radius():
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values(), category_gap="60%")
        .set_series_opts(itemstyle_opts={
            "normal": {
                "color": JsCode("""new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: 'rgba(0, 244, 255, 1)'
                }, {
                    offset: 1,
                    color: 'rgba(0, 77, 167, 1)'
                }], false)"""),
                "barBorderRadius": [30, 30, 30, 30],
                "shadowColor": 'rgb(0, 160, 221)',
            }})
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-渐变圆柱"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/63487345-6acac180-c4dd-11e9-8392-fedac9ac6f91.png)


> Bar-动画配置基本示例

```python
def bar_base_with_animation() -> Bar:
    c = (
        Bar(
            init_opts=opts.InitOpts(
                animation_opts=opts.AnimationOpts(
                    animation_delay=1000, animation_easing="elasticOut"
                )
            )
        )
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-动画配置基本示例", subtitle="我是副标题")
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/61018779-8dd86080-a3ca-11e9-85da-5e9cefd4bbd4.png)

> Bar-背景图基本示例

```python
def bar_base_with_custom_background_image() -> Bar:
    c = (
        Bar(
            init_opts=opts.InitOpts(
                bg_color={
                    "type": "pattern",
                    "image": JsCode("img"),
                    "repeat": "no-repeat",
                }
            )
        )
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(
                title="Bar-背景图基本示例",
                subtitle="我是副标题",
                title_textstyle_opts=opts.TextStyleOpts(color="white"),
            )
        )
    )
    c.add_js_funcs(
        """
        var img = new Image(); img.src = 'https://s2.ax1x.com/2019/07/08/ZsS0fK.jpg';
        """
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/61018825-b1031000-a3ca-11e9-97e3-6e5af30ce878.png)

> Bar-通过 dict 进行配置

```python
def bar_base_dict_config() -> Bar:
    c = (
        Bar({"theme": ThemeType.MACARONS})
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts={"text": "Bar-通过 dict 进行配置", "subtext": "我也是通过 dict 进行配置的"}
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/61018875-d263fc00-a3ca-11e9-9722-6bcd11d93340.png)


> Bar-默认取消显示某 Series

```python
def bar_is_selected() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values(), is_selected=False)
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-默认取消显示某 Series"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/56866219-5bdd7200-6a09-11e9-8768-d09599546822.png)

> Bar-显示 ToolBox

```python
def bar_toolbox() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-显示 ToolBox"),
            toolbox_opts=opts.ToolboxOpts(),
            legend_opts=opts.LegendOpts(is_show=False)
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/56866240-816a7b80-6a09-11e9-9fce-1443541b36dd.png)

> Bar-单系列柱间距离

```python
def bar_same_series_gap() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values(), category_gap="80%")
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-单系列柱间距离"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/57543834-11a0ad00-7388-11e9-8416-918ad00ca2a2.png)

> Bar-不同系列柱间距离

```python
def bar_different_series_gap() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values(), gap="0%")
        .add_yaxis("商家B", Faker.values(), gap="0%")
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-不同系列柱间距离"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/57316521-955c5e80-7128-11e9-9f95-adf413015472.png)

> Bar-Y 轴 formatter

```python
def bar_yaxis_formatter() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-Y 轴 formatter"),
            yaxis_opts=opts.AxisOpts(
                axislabel_opts=opts.LabelOpts(formatter="{value} /月")
            ),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/57181491-1ae0d400-6ec7-11e9-9db5-6e07b0c9f431.png)

> Bar-XY 轴名称

```python
def bar_xyaxis_name() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-XY 轴名称"),
            yaxis_opts=opts.AxisOpts(name="我是 Y 轴"),
            xaxis_opts=opts.AxisOpts(name="我是 X 轴"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/57306732-edd63080-7115-11e9-8bde-b207c4e6f785.png)

> Bar-翻转 XY 轴

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
![](https://user-images.githubusercontent.com/19553554/55603127-b6353b00-579b-11e9-908e-27147c8cac6f.png)

> Bar-堆叠数据（全部）

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
![](https://user-images.githubusercontent.com/19553554/55603135-bdf4df80-579b-11e9-9040-54931e22a22a.png)

> Bar-堆叠数据（部分）

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
![](https://user-images.githubusercontent.com/19553554/55603139-c3522a00-579b-11e9-8e2d-1c725320ab74.png)

> Bar-MarkPoint（指定类型）

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
![](https://user-images.githubusercontent.com/19553554/55603167-f0064180-579b-11e9-87ef-b6afb775612b.png)

> Bar-MarkPoint（自定义）

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
![](https://user-images.githubusercontent.com/19553554/55603172-f5638c00-579b-11e9-9064-d4ceeac29f1c.png)

> Bar-MarkLine（指定类型）

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
![](https://user-images.githubusercontent.com/19553554/55603176-fac0d680-579b-11e9-8bcd-0e96777e9fd8.png)

> Bar-MarkLine（自定义）

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
[](https://user-images.githubusercontent.com/19553554/55603180-ff858a80-579b-11e9-8538-138d24a70a65.png)

> Bar-DataZoom（slider-水平）

```python
def bar_datazoom_slider() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.days_attrs)
        .add_yaxis("商家A", Faker.days_values)
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-DataZoom（slider-水平）"),
            datazoom_opts=opts.DataZoomOpts(),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55603271-630fb800-579c-11e9-8e90-3835d3bddf57.gif)

> Bar-DataZoom（slider-垂直）

```python
def bar_datazoom_slider_vertical() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.days_attrs)
        .add_yaxis("商家A", Faker.days_values, color=Faker.rand_color())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-DataZoom（slider-垂直）"),
            datazoom_opts=opts.DataZoomOpts(orient="vertical"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55603273-65721200-579c-11e9-83a1-22e640d1d599.gif)

> Bar-DataZoom（inside）

```python
def bar_datazoom_inside() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.days_attrs)
        .add_yaxis("商家A", Faker.days_values, color=Faker.rand_color())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-DataZoom（inside）"),
            datazoom_opts=opts.DataZoomOpts(type_="inside"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55603276-67d46c00-579c-11e9-9e26-664b6692a7c4.gif)

> Bar-DataZoom（slider+inside）

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
![](https://user-images.githubusercontent.com/19553554/55603299-92bec000-579c-11e9-89bd-87db197d760f.gif)

> Bar-直方图

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
![](https://user-images.githubusercontent.com/19553554/55603313-a36f3600-579c-11e9-80bd-38efb033daf8.png)

> Bar-直方图（颜色区分）

```python
def bar_histogram_color() -> Bar:
    x = Faker.dogs + Faker.animal
    xlen = len(x)
    y = []
    for idx, item in enumerate(x):
        if idx <= xlen / 2:
            y.append(
                opts.BarItem(
                    name=item,
                    value=(idx + 1) * 10,
                    itemstyle_opts=opts.ItemStyleOpts(color="#749f83"),
                )
            )
        else:
            y.append(
                opts.BarItem(
                    name=item,
                    value=(xlen + 1 - idx) * 10,
                    itemstyle_opts=opts.ItemStyleOpts(color="#d48265"),
                )
            )

    c = (
        Bar()
        .add_xaxis(x)
        .add_yaxis("series0", y, category_gap=0, color=Faker.rand_color())
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-直方图（颜色区分）"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/57544117-f7b39a00-7388-11e9-9315-529511c924f6.png)

> Bar-旋转 X 轴标签

```python
def bar_rorate_xaxis_label() -> Bar:
    c = (
        Bar()
        .add_xaxis(
            [
                "名字很长的X轴标签1",
                "名字很长的X轴标签2",
                "名字很长的X轴标签3",
                "名字很长的X轴标签4",
                "名字很长的X轴标签5",
                "名字很长的X轴标签6",
            ]
        )
        .add_yaxis("商家A", [10, 20, 30, 40, 50, 40])
        .add_yaxis("商家B", [20, 10, 40, 30, 40, 50])
        .set_global_opts(
            xaxis_opts=opts.AxisOpts(axislabel_opts=opts.LabelOpts(rotate=-15)),
            title_opts=opts.TitleOpts(title="Bar-旋转X轴标签", subtitle="解决标签名字过长的问题"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/56972171-16ea4480-6b9d-11e9-834c-b8eb4357808c.png)

> Bar-Graphic 组件示例

```python
def bar_graphic_component() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-Graphic 组件示例"),
            graphic_opts=[
                opts.GraphicGroup(
                    graphic_item=opts.GraphicItem(
                        rotation=JsCode("Math.PI / 4"),
                        bounding="raw",
                        right=110,
                        bottom=110,
                        z=100,
                    ),
                    children=[
                        opts.GraphicRect(
                            graphic_item=opts.GraphicItem(
                                left="center", top="center", z=100
                            ),
                            graphic_shape_opts=opts.GraphicShapeOpts(
                                width=400, height=50
                            ),
                            graphic_basicstyle_opts=opts.GraphicBasicStyleOpts(
                                fill="rgba(0,0,0,0.3)"
                            ),
                        ),
                        opts.GraphicText(
                            graphic_item=opts.GraphicItem(
                                left="center", top="center", z=100
                            ),
                            graphic_textstyle_opts=opts.GraphicTextStyleOpts(
                                text="pyecharts bar chart",
                                font="bold 26px Microsoft YaHei",
                                graphic_basicstyle_opts=opts.GraphicBasicStyleOpts(
                                    fill="#fff"
                                ),
                            ),
                        ),
                    ],
                )
            ],
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/58749280-a80f4c80-84b6-11e9-9dbc-068a28255ccf.png)

> Bar-Graphic (Rect + Text) 组件示例 1

```python
def bar_graphic_rect_text_one_component() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-Graphic Rect+Text 1 组件示例"),
            graphic_opts=[
                opts.GraphicGroup(
                    graphic_item=opts.GraphicItem(
                        rotation=JsCode("Math.PI / 4"),
                        bounding="raw",
                        right=110,
                        bottom=110,
                        z=100,
                    ),
                    children=[
                        opts.GraphicRect(
                            graphic_item=opts.GraphicItem(
                                left="center", top="center", z=100
                            ),
                            graphic_shape_opts=opts.GraphicShapeOpts(
                                width=400, height=50
                            ),
                            graphic_basicstyle_opts=opts.GraphicBasicStyleOpts(
                                fill="rgba(0,0,0,0.3)"
                            ),
                        ),
                        opts.GraphicText(
                            graphic_item=opts.GraphicItem(
                                left="center", top="center", z=100
                            ),
                            graphic_textstyle_opts=opts.GraphicTextStyleOpts(
                                text="pyecharts bar chart",
                                font="bold 26px Microsoft YaHei",
                                graphic_basicstyle_opts=opts.GraphicBasicStyleOpts(
                                    fill="#fff"
                                ),
                            ),
                        ),
                    ],
                )
            ],
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/59005268-6502ff80-884f-11e9-95d9-7dfbcce96169.png)

> Bar-Graphic (Rect + Text) 组件示例 2

```python
def bar_graphic_rect_text_two_component() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-Graphic Rect+Text 2 组件示例"),
            graphic_opts=[
                opts.GraphicGroup(
                    graphic_item=opts.GraphicItem(
                        left="50%",
                        top="15%",
                    ),
                    children=[
                        opts.GraphicRect(
                            graphic_item=opts.GraphicItem(
                                z=100,
                                left="center",
                                top="middle",
                            ),
                            graphic_shape_opts=opts.GraphicShapeOpts(
                                width=190, height=90,
                            ),
                            graphic_basicstyle_opts=opts.GraphicBasicStyleOpts(
                                fill="#fff",
                                stroke="#555",
                                line_width=2,
                                shadow_blur=8,
                                shadow_offset_x=3,
                                shadow_offset_y=3,
                                shadow_color="rgba(0,0,0,0.3)",
                            )
                        ),
                        opts.GraphicText(
                            graphic_item=opts.GraphicItem(
                                left="center",
                                top="middle",
                                z=100,
                            ),
                            graphic_textstyle_opts=opts.GraphicTextStyleOpts(
                                text=JsCode(
                                    "['横轴表示数据类别',"
                                    "'纵轴表示数值的值',"
                                    "'这个文本块可以放在图中各',"
                                    "'种位置'].join('\\n')"
                                ),
                                font="14px Microsoft YaHei",
                                graphic_basicstyle_opts=opts.GraphicBasicStyleOpts(
                                    fill="#333"
                                )
                            )
                        )
                    ]
                )
            ],
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/59005274-6af8e080-884f-11e9-824e-2fa7ff62a93e.png)

> Bar-Graphic (Image) 组件示例

```python
def bar_graphic_image_component() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-Graphic Image 组件示例"),
            graphic_opts=[
                opts.GraphicImage(
                    graphic_item=opts.GraphicItem(
                        id_="logo",
                        right=20,
                        top=20,
                        z=-10,
                        bounding="raw",
                        origin=[75, 75],
                    ),
                    graphic_imagestyle_opts=opts.GraphicImageStyleOpts(
                        image="http://echarts.baidu.com/images/favicon.png",
                        width=150,
                        height=150,
                        opacity=0.4,
                    ),
                )
            ],
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/59005282-6fbd9480-884f-11e9-8a8b-abfbfd681056.png)

> Bar-Graphic (Image-Rotate) 组件示例

```python
def bar_graphic_image_with_js_component() -> Grid:
    bar = (
        Bar(init_opts=opts.InitOpts(chart_id="1234"))
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-Graphic Image（旋转功能）组件示例"),
            graphic_opts=[
                opts.GraphicImage(
                    graphic_item=opts.GraphicItem(
                        id_="logo",
                        right=20,
                        top=20,
                        z=-10,
                        bounding="raw",
                        origin=[75, 75],
                    ),
                    graphic_imagestyle_opts=opts.GraphicImageStyleOpts(
                        image="http://echarts.baidu.com/images/favicon.png",
                        width=150,
                        height=150,
                        opacity=0.4,
                    ),
                )
            ],
        )
    )
    c = (
        Grid(
            init_opts=opts.InitOpts(chart_id="1234")
        )
        .add(
            chart=bar,
            grid_opts=opts.GridOpts(
                pos_left="5%",
                pos_right="4%",
                pos_bottom="5%",
            )
        )
        .add_js_funcs("""
            var rotation = 0;
            setInterval(function () {
                chart_1234.setOption({
                    graphic: {
                        id: 'logo',
                        rotation: (rotation += Math.PI / 360) % (Math.PI * 2)
                    }
                });
            }, 30);
        """)
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/59005286-75b37580-884f-11e9-9619-dcf3887dd66b.png)

> Bar-Brush 示例

```python
def bar_with_brush() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Bar-Brush 示例", subtitle="我是副标题"),
            brush_opts=opts.BrushOpts(),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/61018926-f7f10580-a3ca-11e9-9719-39142c0195f6.png)

> Bar-自定义柱状颜色

```python
def bar_custom_bar_color() -> Bar:
    color_function = """
        function (params) {
            if (params.value > 0 && params.value < 50) {
                return 'red';
            } else if (params.value > 50 && params.value < 100) {
                return 'blue';
            }
            return 'green';
        }
        """
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis(
            "商家A",
            Faker.values(),
            itemstyle_opts=opts.ItemStyleOpts(color=JsCode(color_function)),
        )
        .add_yaxis(
            "商家B",
            Faker.values(),
            itemstyle_opts=opts.ItemStyleOpts(color=JsCode(color_function)),
        )
        .add_yaxis(
            "商家C",
            Faker.values(),
            itemstyle_opts=opts.ItemStyleOpts(color=JsCode(color_function)),
        )
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-自定义柱状颜色"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/63005440-1dcc6700-beaf-11e9-9281-8b20a047c113.png)

> Bar-堆叠显示百分比

```python
def stack_bar_percent() -> Bar:
    list2 = [
        {"value": 12, "percent": 12 / (12 + 3)},
        {"value": 23, "percent": 23 / (23 + 21)},
        {"value": 33, "percent": 33 / (33 + 5)},
        {"value": 3, "percent": 3 / (3 + 52)},
        {"value": 33, "percent": 33 / (33 + 43)},
    ]

    list3 = [
        {"value": 3, "percent": 3 / (12 + 3)},
        {"value": 21, "percent": 21 / (23 + 21)},
        {"value": 5, "percent": 5 / (33 + 5)},
        {"value": 52, "percent": 52 / (3 + 52)},
        {"value": 43, "percent": 43 / (33 + 43)},
    ]

    c = (
        Bar(init_opts=opts.InitOpts(theme=ThemeType.LIGHT))
        .add_xaxis([1, 2, 3, 4, 5])
        .add_yaxis("product1", list2, stack="stack1", category_gap="50%")
        .add_yaxis("product2", list3, stack="stack1", category_gap="50%")
        .set_series_opts(
            label_opts=opts.LabelOpts(
                position="right",
                formatter=JsCode(
                    "function(x){return Number(x.data.percent * 100).toFixed() + '%';}"
                ),
            )
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/68597426-e5e9b580-04d7-11ea-882f-d5cce5ccd484.png)


## Boxplot：箱形图

> *class pyecharts.charts.Boxplot(RectChart)*

```python
class Boxplot(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Boxplot.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
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

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### Demo

> BoxPlot-基本示例

```python
from pyecharts import options as opts
from pyecharts.charts import Boxplot


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
![](https://user-images.githubusercontent.com/19553554/55603413-27c1b900-579d-11e9-954b-a1619846262e.png)


## EffectScatter：涟漪特效散点图

> *class pyecharts.charts.EffectScatter(RectChart)*

```python
class EffectScatter(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.EffectScatter.add_yaxis*

```python
 def add_yaxis(
     # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
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

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### Demo

> EffectScatter-基本示例

```python
from pyecharts.faker import Faker
from pyecharts import options as opts
from pyecharts.charts import EffectScatter
from pyecharts.globals import SymbolType


def effectscatter_base() -> EffectScatter:
    c = (
        EffectScatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="EffectScatter-基本示例"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55603439-4758e180-579d-11e9-9179-646a02519dcc.png)

> EffectScatter-显示分割线

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
![](https://user-images.githubusercontent.com/19553554/55603444-4d4ec280-579d-11e9-9b15-09cc6cd3c2e0.png)

> EffectScatter-不同Symbol

```python
def effectscatter_symbol() -> EffectScatter:
    c = (
        EffectScatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("", Faker.values(), symbol=SymbolType.ARROW)
    ).set_global_opts(title_opts=opts.TitleOpts(title="EffectScatter-不同Symbol"))
    return c
```
![](https://user-images.githubusercontent.com/19553554/55603452-5770c100-579d-11e9-97b6-a7ed280834a4.png)


## HeatMap：热力图

> *class pyecharts.charts.HeatMap(RectChart)*

```python
class HeatMap(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.HeatMap.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
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

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### Demo

> HeatMap-基本示例

```python
import random

from pyecharts.faker import  Faker
from pyecharts import options as opts
from pyecharts.charts import HeatMap


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
![](https://user-images.githubusercontent.com/19553554/55603513-9ef74d00-579d-11e9-837b-5e5288569e8c.gif)

> HeatMap-Label 显示

```python
def heatmap_with_label_show() -> HeatMap:
    value = [[i, j, random.randint(0, 50)] for i in range(24) for j in range(7)]
    c = (
        HeatMap()
        .add_xaxis(Faker.clock)
        .add_yaxis(
            "series0",
            Faker.week,
            value,
            label_opts=opts.LabelOpts(is_show=True, position="inside"),
        )
        .set_global_opts(
            title_opts=opts.TitleOpts(title="HeatMap-Label 显示"),
            visualmap_opts=opts.VisualMapOpts(),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/71709711-c9149300-2e33-11ea-8e89-56c38dac4bc9.png)


## Kline/Candlestick：K线图

> *class pyecharts.charts.Kline(RectChart)*

```python
class Kline(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Kline.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
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

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### Demo

> Kline-基本示例

```python
from pyecharts import options as opts
from pyecharts.charts import Kline


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
![](https://user-images.githubusercontent.com/19553554/55603539-bb938500-579d-11e9-920c-c701f24cb9b4.png)

> Kline-显示分割区域

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
![](https://user-images.githubusercontent.com/19553554/55603546-bfbfa280-579d-11e9-9bc7-fac4cd49ba59.png)

> Kline-DataZoom-slider

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
![](https://user-images.githubusercontent.com/19553554/55603567-d960ea00-579d-11e9-9368-2fa6f9c28cad.gif)

> Kline-DataZoom-slider-Position（缩小 sliderbar）

```python
def kline_datazoom_slider_position() -> Kline:
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
            datazoom_opts=[opts.DataZoomOpts(pos_bottom="-2%")],
            title_opts=opts.TitleOpts(title="Kline-DataZoom-slider-Position"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/57308413-e5cbc000-7118-11e9-932d-c0dd5356b1be.png)

> Kline-ItemStyle

```python
def kline_itemstyle() -> Kline:
    c = (
        Kline()
        .add_xaxis(["2017/7/{}".format(i + 1) for i in range(31)])
        .add_yaxis(
            "kline",
            data,
            itemstyle_opts=opts.ItemStyleOpts(
                color="#ec0000",
                color0="#00da3c",
                border_color="#8A0000",
                border_color0="#008F28",
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
            datazoom_opts=[opts.DataZoomOpts(type_="inside")],
            title_opts=opts.TitleOpts(title="Kline-ItemStyle"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/56814513-f2772b00-6871-11e9-826d-1d590d1b3f58.png)

> Kline-DataZoom-inside

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
![](https://user-images.githubusercontent.com/19553554/55603580-f1386e00-579d-11e9-948c-0207f25ebd5b.gif)

> Kline-MarkLine

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
![](https://user-images.githubusercontent.com/19553554/55603591-001f2080-579e-11e9-810b-0c5c43e1d0e8.png)


## Line：折线/面积图

> *class pyecharts.charts.Line(RectChart)*

```python
class Line(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Line.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    y_axis: Sequence,

    # 是否选中图例
    is_selected: bool = True,

    # 是否连接空数据，空数据使用 `None` 填充
    is_connect_nones: bool = False,

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
    symbol_size: Union[Numeric, Sequence] = 4,

    # 数据堆叠，同个类目轴上系列配置相同的　stack　值可以堆叠放置。
    stack: Optional[str] = None,

    # 是否平滑曲线
    is_smooth: bool = False,

    # 是否显示成阶梯图
    is_step: bool = False,
    
    # 是否开启 hover 在拐点标志上的提示动画效果。
    is_hover_animation: bool = True,

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

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### Demo

> Line-基本示例

```python
import pyecharts.options as opts
from pyecharts.faker import  Faker
from pyecharts.charts import Line


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
![](https://user-images.githubusercontent.com/19553554/55603644-3ceb1780-579e-11e9-818c-2841b0d66ff6.png)

> Line-数值 X 轴

```python
def line_xaxis_type() -> Line:
    c = (
        Line()
        .add_xaxis(Faker.values())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Line-数值 X 轴"),
            xaxis_opts=opts.AxisOpts(type_="value"),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/65735412-d837c680-e109-11e9-80cf-b888fc5b5efe.png)

> Line-连接空数据

```python
def line_connect_null() -> Line:
    y = Faker.values()
    y[3], y[5] = None, None
    c = (
        Line()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", y, is_connect_nones=True)
        .set_global_opts(title_opts=opts.TitleOpts(title="Line-连接空数据"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/58220358-2ba39d80-7d41-11e9-935f-17f12f617d7e.png)

> Line-平滑曲线

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
![](https://user-images.githubusercontent.com/19553554/55603648-41afcb80-579e-11e9-946b-671f308dd4b8.png)

> Line-面积图

```python
def line_areastyle() -> Line:
    c = (
        Line()
        .add_xaxis(Faker.choose())
        .add_yaxis(
            "商家A", Faker.values(), areastyle_opts=opts.AreaStyleOpts(opacity=0.5)
        )
        .add_yaxis(
            "商家B", Faker.values(), areastyle_opts=opts.AreaStyleOpts(opacity=0.5)
        )
        .set_global_opts(title_opts=opts.TitleOpts(title="Line-面积图"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/58150164-5d145e80-7c98-11e9-828c-239fb8543098.png)

> Line-面积图（紧贴 Y 轴）

```python
def line_areastyle_boundary_gap() -> Line:
    c = (
        Line()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values(), is_smooth=True)
        .add_yaxis("商家B", Faker.values(), is_smooth=True)
        .set_series_opts(
            areastyle_opts=opts.AreaStyleOpts(opacity=0.5),
            label_opts=opts.LabelOpts(is_show=False),
        )
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Line-面积图（紧贴 Y 轴）"),
            xaxis_opts=opts.AxisOpts(
                axistick_opts=opts.AxisTickOpts(is_align_with_label=True),
                is_scale=False,
                boundary_gap=False,
            ),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/58150186-6ac9e400-7c98-11e9-882b-3085dc6c5b76.png)

> Line-对数轴示例

```python
def line_yaxis_log() -> Line:
    c = (
        Line()
        .add_xaxis(xaxis_data=["一", "二", "三", "四", "五", "六", "七", "八", "九"])
        .add_yaxis(
            "2 的指数",
            y_axis=[1, 2, 4, 8, 16, 32, 64, 128, 256],
            linestyle_opts=opts.LineStyleOpts(width=2),
        )
        .add_yaxis(
            "3 的指数",
            y_axis=[1, 3, 9, 27, 81, 247, 741, 2223, 6669],
            linestyle_opts=opts.LineStyleOpts(width=2),
        )
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Line-对数轴示例"),
            xaxis_opts=opts.AxisOpts(name="x"),
            yaxis_opts=opts.AxisOpts(
                type_="log",
                name="y",
                splitline_opts=opts.SplitLineOpts(is_show=True),
                is_scale=True,
            ),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/57543749-d0a89880-7387-11e9-8b7b-18d46e73616c.png)

> Line-MarkPoint

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
![](https://user-images.githubusercontent.com/19553554/55603654-47a5ac80-579e-11e9-81a7-e4c3ce611de0.png)

> Line-MarkPoint（自定义）

```python
def line_markpoint_custom() -> Line:
    x, y = Faker.choose(), Faker.values()
    c = (
        Line()
        .add_xaxis(x)
        .add_yaxis(
            "商家A",
            y,
            markpoint_opts=opts.MarkPointOpts(
                data=[opts.MarkPointItem(name="自定义标记点", coord=[x[2], y[2]], value=y[2])]
            ),
        )
        .set_global_opts(title_opts=opts.TitleOpts(title="Line-MarkPoint（自定义）"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/63036891-8d167b00-bef0-11e9-8b61-cf65c313522c.png)

> Line-MarkLine

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
![](https://user-images.githubusercontent.com/19553554/55603660-4d02f700-579e-11e9-9d99-c4c91618e1de.png)

> Line-阶梯图

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
![](https://user-images.githubusercontent.com/19553554/55603664-542a0500-579e-11e9-9d5f-85ad3a605339.png)

> Line-ItemStyle

```python
def line_itemstyle() -> Line:
    c = (
        Line()
        .add_xaxis(xaxis_data=Faker.choose())
        .add_yaxis(
            "商家A",
            Faker.values(),
            symbol="triangle",
            symbol_size=20,
            linestyle_opts=opts.LineStyleOpts(color="green", width=4, type_="dashed"),
            label_opts=opts.LabelOpts(is_show=False),
            itemstyle_opts=opts.ItemStyleOpts(
                border_width=3, border_color="yellow", color="blue"
            ),
        )
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Line-ItemStyle"),
            xaxis_opts=opts.AxisOpts(type_="category"),
            yaxis_opts=opts.AxisOpts(
                type_="value",
                axistick_opts=opts.AxisTickOpts(is_show=True),
                splitline_opts=opts.SplitLineOpts(is_show=True),
            ),
            tooltip_opts=opts.TooltipOpts(is_show=False),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/56972743-1b632d00-6b9e-11e9-8110-c52070cc2783.png)

> Line图-高级自定义

```python
def line_color_with_js_func() -> Line:
    x_data = ["14", "15", "16", "17", "18", "19", "20", "21", "22", "23"]
    y_data = [393, 438, 485, 631, 689, 824, 987, 1000, 1100, 1200]

    background_color_js = (
        "new echarts.graphic.LinearGradient(0, 0, 0, 1, "
        "[{offset: 0, color: '#c86589'}, {offset: 1, color: '#06a7ff'}], false)"
    )
    area_color_js = (
        "new echarts.graphic.LinearGradient(0, 0, 0, 1, "
        "[{offset: 0, color: '#eb64fb'}, {offset: 1, color: '#3fbbff0d'}], false)"
    )

    c = (
        Line(init_opts=opts.InitOpts(bg_color=JsCode(background_color_js)))
        .add_xaxis(xaxis_data=x_data)
        .add_yaxis(
            series_name="注册总量",
            y_axis=y_data,
            is_smooth=True,
            is_symbol_show=True,
            symbol="circle",
            symbol_size=6,
            linestyle_opts=opts.LineStyleOpts(color="#fff"),
            label_opts=opts.LabelOpts(is_show=True, position="top", color="white"),
            itemstyle_opts=opts.ItemStyleOpts(
                color="red", border_color="#fff", border_width=3
            ),
            tooltip_opts=opts.TooltipOpts(is_show=False),
            areastyle_opts=opts.AreaStyleOpts(color=JsCode(area_color_js), opacity=1),
        )
        .set_global_opts(
            title_opts=opts.TitleOpts(
                title="OCTOBER 2015",
                pos_bottom="5%",
                pos_left="center",
                title_textstyle_opts=opts.TextStyleOpts(color="#fff", font_size=16),
            ),
            xaxis_opts=opts.AxisOpts(
                type_="category",
                boundary_gap=False,
                axislabel_opts=opts.LabelOpts(margin=30, color="#ffffff63"),
                axisline_opts=opts.AxisLineOpts(is_show=False),
                axistick_opts=opts.AxisTickOpts(
                    is_show=True,
                    length=25,
                    linestyle_opts=opts.LineStyleOpts(color="#ffffff1f"),
                ),
                splitline_opts=opts.SplitLineOpts(
                    is_show=True, linestyle_opts=opts.LineStyleOpts(color="#ffffff1f")
                ),
            ),
            yaxis_opts=opts.AxisOpts(
                type_="value",
                position="right",
                axislabel_opts=opts.LabelOpts(margin=20, color="#ffffff63"),
                axisline_opts=opts.AxisLineOpts(
                    linestyle_opts=opts.LineStyleOpts(width=2, color="#fff")
                ),
                axistick_opts=opts.AxisTickOpts(
                    is_show=True,
                    length=15,
                    linestyle_opts=opts.LineStyleOpts(color="#ffffff1f"),
                ),
                splitline_opts=opts.SplitLineOpts(
                    is_show=True, linestyle_opts=opts.LineStyleOpts(color="#ffffff1f")
                ),
            ),
            legend_opts=opts.LegendOpts(is_show=False),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/17564655/68598066-09f9c680-04d9-11ea-9390-9d161c9228e8.png)


## PictorialBar：象形柱状图

> *class pyecharts.charts.PictorialBar(Bar)*

```python
class PictorialBar(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.PictorialBar.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
    series_name: str,

    # 系列数据
    yaxis_data: Sequence[Numeric, opts.BarItem, dict],

    # 图形类型。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    # URL 为图片链接例如：'image://http://xxx.xxx.xxx/a/b.png'
    # URL 为 dataURI 例如：'image://data:image/gif;base64,R0lGODlhEAAQAMQAAORHHOVSKudfO...
    # 可以通过 'path://' 将图标设置为任意的矢量路径。这种方式相比于使用图片的方式，不用担心因为缩放而产生锯齿或模糊，
    # 而且可以设置为任意颜色。路径图形会自适应调整为合适的大小。路径的格式参见 SVG PathData。
    # 可以从 Adobe Illustrator 等工具编辑导出。例如：
    # 'path://M30.9,53.2C16.8,53.2,5.3,41.7,5.3,27.6S16.8,2,30.9,2C45,2,56.4,13.5,56.4,2...'
    symbol: Optional[str] = None,

    # 图形的大小。
    # 可以用数组分开表示宽和高，例如 [20, 10] 表示标记宽为20，
    # 高为 10，也可以设置成诸如 10 这样单一的数字，表示 [10, 10]。
    # 可以设置成绝对值（如 10），也可以设置成百分比（如 '120%'、['55%', 23]）。
    symbol_size: Union[Numeric, Sequence, None] = None,

    # 图形的定位位置。可取值：
    # 'start'：图形边缘与柱子开始的地方内切。
    # 'end'：图形边缘与柱子结束的地方内切。
    # 'center'：图形在柱子里居中。
    symbol_pos: Optional[str] = None,

    # 图形相对于原本位置的偏移。symbolOffset 是图形定位中最后计算的一个步骤，
    # 可以对图形计算出来的位置进行微调。
    # 可以设置成绝对值（如 10），也可以设置成百分比（如 '120%'、['55%', 23]）。
    # 当设置为百分比时，表示相对于自身尺寸 symbolSize 的百分比。
    # 例如 [0, '-50%'] 就是把图形向上移动了自身尺寸的一半的位置。
    symbol_offset: Optional[Sequence] = None,

    # 图形的旋转角度。
    # 注意，symbolRotate 并不会影响图形的定位（哪怕超出基准柱的边界），而只是单纯得绕自身中心旋转。
    # 此属性可以被设置在系列的 根部，表示对此系列中所有数据都生效；
    # 也可以被设置在 data 中的 每个数据项中，表示只对此数据项生效。
    symbol_rotate: Optional[Numeric] = None,

    # 指定图形元素是否重复。值可为：
    # false/null/undefined：不重复，即每个数据值用一个图形元素表示。
    # true：使图形元素重复，即每个数据值用一组重复的图形元素表示。重复的次数依据 data 计算得到。
    # a number：使图形元素重复，即每个数据值用一组重复的图形元素表示。重复的次数是给定的定值。
    # 'fixed'：使图形元素重复，即每个数据值用一组重复的图形元素表示。
    # 重复的次数依据 symbolBoundingData 计算得到，即与 data 无关。这在此图形被用于做背景时有用。
    symbol_repeat: Optional[str] = None,

    # 指定图形元素重复时，绘制的顺序。这个属性在两种情况下有用处：
    # 当 symbolMargin 设置为负值时，重复的图形会互相覆盖，这是可以使用 symbolRepeatDirection 来指定覆盖顺序。
    # 当 animationDelay 或 animationDelayUpdate 被使用时，symbolRepeatDirection 指定了 index 顺序。
    # 这个属性的值可以是：'start' 或 'end'。
    symbol_repeat_direction: Optional[str] = None,

    # 图形的两边间隔（『两边』是指其数值轴方向的两边）。可以是绝对数值（如 20），或者百分比值（如 '-30%'），
    # 表示相对于自身尺寸 symbolSize 的百分比。只有当 symbolRepeat 被使用时有意义。
    # 可以是正值，表示间隔大；也可以是负数。当 symbolRepeat 被使用时，负数时能使图形重叠。
    # 可以在其值结尾处加一个 "!"，如 "30%!" 或 25!，表示第一个图形的开始和最后一个图形结尾留白，
    # 不紧贴边界。默认会紧贴边界。
    symbol_margin: Union[Numeric, str, None] = None,

    # 是否剪裁图形。
    # false/null/undefined：图形本身表示数值大小。
    # true：图形被剪裁后剩余的部分表示数值大小。
    # symbolClip 常在这种场景下使用：同时表达『总值』和『当前数值』。在这种场景下，可以使用两个系列，
    # 一个系列是完整的图形，当做『背景』来表达总数值，另一个系列是使用 symbolClip 进行剪裁过的图形，表达当前数值。
    is_symbol_clip: bool = False,

    # 是否选中图例
    is_selected: bool = True,

    # 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用。
    xaxis_index: Optional[Numeric] = None,

    # 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用。
    yaxis_index: Optional[Numeric] = None,

    # 系列 label 颜色
    color: Optional[str] = None,

    # 同一系列的柱间距离，默认为类目间距的 20%，可设固定值
    category_gap: Union[Numeric, str] = "20%",

    # 不同系列的柱间距离，为百分比（如 '30%'，表示柱子宽度的 30%）。
    # 如果想要两个系列的柱子重叠，可以设置 gap 为 '-100%'。这在用柱子做背景的时候有用。
    gap: Optional[str] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[opts.LabelOpts, dict] = opts.LabelOpts(),

    # 标记点配置项，参考 `series_options.MarkPointOpts`
    markpoint_opts: Union[opts.MarkPointOpts, dict, None] = None,

    # 标记线配置项，参考 `series_options.MarkLineOpts`
    markline_opts: Union[opts.MarkLineOpts, dict, None] = None,

    # 提示框组件配置项，参考 `series_options.TooltipOpts`
    tooltip_opts: Union[opts.TooltipOpts, dict, None] = None,

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### Demo

> PictorialBar-各省份人口数量（虚假数据）

```python
import json
import os

from pyecharts import options as opts
from pyecharts.charts import Page, PictorialBar
from pyecharts.globals import SymbolType


location = ["山西", "四川", "西藏", "北京", "上海", "内蒙古", "云南", "黑龙江", "广东", "福建"]
values = [13, 42, 67, 81, 86, 94, 166, 220, 249, 262]

with open(os.path.join("fixtures", "symbol.json"), "r", encoding="utf-8") as f:
    symbols = json.load(f)

def pictorialbar_base() -> PictorialBar:
    c = (
        PictorialBar()
        .add_xaxis(location)
        .add_yaxis(
            "",
            values,
            label_opts=opts.LabelOpts(is_show=False),
            symbol_size=18,
            symbol_repeat="fixed",
            symbol_offset=[0, 0],
            is_symbol_clip=True,
            symbol=SymbolType.ROUND_RECT,
        )
        .reversal_axis()
        .set_global_opts(
            title_opts=opts.TitleOpts(title="PictorialBar-各省份人口数量（虚假数据）"),
            xaxis_opts=opts.AxisOpts(is_show=False),
            yaxis_opts=opts.AxisOpts(
                axistick_opts=opts.AxisTickOpts(is_show=False),
                axisline_opts=opts.AxisLineOpts(
                    linestyle_opts=opts.LineStyleOpts(opacity=0)
                ),
            ),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/58700715-72456780-83d3-11e9-86b2-fe913aadf168.png)

> PictorialBar-自定义 Symbol

```python
def pictorialbar_custom_symbol() -> PictorialBar:
    c = (
        PictorialBar()
        .add_xaxis(location)
        .add_yaxis(
            "",
            values,
            label_opts=opts.LabelOpts(is_show=False),
            symbol_size=22,
            symbol_repeat="fixed",
            symbol_offset=[0, -5],
            is_symbol_clip=True,
            symbol=symbols["boy"],
        )
        .reversal_axis()
        .set_global_opts(
            title_opts=opts.TitleOpts(title="PictorialBar-自定义 Symbol"),
            xaxis_opts=opts.AxisOpts(is_show=False),
            yaxis_opts=opts.AxisOpts(
                axistick_opts=opts.AxisTickOpts(is_show=False),
                axisline_opts=opts.AxisLineOpts(
                    linestyle_opts=opts.LineStyleOpts(opacity=0)
                ),
            ),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/58700722-77a2b200-83d3-11e9-91b5-0e5d04f9beff.png)

> PictorialBar-Vehicles in X City

```python
def pictorialbar_multi_custom_symbols() -> PictorialBar:
    c = (
        PictorialBar()
        .add_xaxis(["reindeer", "ship", "plane", "train", "car"])
        .add_yaxis(
            "2015",
            [
                {"value": 157, "symbol": symbols["reindeer"]},
                {"value": 21, "symbol": symbols["ship"]},
                {"value": 66, "symbol": symbols["plane"]},
                {"value": 78, "symbol": symbols["train"]},
                {"value": 123, "symbol": symbols["car"]},
            ],
            label_opts=opts.LabelOpts(is_show=False),
            symbol_size=22,
            symbol_repeat="fixed",
            symbol_offset=[0, 5],
            is_symbol_clip=True,
        )
        .add_yaxis(
            "2016",
            [
                {"value": 184, "symbol": symbols["reindeer"]},
                {"value": 29, "symbol": symbols["ship"]},
                {"value": 73, "symbol": symbols["plane"]},
                {"value": 91, "symbol": symbols["train"]},
                {"value": 95, "symbol": symbols["car"]},
            ],
            label_opts=opts.LabelOpts(is_show=False),
            symbol_size=22,
            symbol_repeat="fixed",
            symbol_offset=[0, -25],
            is_symbol_clip=True,
        )
        .reversal_axis()
        .set_global_opts(
            title_opts=opts.TitleOpts(title="PictorialBar-Vehicles in X City"),
            xaxis_opts=opts.AxisOpts(is_show=False),
            yaxis_opts=opts.AxisOpts(
                axistick_opts=opts.AxisTickOpts(is_show=False),
                axisline_opts=opts.AxisLineOpts(
                    linestyle_opts=opts.LineStyleOpts(opacity=0)
                ),
            ),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/58700732-7c676600-83d3-11e9-9d1d-01086c2f2efa.png)


## Scatter：散点图

> *class pyecharts.charts.Scatter(RectChart)*

```python
class Scatter(
    # 初始化配置项，参考 `global_options.InitOpts`
    init_opts: opts.InitOpts = opts.InitOpts()
)
```

> *func pyecharts.charts.Scatter.add_yaxis*

```python
def add_yaxis(
    # 系列名称，用于 tooltip 的显示，legend 的图例筛选。
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

    # 图元样式配置项，参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[opts.ItemStyleOpts, dict, None] = None,
)
```

### Demo

> Scatter-基本示例

```python
from pyecharts.faker import Faker
from pyecharts import options as opts
from pyecharts.charts import Scatter


def scatter_base() -> Scatter:
    c = (
        Scatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Scatter-基本示例"))
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55603717-a408cc00-579e-11e9-921b-b14cfa4503a4.png)

> Scatter-显示分割线

```python
def scatter_spliteline() -> Scatter:
    c = (
        Scatter()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Scatter-显示分割线"),
            xaxis_opts=opts.AxisOpts(splitline_opts=opts.SplitLineOpts(is_show=True)),
            yaxis_opts=opts.AxisOpts(splitline_opts=opts.SplitLineOpts(is_show=True)),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/55603757-dd413c00-579e-11e9-8086-6b61c9b7b5da.png)

> Scatter-VisualMap(Color)

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
![](https://user-images.githubusercontent.com/19553554/55603783-019d1880-579f-11e9-855f-d55151769743.gif)

> Scatter-VisualMap(Size)

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
![](https://user-images.githubusercontent.com/19553554/55603785-03ff7280-579f-11e9-8208-c80f0e47871f.gif)

> Scatter-多维度数据

```python
def scatter_muti_dimension_data() -> Scatter:
    c = (
        Scatter()
        .add_xaxis(Faker.choose())
        .add_yaxis(
            "商家A",
            [list(z) for z in zip(Faker.values(), Faker.choose())],
            label_opts=opts.LabelOpts(
                formatter=JsCode(
                    "function(params){return params.value[1] +' : '+ params.value[2];}"
                )
            ),
        )
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Scatter-多维度数据"),
            tooltip_opts=opts.TooltipOpts(
                formatter=JsCode(
                    "function (params) {return params.name + ' : ' + params.value[2];}"
                )
            ),
            visualmap_opts=opts.VisualMapOpts(
                type_="color", max_=150, min_=20, dimension=1
            ),
        )
    )
    return c
```
![](https://user-images.githubusercontent.com/19553554/58701461-8ee29f00-83d5-11e9-9f43-ba73cc0946cf.png)


## Overlap：层叠多图

### Demo

> Overlap-line+scatter

```python
def overlap_line_scatter() -> Bar:
    x = Faker.choose()
    bar = (
        Bar()
        .add_xaxis(x)
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Overlap-line+scatter"))
    )
    line = (
        Line()
        .add_xaxis(x)
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
    )
    bar.overlap(line)
    return bar

overlap_line_scatter().render()
```
![](https://user-images.githubusercontent.com/19553554/56574713-8341d280-65f6-11e9-9a13-178472520dc8.png)

> Overlap-bar+line（双 Y 轴）

```python
def overlap_bar_line() -> Bar:
    bar = (
        Bar()
        .add_xaxis(Faker.months)
        .add_yaxis("蒸发量", v1)
        .add_yaxis("降水量", v2)
        .extend_axis(
            yaxis=opts.AxisOpts(
                axislabel_opts=opts.LabelOpts(formatter="{value} °C"), interval=5
            )
        )
        .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
        .set_global_opts(
            title_opts=opts.TitleOpts(title="Overlap-bar+line（双 Y 轴）"),
            yaxis_opts=opts.AxisOpts(
                axislabel_opts=opts.LabelOpts(formatter="{value} ml")
            ),
        )
    )

    line = Line().add_xaxis(Faker.months).add_yaxis("平均温度", v3, yaxis_index=1)
    bar.overlap(line)
```
![](https://user-images.githubusercontent.com/19553554/56789638-f0db4200-6834-11e9-90e2-54015b379fe9.png)
