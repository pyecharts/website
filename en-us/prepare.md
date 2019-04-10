> Basic Usage: This document describes the basic usage of the pyecharts library.

### Install pyecharts

#### Compatibility

Latest pyecharts 1.0.0 will drop python 2.7 support and will not be backward compactible.

#### pyecharts

pip install
```shell
$ pip install pyecharts
```

source code install
```shell
$ git clone https://github.com/pyecharts/pyecharts.git
$ cd pyecharts
$ pip install -r requirements.txt
$ python setup.py install
```

#### Map plugin

No more map plugin. Pyecharts 1.0.0 allow you register online resources from assets.pyecharts.org,  echarts-maps organisation or your own hosted assets.

### Quick start

Now, you are ready to make your first chart!
```python
from pyecharts import Bar
from pyecharts import options as opts

(Bar()
    .add_xaxis(["Microsoft", "Amazon", "IBM", "Oracl", "Google", "Alibaba"])
    .add_yaxis('2017-2018 Revenue in (billion $)', [21.2, 20.4, 10.3, 6.08, 4, 2.2])
    .set_global_opts(title_opts=opts.TitleOpts(title="Top cloud providers 2018", subtitle="2017-2018 Revenue"))
    .render() # generate a local HTML file
)
```

![guide-0](https://user-images.githubusercontent.com/4280312/55591624-e940e580-572d-11e9-9fe0-6d85d78be46a.png)

* ```add_xaxis()```
    show data item on xaxis

* ```add_yaxis()```
    bar chart values for yaxis 

* ```render()```
    creat a file named `render.html` in the root directory defaultly, which supports path parameter and set the location the file save in, for instance render(r"e:\my_first_chart.html"), open file with your browser.

In order to have toolbox buttons, you need to give a bit more configuration. Then you can click the image download button.

```python
from pyecharts import Bar
from pyecharts import options as opts

(Bar()
    .add_xaxis(["Microsoft", "Amazon", "IBM", "Oracl", "Google", "Alibaba"])
    .add_yaxis('2017-2018 Revenue in (billion $)', [21.2, 20.4, 10.3, 6.08, 4, 2.2])
    .set_global_opts(title_opts=opts.TitleOpts(title="Top cloud providers 2018", subtitle="2017-2018 Revenue"),
                     toolbox_opts=opts.ToolboxOpts())
    .render() # generate a local HTML file
)
```
![guide-1](https://user-images.githubusercontent.com/4280312/55645894-b05a4c80-57d1-11e9-8eda-e41f5ef7e9d0.png)


### Use theme

You will need pass on theme parameter:

```python
from pyecharts.globals import ThemeType
from pyecharts import Bar
from pyecharts import options as opts

(Bar(init_opts=opts.InitOpts(theme=ThemeType.DARK)))
    .add_xaxis(["Microsoft", "Amazon", "IBM", "Oracl", "Google", "Alibaba"])
    .add_yaxis('2017-2018 Revenue in (billion $)', [21.2, 20.4, 10.3, 6.08, 4, 2.2])
    .set_global_opts(title_opts=opts.TitleOpts(title="Top cloud providers 2018", subtitle="2017-2018 Revenue"))
    .render() # generate a local HTML file
)

```
![guide-2](https://user-images.githubusercontent.com/4280312/55646201-7b022e80-57d2-11e9-98bd-17f81f3a3333.png)

pyecharts supports extra 5 body colors, [Please move to the theme color for more configuration information](en-us/themes).


### Rendering as image

Pyecharts 1.0.0 can use selenim to render image. By default, 'png', 'jpeg' and 'svg' are supported.

```
pip install snapshot-selenium
```

By default, it uses Google Chrome in headless mode.

1. You will have to download chrome driver and make sure it is accessible on user path.

```
from pyecharts.render import make_snapshot
import snapshot_selenium.snapshot as driver

bar = (Bar()
    .add_xaxis(["Microsoft", "Amazon", "IBM", "Oracl", "Google", "Alibaba"])
    .add_yaxis('2017-2018 Revenue in (billion $)', [21.2, 20.4, 10.3, 6.08, 4, 2.2])
    .set_global_opts(title_opts=opts.TitleOpts(title="Top cloud providers 2018", subtitle="2017-2018 Revenue"))
)
make_snapshot(driver, bar.render(), 'bar.png')
```

To use Safari on MacOS, you will need to enable develop mode of Safari and eanble remote automation. 

```
from pyecharts.render import make_snapshot
import snapshot_selenium.snapshot as driver

bar = ...

make_snapshot(driver, bar.render(), 'bar.png', browser='Safari')
```

![safari-1](https://user-images.githubusercontent.com/4280312/55689958-3cf83c80-5983-11e9-997a-a7d711f48875.png)


For more details, please refer to [selenium driver on mac](https://www.dev2qa.com/python-how-to-launch-safari-firefox-chrome-in-selenium-webdriver/)

#### more image formats

For more image formats, you have install PIL to get pdf, gif, raw etc.

```
pip install PIL
```

#### Use phantomjs

For old users, you can still use phantomjs. 

```
pip install snapshot-phantomjs
```

And tweak the import line slightly, you will be using phantomjs instead of selenium.

```
from pyecharts.render import make_snapshot
import snapshot_phantomjs.snapshot as driver

bar = ...

make_snapshot(driver, bar.render(), 'bar.png')
```


### Pandas & Numpy examples

Here is the example to work with Pandas and Numpy.

![pandas-numpy](https://user-images.githubusercontent.com/19553554/35104252-3e36cee2-fca3-11e7-8e43-09bbe8dbbd1e.pnghttps://user-images.githubusercontent.com/4280312/55858071-a1bfbc80-5b66-11e9-9189-1e309b667cb1.png)

**Note:** When using Pandas&Numpy, ensure that the integer type is int instead of numpy.int32

**Of course you can use the cooler way, use Jupyter Notebook to show the chart. What matplotlib have，so do pyecharts**


like this

![notebook-0](https://user-images.githubusercontent.com/19553554/35104153-f6256212-fca2-11e7-854c-bacc61eabf6f.gif)

and this

![notebook-1](https://user-images.githubusercontent.com/19553554/35104157-fa39e170-fca2-11e7-9738-1547e22914a6.gif)

more Jupyter notebook examples, please refer to [notebook-use-cases](https://github.com/chenjiandongx/pyecharts/blob/master/document/notebook-use-cases.ipynb). You could download and run it on your notebook.

Use Jupyter Notebook to display charts, just call your own instance and be compatible with Python2 and Python3's Jupyter Notebook environment. All charts can be displayed normally, and the interactive experience is consistent with the browser. It is even no need PPT with this method to display report! !
