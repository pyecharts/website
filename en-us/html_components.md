## Component General configuration items

```python
class ComponentTitleOpts(
    # Main title, supports \n line breaks
    title: str = "",

    # subtitle, with \n line breaks
    subtitle: str = "",

    # Main title CSS style
    title_style: Optional[dict] = None,

    # Subtitle CSS style
    subtitle_style: Optional[dict] = None,
)
```

> Note: Table and Image are currently not compatible with the Page class.

## Table: table

> *class pyecharts.components.Table*

```python
class Table(
    ## HTML title
    page_title: str = CurrentConfig.PAGE_TITLE,

    # Remote HOST, defaults to "https://assets.pyecharts.org/assets/"
    js_host: str = "",
)
```

> *func pyecharts.components.Table.add*

```python
def add(
    # Table headers
    headers: Sequence,

    # Table Data
    rows: Sequence, 

    # Table attributes
    attributes: Optional[dict] = None
)
```

> *func pyecharts.components.Table.set_global_opts*

```python
def set_global_opts(
    # Title configuration items, see `ComponentTitleOpts`
    title_opts: Union[ComponentTitleOpts, dict, None] = None
)
```


### Demo

[gallery example](http://gallery.pyecharts.org/#/Table/README)

## Image：Image

> *class pyecharts.components.Image*

```python
class Image(
    # HTML Title
    page_title: str = CurrentConfig.PAGE_TITLE,

    # js host，default "https://assets.pyecharts.org/assets/"
    js_host: str = "",
)
```

> *func pyecharts.components.Image.add*

```python
def add(
    # image src
    src: str, 

    # <img> tag CSS
    style_opts: Optional[dict] = None
)
```

> *func pyecharts.components.Image.set_global_opts*

```python
def set_global_opts(
    # Title configuration items, see `ComponentTitleOpts`
    title_opts: Union[ComponentTitleOpts, dict, None] = None
)
```

### Demo

[gallery example](http://gallery.pyecharts.org/#/Image/README)
