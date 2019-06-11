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

```python
from pyecharts.components import Table
from pyecharts.options import ComponentTitleOpts


def table_base() -> Table:
    table = Table()

    headers = ["City name", "Area", "Population", "Annual Rainfall"]
    rows = [
        ["Brisbane", 5905, 1857594, 1146.4],
        ["Adelaide", 1295, 1158259, 600.5],
        ["Darwin", 112, 120900, 1714.7],
        ["Hobart", 1357, 205556, 619.5],
        ["Sydney", 2058, 4336374, 1214.8],
        ["Melbourne", 1566, 3806092, 646.9],
        ["Perth", 5386, 1554769, 869.4],
    ]
    table.add(headers, rows).set_global_opts(
        title_opts=ComponentTitleOpts(title="Table-我是主标题", subtitle="我是副标题支持换行哦")
    )
    return table
```
![](https://user-images.githubusercontent.com/19553554/58699998-7d979380-83d1-11e9-835f-cab3cfdbee06.png)


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

```python
from pyecharts.components import Image
from pyecharts.options import ComponentTitleOpts


def image_base() -> Image:
    image = Image()

    img_src = (
        "https://user-images.githubusercontent.com/19553554/396123"
        "58-499eb2ae-4f91-11e8-8f56-179c4f0bf2df.png"
    )
    image.add(
        src=img_src,
        style_opts={"width": "200px", "height": "200px", "style": "margin-top: 20px"},
    ).set_global_opts(
        title_opts=ComponentTitleOpts(title="Image-基本示例", subtitle="我是副标题支持换行哦")
    )
    return image
```
![](https://user-images.githubusercontent.com/19553554/58700076-b3d51300-83d1-11e9-90e2-2225f71f5a57.png)
