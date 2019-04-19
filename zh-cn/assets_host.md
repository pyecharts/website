pyecharts 使用的所有静态资源文件存放于 [pyecharts-assets](https://github.com/pyecharts/pyecharts-assets) 项目中，默认挂载在 Gihhub 服务器，HOST 为 `https://assets.pyecharts.org/assets/`。

pyecharts 提供了快捷地更改全局 HOST 的方式，下面以开发者启动本地 FILE SERVER 为例，操作示例如下。

0. 获取 pyecharts-assets 项目

```shell
$ git clone https://github.com/pyecharts/pyecharts-assets.git
```

1. 启动 HTTP file server

```shell
$ cd pyecharts-assets
$ python -m http.server
# Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
# 默认会在本地 8000 端口启动一个文件服务器
```

2. 配置 pyecharts 全局 HOST

```python
from pyecharts.globals import CurrentConfig
CurrentConfig.ONLINE_HOST = "http://127.0.0.1:8000/assets/"
# 只需要在顶部声明 CurrentConfig.ONLINE_HOST 即可

from pyecharts.charts import Bar

bar = Bar()
# 接下来所有图形的静态资源文件都会来自刚启动的服务器
```
