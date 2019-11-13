使用 pyecharts 渲染成图片一直是开发者比较关心的功能，pyecharts 提供了 `selenium`, `phantomjs` 和 `pyppeteer` 三种方式。

## make_snapshot

> make_snapshot 用于 pyecharts 直接生成图片

### 引入

```python
from pyecharts.render import make_snapshot
```

### API

```python
def make_snapshot(
    # 渲染引擎，可选 selenium 或者 phantomjs
    engine: Any,

    # 传入 HTML 文件路径
    file_name: str,

    # 输出图片路径
    output_name: str,

    # 延迟时间，避免图还没渲染完成就生成了图片，造成图片不完整
    delay: float = 2,

    # 像素比例，用于调节图片质量
    pixel_ratio: int = 2,

    # 渲染完图片是否删除原 HTML 文件
    is_remove_html: bool = False,

    # 浏览器类型，目前仅支持 Chrome, Safari，使用 snapshot-selenium 时有效
    browser: str = "Chrome",
    **kwargs,
)
```

## snapshot-selenium

### 安装

```shell
$ pip install snapshot-selenium
```

[snapshot-selenium](https://github.com/pyecharts/snapshot-selenium) 是 pyecharts + selenium 渲染图片的扩展，使用 selenium 需要配置 browser driver，这部分可以参考 [selenium-python](https://selenium-python.readthedocs.io/installation.html#drivers) 相关介绍，推荐使用 Chrome 浏览器，可以开启 headless 模式。目前支持 Chrome, Safari。


### 使用

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

### 安装

```shell
$ pip install snapshot-phantomjs
```

[snapshot-phantomjs](https://github.com/pyecharts/snapshot-phantomjs) 是 pyecharts + phantomjs 渲染图片的扩展，需要先安装 phantomjs，安装方法请参照官网 [phantomjs.org/download.html](http://phantomjs.org/download.html)

### 使用

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

### 安装

```shell
$ pip install snapshot-pyppeteer

# 安装完后建议执行 chromium 安装命令
pyppeteer-install
```

[snapshot-pyppeteer](https://github.com/pyecharts/snapshot-pyppeteer) 是 pyecharts + pyppeteer 渲染图片的扩展，需要先安装 pyppeteer 和 Chromium 安装方法请参照仓库地址 [snapshot-pyppeteer](https://github.com/pyecharts/snapshot-pyppeteer)

### 使用

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