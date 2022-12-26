> This guide describes how to use pyecharts in Django.

## Django Template Rendering

### Step 0: Create a new Django project

```shell
$ django-admin startproject pyecharts_django_demo
```

Create an application

```shell
$ python manage.py startapp demo
```
Register the application in `pyecharts_django_demo/settings.py`

```python
# pyecharts_django_demo/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'demo'  # <---
]
```

Edit the `demo/urls.py` file

```python
# demo/urls.py
from django.conf.urls import url

from . import views

urlpatterns = [
    url(r'^$', views.index, name='index'),
]
```

Add 'demo.urls' to `pyecharts_django_demo/urls.py`

```python
pyecharts_django_demo/urls.py
from django.conf.urls import include, url
from django.contrib import admin

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'demo/', include('demo.urls'))  # <---
]
```

### Step 1: Copy the pyecharts template

First, create a new templates folder under the `demo` folder

```shell
chenjiandongx@DESKTOP-E83NUHA:/mnt/d/Python/pyecharts-django-demo/pyecharts_django_demo/demo$ ls
__init__.py  __pycache__  admin.py  apps.py  migrations  models.py  templates  tests.py  urls.py  views.py
```

Copy the pyecharts template, located in `pyecharts.render.templates`, to the templates folder you just created

```shell
chenjiandongx@DESKTOP-E83NUHA:/mnt/d/Python/pyecharts-django-demo/pyecharts_django_demo/demo/templates$ tree
.
├── jupyter_lab.html
├── jupyter_notebook.html
├── macro
├── nteract.html
├── simple_chart.html
├── simple_page.html
└── table.html
```

### Step 2: Render the chart

Save the following code to `demo/views.py`.

```python
from jinja2 import Environment, FileSystemLoader
from pyecharts.globals import CurrentConfig
from django.http import HttpResponse

CurrentConfig.GLOBAL_ENV = Environment(loader=FileSystemLoader("./demo/templates"))

from pyecharts import options as opts
from pyecharts.charts import Bar


def index(request):
    c = (
        Bar()
        .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
        .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
        .add_yaxis("商家B", [15, 25, 16, 55, 48, 8])
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-基本示例", subtitle="我是副标题"))
    )
    return HttpResponse(c.render_embed())
```

### Step 3: Run the project


```shell
$ python manage.py runserver
```

Use your browser to open http://127.0.0.1:8000/demo to access the service

![](https://user-images.githubusercontent.com/19553554/56732269-5d9c0100-678f-11e9-9006-e23c62b4decf.png)


## Django front-end and back-end separation

### Step 0: Create a new Django project

```shell
$ django-admin startproject pyecharts_django_demo
```

Create an application

```shell
$ python manage.py startapp demo
```
Register the application in `pyecharts_django_demo/settings.py`

```python
# pyecharts_django_demo/settings.py
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

Add 'demo.urls' to `pyecharts_django_demo/urls.py`

```python
from django.contrib import admin
from django.urls import path
from django.conf.urls import url, include

urlpatterns = [
    path('admin/', admin.site.urls),
    url(r'^demo/', include('demo.urls'))
]
```

Edit the `demo/urls.py` file (create a new one if you don't have one)

```python
from django.conf.urls import url
from . import views

urlpatterns = [
    url(r'^bar/$', views.ChartView.as_view(), name='demo'),
    url(r'^index/$', views.IndexView.as_view(), name='demo'),
]
```

### Step 2 Write HTML code for drawing

First, create a new templates folder in the root folder, create a new index.html

```shell
sunhailindeMacBook-Pro:pyecharts_django_demo sunhailin$ ls
__pycache__ db.sqlite3 demo manage.py pyecharts_django_demo templates
```

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
                fetchData(chart);
            }
        );

        function fetchData() {
            $.ajax({
                type: "GET",
                url: "http://127.0.0.1:8000/demo/bar",
                dataType: 'json',
                success: function (result) {
                    chart.setOption(result.data);
                }
            });
        }
    </script>
</body>
</html>
```

### Step 3: Write Django and pyecharts code to render charts

Note: Currently, due to the problem of json data type, it is not possible to convert JSCode data in pyecharts to json data format and return it to the front-end page. Therefore, avoid using JSCode for charting if you are using front-end and back-end separation.

Save the following code to `demo/views.py`

```python
import json
from random import randrange

from django.http import HttpResponse
from rest_framework.views import APIView

from pyecharts.charts import Bar
from pyecharts import options as opts


# Create your views here.
def response_as_json(data):
    json_str = json.dumps(data)
    response = HttpResponse(
        json_str,
        content_type="application/json",
    )
    response["Access-Control-Allow-Origin"] = "*"
    return response


def json_response(data, code=200):
    data = {
        "code": code,
        "msg": "success",
        "data": data,
    }
    return response_as_json(data)


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
        .dump_options_with_quotes()
    )
    return c


class ChartView(APIView):
    def get(self, request, *args, **kwargs):
        return JsonResponse(json.loads(bar_base()))


class IndexView(APIView):
    def get(self, request, *args, **kwargs):
        return HttpResponse(content=open("./templates/index.html").read())
```

### Step 4: Run the project

```shell
$ python manage.py runserver
```

Use your browser to open http://127.0.0.1:8000/demo/index to access the service

![](https://user-images.githubusercontent.com/17564655/57363412-a30af600-71b3-11e9-934b-0caa11c979b7.png)


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
    <div id="bar" style="width:1600px; height:800px;"></div>
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
                url: "http://127.0.0.1:8000/demo/bar",
                dataType: 'json',
                success: function (result) {
                    chart.setOption(result.data);
                }
            });
        }
    </script>
</body>
</html>
```

## Timed incremental chart update
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
    <div id="bar" style="width:1600px; height:800px;"></div>
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
                url: "http://127.0.0.1:8000/demo/line",
                dataType: "json",
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

The backend code needs to be changed accordingly

Edit the `demo/urls.py` file (or create a new one if you don't have one)

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
import json
from random import randrange

from django.http import HttpResponse
from rest_framework.views import APIView

from pyecharts.charts import Line
from pyecharts import options as opts

# Create your views here.
def response_as_json(data):
    json_str = json.dumps(data)
    response = HttpResponse(
        json_str,
        content_type="application/json",
    )
    response["Access-Control-Allow-Origin"] = "*"
    return response


def json_response(data, code=200):
    data = {
        "code": code,
        "msg": "success",
        "data": data,
    }
    return response_as_json(data)


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
        .dump_options_with_quotes()
    )
    return line


class ChartView(APIView):
    def get(self, request, *args, **kwargs):
        return JsonResponse(json.loads(line_base()))


cnt = 9


class ChartUpdateView(APIView):
    def get(self, request, *args, **kwargs):
        global cnt
        cnt = cnt + 1
        return JsonResponse({"name": cnt, "value": randrange(0, 100)})

class IndexView(APIView):
    def get(self, request, *args, **kwargs):
        return HttpResponse(content=open("./templates/index.html").read())
```

## Django 4.0 Change

Before
```python
from django.conf.urls import include, url 
```

After
```python
from django.urls import include
from django.urls import re_path as url
```

