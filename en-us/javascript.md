pyecharts supports passing in native JS functions, most of which are used when setting the formatter, such as the `Geo` chart formatter which is set by default via a callback function

Using callback functions to set the `Tooltip Formatter`

```python
GEO = """function (params) {
        return params.name + ' : ' + params.value[2];
    }"""
```

> Note: If you want to use `\n`, `\t` strings, you need to convert to `\\n`, `\\t`

Then configure in `set_global_opts` that all JS functions should be wrapped in `utils.JsCode` class

```python
from pyecharts.commons import utils

geo.set_global_opts(
    opts.TooltipOpts(formatter=utils.JsCode(TooltipFormatterType.GEO)),
)
```

Set the `Label Formatter` floating point digits using the callback function

```python
FORMATTER = """"function (params) {
    return window.parseFloat(params.value).toFixed(2)
}
""
```

Or you can attach JS code to any chart

```python
from pyecharts.charts import Bar

bar = Bar()
bar.add_js_funcs("console.log('hello world')")
```

You can see the output ``hello world`` by opening the browser console.
