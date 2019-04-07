> 高级用法篇：本文档描述了 pyecharts 库的高级进阶用法。

## 概述

注意的是目前暂不支持 `lambda` 表达式。

例子：

```python
from pyecharts import Bar


def label_formatter(params):
    return params.value + ' [Good!]'


attr = ["Jan", "Feb"]
v1 = [2.0, 4.9]
bar = Bar("Bar chart", "precipitation and evaporation one year")
bar.add("precipitation", attr, v1, is_label_show=True, label_formatter=label_formatter)
bar.render()
```

> 回调函数格式参考自  [series[i]-bar.label.formatter](http://echarts.baidu.com/option.html#series-bar.label.formatter) 。

效果图

![bar-label-formatter-callback](https://user-images.githubusercontent.com/9875406/38666230-07c1aa66-3e71-11e8-9e9f-43fb7d707a64.png)

### Tooltip 示例

举个例子，pyecharts 用户经常会提问 Geo 图中如何在 tooltip 中只显示地图坐标名称和数值，不显示经纬度。

像这样

```python
def test_geo_shantou_city():
    data = [('澄海区', 30), ('南澳县', 40), ('龙湖区', 50), ('金平区', 60)]
    geo = Geo("汕头市地图示例", **style.init_style)
    attr, value = geo.cast(data)
    geo.add(
        "",
        attr,
        value,
        maptype="汕头",
        is_visualmap=True,
        is_legend_show=False,
        label_emphasis_textsize=15,
        label_emphasis_pos='right',
    )
    geo.render()
```
得到

![](https://user-images.githubusercontent.com/19553554/39248236-186a50ae-48ce-11e8-84eb-e58ba17eca5c.png)

而现在，你可以这么操作，先定义一个 `geo_formatter` 函数

```python
def geo_formatter(params):
    return params.name + ' : ' + params.value[2]

def test_geo_shantou_city():
    data = [('澄海区', 30), ('南澳县', 40), ('龙湖区', 50), ('金平区', 60)]
    geo = Geo("汕头市地图示例", **style.init_style)
    attr, value = geo.cast(data)
    geo.add(
        "",
        attr,
        value,
        maptype="汕头",
        is_visualmap=True,
        is_legend_show=False,
        tooltip_formatter=geo_formatter,    # 重点在这里，将函数直接传递为参数。
        label_emphasis_textsize=15,
        label_emphasis_pos='right',
    )
    geo.render()
```
就可以看到下面的效果了。

![](https://user-images.githubusercontent.com/19553554/39248244-1be6da4a-48ce-11e8-931f-059879c5dcf4.png)

### Label 示例

使用回调函数强制设置浮点数位数

```python
from pyecharts import Bar, Grid
from pyecharts.javascripthon.dom import window


def custom_formatter(params):
    return window.parseFloat(params.value).toFixed(2)


attr = ["aa", "bb", "Diabetes Mellitus Requiring Medication", "d", "e", "fff"]
v1 = [5.12, 20.85, 36.69, 10.10, 75.20, 90.36]
v2 = [10.00, 25.45, 8.23, 60.00, 20.50, 80.00]
bar = Bar("x 轴和 y 轴交换")
bar.add(
    "商家A",
    attr,
    v1,
    is_label_show=True,
    label_pos="right",
    label_formatter=custom_formatter,
)
bar.add(
    "商家B",
    attr,
    v2,
    is_convert=True,
    is_label_show=True,
    label_pos="right",
    label_formatter=custom_formatter,
)
grid = Grid()
grid.add(bar, grid_left="40%")
grid.render()
```
![](https://user-images.githubusercontent.com/19553554/44003191-5c5e7764-9e81-11e8-98f1-757a208ec337.png)
