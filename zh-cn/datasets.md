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
}
```

### 提供自定义数据

具体可参考 [pyecharts/geo-region-coords](https://github.com/pyecharts/geo-region-coords)
