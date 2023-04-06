# Version log

### version 2.0.3 - 2023-04-06 (Current)
***Add***
* [pr#2158](https://github.com/pyecharts/pyecharts/pull/2158) Add a rendering configuration (embedding `js` files into `HTML` files) by @omixwxm

***Fixed***
* [issue#2144](https://github.com/pyecharts/pyecharts/issues/2144) Fix `legend` selection state exception when using `timeline`
* [issue#2153](https://github.com/pyecharts/pyecharts/issues/2153) Fix exception for `Grid.visualMap`.
* [issue#2165](https://github.com/pyecharts/pyecharts/issues/2165) Fix `dataset` exception for `Line` diagrams

**Updated**
* Code coverage: 99%
* [commit#6deda6a](https://github.com/pyecharts/pyecharts/pull/2155/commits/6deda6a9abfe597d7af1c5fcb5e32d327ac73e68) Update Map Configuration


### version 2.0.2 - 2023-02-28
***Add***
* [issue#2118](https://github.com/pyecharts/pyecharts/issues/2118) Add `Graph` arguments
* [issue#2125](https://github.com/pyecharts/pyecharts/issues/2125) Add `Line` arguments

***Fixed***
* [issue#2116](https://github.com/pyecharts/pyecharts/issues/2116) Fix `Grid.visualMap` error


### version 2.0.1 - 2023-01-08
***Fixed***
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/d7788ba4b56545bbfe92e39516b6842ac39e9837) Fix an issue that caused the map data in `faker.py` to be displayed incorrectly due to a change in the map base map.

### version 2.0.0 - 2023-01-04

***Add***
* [issue#1859](https://github.com/pyecharts/pyecharts/issues/1859) Added view control for `option.grid3D.viewControl.alpha` and `beta` in `Grid3DOpts`.
* [issue#1825](https://github.com/pyecharts/pyecharts/issues/1825) Added parameters for multiple parallel coordinate systems
* [issue#1785](https://github.com/pyecharts/pyecharts/issues/1785) `Boxplot` added support for `boxWidth` configuration
* Timeline has new axis index settings (set `current_index` to set the starting index position of the timeline via `add_schema`)
* [pull#1934](https://github.com/pyecharts/pyecharts/pull/1934) added `DataZoomOpts` and `TooltipOpts` configuration
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/3547c50434400e6bd347204afff56331f27ea767) Add configuration for `ThreeAxisChart` and `Axis3DOpts`
* [pull#1971](https://github.com/pyecharts/pyecharts/pull/1971) Fix `MarkLineItem` missing `linestyle_opts` parameter
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#2004](https://github.com/pyecharts/pyecharts/issues/2004) Add `borderRadius` parameter to `ItemStyle` of series configuration item
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#1990](https://github.com/pyecharts/pyecharts/issues/1990) Add `Scatter` pattern data to calendar chart
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/d25cca137b13fdd852bf91d74de816847877bd05) Add `Custom` graphs
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/a85711c3114127d866ffac16d27672802d009e81) Add `Lines3D` graphics configuration
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/a85711c3114127d866ffac16d27672802d009e81) Add `globe` configuration for 3D graphics
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/73a5b11689d9626b61122a58d48e85536800a135) `InitOpts` adds `bg_color` and `is_fill_bg_color` for filling canvas colors.
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/73a5b11689d9626b61122a58d48e85536800a135) `Tab` add `tab_css_opts`, `TabChartGlobalOpts` for configuring Tab related CSS styles 
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/7f5a2eae7cc15b0929a42b0082d7409040e6d382) `Gauge` add `tab_css_opts`, `TabChartGlobalOpts` to configure Tab related CSS styles
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/84483fd6165db0cf607fb95dd4e431d83f2871fe) Added `add_geo_json` API for adding custom `GeoJson` data to `Geo` and `Map`. 
* [commit/dev](https://github.com/pyecharts/pyecharts/pull/2104/commits/74c151a371ffb44336a3aea3d624e27535527711) Added `GraphGL`
* [commit/dev](https://github.com/pyecharts/pyecharts/pull/2104/commits/aaf8076e6d28787dd16d4219f1e473c3c076eb54) Added `GeoRegionsOpts` for `Geo` configure `regions` arguments

***Fixed***
* [issue#1794](https://github.com/pyecharts/pyecharts/issues/1794) Fix `Toolbox` exception
* [issue#1805](https://github.com/pyecharts/pyecharts/issues/1805) Fix `Gauge` data label exception
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#2003](https://github.com/pyecharts/pyecharts/issues/2003) Fix an issue with adding multiple `Gauge` in `Grid`.
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#1994](https://github.com/pyecharts/pyecharts/issues/1994) Fix `Bar` diagram not working with `add_dataset` method in `Timeline`.
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#1974](https://github.com/pyecharts/pyecharts/issues/1974) Fix `logBase` scale axis exception
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#1946](https://github.com/pyecharts/pyecharts/issues/1946) Fix `Toolbox` exception in `Timeline`.
* [pull#1978](https://github.com/pyecharts/pyecharts/pull/1978) Fix color add exception @jackzhenguo
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/2b6fd503349b72b6addad57ff33d253c22743a78) [issue#1871](https://github.com/pyecharts/pyecharts/issues/1871) Fix an issue with using multiple `Radar` graphs in `Timeline`.
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/d25cca137b13fdd852bf91d74de816847877bd05) Fix `add_dataset` exception in certain scenarios
* [issue#2075](https://github.com/pyecharts/pyecharts/issues/2075) Fix `Grid` not adding multiple `Radar` graphs properly.
* [issue#2059](https://github.com/pyecharts/pyecharts/issues/2059) Fix `animationOpts` can't use dictionary configuration.
* [issue#2051](https://github.com/pyecharts/pyecharts/issues/2051) Update Map for Hunan Province.
* [commit/assets](https://github.com/pyecharts/pyecharts-assets/commit/5b95f0b0fbfd641b7cd74e6f597354df1abcbb6c) Update Map for China.

***Updated***
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/d25cca137b13fdd852bf91d74de816847877bd05) [commit/dev](https://github.com/pyecharts/pyecharts/commit/a85711c3114127d866ffac16d27672802d009e81) Update the parameters of some configuration items
* [commit/dev](https://github.com/pyecharts/pyecharts/commit/a85711c3114127d866ffac16d27672802d009e81) Update a lot of unit test code (currently 99% unit test coverage)
* [commit/dev](https://github.com/pyecharts/pyecharts/pull/2104/commits/73d56348de063b3135687f23c876a47dcc7ccd73) Make CI Remove Python 3.6
* [commit/dev](https://github.com/pyecharts/pyecharts/pull/2104/commits/29a6c4249bce6dea209e81f58065f9e8486a9beb) Make CI Support Python 3.11
* [commit/dev](https://github.com/pyecharts/pyecharts/pull/2104/commits/4d0edd9f8c1fd667c03b3fd575ffa759a89f311e) `Geo / BMap` diagram support `scatterGL`, `flowGL`, `linesGL`

### version 1.9.0 - 2020-10-29 (Current)

***Add***
* [pr#1737](https://github.com/pyecharts/pyecharts/pull/1737) Added `ChartItem` configuration for some charts (removed `warning` prompt)
* [pr#1737](https://github.com/pyecharts/pyecharts/pull/1726) Added `xcoord` and `ycoord` configuration items for `MarkLineItem`

***Updated***
* [pr#1724](https://github.com/pyecharts/pyecharts/pull/1724) Updated the `Geo` and `Map` configuration items
* [pr#1694](https://github.com/pyecharts/pyecharts/pull/1694) Update `Echarts` to `Apache Echarts`
* [pr#1691](https://github.com/pyecharts/pyecharts/pull/1691) update `README.md`
* [pr#1661](https://github.com/pyecharts/pyecharts/pull/1661) Update the style configuration for the `Timeline` diagram
* [pr#1660](https://github.com/pyecharts/pyecharts/pull/1660) Update the `LabelLine` configuration for the `Pie` diagram

### version 1.8.1 - 2020-06-10

***Add***
* [pr#1642](https://github.com/pyecharts/pyecharts/pull/1642) Updated `Geo/Map` area map mapping relations (added multiple area maps)
* [pr#1641](https://github.com/pyecharts/pyecharts/pull/1641) Added multiple country map js files.
