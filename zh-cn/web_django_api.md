> 本指南按照 Django [官方教程](https://docs.djangoproject.com/en/1.11/intro/tutorial01/)，通过完成一个 Django 小项目来说明如何在 Django 中使用 pyecharts。结合 Django Rest Framework 实现前后端分离

## Step 0: 安装 Django 和 Django Rest framework 的依赖 (基于 Django 2.2.1)

```shell
pip install django
pip install djangorestframework
pip install markdown
pip install django-simple-serializer
```

## Step 1: 新建一个 django 项目

```shell
$ django-admin startproject pyecharts_django
```

创建一个应用程序

```shell
$ python manage.py startapp demo
```
在 `pyecharts_django_demo/settings.py` 中注册应用程序

```python
# pyecharts_django/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'demo',  # <--- app 名称
    'rest_framework',
]
```

在 `pyecharts_django/urls.py` 中新增 'demo.urls'

```python
from django.contrib import admin
from django.urls import path
from django.conf.urls import url, include

urlpatterns = [
    path('admin/', admin.site.urls),
    url(r'^demo/', include('demo.urls'))
]
```

编辑 `demo/urls.py` 文件(没有就新建一个)

```python
from django.conf.urls import url
from . import views

urlpatterns = [
    url(r'^bar/$', views.ChartView.as_view(), name='demo'),
    url(r'^index/$', views.IndexView.as_view(), name='demo'),
]
```

## Step 2 编写画图 html 代码

先在根目录文件夹下新建 templates 文件夹，新建一个 index.html

```shell
sunhailindeMacBook-Pro:pyecharts_django sunhailin$ ls
__pycache__   db.sqlite3   demo   manage.py  pyecharts_django  templates
```

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
        var chart = echarts.init(document.getElementById('bar'), 'white', {renderer: 'canvas'});

        $(
            function () {
                getData(chart);
            }
        );

        function getData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:8000/demo/bar",
                dataType: 'json',
                success: function (result) {
                    console.log(result);
                    chart.setOption(result.data);
                }
            });
        }
    </script>
</body>
</html>
```

## Step 3: 编写 Django 和 pyecharts 代码渲染图表

将下列代码保存到 `demo/views.py` 中

```python
from random import randrange

from django.http import HttpResponse
from dss.Serializer import serializer
from rest_framework.views import APIView

from pyecharts.charts import Bar
from pyecharts import options as opts


# Create your views here.
def response_as_json(data, foreign_penetrate=False):
    json_str = serializer(data=data, output_type="json", foreign=foreign_penetrate)
    response = HttpResponse(
        json_str,
        content_type="application/json",
    )
    response["Access-Control-Allow-Origin"] = "*"
    return response


def json_response(data, code=200, foreign_penetrate=False, **kwargs):
    data = {
        "code": code,
        "msg": "success",
        "data": data,
    }
    return response_as_json(data, foreign_penetrate=foreign_penetrate)


def json_error(error_string="error", code=500, **kwargs):
    data = {
        "code": code,
        "msg": error_string,
        "data": {}
    }
    data.update(kwargs)
    return response_as_json(data)


JsonResponse = json_response
JsonError = json_error


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


class ChartView(APIView):
    def get(self, request, *args, **kwargs):
        return JsonResponse(bar_base())


class IndexView(APIView):
    def get(self, request, *args, **kwargs):
        return HttpResponse(content=open("./templates/index.html").read())

```

## Step 4: 运行项目

```shell
$ python manage.py runserver
```

使用浏览器打开 http://127.0.0.1:8000/demo/index 即可访问服务

![](https://user-images.githubusercontent.com/17564655/57363412-a30af600-71b3-11e9-934b-0caa11c979b7.png)


## Extension Function 1: 定时全量更新图表 (前端主动向后端进行数据刷新)

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
                url: "http://127.0.0.1:8000/demo/bar",
                dataType: 'json',
                success: function (result) {
                    console.log(result);
                    chart.setOption(result.data);
                }
            });
        }
    </script>
</body>
</html>
```

## Extension Function 2: 定时增量更新图表

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
        var old_data = [];
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
            interval = setInterval(getDynamicData, 2000);
            alert("计时器启动成功!")
        }

        function getData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:8000/demo/line",
                dataType: 'json',
                success: function (result) {
                    var options = result.data;
                    chart.setOption(options);
                    old_data = chart.getOption().series[0].data;
                }
            });
        }

        function getDynamicData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:8000/demo/lineUpdate",
                dataType: 'json',
                success: function (result) {
                    var options = result.data;
                    old_data.push([options.name, options.value]);
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

后端代码也需要相应做出改变

编辑 `demo/urls.py` 文件(没有就新建一个)

```python
from django.conf.urls import url
from . import views

urlpatterns = [
    url(r'^line/$', views.ChartView.as_view(), name='demo'),
    url(r'^lineUpdate/$', views.ChartUpdateView.as_view(), name='demo'),
    url(r'^index/$', views.IndexView.as_view(), name='demo'),
]
```


```python
from random import randrange

from django.http import HttpResponse
from dss.Serializer import serializer
from rest_framework.views import APIView

from pyecharts.charts import Line
from pyecharts import options as opts

# Create your views here.
def response_as_json(data, foreign_penetrate=False):
    json_str = serializer(data=data, output_type="json", foreign=foreign_penetrate)
    response = HttpResponse(
        json_str,
        content_type="application/json",
    )
    response["Access-Control-Allow-Origin"] = "*"
    return response


def json_response(data, code=200, foreign_penetrate=False, **kwargs):
    data = {
        "code": code,
        "msg": "success",
        "data": data,
    }
    return response_as_json(data, foreign_penetrate=foreign_penetrate)


def json_error(error_string="error", code=500, **kwargs):
    data = {
        "code": code,
        "msg": error_string,
        "data": {}
    }
    data.update(kwargs)
    return response_as_json(data)


JsonResponse = json_response
JsonError = json_error

i = 9


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
        .get_options()
    )
    return line


class ChartView(APIView):
    def get(self, request, *args, **kwargs):
        return JsonResponse(line_base())


class ChartUpdateView(APIView):
    def get(self, request, *args, **kwargs):
        global i
        i = i + 1
        return JsonResponse({"name": i, "value": randrange(0, 100)})

class IndexView(APIView):
    def get(self, request, *args, **kwargs):
        return HttpResponse(content=open("./templates/index.html").read())

```