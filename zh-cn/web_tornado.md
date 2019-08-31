> 本指南介绍了如何在 Tornado 中使用 pyecharts。

## Tornado 前后端分离

> 前后端分离可以使用动态更新数据，增量更新数据等功能。

### Step 0: 安装 Tornado 的依赖

```shell
$ pip install tornado
```

### Step 1: 新建项目和 HTML 文件

新建一个项目文件夹(空的即可)，新建 server.py、index.html。

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
                    url: "http://127.0.0.1:8889/getBarChart",
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

### Step 2: 编写 Tornado 和 pyecharts 的代码

注: 目前由于 json 数据类型的问题，无法将 pyecharts 中的 JSCode 类型的数据转换成 json 数据格式返回到前端页面中使用。因此在使用前后端分离的情况下尽量避免使用 JSCode 进行画图。

示例代码
```python
import tornado.web
import tornado.ioloop
import tornado.httpserver

from pyecharts.charts import Bar
from pyecharts import options as opts


def bar_base() -> str:
    c = (
        Bar()
        .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
        .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
        .add_yaxis("商家B", [15, 25, 16, 55, 48, 8])
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-基本示例", subtitle="我是副标题"))
    )
    return c.dump_options()


def set_default_header(self):
    # 后面的*可以换成ip地址，意为允许访问的地址
    self.set_header("Access-Control-Allow-Origin", "*")
    self.set_header("Access-Control-Allow-Headers", "x-requested-with")
    self.set_header("Access-Control-Allow-Methods", "POST, GET, PUT, DELETE")
    self.set_header("Content-Type", "application/json; charset=UTF-8")


class BarChart(tornado.web.RequestHandler):
    def data_received(self, chunk):
        pass

    def get(self):
        set_default_header(self)
        chart_result = bar_base()
        # 返回结果
        self.write(chart_result)
        self.finish()


class PageHandler(tornado.web.RequestHandler):
    def data_received(self, chunk):
        pass

    def get(self):
        self.render("index.html")


def make_app():
    return tornado.web.Application([
        (r"/", PageHandler),
        (r"/getBarChart", BarChart),
    ])


if __name__ == "__main__":
    port = 8889
    app = make_app()
    sockets = tornado.netutil.bind_sockets(port)
    http_server = tornado.httpserver.HTTPServer(app)
    http_server.add_sockets(sockets)
    print("Server Start Running!\nHost: {} Port: {}".format("127.0.0.1", port))
    tornado.ioloop.IOLoop.instance().start()
```

### Step 3: 运行项目

```shell
$ python server.py
```

使用浏览器打开 http://127.0.0.1:8889 即可访问服务

![image](https://user-images.githubusercontent.com/17564655/64065362-2fe42e80-cc3f-11e9-8d06-7552414748f1.png)


## 定时全量更新图表
> 前端主动向后端进行数据刷新

定时刷新的核心在于 html 的 `setInterval` 方法。

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
                url: "http://127.0.0.1:8889/getBarChart",
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

## 定时增量更新图表

* 可以参照 Flask，Sanic，Django 的实现方式进行实现。
