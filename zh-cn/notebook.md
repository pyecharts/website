不同的 Notebook 环境有自己不同的渲染要求，pyecharts 在底层做了适配处理，但因为我们无法在 `import pyecharts` 的时候知道用户具体使用的是哪种 Notebook 环境，所以需要用户在使用时在**顶部**声明环境类型。

## Jupyter Notebook

Jupyter Notebook 直接调用 `render_notebook` 随时随地渲染图表，默认为 `Jupter-Notebook`。

![](https://user-images.githubusercontent.com/19553554/55602094-715ad580-5796-11e9-8477-d745ce9b8a20.png)

## Jupyter Lab

Jupyter Lab 渲染的时候有两点需要注意
1. 在顶部声明 Notebook 类型，必须在引入 pyecharts.charts 等模块前声明
    ```python
    from pyecharts.globals import CurrentConfig, NotebookType
    CurrentConfig.NOTEBOOK_TYPE = NotebookType.JUPYTER_LAB
    ```
2. 在第一次渲染的时候调用 `load_javascript()` 会预先加载基本 JavaScript 文件到 Notebook 中。如若后面其他图形渲染不出来，则请开发者尝试再次调用，因为 `load_javascript` 只会预先加载最基本的 js 引用。而主题、地图等 js 文件需要再次**按需加载**。
3. `load_javascript()` 和 `render_notebook()` 方法需要在不同的 cell 中调用，这是 Notebook 的内联机制，其实本质上我们是返回了带有 `_html_`, `_javascript_` 对象的 class。notebook 会自动去调用这些方法。

![](https://user-images.githubusercontent.com/19553554/55602584-f2b36780-5798-11e9-8ce4-b579344b3a8f.png)
![](https://user-images.githubusercontent.com/19553554/55602583-f2b36780-5798-11e9-9fcd-ad0de498f7f1.png)

## Nteract

Nteract 渲染的时候有两点需要注意
1. 在顶部声明 Notebook 类型，必须在引入 pyecharts.charts 等模块前声明
    ```python
    from pyecharts.globals import CurrentConfig, NotebookType
    CurrentConfig.NOTEBOOK_TYPE = NotebookType.NTERACT
    ```

nteract 调用 `render_notebook` 方法即可渲染

```python
from pyecharts.globals import CurrentConfig, NotebookType
CurrentConfig.NOTEBOOK_TYPE = NotebookType.NTERACT

import pyecharts.options as opts
from pyecharts.charts import Bar, Line

bar = (
    Bar()
    .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
    .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
    .add_yaxis("商家B", [15, 6, 45, 20, 35, 66])
    .set_global_opts(title_opts=opts.TitleOpts(title="主标题", subtitle="副标题"))
)

bar.render_notebook()
```

![](https://user-images.githubusercontent.com/17564655/60228718-2698b780-98c6-11e9-8d66-a9d8d057c344.png)

## Zeppelin

Zeppelin 渲染的时候有需要注意
1. 在顶部声明 Notebook 类型，必须在引入 pyecharts.charts 等模块前声明
    ```python
    from pyecharts.globals import CurrentConfig, NotebookType
    CurrentConfig.NOTEBOOK_TYPE = NotebookType.ZEPPELIN
    ```

Zeppelin 调用 `render_notebook` 方法即可渲染
```python
%python
from pyecharts.globals import CurrentConfig, NotebookType
CurrentConfig.NOTEBOOK_TYPE = NotebookType.ZEPPELIN

import pyecharts.options as opts
from pyecharts.charts import Bar

bar = (
    Bar()
    .add_xaxis(["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"])
    .add_yaxis("商家A", [5, 20, 36, 10, 75, 90])
    .add_yaxis("商家B", [15, 6, 45, 20, 35, 66])
    .set_global_opts(title_opts=opts.TitleOpts(title="主标题", subtitle="副标题"))
)

bar.render_notebook()
```

![](https://user-images.githubusercontent.com/17564655/60228824-8abb7b80-98c6-11e9-9435-0fc8777624d0.png)
