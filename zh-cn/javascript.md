pyecharts 支持传入原生 JS 函数，这些函数大都用于在设置 formatter 的时候使用，如 `Geo` 图的 formatter 默认就是通过回调函数设置的

使用回调函数设置 `Tooltip Formatter`

```python
GEO = """function (params) {
        return params.name + ' : ' + params.value[2];
    }"""
```

> Note: 想使用 `\n`, `\t` 字符串的话，需要转换为 `\\n`, `\\t`

然后在 `set_global_opts` 中配置，所有的 JS 函数均要使用 `utils.JsCode` 类封装

```python
from pyecharts.commons import utils

geo.set_global_opts(
    opts.TooltipOpts(formatter=utils.JsCode(TooltipFormatterType.GEO)),
)
```

使用回调函数设置 `Label Formatter` 浮点数位数

```python
FORMATTER = """"function (params) {
    return window.parseFloat(params.value).toFixed(2)
}
""
```

或者可以在任何图表上附加 JS 代码

```python
from pyecharts.charts import Bar

bar = Bar()
bar.add_js_funcs("console.log('hello world')")
```

打开浏览器控制台就可以看到输出了 `hello world`。
