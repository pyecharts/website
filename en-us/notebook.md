Different Notebook environments have their own different rendering requirements. pyecharts does the adaptation process at the bottom, but since we can't know exactly which Notebook environment the user is using when `import pyecharts`, we need the user to declare the environment type at the **top** when using it.

## Jupyter Notebook

Jupyter Notebook calls `render_notebook` directly to render charts anytime, anywhere, default is `Jupter-Notebook`.

![](https://user-images.githubusercontent.com/19553554/55602094-715ad580-5796-11e9-8477-d745ce9b8a20.png)

## Jupyter Lab

There are two things to keep in mind when rendering in Jupyter Lab
1. Declare the Notebook type at the top, which must be declared before introducing modules like pyecharts.charts
    ```python
    from pyecharts.globals import CurrentConfig, NotebookType
    CurrentConfig.NOTEBOOK_TYPE = NotebookType.JUPYTER_LAB
    ```
2. Calling `load_javascript()` during the first rendering will preload the basic JavaScript file into Notebook. If other graphics are not rendered later, the developer should try to call it again, because `load_javascript` will only preload the most basic js references. And js files such as themes, maps, etc. need to be loaded again **on demand**.
3. `load_javascript()` and `render_notebook()` methods need to be called in different cells, this is Notebook's inline mechanism, in fact we are essentially returning the class with `_html_`, `_javascript_` objects. notebook will automatically call these methods.

![](https://user-images.githubusercontent.com/19553554/55602584-f2b36780-5798-11e9-8ce4-b579344b3a8f.png)
![](https://user-images.githubusercontent.com/19553554/55602583-f2b36780-5798-11e9-9fcd-ad0de498f7f1.png)

## Nteract

There are two things to keep in mind when rendering with Nteract
1. Declare the Notebook type at the top, which must be declared before introducing modules like pyecharts.charts
    ```python
    from pyecharts.globals import CurrentConfig, NotebookType
    CurrentConfig.NOTEBOOK_TYPE = NotebookType.NTERACT
    ```

nteract calls the `render_notebook` method to render

``` python
from pyecharts.globals import CurrentConfig, NotebookType
CurrentConfig.NOTEBOOK_TYPE = NotebookType.NTERACT

import pyecharts.options as opts
from pyecharts.charts import Bar, Line

bar = (
    Bar()
    .add_xaxis(["shirt", "cardigan", "chiffon", "pants", "heels", "socks"])
    .add_yaxis("Merchant A", [5, 20, 36, 10, 75, 90])
    .add_yaxis("Merchant B", [15, 6, 45, 20, 35, 66])
    .set_global_opts(title_opts=opts.TitleOpts(title="Main Title", subtitle="Subtitle"))
)

bar.render_notebook()
```

![](https://user-images.githubusercontent.com/17564655/60228718-2698b780-98c6-11e9-8d66-a9d8d057c344.png)

## Zeppelin

There are some things to note when rendering in Zeppelin
1. Declare the Notebook type at the top, which must be declared before introducing modules like pyecharts.charts
    ```python
    from pyecharts.globals import CurrentConfig, NotebookType
    CurrentConfig.NOTEBOOK_TYPE = NotebookType.ZEPPELIN
    ```

Zeppelin calls the `render_notebook` method to render
```python
%python
from pyecharts.globals import CurrentConfig, NotebookType
CurrentConfig.NOTEBOOK_TYPE = NotebookType.ZEPPELIN

import pyecharts.options as opts
from pyecharts.charts import Bar

bar = (
    Bar()
    .add_xaxis(["shirt", "cardigan", "chiffon", "pants", "heels", "socks"])
    .add_yaxis("Merchant A", [5, 20, 36, 10, 75, 90])
    .add_yaxis("Merchant B", [15, 6, 45, 20, 35, 66])
    .set_global_opts(title_opts=opts.TitleOpts(title="Main Title", subtitle="Subtitle"))
)

bar.render_notebook()
```

![](https://user-images.githubusercontent.com/17564655/60228824-8abb7b80-98c6-11e9-9435-0fc8777624d0.png)
