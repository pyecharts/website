**Q: 如何离线安装 pyecharts？**

A: TODO

---

**Q: 关于 JSCode 在 Web 框架中使用前后端分离模式情况下出现解析异常**

A1: 由于 json 数据类型的问题，无法将 pyecharts 中的 JSCode 类型的数据转换成 json 数据格式返回到前端页面中使用。因此在使用前后端分离的情况下尽量避免使用 JSCode 进行画图。

A2: 暂时的解决方案如下(以使用 Jquery Ajax 获取数据的情况为例):

前端部分
```javascript
$.ajax({
    type: "GET",  // POST 获取其他
    url: "<后端的数据接口>",
    dataType: 'json',
    success: function (result) {
        console.log(result);
        let jsonResult = JSON.stringify(result);
        jsonResult = JSON.parse(jsonResult, function (key, value) {
           if (value.match(/(?:\/\*[\s\S]*?\*\/|\/\/.*?\r?\n|[^{])+\{([\s\S]*)\}$/) !== null) {
               return eval("(" + value + ")");
           } else {
               return value;
           }
        });
        // chart 是事先在全局定义的 echarts 的 init 的变量名
        chart.setOption(jsonResult);
    }
});
```

后端部分(只给出画图核心的代码部分, 以 Line 图为例子)
```python
def line_base() -> Line:
    line = (
        Line()
        .add_xaxis(list(range(10)))
        .add_yaxis(series_name="", y_axis=[randrange(0, 100) for _ in range(10)])
        .set_global_opts(
            yaxis_opts=opts.AxisOpts(
                axislabel_opts=opts.LabelOpts(
                    is_show=True, formatter="function(params) { return params + 8;}"
                )
            )
        )
        .dump_options()
    )
    return line
```

目前解决在 Web 框架下前后端分离模式的情况下出现 json 解析异常的核心就是在需要用到 JSCode 的地方都不使用 JSCode 进行传参。
前端主要就是在解析 json 的情况下通过 JSON.parse 的回调函数进行处理。
通过右侧的正则表达式判断是否为 js 的 function `/(?:\/\*[\s\S]*?\*\/|\/\/.*?\r?\n|[^{])+\{([\s\S]*)\}$/`，从而避免字符串的同名冲突的问题。

示例如下:
![](https://user-images.githubusercontent.com/17564655/61172141-24677600-a5b3-11e9-9425-5cafae45a315.png)
