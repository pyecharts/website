> pyecharts.org 不做版本管理，您所看到的当前文档为最新版文档，若文档与您使用的版本出现不一致情况，请及时更新 pyecharts。

如何查看使用的 pyecharts 版本？

```python
import pyecharts

print(pyecharts.__version__)
```

## 如何安装

**pip 安装**
```shell
$ pip(3) install pyecharts
```

**源码安装**
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

### 使用 Notebook

当然你也可以采用更加酷炫的方式，使用 Notebook 来展示图表，matplotlib 有的，pyecharts 也会有的。pyecharts 支持 Jupyter Notebook / Jupyter Lab / Nteract / Zeppelin 四种环境的渲染。具体内容请参考 [进阶话题/Notebook](zh-cn/notebook)
