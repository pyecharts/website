pyecharts 内置了多个全局变量，位于 pyecharts.globals 文件

```python
# 渲染方式
RenderType = _RenderType()

# 允许的生成的文件类型
FileType = _FileType()

# Symbol 样式类型
SymbolType = _SymbolType()

# 图表类型
ChartType = _ChartType

# Tooltip 格式器类型
TooltipFormatterType = _ToolTipFormatterType()

# 主题类型
ThemeType = _ThemeType()

# Geo 图形类型
GeoType = _GeoType()

# BMap 图形全局参数
BMapType = _BMapType

# Notebook 环境类型
NotebookType = _NotebookType()

# 远程资源 Host
OnlineHostType = _OnlineHost()

# 全局环境配置类
class _CurrentConfig:
    # 全局网页标题
    PAGE_TITLE = "Awesome-pyecharts"
    # 全局 Host
    ONLINE_HOST = OnlineHostType.DEFAULT_HOST
    # 全局 Notebook 类型
    NOTEBOOK_TYPE = NotebookType.JUPYTER_NOTEBOOK
    # 全局 jinja2.Environment 实例
    GLOBAL_ENV = Environment(
        keep_trailing_newline=True,
        trim_blocks=True,
        lstrip_blocks=True,
        loader=FileSystemLoader(
            os.path.join(
                os.path.abspath(os.path.dirname(__file__)), "render", "templates"
            )
        ),
    )

# 全局环境唯一实例
CurrentConfig = _CurrentConfig()
```
