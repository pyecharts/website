**Q: How to use pyecharts offline?**

A: If you need to use pyecharts on a non-internet environment, you need to install pyecharts offline and provide local static resource HOST service.

Find a machine with internet access and perform the following steps
```shell
# Install pyecharts first
$ pip install pyecharts
$ cd ~ && mkidr pyecharts-dep && cd pyecharts-dep
# Download all the dependencies used by pyecharts to the pyecharts-dep folder
$ pip download pyecharts
# clone pyecharts-assets project
$ git clone https://github.com/pyecharts/pyecharts-assets.git
# package up the pyecharts-dep folder and transfer it to the machine where you want to use pyecharts offline
```

Switch to the machine you want to use offline, and perform the following steps
```shell
# 1. First install the packages in pyecharts-dep except pyecharts-X.Y.Z-py2.py3-none-any.whl
$ ls | grep -v "^pyecharts*" | xargs pip install
# 2. Install the pyecharts-X.Y.Z-py2.py3-none-any.whl package
$ ls | grep "pyecharts*" | xargs pip install
# 3. Start the local service
$ cd pyecharts-assets && python -m http.server
```

---

**Q: About JSCode parsing exception in web framework using front/back end separation mode**

A1: Due to the problem of json data type, the JSCode data in pyecharts cannot be converted into json data format and returned to the front-end page. Therefore, avoid using JSCode for drawing when using front-end and back-end separation.

A2: The tentative solution is as follows (taking the case of using Jquery Ajax to get data as an example):

Front-end part
```javascript
$.ajax({
    type: "GET", // POST to get other
    url: "<backend data interface>",
    dataType: 'json',
    success: function (result) {
        // console.log(result);
        let jsonResult = JSON.stringify(result);
        jsonResult = JSON.parse(jsonResult, function (key, value) {
           if (value.match(/(? :\/\*[\s\S]*? \*\/|\/\/. *? \r?\n|[^{])+\{([\s\S]*)\}$/) ! == null) {
               return eval("(" + value + ")");
           } else {
               return value;
           }
        });
        // chart is the variable name of the init of echarts defined globally in advance
        chart.setOption(jsonResult);
    }
});
```

The backend part (only the core code part of the chart is given, using the Line chart as an example)
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
        .dump_options_with_quotes() # 保留 JS 方法引号
    )
    return line
```

The front end is mainly handled by the JSON.parse callback function in the case of parsed json. The regular expression on the right-hand side determines whether the function `/(? :\/\*[\s\S]*? \*\/|\/\/. *? \r?\n|[^{])+\{([\s\S]*)\}$/`, thus avoiding the problem of same-name conflict of strings.

Example:
![](https://user-images.githubusercontent.com/17564655/61172141-24677600-a5b3-11e9-9425-5cafae45a315.png)


**Q: Invalid line break with '\\n' in Tooltip**

A: Please use ```<br/>``` instead of ```\n```
