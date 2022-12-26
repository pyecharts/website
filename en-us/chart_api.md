The `Base` class is the base class for all charts, including combined charts, and the `Base` class API is as follows

> *func pyecharts.Base.add_js_funcs*

```python
# add js code, the js code will be rendered into the HTML for execution
def add_js_funcs(*fns):
```

> *func pyecharts.Base.set_colors*

``` python
# Set global Label colours
def set_colors(colors: colors: Sequence[str])
```

> *func pyecharts.Base.get_options*

``` python
# Get global options
def get_options() -> dict:
```

> *func pyecharts.Base.dump_options*

``` python
# Get global options, in JSON format (JsCode generated functions without quotes)
def dump_options() -> str:
```

```python
# Get global options, in JSON format (JsCode generated function with quotes, used when transferring data separately from front and back end)
def dump_options_with_quotes() -> str:
```

> *func pyecharts.Base.render*

``` python
# Render the chart to an HTML file
def render(
    # Generate the path to the image
    path: str = "render.html",

    # Template path
    template_name: str = "simple_chart.html",

    # jinja2.Environment class instance, you can configure various environment parameters
    env: Optional[Environment] = None,
) -> str
```

> *func pyecharts.Base.render_embed*

``` python
# Render charts to HTML strings
def render_embed(
    # Template path
    template_name: str = "simple_chart.html",
    
    # jinja2.Environment class instance that can be configured with various environment parameters
    env: Optional[Environment] = None,
) -> str:
```

> *func pyecharts.Base.render_notebook*

``` python
# Render the graph to the notebook
def render_notebook()
```

> *func pyecharts.Base.load_javascript*

```python
# Load js resource, needed when the notebook environment is JupyterLab, just use load before rendering the graph for the first time.
def load_javascript()
```
