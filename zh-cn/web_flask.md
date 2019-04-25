> 本指南会以一个小的 Flask 项目为例，说明如何在 Flask 中使用 pyecharts。关于 jinja2 模板的更多内容，可以参考 [jinja2](http://jinja.pocoo.org/docs/2.10/)

## Step 0: 新建一个 Flask 项目

```shell
$ mkdir pyecharts-flask-demo
$ cd pyecharts-flask-demo
$ mkdir templates
```

## Step 1: 拷贝 pyecharts 模板

将 pyecharts 模板，位于 `pyecharts.render.templates` 拷贝至刚新建的 templates 文件夹

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

## Step 2: 渲染图表 

请将下面的代码保存为 server.py 文件并移至项目的根目录下。

目录结构如下
```shell
chenjiandongx@DESKTOP-E83NUHA:/mnt/d/Python/pyecharts-flask-demo$ tree -L 1
.
├── server.py
└── templates
```

示例代码
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

## Step 3: 运行项目

```shell
$ python server.py
```
