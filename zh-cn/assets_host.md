pyecharts 使用的所有静态资源文件存放于 [pyecharts-assets](https://github.com/pyecharts/pyecharts-assets) 项目中，默认挂载在  `https://assets.pyecharts.org/assets/`

## Localhost-Server

pyecharts 提供了更改全局 HOST 的快捷方式，下面以开发者启动本地 FILE SERVER 为例，操作如下。

1. 获取 pyecharts-assets 项目

    ```shell
    $ git clone https://github.com/pyecharts/pyecharts-assets.git
    ```

2. 启动 HTTP file server

    ```shell
    $ cd pyecharts-assets
    $ python -m http.server
    # Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
    # 默认会在本地 8000 端口启动一个文件服务器
    ```

3. 配置 pyecharts 全局 HOST

    ```python
    # 只需要在顶部声明 CurrentConfig.ONLINE_HOST 即可
    from pyecharts.globals import CurrentConfig
    CurrentConfig.ONLINE_HOST = "http://127.0.0.1:8000/assets/"

    # 接下来所有图形的静态资源文件都会来自刚启动的服务器
    from pyecharts.charts import Bar
    bar = Bar()
    ```

## Notebook-Server

pyecharts v1.5.1+ 起开始支持 Notebook 插件作为静态资源服务。

1. 获取 pyecharts-assets 项目

    ```shell
    $ git clone https://github.com/pyecharts/pyecharts-assets.git
    ```

2. 安装扩展插件

    ```shell
    $ cd pyecharts-assets
    # 安装并激活插件
    $ jupyter nbextension install assets
    $ jupyter nbextension enable assets/main
    ```

3. 配置 pyecharts 全局 HOST

    ```python
    # 只需要在顶部声明 CurrentConfig.ONLINE_HOST 即可
    from pyecharts.globals import CurrentConfig, OnlineHostType

    # OnlineHostType.NOTEBOOK_HOST 默认值为 http://localhost:8888/nbextensions/assets/
    CurrentConfig.ONLINE_HOST = OnlineHostType.NOTEBOOK_HOST

    # 接下来所有图形的静态资源文件都会来自刚启动的服务器
    from pyecharts.charts import Bar
    bar = Bar()
    ```
