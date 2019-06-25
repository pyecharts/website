## 如何安装

### pyecharts

#### pip 安装
```shell
$ pip install pyecharts
```

#### 源码安装
```shell
$ git clone https://github.com/pyecharts/pyecharts.git
$ cd pyecharts
$ pip install -r requirements.txt
$ python setup.py install
# 或者执行 python install.py
```

## 5 分钟上手

> 首先开始来绘制你的第一个图表

```python
from pyecharts.charts import Bar

bar = Bar()
bar.add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
bar.add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
# render 会生成本地 HTML 文件，默认会在当前目录生成 render.html 文件
# 也可以传入路径参数，如 bar.render("mycharts.html")
bar.render()
```
![](https://user-images.githubusercontent.com/19553554/55601215-656d1480-5792-11e9-87ac-19b912619d7f.png)

> pyecharts 所有方法均支持链式调用。

```python
from pyecharts.charts import Bar

bar = (
    Bar()
    .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
    .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
)
bar.render()
```

> 使用 options 配置项，在 pyecharts 中，一切皆 Options。

```python
from pyecharts.charts import Bar
from pyecharts import options as opts

# V1 版本开始支持链式调用
# 你所看到的格式其实是 `black` 格式化以后的效果
# 可以执行 `pip install black` 下载使用
bar = (
    Bar()
    .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
    .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
    .set_global_opts(title_opts=opts.TitleOpts(title="主标题", subtitle="副标题"))
    # 或者直接使用字典参数
    # .set_global_opts(title_opts={"text": "主标题", "subtext": "副标题"})
)
bar.render()

# 不习惯链式调用的开发者依旧可以单独调用方法
bar = Bar()
bar.add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
bar.add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
bar.set_global_opts(title_opts=opts.TitleOpts(title="主标题", subtitle="副标题"))
bar.render()
```
![](https://user-images.githubusercontent.com/19553554/55601443-85510800-5793-11e9-8479-26ff27cdec7e.png)

> 渲染成图片文件，这部分内容请参考 **进阶话题-渲染图片**

```python
from pyecharts.charts import Bar
from pyecharts.render import make_snapshot

# 使用 snapshot-selenium 渲染图片
from snapshot_selenium import snapshot

bar = (
    Bar()
    .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
    .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
)
make_snapshot(snapshot, bar.render(), "bar.png")
```

### 使用主题

pyecharts 提供了 10+ 种内置主题，开发者也可以定制自己喜欢的主题，**进阶话题-定制主题** 有相关介绍。

```python
from pyecharts.charts import Bar
from pyecharts import options as opts
# 内置主题类型可查看 pyecharts.globals.ThemeType
from pyecharts.globals import ThemeType

bar = (
    Bar(init_opts=opts.InitOpts(theme=ThemeType.LIGHT))
    .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
    .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
    .add_yaxis("商家B", [15, 6, 45, 20, 35, 66])
    .set_global_opts(title_opts=opts.TitleOpts(title="主标题", subtitle="副标题"))
)
```
![](https://user-images.githubusercontent.com/19553554/55601589-26d85980-5794-11e9-828e-56ae109819f2.png)

> Note: 在使用 Pandas&Numpy 时，请确保将数值类型转换为 python 原生的 int/float。比如整数类型请确保为 int，而不是 numpy.int32

### Notebook 示例

> 当然你也可以采用更加酷炫的方式，使用 Notebook 来展示图表，matplotlib 有的，pyecharts 也会有的

#### Jupyter Notebook

Jupyter Notebook 直接调用 `render_notebook` 随时随地渲染图表

![](https://user-images.githubusercontent.com/19553554/55602094-715ad580-5796-11e9-8477-d745ce9b8a20.png)

#### Jupyter Lab

Jupyter Lab 渲染的时候有两点需要注意
1. 在顶部声明 Notebook 类型，必须在引入 pyecharts.charts 等模块前声明
    ```python
    from pyecharts.globals import CurrentConfig, NotebookType
    CurrentConfig.NOTEBOOK_TYPE = NotebookType.JUPYTER_LAB
    ```
2. 在第一次渲染的时候调用 `load_javascript()` 会预先加载基本 JavaScript 文件到 Notebook 中。如若后面其他图形渲染不出来，则请开发者尝试再次调用，因为 `load_javascript` 只会预先加载最基本的 js 引用。而主题、地图等 js 文件需要再次按需加载。

![](https://user-images.githubusercontent.com/19553554/55602584-f2b36780-5798-11e9-8ce4-b579344b3a8f.png)
![](https://user-images.githubusercontent.com/19553554/55602583-f2b36780-5798-11e9-9fcd-ad0de498f7f1.png)

#### nteract

nteract 渲染的时候在顶部引入 IPython.display 的两个方法
```python
from IPython.display import display, HTML
```

nteract 调用 `render_embed` 再通过 `IPython.display` 的方法即可渲染
```python
import pyecharts.options as opts
from pyecharts.charts import Bar, Line
from pyecharts.globals import ThemeType
from IPython.display import HTML, display

bar = (
    Bar(init_opts=opts.InitOpts(theme=ThemeType.MACARONS))
    .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
    .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
    .add_yaxis("商家B", [15, 6, 45, 20, 35, 66])
    .set_global_opts(title_opts=opts.TitleOpts(title="主标题", subtitle="副标题"))
)

# 渲染图例
html_content = bar.render_embed()
display(HTML(html_content))
```

![](https://user-images.githubusercontent.com/17564655/60080911-5c715b00-9763-11e9-9e14-7afaa0df2efe.png)

#### Zeppelin

Zeppelin 渲染的时候有需要注意
1. Zeppelin 环境下的 Python 解释器需要切换到 Python3 且环境下的 Python3 版本为 Python 3.6+

Zeppelin 直接调用 `render_embed` 之后通过 Zeppelin 的内置规则进行渲染
```python
%python
import pyecharts.options as opts
from pyecharts.charts import Bar
from pyecharts.globals import ThemeType

bar = (
    Bar(init_opts=opts.InitOpts(theme=ThemeType.MACARONS))
    .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
    .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
    .add_yaxis("商家B", [15, 6, 45, 20, 35, 66])
    .set_global_opts(title_opts=opts.TitleOpts(title="主标题", subtitle="副标题"))
)

# print 函数中的 %html 即是 Zeppelin 输出 HTML 代码的规则
html_content = bar.render_embed()
print("%html " + html_content)
```

![](https://user-images.githubusercontent.com/17564655/60081761-fd144a80-9764-11e9-9e88-f5056eecf871.png)
