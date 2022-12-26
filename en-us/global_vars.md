pyecharts has several global variables built in, located in the pyecharts.globals file

```python
# Render type
RenderType = _RenderType()

# Allowed generated file types
FileType = _FileType()

# Symbol style type
SymbolType = _SymbolType()

# Chart types
ChartType = _ChartType

# TooltipFormatter type
TooltipFormatterType = _ToolTipFormatterType()

# Theme type
ThemeType = _ThemeType()

# Geo graphical type
GeoType = _GeoType()

# BMap graph global parameters
BMapType = _BMapType

# Notebook environment type
NotebookType = _NotebookType()

# Remote resource Host
OnlineHostType = _OnlineHost()

# Warning control class - will be deprecated after the 1.9.0 release
WarningType = _WarningControl()

# Global environment configuration class
class _CurrentConfig:
    # Global page title
    PAGE_TITLE = "Awesome-pyecharts"
    # Global Host
    ONLINE_HOST = OnlineHostType.DEFAULT_HOST
    # Global Notebook type
    NOTEBOOK_TYPE = NotebookType.JUPYTER_NOTEBOOK
    # global jinja2.Environment instance
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

# Unique instance of the global environment
CurrentConfig = _CurrentConfig()
```
