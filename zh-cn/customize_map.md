> 地图自定义篇：考虑到项目更好的通用性，以及更好可扩展性，所以决定对地图部分提供自定义模式。适用在 pyecharts v0.1.9.7 以后的版本。

> Echarts 官方地图下载地址 [download-map](http://echarts.baidu.com/download-map.html) 已经暂时关闭

## VERSION 0.5.7+

从 v0.5.7 开始，新增了 [echarts-cities-pypkg](https://github.com/pyecharts/echarts-cities-pypkg) 插件，扩展 Geo/Geoline 图的地理坐标数据。可以从指定的国家/地区中检索区域坐标。数据来自 [geonames.org](geonames.org), 总共包含了 [138,398](https://github.com/echarts-maps/echarts-cities-js) 个地区。具体的国家/地区映射表参照 [countries_regions_db.json](https://github.com/pyecharts/pyecharts/blob/master/pyecharts/datasets/countries_regions_db.json)。

安装扩展包

```shell
$ pip install echarts-cities-pypkg
```

## 如何制作自己的地图扩展
