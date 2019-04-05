## 地理经纬度坐标

### 原始数据

pyecharts 内置了一些常用的城市地理坐标数据，这些数据保存在 *pyecharts/datasets/city_coordinates.json* 文件中。格式可描述为以下形式：

```
{<name>: [<longitude>, <latitude>]}
```

示例

```json
{
    "阿城": [126.58, 45.32],
    "阿克苏": [80.19, 41.09],
    "阿勒泰": [88.12, 47.50],
    ...
}
```

### 提供自定义数据

具体可参考 [pyecharts/geo-region-coords](https://github.com/pyecharts/geo-region-coords)

### 使用例子

Geo/Geolines:

* `add_coordinate` 用于新增一个自定义城市地理位置的功能。
* `add_coordinate_json`  用于导入自定义地理位置 JSON 文件。

方法接口如下：

```
class Geo:
    add_coordinate(self, name: six.text_type, longitude: float, latitude: float): -> None
    """
    example:
        add_coordinate("某地", 100.0, 20.0)
    """
    
    # v0.5.9+
    add_coordinate_json(self, json_file: six.text_type): -> None
    """
    example:
        add_coordinate_json("my_coords.json")
    """

    # my_coords.json
    """
    {
        "某地": [100.0, 20.0],
        ...
    }
    """
```

整个使用例子如下：

```python
from pyecharts import Geo

data = [('广州', 45), ('漳州', 35), ('A市', 43)]
geo = Geo("全国主要城市空气质量", "data from pm2.5", **style.init_style)
attr, value = geo.cast(data)
geo.add_coordinate('A市', 119.3, 26.08) # 添加 pyecharts 未提供的城市地理坐标
geo.add(
    "全国主要城市空气质量",
    attr,
    value,
    type="effectScatter",
    is_random=True,
    is_visualmap=True,
    is_piecewise=True,
    visual_text_color="#fff",
    pieces=[
        {"min": 0, "max": 13, "label": "0 < x < 13"},
        {"min": 14, "max": 16, "label": "14 < x < 16"},
    ],
    effect_scale=5,
)
geo.render()
```

## 国际城市地理坐标

自 v0.5.7 之后，[echarts-cities-pypkg](https://github.com/pyecharts/echarts-cities-pypkg) 给 pyecharts 补充了 [138,398 个城市地理坐标](https://github.com/echarts-maps/echarts-cities-js)，覆盖了200 多个国家。你可以配合 echarts-countries-pypkg 画地理散点图。

### 安装方法

```
pip install echarts-cities-pypkg
```

### 使用方法

```python
from pyecharts.datasets.coordinates import get_coordinate

coordinate = get_coordinate('Oxford', region="英国")
print(coordinate) # [-1.25596, 51.75222]
```
