> The current document you see is the latest version of the document. If there is a discrepancy between the document and the version you are using, please update pyecharts in a timely manner.

How do I check which version of pyecharts I am using?

```python
import pyecharts

print(pyecharts.__version__)
```

## How to install

**pip install**
```shell
$ pip(3) install pyecharts
```

**source install**
```shell
$ git clone https://github.com/pyecharts/pyecharts.git
$ cd pyecharts
$ pip install -r requirements.txt
$ python setup.py install
# or execute python install.py
```

## 5 minutes to get started

> Start by drawing your first graph

```python
from pyecharts.charts import Bar

bar = Bar()
bar.add_xaxis(["shirts", "cardigans", "chiffons", "trousers", "heels", "socks"])
bar.add_yaxis("Merchant A", [5, 20, 36, 10, 75, 90])
# render will generate a local HTML file, by default render.html will be generated in the current directory
# You can also pass in a path parameter, e.g. bar.render("mycharts.html")
bar.render()
```
![](https://user-images.githubusercontent.com/19553554/55601215-656d1480-5792-11e9-87ac-19b912619d7f.png)

> pyecharts all methods support chain calls.

```python
from pyecharts.charts import Bar

bar = (
    Bar()
    .add_xaxis(["shirts", "cardigans", "chiffons", "trousers", "heels", "socks"])
    .add_yaxis("Merchant A", [5, 20, 36, 10, 75, 90])
)
bar.render()
```

> Use the options configuration item, in pyecharts everything is Options.

```python
from pyecharts.charts import Bar
from pyecharts import options as opts

# Chain calls are supported from V1 onwards
# The format you see is actually ``black`` formatted
# You can download it by running `pip install black`
bar = (
    bar()
    .add_xaxis(["shirt", "cardigan", "chiffon", "trousers", "heels", "socks"])
    .add_yaxis("Merchant A", [5, 20, 36, 10, 75, 90])
    .set_global_opts(title_opts=opts.TitleOpts(title="Main Title", subtitle="Sub Title"))
    # Or just use the dictionary parameters
    # .set_global_opts(title_opts={"text": "main_title", "subtext": "subtitle"})
)
bar.render()

# Developers who are not used to chain calls can still call the methods individually
bar = Bar()
bar.add_xaxis(["shirt", "cardigan", "chiffon", "trousers", "heels", "socks"])
bar.add_yaxis("Merchant A", [5, 20, 36, 10, 75, 90])
bar.set_global_opts(title_opts=opts.TitleOpts(title="Main Title", subtitle="Sub Title"))
bar.render()
```
![](https://user-images.githubusercontent.com/19553554/55601443-85510800-5793-11e9-8479-26ff27cdec7e.png)

> Render to an image file, see **Advanced Topics - Rendering Images** for this part

```python
from pyecharts.charts import Bar
from pyecharts.render import make_snapshot

# Render images using snapshot-selenium
from snapshot_selenium import snapshot

bar = (
    bar()
    .add_xaxis(["shirt", "cardigan", "chiffon", "trousers", "heels", "socks"])
    .add_yaxis("Merchant A", [5, 20, 36, 10, 75, 90])
)
make_snapshot(snapshot, bar.render(), "bar.png")
```

### Using themes

pyecharts provides 10+ built-in themes, and developers can also customize their favorite themes, as described in **Advanced Topics - Customizing Themes**.

```python
from pyecharts.charts import Bar
from pyecharts import options as opts
# Built-in theme types can be found in pyecharts.globals.ThemeType
from pyecharts.globals import ThemeType

bar = (
    Bar(init_opts=opts.InitOpts(theme=ThemeType.LIGHT))
    .add_xaxis(["shirt", "cardigan", "chiffon", "trousers", "heels", "socks"])
    .add_yaxis("Merchant A", [5, 20, 36, 10, 75, 90])
    .add_yaxis("Merchant B", [15, 6, 45, 20, 35, 66])
    .set_global_opts(title_opts=opts.TitleOpts(title="Main Title", subtitle="Sub Title"))
)
```
![](https://user-images.githubusercontent.com/19553554/55601589-26d85980-5794-11e9-828e-56ae109819f2.png)

> Note: When using Pandas&Numpy, make sure to convert the numeric type to python's native int/float. e.g. make sure the integer type is int, not numpy.int32

### Using Notebook

Of course you can also take a cooler approach and use Notebook to display diagrams. matplotlib has it, so will pyecharts. pyecharts supports Jupyter Notebook / Jupyter Lab / Nteract / Zeppelin for rendering in all four environments. See [Advanced Topics/Notebook](zh-cn/notebook) for details
