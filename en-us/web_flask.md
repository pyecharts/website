> This guide describes how to use pyecharts in Flask.

## Flask Template Rendering

### Step 0: Create a new Flask project

```shell
$ mkdir pyecharts-flask-demo
$ cd pyecharts-flask-demo
$ mkdir templates
```

### Step 1: Copy the pyecharts template

Copy the pyecharts template, located in `pyecharts.render.templates`, to the templates folder you just created

```shell
chenjiandongx@DESKTOP-E83NUHA:/mnt/d/Python/pyecharts-flask-demo/templates$ tree
.
├── jupyter_lab.html
├── jupyter_notebook.html
├── macro
├── nteract.html
├── simple_chart.html
├── simple_page.html
└── table.html
```

### Step 2: Rendering the chart

Please save the following code as server.py file and move it to the root directory of your project.

The directory structure is as follows
```shell
chenjiandongx@DESKTOP-E83NUHA:/mnt/d/Python/pyecharts-flask-demo$ tree -L 1
.
├── server.py
└── templates
```

Example Code
```python
from flask import Flask
from jinja2 import Markup, Environment, FileSystemLoader
from pyecharts.globals import CurrentConfig

# 关于 CurrentConfig，可参考 [基本使用-全局变量]
CurrentConfig.GLOBAL_ENV = Environment(loader=FileSystemLoader("./templates"))

from pyecharts import options as opts
from pyecharts.charts import Bar


app = Flask(__name__, static_folder="templates")


def bar_base() -> Bar:
    c = (
        Bar()
        .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
        .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
        .add_yaxis("商家B", [15, 25, 16, 55, 48, 8])
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-基本示例", subtitle="我是副标题"))
    )
    return c


@app.route("/")
def index():
    c = bar_base()
    return Markup(c.render_embed())


if __name__ == "__main__":
    app.run()
```

### Step 3: Run the project

```shell
$ python server.py
```

Use browser open http://127.0.0.1:5000

![](https://user-images.githubusercontent.com/19553554/56732149-0138e180-678f-11e9-8641-cb659188e716.png)

## Flask front and back-end separation

> Separation of front and back ends can be used to dynamically update data, incrementally update data, etc.

### Step 0, Step 1 see template rendering section above

### Step 3: Create a new HTML file

The new HTML file is saved in the templates folder in the root of the project, here is index.html for example. It mainly uses `jquery` and the `echarts.min.js` dependency managed by `pyecharts`.

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
        $(
            function () {
                var chart = echarts.init(document.getElementById('bar'), 'white', {renderer: 'canvas'});
                $.ajax({
                    type: "GET",
                    url: "http://127.0.0.1:5000/barChart",
                    dataType: 'json',
                    success: function (result) {
                        chart.setOption(result);
                    }
                });
            }
        )
    </script>
</body>
</html>
```

### Step 4: Write flask and pyecharts code to render charts

Please save the following code as app.py file and move it to the root directory of your project.

The directory structure is as follows
```shell
sunhailindeMacBook-Pro:pyecharts_flask sunhailin$ tree -L 1
.
├── app.py
└── templates
```

Note: At present, due to the problem of json data type, the JSCode data in pyecharts cannot be converted into json data format and returned to the front-end page. Therefore, avoid using JSCode for drawing if you are using front-end and back-end separation.

app.py
```python
from random import randrange

from flask import Flask, render_template

from pyecharts import options as opts
from pyecharts.charts import Bar


app = Flask(__name__, static_folder="templates")


def bar_base() -> Bar:
    c = (
        Bar()
        .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
        .add_yaxis("商家A", [randrange(0, 100) for _ in range(6)])
        .add_yaxis("商家B", [randrange(0, 100) for _ in range(6)])
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-基本示例", subtitle="我是副标题"))
    )
    return c


@app.route("/")
def index():
    return render_template("index.html")


@app.route("/barChart")
def get_bar_chart():
    c = bar_base()
    return c.dump_options_with_quotes()


if __name__ == "__main__":
    app.run()
```

### Step 5: Run the project

```shell
$ python app.py
```
Use your browser to open http://127.0.0.1:5000 to access the service


## Timed full update of charts
> Active data refresh from front-end to back-end

The core of timed refresh is the HTML `setInterval` method.

index.
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
                fetchData(chart);
                setInterval(fetchData, 2000);
            }
        );

        function fetchData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:5000/barChart",
                dataType: 'json',
                success: function (result) {
                    chart.setOption(result);
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
                fetchData(chart);
                setInterval(getDynamicData, 2000);
            }
        );

        function fetchData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:5000/lineChart",
                dataType: "json",
                success: function (result) {
                    chart.setOption(result);
                    old_data = chart.getOption().series[0].data;
                }
            });
        }

        function getDynamicData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:5000/lineDynamicData",
                dataType: "json",
                success: function (result) {
                    old_data.push([result.name, result.value]);
                    chart.setOption({
                        series: [{data: old_data}]
                    });
                }
            });
        }

    </script>
</body>
</html>
```

Incremental updates to the back-end code also require corresponding changes

```python
from random import randrange

from flask.json import jsonify
from flask import Flask, render_template

from pyecharts import options as opts
from pyecharts.charts import Line


app = Flask(__name__, static_folder="templates")


def line_base() -> Line:
    line = (
        Line()
        .add_xaxis(["{}".format(i) for i in range(10)])
        .add_yaxis(
            series_name="",
            y_axis=[randrange(50, 80) for _ in range(10)],
            is_smooth=True,
            label_opts=opts.LabelOpts(is_show=False),
        )
        .set_global_opts(
            title_opts=opts.TitleOpts(title="动态数据"),
            xaxis_opts=opts.AxisOpts(type_="value"),
            yaxis_opts=opts.AxisOpts(type_="value"),
        )
    )
    return line


@app.route("/")
def index():
    return render_template("index.html")


@app.route("/lineChart")
def get_line_chart():
    c = line_base()
    return c.dump_options_with_quotes()


idx = 9


@app.route("/lineDynamicData")
def update_line_data():
    global idx
    idx = idx + 1
    return jsonify({"name": idx, "value": randrange(50, 80)})


if __name__ == "__main__":
    app.run()
```
![](https://user-images.githubusercontent.com/19553554/57461309-599cd280-72a9-11e9-8a45-06df9b882f51.gif)
