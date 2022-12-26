pyecharts basically uses both XXXOpts/XXXItems and dict data forms for configuration items, which are fully equivalent.

For example, the following three have the same effect

```python
c = Bar(init_opts=opts.InitOpts(width="620px", height="420px"))
c = Bar(dict(width="620px", height="420px"))
c = Bar({"width": "620px", "height": "420px"})
```

All other configuration items can be done this way

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
                name="class",
                type_="category",
                data=["excellent", "good", "lightly polluted", "moderately polluted", "heavily polluted", "severely polluted"],
            ),
        ]
    )
)

# is equivalent to

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
                name="class",
                type_="category",
                data=["excellent", "good", "lightly polluted", "moderately polluted", "heavily polluted", "severely polluted"],
            ),
        ]
    )
)

# is equivalent to

c = (
    Parallel()
    .add_schema(
        [
            {"dim": 0, "name": "data"},
            {"dim": 1, "name": "AQI"},
            {"dim": 2, "name": "PM2.5"}, {"dim": 2, "name": "PM2.5"},
            {"dim": 3, "name": "PM10"}, {"dim": 3, "name": "PM10"},
            {"dim": 4, "name": "CO"}, {"dim": 4, "name": "CO",
            {"dim": 5, "name": "NO2"}, {"dim": 5, "name": "NO2"},
            {"dim": 6, "name": "CO2"}, {"dim": 6, "name": "CO2"},
            {
                "dim": 7, "name": "class", "type": "category",
                "data": ["excellent", "good", "lightly polluted", "moderately polluted", "heavily polluted", "severely polluted"],
            ),
        ]
    )
)
```

> Note: Not every configuration item has a name equivalent to the dict key, e.g. max_, min_, type_, etc., because it conflicts with Python's native keywords, so _ is used as a suffix; you should refer to the `self.opts` property of each configuration item.
