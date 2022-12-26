> This guide describes how to use pyecharts in Sanic.

## Sanic Front and Back End Separation

> Front and back-end separation allows you to use features such as dynamic data update, incremental data update, etc.

### Step 0: Install Sanic dependencies

```shell
$ pip install Sanic
```

### Step 1: Create a new project and HTML file

Create a new project folder (empty), a new app.py, templates folder and a new index.html in the templates folder.

index.html
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Awesome-pyecharts</title>
    <script src="https://cdn.bootcss.com/jquery/3.0.0/jquery.min.js"></script>
    <script type="text/javascript" src="https://assets.pyecharts.org/assets/echarts.min.js"></script>

</head>
<body>
    <div id="bar" style="width:1000px; height:600px;"></div>
    <script>
        var chart = echarts.init(document.getElementById('bar'), 'white', {renderer: 'canvas'});

        $(
            function () {
                fetchData();
            }
        );

        function fetchData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:8000/barChart",
                dataType: 'json',
                success: function (result) {
                    chart.setOption(JSON.parse(result));
                }
            });
        }
    </script>
</body>
</html>
```

### Step 2: Write the code for Sanic and pyecharts

Note: At present, due to the problem of json data type, it is impossible to convert JSCode data in pyecharts into json data format and return it to the front-end page. Therefore, you should avoid using JSCode for drawing when you are using front-end and back-end separation.

Sample code
```python
from random import randrange

from sanic import Sanic
from sanic.response import json, html

from pyecharts import options as opts
from pyecharts.charts import Bar

# 初始化 Sanic
app = Sanic(__name__)


def bar_base() -> Bar:
    c = (
        Bar()
        .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
        .add_yaxis("商家A", [randrange(0, 100) for _ in range(6)])
        .add_yaxis("商家B", [randrange(0, 100) for _ in range(6)])
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-基本示例", subtitle="我是副标题"))
    )
    return c


@app.route("/barChart", methods=["GET"])
async def draw_bar_chart(request):
    c = bar_base()
    return json(c.dump_options_with_quotes())


@app.route("/", methods=["GET"])
async def index(request):
    return html(open("./templates/index.html").read())


if __name__ == '__main__':
    app.run()
```

### Step 3: Run the project

```shell
$ python app.py
```

Use your browser to open http://127.0.0.1:8000 to access the service

![](https://user-images.githubusercontent.com/17564655/57364426-c171f100-71b5-11e9-8a7a-f0636363bba1.png)


## Timed full update of charts
> Active data refresh from front-end to back-end

The core of timed refresh is the `setInterval` method of html.

index.html
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Awesome-pyecharts</title>
    <script src="https://cdn.bootcss.com/jquery/3.0.0/jquery.min.js"></script>
    <script type="text/javascript" src="https://assets.pyecharts.org/assets/echarts.min.js"></script>

</head>
<body>
    <div id="bar" style="width:1000px; height:600px;"></div>
    <script>
        var chart = echarts.init(document.getElementById('bar'), 'white', {renderer: 'canvas'});

        $(
            function () {
                fetchData();
                setInterval(fetchData, 2000);
            }
        );

        function fetchData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:8000/barChart",
                dataType: "json",
                success: function (result) {
                    chart.setOption(JSON.parse(result));
                }
            });
        }
    </script>
</body>
</html>
```

## Timed incremental chart updates

index.html

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Awesome-pyecharts</title>
    <script src="https://cdn.bootcss.com/jquery/3.0.0/jquery.min.js"></script>
    <script type="text/javascript" src="https://assets.pyecharts.org/assets/echarts.min.js"></script>

</head>
<body>
    <div id="bar" style="width:1000px; height:600px;"></div>
    <script>
        var chart = echarts.init(document.getElementById('bar'), 'white', {renderer: 'canvas'});
        var old_data = [];
        $(
            function () {
                fetchData();
                setInterval(getDynamicData, 2000);
            }
        );

        function fetchData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:8000/lineChart",
                dataType: "json",
                success: function (result) {
                    chart.setOption(JSON.parse(result));
                    old_data = chart.getOption().series[0].data;
                }
            });
        }

        function getDynamicData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:8000/lineDynamicData",
                dataType: "json",
                success: function (result) {
                    old_data.push([result.name, result.value]);
                    chart.setOption({
                        series: [{
                            data: old_data
                        }]
                    });
                }
            });
        }

    </script>
</body>
</html>
```

The back-end code also needs to be changed accordingly

```python
from random import randrange

from sanic import Sanic
from sanic.response import json, html

from pyecharts import options as opts
from pyecharts.charts import Line

# 初始化 Sanic
app = Sanic(__name__)


def line_base() -> Line:
    line = (
        Line()
        .add_xaxis(list(range(10)))
        .add_yaxis(series_name="", y_axis=[randrange(0, 100) for _ in range(10)])
        .set_global_opts(
            title_opts=opts.TitleOpts(title="动态数据"),
            xaxis_opts=opts.AxisOpts(type_="value"),
            yaxis_opts=opts.AxisOpts(type_="value")
        )
    )
    return line


@app.route("/lineChart", methods=["GET"])
async def draw_line_chart(request):
    c = line_base()
    return json(c.dump_options_with_quotes())

cnt = 9

@app.route("/lineDynamicData", methods=["GET"])
async def update_line_data(request):
    global cnt
    cnt = cnt + 1
    return json({"name": cnt, "value": randrange(0, 100)})


@app.route("/", methods=["GET"])
async def index(request):
    return html(open("./templates/index.html").read())


if __name__ == '__main__':
    app.run()
```
