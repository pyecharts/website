pyecharts 对配置项基本上都采用 XXXOpts/XXXItems 以及 dict 两种数据形式，这两种是完全等价的。

比如下面三者效果是一致的

```python
c = Bar(init_opts=opts.InitOpts(width="620px", height="420px"))
c = Bar(dict(width="620px", height="420px"))
c = Bar({"width": "620px", "height": "420px"})
```

其他配置项均可这么操作

```python
c = (
    Parallel()
    .add_schema(
        [
            opts.ParallelAxisOpts(dim=0, name="data"),
            opts.ParallelAxisOpts(dim=1, name="AQI"),
            opts.ParallelAxisOpts(dim=2, name="PM2.5"),
            opts.ParallelAxisOpts(dim=3, name="PM10"),
            opts.ParallelAxisOpts(dim=4, name="CO"),
            opts.ParallelAxisOpts(dim=5, name="NO2"),
            opts.ParallelAxisOpts(dim=6, name="CO2"),
            opts.ParallelAxisOpts(
                dim=7,
                name="等级",
                type_="category",
                data=["优", "良", "轻度污染", "中度污染", "重度污染", "严重污染"],
            ),
        ]
    )
)

# 等价于

c = (
    Parallel()
    .add_schema(
        [
            dict(dim=0, name="data"),
            dict(dim=1, name="AQI"),
            dict(dim=2, name="PM2.5"),
            dict(dim=3, name="PM10"),
            dict(dim=4, name="CO"),
            dict(dim=5, name="NO2"),
            dict(dim=6, name="CO2"),
            dict(
                dim=7,
                name="等级",
                type_="category",
                data=["优", "良", "轻度污染", "中度污染", "重度污染", "严重污染"],
            ),
        ]
    )
)

# 等价于

c = (
    Parallel()
    .add_schema(
        [
            {"dim": 0, "name": "data"},
            {"dim": 1, "name": "AQI"},
            {"dim": 2, "name": "PM2.5"},
            {"dim": 3, "name": "PM10"},
            {"dim": 4, "name": "CO"},
            {"dim": 5, "name": "NO2"},
            {"dim": 6, "name": "CO2"},
            {
                "dim": 7, "name": "等级", "type": "category",
                "data": ["优", "良", "轻度污染", "中度污染", "重度污染", "严重污染"],
            ),
        ]
    )
)
```

> Note: 不是每个配置项的名字都与 dict key 相等，比如 max_, min_, type_ 等，因为和 Python 原生关键字冲突了，所以使用 _ 下划线作为后缀，具体应该参考每个配置项的 `self.opts` 属性。
