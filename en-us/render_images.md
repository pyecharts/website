Rendering to images using pyecharts has always been a feature of interest to developers. pyecharts provides `selenium`, `phantomjs` and `pyppeteer` in three ways.

## make_snapshot

> make_snapshot for pyecharts to generate images directly

### Introduce

```python
from pyecharts.render import make_snapshot
```

### API

```python
def make_snapshot(
    # Rendering engine, either selenium or phantomjs
    engine: Any,

    # pass in the path to the HTML file
    file_name: str,

    # The path to the output image
    output_name: str,

    # Delay time to avoid generating images before the image has been rendered, resulting in incomplete images
    delay: float = 2,

    # pixel ratio, used to adjust the image quality
    pixel_ratio: int = 2,

    # Whether to remove the original HTML file after rendering the image
    is_remove_html: bool = False,

    # Browser type, currently only supports Chrome, Safari, valid when using snapshot-selenium
    browser: str = "Chrome",
    **kwargs,
)
```

## snapshot-selenium

### Install

```shell
$ pip install snapshot-selenium
```

[snapshot-selenium](https://github.com/pyecharts/snapshot-selenium) is an extension for pyecharts + selenium to render images, you need to configure the browser driver to use selenium, you can refer to [selenium-python](https://selenium-python.readthedocs.io/installation.html#drivers) for this part. Chrome, Safari are currently supported.


### Usage

```python
from pyecharts import options as opts
from pyecharts.charts import Bar
from pyecharts.render import make_snapshot

from snapshot_selenium import snapshot

def bar_chart() -> Bar:
    c = (
        Bar()
        .add_xaxis(["衬衫", "毛衣", "领带", "裤子", "风衣", "高跟鞋", "袜子"])
        .add_yaxis("商家A", [114, 55, 27, 101, 125, 27, 105])
        .add_yaxis("商家B", [57, 134, 137, 129, 145, 60, 49])
        .reversal_axis()
        .set_series_opts(label_opts=opts.LabelOpts(position="right"))
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-测试渲染图片"))
    )
    return c

make_snapshot(snapshot, bar_chart().render(), "bar0.png")
```

## snapshot-phantomjs

### Install

```shell
$ pip install snapshot-phantomjs
```

[snapshot-phantomjs](https://github.com/pyecharts/snapshot-phantomjs) is an extension of pyecharts + phantomjs to render images, you need to install phantomjs first, please refer to the official website for the installation method [phantomjs.org/download.html](http://phantomjs.org/download.html)

### Usage

```python
from pyecharts import options as opts
from pyecharts.charts import Bar
from pyecharts.render import make_snapshot

from snapshot_phantomjs import snapshot

def bar_chart() -> Bar:
    c = (
        Bar()
        .add_xaxis(["衬衫", "毛衣", "领带", "裤子", "风衣", "高跟鞋", "袜子"])
        .add_yaxis("商家A", [114, 55, 27, 101, 125, 27, 105])
        .add_yaxis("商家B", [57, 134, 137, 129, 145, 60, 49])
        .reversal_axis()
        .set_series_opts(label_opts=opts.LabelOpts(position="right"))
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-测试渲染图片"))
    )
    return c

make_snapshot(snapshot, bar_chart().render(), "bar0.png")
```

## snapshot-pyppeteer

### Install

```shell
$ pip install snapshot-pyppeteer

# After installation, it is recommended to execute the chromium installation command
pyppeteer-install
```

[snapshot-pyppeteer](https://github.com/pyecharts/snapshot-pyppeteer) is an extension for pyecharts + pyppeteer to render images, you need to install pyppeteer and Chromium first, please refer to the repository address for the installation method. [snapshot-pyppeteer](https://github.com/pyecharts/snapshot-pyppeteer)

### Usage

```python
from snapshot_pyppeteer import snapshot

from pyecharts.charts import Bar
from pyecharts.faker import Faker
from pyecharts import options as opts
from pyecharts.render import make_snapshot


def bar_base() -> Bar:
    c = (
        Bar()
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts(title="Bar-基本示例", subtitle="我是副标题"))
    )
    make_snapshot(snapshot, c.render(), "bar.png")


if __name__ == '__main__':
    bar_base()
```
