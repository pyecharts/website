## Python -> JSON

pyecharts 本质上在做的事情就是将 Echarts 的配置项由 Python dict 序列化为 JSON 格式，所以 pyecharts 支持什么格式的数据类型取决于 JSON 支持什么数据类型。

在 Python 中对 JSON 的格式转换如下

```
Python          JSON
------          ----
int, float      number
str             string
bool            boolean
dict            object
list            array
```

这也就意味着在你将数据传入到 pyecharts 的时候，需要自行将数据格式转换成上述 Python 原生的数据格式。使用数据分析大都需要使用 numpy/pandas，但是 numpy 的 numpy.int64/numpy.int32/... 等数据类型并不继承自 `Python.int`。

**Q1: 如何转换？**

```python
# for int
[int(x) for x in your_numpy_array_or_something_else]
# for float
[float(x) for x in your_numpy_array_or_something_else]
# for str
[str(x) for x in your_numpy_array_or_something_else]
```

**Q2: 有没有更方便的转换方法？**

`Series.tolist()`

**Q3: pyecharts 没有自动转换的原因？**

pyecharts 是一个通用的第三方库，我们不可能关心开发者的所有使用场景，这个转换需要我们引入 `numpy/pandas` 两个第三方库，而这两个库 `太重了`，所以我们将这个工作交给了开发者。
