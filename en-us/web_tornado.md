> This guide describes how to use pyecharts in Tornado.

## Tornado Front and Back End Separation

> Front and back-end separation allows you to use features such as dynamically updating data, incrementally updating data, etc.

### Step 0: Install Tornado dependencies

```shell
$ pip install tornado
```

### Step 1: Create a new project and HTML file

Create a new project folder (empty), create server.py, index.html.

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

### Step 2: Write the code for Tornado and pyecharts

Note: At present, due to the problem of json data type, it is impossible to convert JSCode data in pyecharts into json data format and return it to the front-end page. Therefore, you should avoid using JSCode for drawing if you are using front-end and back-end separation.

Sample code
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

### Step 3: Run the project

```shell
$ python server.py
```

Use your browser to open http://127.0.0.1:8889 to access the service

![image](https://user-images.githubusercontent.com/17564655/64065362-2fe42e80-cc3f-11e9-8d06-7552414748f1.png)


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

# # Timed incremental chart updates

* Can be implemented by referring to Flask, Sanic, Django implementations.
