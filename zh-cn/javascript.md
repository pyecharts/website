pyecharts 支持传入原生 JS 函数，这些函数大都用于在设置 formatter 的时候使用，如 `Geo` 图的 formatter 默认就是通过回调函数设置的

```python
GEO = """function (params) {
        return params.name + ' : ' + params.value[2];
    }"""
```

然后在 `set_global_opts` 中配置，所有的 JS 函数均要使用 `utils.produce_js_func` 封装

```python
from pyecharts.commons import utils

geo.set_global_opts(
    opts.TooltipOpts(formatter=utils.produce_js_func(TooltipFormatterType.GEO)),
)
```

或者可以在任何图表上附加 JS 代码

```python
from pyecharts.charts import Bar

bar = Bar()
bar.add_js_funcs("console.log('hello world')")
```

打开浏览器控制台就可以看到输出了 `hello world`。
