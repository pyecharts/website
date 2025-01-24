# 版本日志

### version 2.0.8 - 2025-01-24 (Current)

**Added**
* 增加对于谷歌地图 `GMap` 的兼容，使用方式参考 `AMap`
* 增加对于 Leaflet 地图 `LMap` 的兼容，使用方式参考 `AMap`
* 增加对于 Echarts Stat 统计插件的兼容

**Updated**
* 更新 `Base` 类，增加 `use_echarts_stat` api 用于嵌入 Echarts 统计插件
* `Line` 图支持 `dataset_index` 的配置
* `Calendar` 日历图支持多个图例配置

### version 2.0.7 - 2024-11-03

**Added**
* 增加对于高德地图 `AMap` 的兼容，使用方式参考 `BMap`

**Updated**
* [issue#2362](https://github.com/pyecharts/pyecharts/issues/2362) 更新一些配置的引用位置和方式 `markline`, `markarea` 增加动画配置项
* [issue#2350](https://github.com/pyecharts/pyecharts/issues/2350) 更新 `timeline` 支持 `3D` 图。
* [issue#2385](https://github.com/pyecharts/pyecharts/issues/2385) 支持 `marimo` 渲染 `pyecharts` 图表。
* [issue#2373](https://github.com/pyecharts/pyecharts/issues/2373) 支持 `Page` 使用 `is_embed_js` 参数用于离线可视化
* CI 增加 Python 3.13 的测试，版本兼容 Python 3.13
* `AxisOpts` 增加 `animation_opts` 配置
* `LabelOpts` 增加 `is_value_animation(valueAnimation)` 配置

**Fixed**
* [issue#2361](https://github.com/pyecharts/pyecharts/issues/2361) 修复 `timeline` 的 bug，关联
* 修复 `AnimationOpts` 错误的类型提示

### version 2.0.6 - 2024-06-20
***Add***
* [issue#2325](https://github.com/pyecharts/pyecharts/issues/2325) 增加 RenderSepType 用于执行渲染换行符
* [pr#2338](https://github.com/pyecharts/pyecharts/pull/2338) Migrate the test code from `nose` to `nose2/unittest`
* [pr#2347](https://github.com/pyecharts/pyecharts/pull/2347) 增加 `add_js_events` 实验性 API 添加 JS 操作函数
* [pr#2348](https://github.com/pyecharts/pyecharts/pull/2348) 增加 `Emphasis3DOpts`, `BlurOpts`, `SelectOpts`, `TreeLeavesOpts` 配置项

**Updated**
* [pr#2256](https://github.com/pyecharts/pyecharts/pull/2256) 仪表盘指针配置项 `GaugePointerOpts` 支持设置样式 `itemstyle_opts`
* [pr#2338](https://github.com/pyecharts/pyecharts/pull/2338) 更新 `DataZoomOpts` 配置
* [pr#2338](https://github.com/pyecharts/pyecharts/pull/2338) 更新 `ThreeAxisChart` 配置
* [pr#2347](https://github.com/pyecharts/pyecharts/pull/2347) 更新 `boxplot, custom, effectscatter, funnel, kline, pie, radar` charts configuration.
* [pr#2348](https://github.com/pyecharts/pyecharts/pull/2348) 更新 `bar, boxplot, funnel, heatmap, parallel, pie, tree` charts configuration
* [pr#2345](https://github.com/pyecharts/pyecharts/pull/2345) 更新 series_options.py `(Graph-Label-textBorder)`
* [pr#2350](https://github.com/pyecharts/pyecharts/pull/2350) 更新 Timeline + 3D charts(可能存在部分场景不兼容)
* [pr#22](https://github.com/pyecharts/pyecharts-assets/pull/22) 更新 world.js
* [pr#23](https://github.com/pyecharts/pyecharts-assets/pull/23) 更新 v5 静态资源版本到 Echarts 5.5.0

**Fixed**
* [pr#2286](https://github.com/pyecharts/pyecharts/pull/2286) 修复 VisualMapOpts::out_of_range
* [pr#2338](https://github.com/pyecharts/pyecharts/pull/2338) 修复 BarBackgroundStyleOpts
* [pr#2338](https://github.com/pyecharts/pyecharts/pull/2338) 修复 Timeline + Geo

### version 2.0.5 - 2023-12-04
***Add***
* [issue#2259](https://github.com/pyecharts/pyecharts/issues/2259) 增加 `GeoItem` 用来兼容仅传入经纬度数据的模式
* [issue#2254](https://github.com/pyecharts/pyecharts/issues/2254) 增加对 Numpy 和 Pandas 非原生数据结构作为数据入参的错误提示。

**Updated**
* [issue#2227](https://github.com/pyecharts/pyecharts/issues/2227) 增加部分 `Sunburst` 的配置
* [issue#2263](https://github.com/pyecharts/pyecharts/issues/2263) 所有的图表增加 `Emphasis` 的配置
* [issue#2240](https://github.com/pyecharts/pyecharts/issues/2240) 更新 Radar 图的配置
* [issue#2286](https://github.com/pyecharts/pyecharts/pull/2286) 更新 VisualMapOpts 的配置

**Fixed**
* [issue#2236](https://github.com/pyecharts/pyecharts/issues/2236) 修复 `LegendOpts` 的 `border_width` 在特定配置下导致的样式异常问题
* [issue#2264](https://github.com/pyecharts/pyecharts/issues/2264) 修复 `Grid` 下多个 `DataZoomOpts` 失效的问题
* [issue#2265](https://github.com/pyecharts/pyecharts/issues/2265) 修复 `Sankey` 的配置错误问题

### version 2.0.4 - 2023-08-21
***Add***
* [issue#2219](https://github.com/pyecharts/pyecharts/issues/2219) 【**试验性**】更新 `Geo` 支持 `Pie` 图的配置
* [issue#2096](https://github.com/pyecharts/pyecharts/issues/2096) 增加 `conda-forge` 的 `recipes` 文件 [pull-requests#23709](https://github.com/conda-forge/staged-recipes/pull/23709)

**Updated**
* [issue#2213](https://github.com/pyecharts/pyecharts/issues/2213) 更新 `Kline` 的配置，增加 K 线柱状图宽度的配置
* [issue#2211](https://github.com/pyecharts/pyecharts/issues/2211) 更新 `Graph` 图下,  `GraphNode` 和 `GraphLink` 的配置
* [issue#2194](https://github.com/pyecharts/pyecharts/issues/2194) 更新 `Sankey` 的配置，增加 `EdgeLabel` 的配置与 `LabelOpts` 一致。
* [issue#2176](https://github.com/pyecharts/pyecharts/issues/2176) 更新 `ThemeRiver` 的配置。

### version 2.0.3 - 2023-04-06
***Add***
* [pr#2158](https://github.com/pyecharts/pyecharts/pull/2158) 增加一个渲染配置方式（将 `js` 文件嵌入 `HTML` 文件）by @omixwxm

***Fixed***
* [issue#2144](https://github.com/pyecharts/pyecharts/issues/2144) 修复使用 `timeline` 时 `legend` 选择状态异常
* [issue#2153](https://github.com/pyecharts/pyecharts/issues/2153) 修复 `Grid.visualMap` 的异常
* [issue#2165](https://github.com/pyecharts/pyecharts/issues/2165) 修复 `Line` 图使用 `dataset` 异常的问题

**Updated**
* 代码覆盖率：99%
* [commit#6deda6a](https://github.com/pyecharts/pyecharts/pull/2155/commits/6deda6a9abfe597d7af1c5fcb5e32d327ac73e68) 更新 Map 配置

### version 2.0.2 - 2023-02-28
***Add***
* [issue#2118](https://github.com/pyecharts/pyecharts/issues/2118) `Graph` 图增加参数
* [issue#2125](https://github.com/pyecharts/pyecharts/issues/2125) `Line` 图增加参数

***Fixed***
* [issue#2116](https://github.com/pyecharts/pyecharts/issues/2116) 修复 `Grid.visualMap` 的异常

### version 2.0.1 - 2023-01-08
***Fixed***
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/d7788ba4b56545bbfe92e39516b6842ac39e9837) 修复因为地图底图修改导致 `faker.py` 的地图数据显示异常的问题

### version 2.0.0 - 2023-01-04

***Add***
* [issue#1859](https://github.com/pyecharts/pyecharts/issues/1859) 在`Grid3DOpts`中增加对`option.grid3D.viewControl.alpha`和`beta`的视角控制
* [issue#1825](https://github.com/pyecharts/pyecharts/issues/1825) 新增多个平行坐标系的参数
* [issue#1785](https://github.com/pyecharts/pyecharts/issues/1785) `Boxplot` 新增对 `boxWidth` 的配置支持
* Timeline 新增轴索引设置（通过 `add_schema` 设置 `current_index` 设置 timeline 起始的索引位置）
* [pull#1934](https://github.com/pyecharts/pyecharts/pull/1934) 增加 `DataZoomOpts` 和 `TooltipOpts` 的配置
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/3547c50434400e6bd347204afff56331f27ea767) 增加 `ThreeAxisChart` 和 `Axis3DOpts` 的配置
* [pull#1971](https://github.com/pyecharts/pyecharts/pull/1971) 修复 `MarkLineItem` 缺少 `linestyle_opts` 参数
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#2004](https://github.com/pyecharts/pyecharts/issues/2004) 系列配置项 `ItemStyle` 中添加 `borderRadius` 参数
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#1990](https://github.com/pyecharts/pyecharts/issues/1990) 日历图添加 `Scatter` 模式数据
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/d25cca137b13fdd852bf91d74de816847877bd05) 新增 `Custom` 图形
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/a85711c3114127d866ffac16d27672802d009e81) 新增 `Lines3D` 的图形配置
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/a85711c3114127d866ffac16d27672802d009e81) 增加 3D 图形的 `globe` 配置
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/73a5b11689d9626b61122a58d48e85536800a135) `InitOpts` 增加 `bg_color` 和 `is_fill_bg_color` 用于填充画布颜色。
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/73a5b11689d9626b61122a58d48e85536800a135) `Tab` 增加 `tab_css_opts`, `TabChartGlobalOpts` 用于配置 Tab 相关的 CSS 样式 https://github.com/pyecharts/pyecharts/issues/2076
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/7f5a2eae7cc15b0929a42b0082d7409040e6d382) `Gauge` 新增画图配置
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/84483fd6165db0cf607fb95dd4e431d83f2871fe) 新增 `add_geo_json` API 用于给 `Geo` 和 `Map` 添加自定义 `GeoJson` 数据
* [commit/dev](https://github.com/pyecharts/pyecharts/pull/2104/commits/74c151a371ffb44336a3aea3d624e27535527711) 新增 `GraphGL`
* [commit/dev](https://github.com/pyecharts/pyecharts/pull/2104/commits/aaf8076e6d28787dd16d4219f1e473c3c076eb54) 增加 `GeoRegionsOpts` 用于 `Geo` 配置 `regions` 参数

***Fixed***
* [issue#1794](https://github.com/pyecharts/pyecharts/issues/1794) 修复 `Toolbox` 异常的问题
* [issue#1805](https://github.com/pyecharts/pyecharts/issues/1805) 修复 `Gauge` 的数据标签异常的问题
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#2003](https://github.com/pyecharts/pyecharts/issues/2003) 修复 `Grid` 中添加多个 `Gauge` 异常的问题
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#1994](https://github.com/pyecharts/pyecharts/issues/1994) 修复 `Bar` 图在 `Timeline` 中无法使用 `add_dataset` 方法
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#1974](https://github.com/pyecharts/pyecharts/issues/1974) 修复 `logBase` 刻度轴异常的问题
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#1946](https://github.com/pyecharts/pyecharts/issues/1946) 修复 `Timeline` 中使用 `Toolbox` 异常的问题
* [pull#1978](https://github.com/pyecharts/pyecharts/pull/1978) 修复颜色添加异常的问题 @jackzhenguo
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#1871](https://github.com/pyecharts/pyecharts/issues/1871) 修复 `Timeline` 中使用多个 `Radar` 图异常的问题
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/d25cca137b13fdd852bf91d74de816847877bd05) 修复 `add_dataset` 在特定场景下异常的问题
* [issue#2075](https://github.com/pyecharts/pyecharts/issues/2075) 修复 `Grid` 无法正常添加多个 `Radar` 图的问题
* [issue#2059](https://github.com/pyecharts/pyecharts/issues/2059) 修复 `animationOpts` 无法使用字典配置 https://github.com/pyecharts/pyecharts/commit/8129d79120c9222a598a9fa3fd8cf6a50eb8b6ce
* [issue#2051](https://github.com/pyecharts/pyecharts/issues/2051) 修复湖南省的底图。
* [commit/assets](https://github.com/pyecharts/pyecharts-assets/commit/5b95f0b0fbfd641b7cd74e6f597354df1abcbb6c) 更新中国地图底图（符合地图使用规范）; 更新湖南省的底图

***Updated***
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/d25cca137b13fdd852bf91d74de816847877bd05) [commit/dev](https://github.com/pyecharts/pyecharts/commit/a85711c3114127d866ffac16d27672802d009e81) 更新部分配置项的参数
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/a85711c3114127d866ffac16d27672802d009e81) 更新大量的单元测试代码（目前单元测试覆盖率达到 99%）
* [commit/dev](https://github.com/pyecharts/pyecharts/pull/2104/commits/73d56348de063b3135687f23c876a47dcc7ccd73) Make CI Remove Python 3.6
* [commit/dev](https://github.com/pyecharts/pyecharts/pull/2104/commits/29a6c4249bce6dea209e81f58065f9e8486a9beb) Make CI Support Python 3.11
* [commit/dev](https://github.com/pyecharts/pyecharts/pull/2104/commits/4d0edd9f8c1fd667c03b3fd575ffa759a89f311e) `Geo / BMap` 图支持 `scatterGL`, `flowGL`, `linesGL`

### version 1.9.0 - 2020-10-29 (Current)

***Add***
* [pr#1737](https://github.com/pyecharts/pyecharts/pull/1737) 新增部分图的 `ChartItem` 配置（已移除 `warning` 提示）
* [pr#1737](https://github.com/pyecharts/pyecharts/pull/1726) 新增 `MarkLineItem` 的 `xcoord` 和 `ycoord` 配置项

***Updated***
* [pr#1724](https://github.com/pyecharts/pyecharts/pull/1724) 更新 `Geo` 和 `Map` 的配置项
* [pr#1694](https://github.com/pyecharts/pyecharts/pull/1694) 更新 `Echarts` 为 `Apache Echarts`
* [pr#1691](https://github.com/pyecharts/pyecharts/pull/1691) 更新 `README.md`
* [pr#1661](https://github.com/pyecharts/pyecharts/pull/1661) 更新 `Timeline` 图的 style 配置项
* [pr#1660](https://github.com/pyecharts/pyecharts/pull/1660) 更新 `Pie` 图的 `LabelLine` 配置项

### version 1.8.1 - 2020-06-10

***Add***
* [pr#1642](https://github.com/pyecharts/pyecharts/pull/1642) 更新 `Geo/Map` 的地区图映射关系(新增多个地区图)
* [pr#1641](https://github.com/pyecharts/pyecharts/pull/1641) 新增多个国家地图 js 文件。

### version 1.8.0 - 2020-06-07

***Add***
* [pr#1578](https://github.com/pyecharts/pyecharts/pull/1578) 地图 `maptype` 新增 `world_china_provinces`，在世界地图中显示中国的省份。
* [pr#1578](https://github.com/pyecharts/pyecharts/pull/1578) `PictorialBar` 新增 `encode` 参数。
* [pr#1578](https://github.com/pyecharts/pyecharts/pull/1578) `VisualMapOpts` 新增精度的参数 `precision`
* [pr#1578](https://github.com/pyecharts/pyecharts/pull/1578) `TooltipOpts` 新增 position 参数
* [pr#1578](https://github.com/pyecharts/pyecharts/pull/1578) 大部分 Chart 新增对应的 ChartItem 参数（后续会在 `gallery` 进行展示如何使用）
* [pr#1578](https://github.com/pyecharts/pyecharts/pull/1578) `GridOpts` 的参数更新。

***Fixed***
* [pr#1578](https://github.com/pyecharts/pyecharts/pull/1578) 修复 `ToolboxFeature` 中 `ToolBoxFeatureDataZoomOpts` 的 `xaxis_index` 和 `yaxis_index` 的默认值。原默认值均为 None，会导致 `Bar` 图在 stack 模式，出现轴数据展示异常，现修复默认值为 False 解决改问题。

***Updated***
* [pr#1578](https://github.com/pyecharts/pyecharts/pull/1578) 更新 `Bar` 图中 `add_yaxis` 的参数 `yaxis_data` 的参数名，更改为 `y_axis`，为了和其他图保持统一。
* [pr#1578](https://github.com/pyecharts/pyecharts/pull/1578) 更新 `Gauge` 图中的 `detail_label_opts` 和 `title_detail_opts` 的配置项
* [pr#1578](https://github.com/pyecharts/pyecharts/pull/1578) 更新 `Liquid` 图中的部分参数
* [pr#1580](https://github.com/pyecharts/pyecharts/pull/1580) 更新 README.md 和 LICENSE
* [pr#1602](https://github.com/pyecharts/pyecharts/pull/1602) 更新 `InitOpts` 设置宽度和高度，支持使用百分比进行修改图表的大小。
* 将目前 pyecharts-assets 中的 echarts.min.js 更新至最新版的版本.

### version 1.7.1 - 2020-03-12

***Add***
* [pr#1534](https://github.com/pyecharts/pyecharts/pull/1534) 新增支持 `dataset` 组件（目前的示例代码仅涉及 `Bar`，`Pie`，`Line`，`Scatter` 四种图）

***Updated***
* [pr#1527](https://github.com/pyecharts/pyecharts/pull/1527) 更新 `TreeMap` 的配置和 `example`
* [pr#1528](https://github.com/pyecharts/pyecharts/pull/1527) 更新 `ToolBoxFeatureOpts` 的配置项
* [pr#1536](https://github.com/pyecharts/pyecharts/pull/1536) 更新 `map_filename.json` 让 `Geo`，`Map` 支持 `china-cities` 的图例（即在中国地图下展示所有城市的区域划分）。

***Deleted***
* [pr#1534](https://github.com/pyecharts/pyecharts/pull/1534) 移除 `Sankey` 错误的配置
* [pr#1536](https://github.com/pyecharts/pyecharts/pull/1534) 移除源码的 `Example` 文件夹以及[官方文档](https://pyecharts.org)中的所有 `demo` ；转移至 [pyecharts-gallery](https://pyecharts.gallery.org) 的中进行动态展示，且保留跳转链接直达 `demo` 目录


### version 1.7.0 - 2020-02-28

***Add***
* [pr#1527](https://github.com/pyecharts/pyecharts/pull/1527) 新增两个自定义异常类

***Fixed***
* [pr#1527](https://github.com/pyecharts/pyecharts/pull/1527) 修复 `Geo` 和 `BMap` 图传入与源码坐标数据不存在的地点会导致程序异常的问题（通过参数进行控制是否忽略）
* [pr#1527](https://github.com/pyecharts/pyecharts/pull/1527) 修复 `BMap` 的资源地址被 Chrome 浏览器拦截的问题（HTTP 修改成 HTTPS）

***Updated***
* [pr#1527](https://github.com/pyecharts/pyecharts/pull/1527) 更新 `WordCloud` 词云图对自定义图片的配置，文字样式的配置以及其他功能的配置
* [pr#1527](https://github.com/pyecharts/pyecharts/pull/1527) 更新 `Map3D` 的实现（现在可以支持 `Map3D` 的作图）
* [pr#1491](https://github.com/pyecharts/pyecharts/pull/1491) 更新 `Calendar` 图对年，月，日标签的配置（支持中文设置）

### version 1.6.2 - 2020-01-10

***Add***
* [pr#1477](https://github.com/pyecharts/pyecharts/pull/1477) 新增多个 example (`BMap`, `Gauge`, `Grid`, `Timeline`)

***Fixed***
* [pr#1483](https://github.com/pyecharts/pyecharts/pull/1477) 修复 `Grid` 图无法将 `Geo` 和 `Bar` 一起组合的问题
* [pr#1483](https://github.com/pyecharts/pyecharts/pull/1477) 修复 `Timeline` 图，当 `Bar` 图设置 `reversal` 时无法更新反转后的 `x` 轴的问题

***Updated***

* [pr#1483](https://github.com/pyecharts/pyecharts/pull/1477) 更新相对应的单元测试代码
* [pr#1483](https://github.com/pyecharts/pyecharts/pull/1477) 更新 `Radar` 图的配置，支持 `AngleAxis`，`Polar`(区别于 `Polar` 图), `RadiusAxis` 的配置
* [pr#1483](https://github.com/pyecharts/pyecharts/pull/1477) 更新 `Sankey` 图的配置，支持垂直布局和修改 `Sankey` 图每一层的配置(`levels`)
* [pr#1483](https://github.com/pyecharts/pyecharts/pull/1477) 更新 `tree`, `treemap` 的部分配置
* [pr#1483](https://github.com/pyecharts/pyecharts/pull/1477) 更新 `treemap` 的 `breadcrump` 的配置(`treemap` 下方的层级面包屑框)
* [pr#1477](https://github.com/pyecharts/pyecharts/pull/1477) 更新 `BMap` 对 `custom` 的支持(新增参数在 `GeoChartBase` 中体现)
* [pr#1477](https://github.com/pyecharts/pyecharts/pull/1477) 更新 `Scatter`, `EffectScatter` 对 `symbolRotate`(标记的旋转角度) 的支持 
* [pr#1477](https://github.com/pyecharts/pyecharts/pull/1477) 更新 `Gauge` 对 `radius` 参数的支持
* [pr#1477](https://github.com/pyecharts/pyecharts/pull/1477) 更新 `Timeline` 对 `BMap` 图的支持，以及新增参数调整时间轴控制键的方向 `control_position`
* [pr#1477](https://github.com/pyecharts/pyecharts/pull/1477) 更新 `VisualMapOpts` 对映射控件的一些效果参数的支持

### version 1.6.1 - 2020-01-03

***Add***
* [pr#1470](https://github.com/pyecharts/pyecharts/pull/1470) 通过 CI 和 Appveyor 的测试，支持 Python 3.8
* [pr#1469](https://github.com/pyecharts/pyecharts/pull/1469) 更新 `Graph` 图配置 `Edge` 的 `Option`。
* [pr#1469](https://github.com/pyecharts/pyecharts/pull/1469) 更新 `Line` 图的 `zlevel` 和 `z` 的参数配置
* [pr#1469](https://github.com/pyecharts/pyecharts/pull/1469) 更新 `TitleOpts` 支持一些 `Padding` 和 `Gap` 的配置

***Fixed***
* [pr#1469](https://github.com/pyecharts/pyecharts/pull/1469) 修复 `Timeline` 添加 `GraphicOpts` 无法使用的问题

***Updated***
* [pr#1412](https://github.com/pyecharts/pyecharts/pull/1412) 更新非关键字传参，导致 `delay` 和 `pixel_ratio` 参数作用错位

 
### version 1.6.0 - 2019-11.12

***Add***
* [pr#1371](https://github.com/pyecharts/pyecharts/pull/1371) 新增 gauge 的 title 配置 `title_label_opts`。更新后 `title_label_opts` 是用来控制轮盘内部文本的配置项，`detail_label_opts` 是用来控制轮盘内部数据的配置项。

***Fixed***
* [pr#1367](https://github.com/pyecharts/pyecharts/pull/1367) 更新了 `Geo`，`BMap` 的一些配置项。
* [pr#1404](https://github.com/pyecharts/pyecharts/pull/1404) `Geo` 图的 `ChartType` 为 `Lines` 无法设置弧线上的 `label`。

***Updated***
* [pr#1371](https://github.com/pyecharts/pyecharts/pull/1371) 更新 `Gauge` 的配置将原有的 `label_opts` 修改为 `detail_label_opts`。
* [pr#1374](https://github.com/pyecharts/pyecharts/pull/1374) 更新 `Grid` 图坐标轴的刻度标签的配置。
* [pr#1404](https://github.com/pyecharts/pyecharts/pull/1404) `LegendOpts` 设置图例的 icon，大小，宽度，间隔以及未激活的颜色。
* [pr#1404](https://github.com/pyecharts/pyecharts/pull/1404) `VisualMapOpts` 设置 `itemWidth` 和 `itemHeight` 的设置。


### version 1.5.1 - 2019.9.16

***Add***
* [pr#1324](https://github.com/pyecharts/pyecharts/pulls/1324) 新增 `pyecharts.faker` 包，提供示例数据。
* [pr#1333](https://github.com/pyecharts/pyecharts/pulls/1333) 提供 Jupyter Notebook 插件，提供离线渲染服务。[资源引用](https://pyecharts.org/#/zh-cn/assets_host)

***Fixed***
* [pr#1321](https://github.com/pyecharts/pyecharts/pulls/1321) 修复 Heatmap 无法渲染的问题。


### version 1.5.0 - 2019.9.1

***Add***
* [pr#1302](https://github.com/pyecharts/pyecharts/pulls/1302) 新增 Tab 图形种类。
* [pr#1299](https://github.com/pyecharts/pyecharts/pulls/1299) `render` 函数新增 `**kwargs` 传参方式
* [pr#1314](https://github.com/pyecharts/pyecharts/pulls/1314) Tree 图新增 `is_expand_and_collapse`，`initial_tree_depth:` 参数。

***Updated***
* [pr#1309](https://github.com/pyecharts/pyecharts/pulls/1309) Page 图 resize 后设置为不可拖动和不可重置大小。
* [pr#1308](https://github.com/pyecharts/pyecharts/pulls/1308)，[pr#1313](https://github.com/pyecharts/pyecharts/pulls/1313) 重构模板，使 Image/Tabel 类兼容 Page/Tab，且 Image/Table 类不能多次执行 add 方法，如若需要展示多个 Image/Table 请使用 Page。

***Fixed***
* [pr#1293](https://github.com/pyecharts/pyecharts/pulls/1293) 修复 Page 图 `save_resize_html` 传递 cfg_file 参数时出错的 BUG。
* [pr#1295](https://github.com/pyecharts/pyecharts/pulls/1295) 修复 Page 图 label 颜色修改无效的 BUG.


### version 1.4.0 - 2019.8.15

***Add***
* [issue#1275](https://github.com/pyecharts/pyecharts/issues/1275) 新增对 Timeline 图支持多 X 轴的支持。
* [pr#1260](https://github.com/pyecharts/pyecharts/pulls/1260) 新增对 Timeline 图 graphic_opts 的支持。
* [pr#1273](https://github.com/pyecharts/pyecharts/pulls/1273) 新增对 Polar 图 label 配置项的支持以及 Page 图新增 `DraggablePageLayout` 布局。
* [pr#1273](https://github.com/pyecharts/pyecharts/pulls/1273) Geo 图坐标支持模糊匹配。

***Fixed***
* [pr#1271](https://github.com/pyecharts/pyecharts/pulls/1271) 修复 `dump_options` 出现不规则字符的问题，并新增 `dump_options_with_quotes` 方法。
* [pr#1272](https://github.com/pyecharts/pyecharts/pulls/1272) 修复 Page 渲染错误的问题。


### version 1.3.1 - 2019.7.15

***Add***
* [pr#1253](https://github.com/pyecharts/pyecharts/pulls/1253) `emphasis_itemstyle_opts` 新增 `area_color` 参数，用于设置区域颜色。

***Fixed***
* [pr#1252](https://github.com/pyecharts/pyecharts/pulls/1252) 修复 jshost 失效导致图形无法渲染的 bug。


### version 1.3.0 - 2019.7.13

***Add***
* [pr#1213](https://github.com/pyecharts/pyecharts/pulls/1213) 新增 3D 地图
* [pr#1215](https://github.com/pyecharts/pyecharts/pulls/1215) [issue#726](https://github.com/pyecharts/pyecharts/issues/726) 支持 Zeppelin 和 Nteract Notebook 环境
* [pr#1231](https://github.com/pyecharts/pyecharts/pulls/1212) 新增 `AnimationsOpts` 配置项

***Updated***
* [pr#1223](https://github.com/pyecharts/pyecharts/pulls/1223) 更新 `AngleAxisOpts` 参数

***Fixed***
* [pr#1216](https://github.com/pyecharts/pyecharts/pull/1216) 修复 `dump_options` 方法不能正确处理 Nan 值的问题
* [pr#1212](https://github.com/pyecharts/pyecharts/pulls/1212) [issue#1210](https://github.com/pyecharts/pyecharts/issues/1210) 修复 Chart 初始化不能使用 dict 传参的问题


### version 1.2.1 - 2019.6.19

***Add***
* [pr#1175](https://github.com/pyecharts/pyecharts/pulls/1175)，[pr#1168](https://github.com/pyecharts/pyecharts/pulls/1168) 新增图表示例
* [pr#1169](https://github.com/pyecharts/pyecharts/pulls/1169) `Geo` 图新增 `zoom`，`center` 参数
* [pr#1180](https://github.com/pyecharts/pyecharts/pulls/1180) `Map` 图新增 `emphasis_label_opts`，`emphasis_itemstyle_opts` 参数
* [pr#1203](https://github.com/pyecharts/pyecharts/pulls/1203) `Parallel` 图新增 `is_smooth` 参数
* [issue#1197](https://github.com/pyecharts/pyecharts/issues/1197) `Polar` 图新增 `axistick_opts` 参数

***Updated***
* [pr#1184](https://github.com/pyecharts/pyecharts/pulls/1184) `init_opts` 支持 dict 传参
* [pr#1186](https://github.com/pyecharts/pyecharts/pulls/1186) 重构 Typehints，将 `types module` 移动至根目录

***Fixed***
* [pr#1188](https://github.com/pyecharts/pyecharts/pull/1188) 修复 `dump_options` 方法不能正确转义的问题


### version 1.2.0 - 2019.6.1

***Add***
* [issue#1155](https://github.com/pyecharts/pyecharts/issues/1155) 新增 PictorialBar 图表类型
* [issue#1126](https://github.com/pyecharts/pyecharts/issues/1126) 完善 Components 类，提供 Table/Image 类
* [issue#1160](https://github.com/pyecharts/pyecharts/issues/1160) Page 类支持简单排版功能
* [issue#1163](https://github.com/pyecharts/pyecharts/issues/1163) 新增 Graphic 组件配置项
* [issue#1157](https://github.com/pyecharts/pyecharts/issues/1157) Gauge 新增 `label_opts` 以及 `split_number` 配置项
* [issue#1136](https://github.com/pyecharts/pyecharts/issues/1136) Line 新增 `is_connect_nones` 提供断点连接功能
* [issue#1118](https://github.com/pyecharts/pyecharts/issues/1118) Markline 新增 `linestyle_opts` 配置项
* [issue#1144](https://github.com/pyecharts/pyecharts/issues/1144) Markpint 新增 `itemstyle_opts` 配置项

***Updated***
* [issue#1115](https://github.com/pyecharts/pyecharts/issues/1115) Scatter 图更新接收数据类型格式，支持多维度数据
* [issue#1159](https://github.com/pyecharts/pyecharts/issues/1159) Echarts 版本从 4.1.0 更新至 4.2.1

***Fixed***
* [issue#1139](https://github.com/pyecharts/pyecharts/issues/1139)，[issue#1119](https://github.com/pyecharts/pyecharts/issues/1119) 提供 `is_control_axis_index` 参数，修复 Overlap+Grid 叠加时坐标轴索引混乱的问题
* [issue#1149](https://github.com/pyecharts/pyecharts/issues/1149) 修复 Page 中 js_host 与全局 CurrentConfig.ONLINE_HOST 表现不一致的问题
* [issue#1131](https://github.com/pyecharts/pyecharts/issues/1131) 修复 set_global_opts 和 add_xaxis 方法顺序不一致表现不同的问题
* [issue#1161](https://github.com/pyecharts/pyecharts/issues/1161) 修复 DataZoomOpts 不允许传入非 Sequence 类型的问题


### version 1.1.0 - 2019.5.14

***Add***
* [issue#1052](https://github.com/pyecharts/pyecharts/issues/1052)，[issue#1065](https://github.com/pyecharts/pyecharts/issues/1065) 新增 BMap 图形种类
* [issue#1078](https://github.com/pyecharts/pyecharts/issues/1078)，[issue#396](https://github.com/pyecharts/pyecharts/issues/396) 新增 Sunburst 图形种类
* [issue#1112](https://github.com/pyecharts/pyecharts/issues/1112) Page 类新增 render_embed 方法

***Updated***
* [pr#1036](https://github.com/pyecharts/pyecharts/pull/1036) LabelOpts 支持富文本标签及其他参数的更新
* [pr#1038](https://github.com/pyecharts/pyecharts/pull/731) 新增多个配置项参数
* [issue#1043](https://github.com/pyecharts/pyecharts/issues/1043) LabelOpts 新增文本参数
* [issue#1051](https://github.com/pyecharts/pyecharts/issues/1051) Timeline 新增多个参数

***Fixed***
* [issue#1034](https://github.com/pyecharts/pyecharts/issues/1034) 解决了 Gauge 颜色设置问题 
* [issue#873](https://github.com/pyecharts/pyecharts/issues/873), [issue#870](https://github.com/pyecharts/pyecharts/issues/870) 解决了多条 Y 轴会出现重复的问题(增加了 Y 轴 offset 参数)
* [pr#1038](https://github.com/pyecharts/pyecharts/pull/731)，[issue#1067](https://github.com/pyecharts/pyecharts/issues/1067)，[issue#1048](https://github.com/pyecharts/pyecharts/issues/1048) 修复换行符全局替换的 bug
* [issue#1043](https://github.com/pyecharts/pyecharts/issues/1043) 修复 add_schema 方法没有 return self 导致无法 render 的情况
* [issue#1044](https://github.com/pyecharts/pyecharts/issues/1044) 修复 Table.render 方法无法正常运行的问题
* [issue#1047](https://github.com/pyecharts/pyecharts/issues/1047) 修复 worldcloud_example 文件名错别字
* [issue#1051](https://github.com/pyecharts/pyecharts/issues/1051) 修复 Timeline 图无法添加多个 visualMap


### version 1.0.0 - 2019.4.28

***Updated***
* 全新版本的 pyecharts，详见 [v1.0.0 发布日志](zh-cn/release-note/v100)


### version 0.5.11 - 2018.9.9
    
***Added***
* [issue#731](https://github.com/pyecharts/pyecharts/issues/731) 新增 `mark_point_raw`, `mark_line_raw` 配置项用于个性化展示标记。
    
***Fixed***
* [issue#738](https://github.com/pyecharts/pyecharts/issues/738) 支持设置 Grid, Overlay 和 Timeline 某选项为空 (null)

***Removed***
* 移除 pillow 作为默认依赖，需要用到 Scatter.draw 方法的开发者请先自行安装 pillow。


### version 0.5.10 - 2018.9.4

***Added***
* [issue#699](https://github.com/pyecharts/pyecharts/issues/699) 为漏斗图新增 `funnel_sort` 和 `funnel_gap` 分别用于控制漏斗图的排序方式和数据图形间隔。
* [issue#703](https://github.com/pyecharts/pyecharts/issues/703) 支持设置 Echarts 某选项为空 (null)
* [issue#720](https://github.com/pyecharts/pyecharts/issues/720) 新增 3D 曲面图图形种类。

***Fixed***
* [issue#715](https://github.com/pyecharts/pyecharts/issues/715) 修复 online() 方法不生效的 bug

***Updated***
* [issue#702](https://github.com/pyecharts/pyecharts/issues/702) Toobox 选项标签文本更改为更通用的英语。

***Removed***
* 停止对 Python3.4 版本的支持和维护。


### version 0.5.9 - 2018.8.26

***Added***
* [pr#685](https://github.com/pyecharts/pyecharts/pull/685) 图表方法(`use_theme`/`config`/`add`)支持链式调用
* [pr#690](https://github.com/pyecharts/pyecharts/pull/690) Radar 新增 `set_radar_component` 方法，废弃 `config` 方法；Parallel 图新增 `set_schema` 方法，废弃 `confg` 方法
* [issue#687](https://github.com/pyecharts/pyecharts/issues/687) 新增 `add_coordinate_json` 方法用于支持导入 Geo/Geolines 坐标数据
* [issue#691](https://github.com/pyecharts/pyecharts/issues/691) 为每种图形新增 `is_animation` 初始化参数，用于控制是否显示动画。
* 新增 [geo-region-coords](https://github.com/pyecharts/geo-region-coords) 辅助项目，提供中国地区坐标查询。

***Updated***
* [issue#678](https://github.com/pyecharts/pyecharts/issues/678) 将 `extra_html_text_label` 默认位置移动到图形顶部。
* [pr#677](https://github.com/pyecharts/pyecharts/pull/677) 重构 Polar，更正错误参数。


### version 0.5.8 - 2018.8.13

***Added***
* [issue#655](https://github.com/pyecharts/pyecharts/issues/655) 新增多个自定义主题：westeros, wonderland, chalk, halloween, essos，walden, romantic and purple-passion
* [issue#669](https://github.com/pyecharts/pyecharts/issues/669) 新增 Tree 图形种类。
* Polar 图新增 `angleaxis_label_interval` 参数，用于控制坐标轴刻度标签的显示间隔，在类目轴中有效。


### version 0.5.7 - 2018.8.11

***Added***
* [issue#651](https://github.com/pyecharts/pyecharts/issues/651) Scatter 图新增 `extra_name` 参数，额外的数据项的名称，可以为每个数据点指定一个名称。
* [issue#657](https://github.com/pyecharts/pyecharts/issues/657) 基本图形新增 `extra_html_text_label` 参数用于显示额外的文本标签，仅限于在单图形或者 Page 时使用。
* [issue#660](https://github.com/pyecharts/pyecharts/issues/660) 为 X/Y 坐标轴新增 `xaxis_line_color`, `xaxis_line_width`, `yaxis_line_color`, `yaxis_line_width` 四个参数，用于控制其坐标轴线线的颜色以及宽度。
* [pr#663](https://github.com/pyecharts/pyecharts/pull/663) 新增 `coordinate_region` 参数用于指定国家/地区检索坐标且提供了 echarts-cities-pypkg 为可选的地理数据扩展。引入来自 [geonames.org](http://geonames.org/) 的 138,398 个城市坐标。


### version 0.5.6 - 2018.7.28

***Fixed***
* [issue#452](https://github.com/pyecharts/pyecharts/issues/452) 修复 K 线图不能显示 tooltip【open, close, lowest, highest】的 bug
* [issue#639](https://github.com/pyecharts/pyecharts/issues/639) 修复 Line 图当 X 轴的类型设置为 'value' 的时候，X、Y 轴均显示 Y 轴数据的 bug
* [issue#636](https://github.com/pyecharts/pyecharts/issues/636) 修复 Geo/Geoline 图坐标地点名替换 Legend 的 bug

***Updated***
* 修正参数拼写，将 `tooltip_tragger`, `tooltip_tragger_on` 修正为 `tooltip_trigger`, `tooltip_trigger_on`
* 更新 echarts 及附属 js 文件版本 echarts 4.0.4 -> 4.1.0，echarts-gl 1.1.0 -> 1.1.1，echarts-liquidfill 2.0.0 -> 2.0.1
* [issue#634](https://github.com/pyecharts/pyecharts/issues/634) 新增 `is_datazoom_extra_show`, `datazoom_extra_type`, `datazoom_extra_range`, `datazoom_extra_orient`, `datazoom_extra_xaxis_index`, `datazoom_extra_yaxis_index` 参数用于设置额外的 dataZoom 控制条，可将效果同时作用于 X、Y 轴


### version 0.5.5 - 2018.05.17

***Added***
* [issue#565](https://github.com/pyecharts/pyecharts/issues/565) Geolines 图数据项可以新增数值维度
* [issue#573](https://github.com/pyecharts/pyecharts/issues/573) 新增对 jupyter notebook 家族的新成员 [nteract](https://nteract.io/) 的支持

***Fixed***
* [issue#572](https://github.com/pyecharts/pyecharts/issues/572) 修复 HeatMap 图纵坐标显示索引值，而非 data 值的 bug


### version 0.5.4 - 2018.05.15

***Updated***
* 重构 `Page` 类，新增图表命名名称引用。

***Fixed***
* [issue#555](https://github.com/pyecharts/pyecharts/issues/555) 修复 v0.5.3 Polar 图不能显示的 bug
* [issue#541](https://github.com/pyecharts/pyecharts/issues/541) 修复 v0.5.3 Django + pyecharts 不能正常导入的 bug


### version 0.5.3 - 2018.05.10

***Fixed***
* [issue#544](https://github.com/pyecharts/pyecharts/issues/544) 修复 v0.5.2 主题颜色默认颜色配置与前版本有差别太大的 bug


### version 0.5.2 - 2018.05.04

***Added***
* [issue#512](https://github.com/pyecharts/pyecharts/issues/512) 新增自定义主题功能


### version 0.5.1 - 2018.05.02

***Fixed***
* [issue#516](https://github.com/pyecharts/pyecharts/issues/516) 修复直角坐标系图 X 轴分隔符展示效果不一致的 bug

***Update***
* [issue#518](https://github.com/pyecharts/pyecharts/issues/518) 放弃 sdist 构建方式，使用 wheel 构建项目包，并在 PYPI 上为项目添加 description


### version 0.5.0 - 2018.04.28

***Added***
* [issue#311](https://github.com/pyecharts/pyecharts/issues/311) 提供 Jupyter Notebook 导出为 PDF 没有图片的解决方案
* 新增对 JavaScript 回调函数配置项和事件绑定的支持。详细内容请移步至 [release-note/v050](zh-cn/release-note/v050)。

***Fixed***
* [issue#448](https://github.com/pyecharts/pyecharts/issues/448) 修复 Timeline 中 Overlap 图的 label_color 配置项不生效的 bug
* [issue#504](https://github.com/pyecharts/pyecharts/issues/504) 修复 markpoint 标记点标注不显示的 bug

***Updated***
* 重构底层 `option.py` 配置项代码，使其更加具有`面向对象`特征，相关文件转移至新 package echarts。
* 将地图数据及接口转移至 'pyecharts.datasets' 包，更多内容请参考 [地理地图数据](zh-cn/datasets)。
* `pyecharts.Geo` 和 `pyecharts.GeoLines` 新增 `add_coordinate` 方法用于新增一个自定义城市地理位置的功能。


### version 0.4.1 - 2018.03.13

***Fixed***
* [issue#437](https://github.com/pyecharts/pyecharts/issues/437) 修复 Timeline 图累计多个 Bar 图会导致条形宽度压缩的 bug
* [issue#437](https://github.com/pyecharts/pyecharts/issues/437) 修复 Timeline 图不能正常显示 Tooltip 组件的 bug


### version 0.4.0 - 2018.03.09

***Added***
* `EchartsEnvironment` 类性增 `render_chart_to_file`
* [issue#425](https://github.com/pyecharts/pyecharts/issues/425) 新增 `pieces` 配置项，为 visualMap 组件提供自定义分段标签的功能
* 新增 `tooltip_border_width`, `tooltip_border_color`, `tooltip_background_color` 三个参数用与提示框背景颜色及边框的配置
* [issue#376](https://github.com/pyecharts/pyecharts/issues/376) 新增 `mark_line_coords` 配置项用于指定标记线的起点和终点
* [issue#431](https://github.com/pyecharts/pyecharts/issues/431) pyecharts.Chart 图表类新增 renderer 参数，用于指定渲染方式，支持 canvas / svg 两种方式

***Updated***
* 更新 jupyter-echarts 至 1.4.0: echarts 3.6.2 -> 4.0.4, echarts-gl 1.0.0-b4 -> 1.1.0, echarts-liquidfill 1.0.5 -> 2.0.0, echarts-wordcloud 1.1.0 -> 1.1.2
* 优化内部渲染逻辑，提高渲染效率。

***Fixed***
* 修正 width / height 在 Jupyter Notebook 渲染错误的 Bug
* [issue#432](https://github.com/pyecharts/pyecharts/issues/432) 修复水球图和词云图不能指定 Toolbox 等选项的 Bug


### version 0.3.3 - 2018.03.01

***Added***
* 防止将来的依赖包影响 v0.3.2 的功能: lml==0.0.2, jupyter-echarts-pypkg==0.0.11
* 新增 `name_map`， [允许用户采用自己地图名称](http://echarts.baidu.com/option.html#series-map.nameMap)。

***Changed***
* `Chart.render_embed` 返回 `jinja2.Markup` 实例
* `Base.show_config` 重命名为 `Base.print_echarts_options`
* 移除 `EchartsEnvironment.configure_pyecharts` 方法


### version 0.3.2 - 2018.02.26

从此版本开始，将不再自带地图 js 文件。有需要的开发人员，请自选安装。

***Added***
* 新增 `chart_id` 配置项，可设置图形 id，对应为每个图在 html 中的 div#id
* 新增 jupyter-echarts-pypkg, echarts-china-provinces-pypkg, echarts-china-cities-pypkg 和 echarts-countries-pypkg。第一个是自带安装，后三个是可选安装。
* [issue#395](https://github.com/pyecharts/pyecharts/issues/395) 新增 `is_splitline_show` 配置项，用于控制是否显示网格线
* 新增 AppVeyor CI，为 Windows OS 提供测试功能

***Fixed***
* [issue#322](https://github.com/pyecharts/pyecharts/issues/322) 修复在 timeline 中不能设置多个 legend 的 bug
* [issue#357](https://github.com/pyecharts/pyecharts/issues/357) 修复 Line 图 symbol 大小不能调整的 bug
* [issue#371](https://github.com/pyecharts/pyecharts/issues/371) 修复 Parallel 图 Line 样式失效的 bug
* [issue#378](https://github.com/pyecharts/pyecharts/issues/378) 修复 Geo 图中当多次 render 时相同 value 值会被叠加的 bug
* [issue#338](https://github.com/pyecharts/pyecharts/issues/338) 修复 timeline 中 map 的 visualmap 组件不能正常显示的 bug

***Updated***
* 地图更新：[台湾地图补了市，县，岛](https://github.com/pyecharts/pyecharts/pull/316), [重庆地图补了开州区](https://github.com/pyecharts/pyecharts/pull/317)
* 优化图表 API，图表 js_dependencies 属性返回有序列表
* 优化部分代码逻辑
* [issue#377](https://github.com/pyecharts/pyecharts/issues/377) 为 Kline 提供 Candlestick 别名

***Changed***
* 示例移到新的代码仓库 [pyecharts-users-cases](https://github.com/pyecharts/pyecharts-users-cases)

***Removed***
* [PR#368](https://github.com/pyecharts/pyecharts/pull/368) `pyecharts/templates/js` 被删去了。`jupyter-echarts` 不再内嵌于 pyecharts 。
* echarts-china-cities-js 和 echarts-countries-js 不再是必选，而是可选图库。


### version 0.3.1 - 2017.12.13

***Fixed***
* [issue#290](https://github.com/pyecharts/pyecharts/issues/290) 紧急修复 v0.3.0 版本不能正常显示图形的严重 bug
* [issue#296](https://github.com/pyecharts/pyecharts/issues/296) 修复 Timeline 不能在 notebook 中显示的 bug


### version 0.3.0 - 2017.12.11

***Added***
* 图表 `render` 方法增加 `template_name` 、`object_name`、`extra_context` 等参数，全面支持自定义模板
* 新增统一配置函数 `pyecharts.configure` ，支持设置模板目录，JS 文件仓库路径。
* [issue#252](https://github.com/pyecharts/pyecharts/issues/252) 新增 `xaxis_label_textsize`, `xaxis_label_textcolor`, `yaxis_label_textsize`,`yaxis_label_textcolor` 四个参数修改坐标轴标签的字体和颜色
* [issue#258](https://github.com/pyecharts/pyecharts/issues/258) 新增 `mark_point_valuedim` 参数，并将 `mark_line_valuedim` 和 `mark_point_valuedim` 参数类型修改为list。
* [issue#260](https://github.com/pyecharts/pyecharts/issues/260) 新增 `is_toolbox_show` 参数用于控制是否显示右侧实用工具箱。

***Updated***
* 重写底层逻辑，支持在模板文件中使用 `echarts_*` 系列模板函数
* js 依赖文件支持外部链接方式引入。
* `pyecharts.custom.Page` 类实现 `list` 协议，支持迭代、索引、添加、扩展等操作。
* 图表 width 和 height 支持 '50%' 、'78px' 等其他 css 有效长度形式。
* 更新 jupyter-echarts 至 1.3.3: [上海地图补了崇明区](https://github.com/pyecharts/jupyter-echarts/issues/9), [西藏地图补了山南市](https://github.com/pyecharts/jupyter-echarts/issues/7)


### version 0.2.7 - 2017.10.27

***Added***
* 新增 GeoLines（地理坐标系线图）
* [issue#230](https://github.com/pyecharts/pyecharts/issues/230) 新增工具类 `Style`，用于简化代码编写和统一风格

***Changed***
* [issue#232](https://github.com/pyecharts/pyecharts/issues/232) Grid, Overlap, Timeline 类初始化参数的变动

***Fixed***
* 修复 Geo 系列名无法正常显示的问题
* [issue#229](https://github.com/pyecharts/pyecharts/issues/229) 修复水球图不能自定义图形的问题


### version 0.2.6 - 2017.10.14

***Added***
* 为 [文档](https://github.com/pyecharts/pyecharts/blob/master/docs/zh-cn/documentation.md) 新增 [使用技巧](https://github.com/pyecharts/pyecharts/blob/master/docszh-cn/documentation.md#使用技巧) 介绍
* [issue#194](https://github.com/pyecharts/pyecharts/issues/194) 新增 `is_map_symbol_show` 参数，用于控制 Map 图 [红点的显示](https://www.oschina.net/question1416804_245423)
* [issue#192](https://github.com/pyecharts/pyecharts/issues/192) 新增 `label_emphasis_pos`, `label_emphasis_textsize`, `label_emphasis_textcolor` 参数，用于解决 Geo图 tooltip 不能只显示城市名和数值的问题
* [issue#132](https://github.com/pyecharts/pyecharts/issues/132) 新增图形类型树图
* [issue#181](https://github.com/pyecharts/pyecharts/issues/181) 为 Geo 图新增 `is_roam` 参数解决不能缩放和移动的问题
* [issue#199](https://github.com/pyecharts/pyecharts/issues/199) 为 markLine 新增 `mark_line_symbolsize` 和 `mark_line_valuedim` 参数，解决不能指定维度以及标记大小不能整的问题
* [issue#200](https://github.com/pyecharts/pyecharts/issues/200) 为 xyAxis 通用配置项新增 `is_xaxis_show` 和 `is_yaxis_show` 参数，（控制是否显示 x 轴或 y 轴）解决设计编辑文本的问题
* [issue#201](https://github.com/pyecharts/pyecharts/issues/201) 为 Bar 图新增 `bar_category_gap` 参数，提供绘制直方图的方案
* [issue#208](https://github.com/pyecharts/pyecharts/issues/208) 为 dataZoom 通用配置项 `datazoom_type` 新增类型 'both'（同时拥有 'slider' 以及 'inside')
* [issue#208](https://github.com/pyecharts/pyecharts/issues/208) 为 HeatMap 图新增 **日历热力图**

***Changed***
* 将 label 通用配置项的 `is_emphasis` 参数更改为 `is_label_emphasis`
* show_config() 修改用 JSON 显示

***Fixed***
* [issue#195](https://github.com/pyecharts/pyecharts/issues/195) 修复 HeatMap 图配置 x、y 轴属性无效的问题


### version 0.2.5 - 2017.9.28

***Added***
* [issue#173](https://github.com/pyecharts/pyecharts/issues/173) 为 xyAxis 通用配置项新增 `is_xaxis_boundarygap` 和 `is_yaxis_boundartgap` 参数
* [issue#22](https://github.com/pyecharts/pyecharts/issues/22) 为散点图新增 `extra_data` 参数，可以为数据新增除 x y 轴外的其他维度
* 为 markPoint 新增自定义标记点功能
* 为 visualMap 新增 `visual_dimension` 参数，可以指定 visualmap 映射到哪个数据维度
* 为 Map 图新增 [212个国家和地区](https://github.com/pyecharts/echarts-countries-js#featuring-citiesor-for-single-download)
* 部分解决 Overlap 和 Grid 不能一起使用的问题（当 Overlap 为多 x 轴或多 y 轴的时候坐标轴索引仍会出现问题）


### version 0.2.4 - 2017.9.8

***Added***
* [issue#148](https://github.com/pyecharts/pyecharts/issues/148) 为 Radar.config() 新增 `legend_text_size` 参数
* [issue#148](https://github.com/pyecharts/pyecharts/issues/148) 为 Legend 通用配置项新增 `legend_text_color` 和 `legend_text_font` 参数
* [issue#156](https://github.com/pyecharts/pyecharts/issues/156) 为 xyAxis 通用配置项新增 `xaxis_force_interval` 和 `yaxis_force_interval` 参数
* 为 Visualmap 通用配置项新增 `is_piecewise` 和 `visual_split_number` 参数
* [issue#160](https://github.com/pyecharts/pyecharts/issues/160) 为 Base 类新增 `page_title` 参数，初始化类实例的时候可指定生成的 html 文件 `<title>` 标签的值。自定义类Grid/Overlap/Timeline/Page 以第一个添加的实例的 `page_title` 参数为准。
* [issue#165](https://github.com/pyecharts/pyecharts/issues/165) 为 Radar 图新增 `label` 通用配置项，现可以展示 `label` 文字标签，但是建议在数据量少的时候使用（比如数据量为 1 的时候）

***Changed***
* 压缩 js 文件体积，总体体积减少约 0.3MB

***Fixed***
* [issue#158](https://github.com/pyecharts/pyecharts/issues/158) 修复 Grid/Timeline/Overlap 在 Page 中不能正常使用的 bug


### version 0.2.3 - 2017.9.1

***Fixed***
* [issue#143](https://github.com/pyecharts/pyecharts/issues/143) [issue#146](https://github.com/pyecharts/pyecharts/issues/146) 修复默认状态下 Graph 不显示连线的 bug
* [issue#145](https://github.com/pyecharts/pyecharts/issues/145) 修复 dataZoom 无法正常使用的 bug


### version 0.2.2 - 2017.8.31
***Added***
* Map 图和 Geo 图增加 [363个二线城市地图](https://github.com/pyecharts/echarts-china-cities-js#featuring-citiesor-for-single-download)
* Map 图新增 label 模块，现可以利用标签显示地区名称
* Geo 图新增 3000+ 城市地区经纬度信息，现已基本覆盖全国各个地区
* Geo 图新增 `geo_cities_coords` 参数，用户可以为自己所选地图提供地区经纬度坐标（这将会覆盖原来预存的城市坐标信息），即完全按照用户提供的坐标来定位。
* 新增图形种类 ThemeRiver（主题河流图）
* 新增 `is_more_utils` 参数，在 `add()` 中设置该标志位为 True 则会提供更多的实用工具按钮（建议在 Line, Kilne, Bar 等直角坐标图形中设置）。默认只提供『数据视图』和『下载』按钮。
* [issue#138](https://github.com/pyecharts/pyecharts/issues/138) 新增 `is_xaxis_inverse`, `is_yaxis_inverse`, `xaxis_pos`, `yaxis_pos` 参数，提供倒映直角坐标系功能
* [issue#140](https://github.com/pyecharts/pyecharts/issues/140) 为每种图形（包括 Overlap, Grid, Timeline）都提供 Public 的 `options` 属性，返回实例的 `self._option`

***Fixed***
* [issue#133](https://github.com/pyecharts/pyecharts/issues/133) 回退 Echarts 版本，从 v3.7.0 回退至原先的 v3.6.2，解决标签不能正常显示的 bug


### version 0.2.1 - 2017.8.25

***Added***
* [issue#127](https://github.com/pyecharts/pyecharts/issues/127) 新增数据图切换按钮（只针对部分图有效）

***Fixed***
* [issue#130](https://github.com/pyecharts/pyecharts/issues/130) 更改 freeze_js，更正文件路径表示方法
* 修复直角坐标系的标签显示问题


### version 0.2.0 - 2017.8.25

***Added***
* [issue#118](https://github.com/pyecharts/pyecharts/issues/118) 新增 `datazoom_xaxis_index`, `datazoom_yaxis_index`，可使 datazoom 组件同时控制多个 x y 轴。
* 新增 jupyter-notebook 中的 js host 参数，用户可自行决定使用本地后者网络 js 文件，确保转移 notebook 时图形可正常显示
* 新增图形种类 Boxplot（箱形图）
* [issue#120](https://github.com/pyecharts/pyecharts/issues/120) 新增图形种类 Sankey（桑基图）

***Changed***
* 更新 Flask&Django 模板，加载文件的体积大大减小，出图速度更快。
* 更新 echarts 到 3.7.0

***Fixed***
* 修复 Page 类于其他自定义类共用出现问题的 bug


### version 0.1.9.7 - 2017.8.20

***Fixed***
* [issue#113](https://github.com/pyecharts/pyecharts/issues/113) 修复 requirements.txt 中 jupyter-pip 版本过旧问题
* [issue#109](https://github.com/pyecharts/pyecharts/issues/109) 修复地图不能正常显示的问题


### version 0.1.9.6 - 2017.8.19

***Added***
* [issue#95](https://github.com/pyecharts/pyecharts/issues/95) Overlap 类中新增 `xaxis_index`, `is_add_xaxis`, `yaxis_index`, `is_add_yaxis` 参数，现支持多 Y 轴或多 X轴
* Page 类现在也支持在 jupyter-notebook 中显示了，直接调用 Page() 实例即可。
* Graph 图中新增 `graph_edge_symbol`, `graph_edge_symbolsize` 参数
* [issue#94](https://github.com/pyecharts/pyecharts/issues/94) 提供 pyecharts-snapshot 用于将生成的图片保存为 png 或 pdf 文件，仅静态图片生效。（3D 图和动态图不生效）
* [issue#98](https://github.com/pyecharts/pyecharts/issues/98) 通用配置项中新增 tooltip 模块

***Changed***
* jupyter-notebook 和本地 render() 现在均采用动态加入 js 依赖文件的方法，生成文件体积大大缩小。
* 更改通用配置项中的 label 的参数 `formatter` 为 `label_formatter`
* 更改 `clockwise` 参数为 `is_clockwise`
* 更改 Graph 图中的 `repulsion`, `gravity`, `edge_length`, `layout` 参数为 `graph_repulsion`, `graph_gravity`, `graph_edge_length`, `graph_layout`


### version 0.1.9.5 - 2017.8.16

***Added***
* 为 xyAxis 模块新增下列参数
    `xaxis_interval`, `xaxis_name_size`, `xaxis_name_gap`, `xaxis_margin`, `is_xaxislabel_align`
    `yaxis_interval`, `yaxis_name_size`, `yaxis_name_gap`, `yaxis_margin`, `is_yaxislabel_align`
* [issue#86](https://github.com/pyecharts/pyecharts/issues/86) 为 3D 图新增参数用于配置坐标轴选项（参见通用配置项中的 axis3D）
* 修改自定义模块的接口，现自定义模块有以下 4 个类，具体用法参见文档
    * Grid 类：并行显示多张图
    * Overlap 类：结合不同类型图表叠加画在同张图上
    * Page 类：同一网页按顺序展示多图
    * Timeline 类：提供时间线轮播多张图
* 新增 Timeline 功能，支持轮播多张图表

***Changed***
* jupyter notebook 现在也为离线模式，从本地加载项目所需 js 文件。至此 pyecharts 彻底实现本地化运行。速度更快，不再受网速影响。

***Removed***
* 删除冗余 js 文件，压缩项目体积。
* 废弃 xAxis，yAxis 中的 `interval`, `xy_font_size`, `namegap` 参数。


### version 0.1.9.4 - 2017.8.10

***Added***
* [issue#76](https://github.com/pyecharts/pyecharts/issues/76) 新增 Page 类，现能同时在一个 html 页面内按顺序展示多个图形。（参见用户自定义）

***Changed***
* 更改 Image 依赖模块为 pillow


### version 0.1.9.3 - 2017.8.10

***Added***
* [issue#72](https://github.com/pyecharts/pyecharts/issues/72) [issue#41](https://github.com/pyecharts/pyecharts/issues/41) 新增 `xaxis_type`, `yaxis_type` 参数，可通过设置该参数指定直角坐标系数轴类型。（参见 Line，Scattre 图）
* [issue#09](https://github.com/pyecharts/pyecharts/issues/9) 集成 Flask + Django

***Removed***
* 废弃 `npcast()`, `pdcast()` 方法，新版本已经在内部封装了处理逻辑，具体参见文档的 pandas&numpy 示例


### version 0.1.9.2 - 2017.8.6

***Added***
* [issue#52](https://github.com/pyecharts/pyecharts/issues/52) 新增 `xaxis_rotate`, `yaxis_rotate` 参数，可通过设置该参数解决强制显示所有坐标轴标签时因过于密集重叠的问题。参见（Bar 图）
* 新增 `xaxis_min`, `xaxis_max`. `yaxis_min`, `yaxis_max` 参数，可设置坐标轴上的最大最小值，针对数值轴有效。

***Changed***
* [issue#67](https://github.com/pyecharts/pyecharts/issues/67) `render()` 方法现在为离线模式，实现本地生成 .html 文件，加载速度更快。

***Fixed***
* [issue#61](https://github.com/pyecharts/pyecharts/issues/61) 解决 3D 图形不能在 jupyter notebook 上正常显示的问题。

***Removed***
* 废弃 `render_notebook()` 方法，现可直接调用图形实例显示在 jupyter notebook 上。


### version 0.1.9.1 - 2017.7.31

***Added***
* 加入 Travis-CI 自动化测试。
* [issue#46](https://github.com/pyecharts/pyecharts/issues/46) legend 增加 `legend_selectedmode` 参数，图例可以设置为单例或者多例。（参见 Radar 图）
* visualmap 组件增加 `visual_type` 和 `visual_range_size` 参数。现在支持映射到颜色和图形大小两种方式。（参见 Scatter 图）


### version 0.1.9 - 2017.7.30

***Added***
* [issue#28](https://github.com/pyecharts/pyecharts/issues/28) datazoom 中增加了将组件效果显示在 y 坐标轴中的功能。（参见 KLine 图）
* 新增对 Pandas 和 Numpy 数据的简单处理。解决直接传入 Pandas 和 Numpy 数据类型出错的问题。（参见开始使用）
* 新增 Bar3D, Line3D, Scatter3D 三种 3D 立体图。

***Fixed***
* [issue#34](https://github.com/pyecharts/pyecharts/issues/34) 解决在 macos 下安装出错的问题。


### version 0.1.8 - 2017.7.28

***Added***
* [issue#05](https://github.com/pyecharts/pyecharts/issues/5) 新增在 Jupyter Notebook 中展示图表功能。感谢 [@ygw365](https://github.com/ygw365) 提供这部分的代码模板 和 [@muxuezi](https://github.com/muxuezi) 协助对代码进行改进!
* 新增对自定义地图的使用说明


### version 0.1.7 - 2017.7.26

***Added***
* 增加并行显示图表功能


### version 0.1.6 - 2017.7.24

***Added***
* 新增了热力图


### version 0.1.5 - 2017.7.22

***Added***
* 新增了 K 线图


### version 0.1.4 - 2017.7.20

***Added***
* 第一个稳定版本
