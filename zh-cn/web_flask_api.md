> 本指南会以一个小的 Flask 前后端分离项目为例，说明如何在 Flask 中使用 pyecharts。

## Step 0:

```shell
$ mkdir pyecharts-flask-demo
$ cd pyecharts-flask-demo
$ mkdir templates
```

## Step 1: 新建一个 html 文件

新建 html 文件保存位于项目根目录的 templates 文件夹
这里以如下 html 为例. 主要用到了 `jquery` 和 `pyecharts` 管理的 `echarts.min.js` 依赖


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
    <div id="bar" style="width:1600px; height:800px;"></div>
    <script>
        $(
            function () {
                var chart = echarts.init(document.getElementById('bar'), 'white', {renderer: 'canvas'});
                $.ajax({
                    type: "GET",
                    url: "http://127.0.0.1:5000/barChart",
                    dataType: 'json',
                    success: function (result) {
                        console.log(result);
                        chart.setOption(result);
                    }
                });
            }
        )
    </script>
</body>
</html>
```

## Step 2: 编写 flask 和 pyecharts 代码渲染图表

请将下面的代码保存为 app.py 文件并移至项目的根目录下。

目录结构如下
```shell
sunhailindeMacBook-Pro:pyecharts_flask sunhailin$ tree -L 1
.
├── app.py
└── templates
```

示例代码
```python
from random import randrange

from flask.json import jsonify
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
        .get_options()
    )
    return c


@app.route("/")
def index():
    return render_template("index.html")


@app.route("/barChart")
def get_bar_chart():
    c = bar_base()
    return jsonify(c)


if __name__ == "__main__":
    app.run()

```

## Step 3: 运行项目

```shell
$ python3 app.py
```

使用浏览器打开 http://127.0.0.1:5000 即可访问服务

![](https://user-images.githubusercontent.com/17564655/57358164-633e1180-71a7-11e9-8937-062f27c0147c.png)


## Extension Function: 定时更新图表 (前端主动向后端进行数据刷新)

定时刷新的核心在于 html 的 `setInterval` 方法，这里附上定时刷新的 demo html 代码。

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
    <div id="bar" style="width:1600px; height:800px;"></div>
    <script>
        var interval = null; //计时器
        var chart = echarts.init(document.getElementById('bar'), 'white', {renderer: 'canvas'});

        $(
            function () {
                getData(chart);
                startInterval()
            }
        );

        function startInterval() {
            if (interval !== null) {
                clearInterval(interval);
                interval = null;
            }
            interval = setInterval(getData, 2000);
            alert("计时器启动成功!")
        }

        function getData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:5000/barChart",
                dataType: 'json',
                success: function (result) {
                    console.log(result);
                    chart.setOption(result);
                }
            });
        }
    </script>
</body>
</html>
```
