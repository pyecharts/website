`Base` 类是所有图表的基类，包括组合图表，`Base` 类 API 如下

> *func pyecharts.Base.produce_js_func*

产生并包装一段 js 代码
```python
def produce_js_func(fn: str) -> str
```

> *func pyecharts.Base.add_js_funcs*

新增 js 代码，js 代码会被渲染进 HTML 中执行
```python
def add_js_funcs(self, *fns):
```

> *func pyecharts.Base.get_options*

获取全局 options
```python
def get_options(self) -> dict:
```

> *func pyecharts.Base.dump_options*

获取全局 options，JSON 格式
```python
def dump_options(self) -> str:
```

> *func pyecharts.Base.render*

渲染图表
```python
def render(
    self,
    # 生成图片路径
    path: str = "render.html",

    # 模板路径
    template_name: str = "simple_chart.html",

    # jinja2.Environment 类实例，可以配置各类环境参数
    env: Optional[Environment] = None,
) -> str
```

> *func pyecharts.Base.render_notebook*

将图形渲染到 notebook
```python
def render_notebook(self)
```

> *func pyecharts.Base.load_javascript*

加载 js 资源，在 notebook 环境为 JupyterLab 时需要用到，仅在第一次渲染图前使用加载即可。
```python
def load_javascript(self)
```
