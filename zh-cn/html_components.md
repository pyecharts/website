## Component 通用配置项

```python
class ComponentTitleOpts(
    # 主标题，支持 \n 换行
    title: str = "",

    # 副标题，支持 \n 换行
    subtitle: str = "",

    # 主标题 CSS 样式
    title_style: Optional[dict] = None,

    # 副标题 CSS 样式
    subtitle_style: Optional[dict] = None,
)
```

> Note: 目前 Table 和 Image 两者与 Page 类并不兼容

## Table：表格

> *class pyecharts.components.Table*

```python
class Table(
    # HTML 标题
    page_title: str = CurrentConfig.PAGE_TITLE,

    # 远程 HOST，默认为 "https://assets.pyecharts.org/assets/"
    js_host: str = "",
)
```

> *func pyecharts.components.Table.add*

```python
def add(
    # 表格 headers
    headers: Sequence,

    # 表格数据
    rows: Sequence, 

    # 表格样式属性
    attributes: Optional[dict] = None
)
```

> *func pyecharts.components.Table.set_global_opts*

```python
def set_global_opts(
    # 标题配置项，参考 `ComponentTitleOpts`
    title_opts: Union[ComponentTitleOpts, dict, None] = None
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Table/README)


## Image：图像

> *class pyecharts.components.Image*

```python
class Image(
    # HTML 标题
    page_title: str = CurrentConfig.PAGE_TITLE,

    # 远程 HOST，默认为 "https://assets.pyecharts.org/assets/"
    js_host: str = "",
)
```

> *func pyecharts.components.Image.add*

```python
def add(
    # 图像 src
    src: str, 

    # <img> 标签 CSS 样式
    style_opts: Optional[dict] = None
)
```

> *func pyecharts.components.Image.set_global_opts*

```python
def set_global_opts(
    # 标题配置项，参考 `ComponentTitleOpts`
    title_opts: Union[ComponentTitleOpts, dict, None] = None
)
```

### Demo

[gallery 示例](http://gallery.pyecharts.org/#/Image/README)
