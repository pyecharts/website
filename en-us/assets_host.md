All static resource files used by pyecharts are stored in the [pyecharts-assets](https://github.com/pyecharts/pyecharts-assets) project, which is mounted by default in `https://assets.pyecharts.org/assets/`

## Localhost-Server

pyecharts provides a shortcut to change the global HOST. The following is an example of how to start the local FILE SERVER for developers.

1. Get the pyecharts-assets project

    ```shell
    $ git clone https://github.com/pyecharts/pyecharts-assets.git
    ```

2. Start the HTTP file server

    ```shell
    $ cd pyecharts-assets
    $ python -m http.server
    # Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
    # By default, a file server will be started locally on port 8000
    ````

3. configure pyecharts global HOST

    ```python
    # Just declare CurrentConfig.ONLINE_HOST at the top
    from pyecharts.globals import CurrentConfig
    CurrentConfig.ONLINE_HOST = "http://127.0.0.1:8000/assets/"

    # All the static resource files for the next graph will come from the server that was just started
    from pyecharts.charts import Bar
    bar = Bar()
    ```

## Notebook-Server

pyecharts v1.5.1+ starts to support Notebook plugin as a static resource service.

1. Get the pyecharts-assets project

    ```shell
    $ git clone https://github.com/pyecharts/pyecharts-assets.git
    ```

2. Install the extension plugin

    ```shell
    $ cd pyecharts-assets
    # Install and activate the plugin
    $ jupyter nbextension install assets
    $ jupyter nbextension enable assets/main
    ``` 3.

3. configure pyecharts global HOST

    ```python
    # Just declare CurrentConfig.ONLINE_HOST at the top
    from pyecharts.globals import CurrentConfig, OnlineHostType

    # OnlineHostType.NOTEBOOK_HOST defaults to http://localhost:8888/nbextensions/assets/
    CurrentConfig.ONLINE_HOST = OnlineHostType.NOTEBOOK_HOST

    # All the next static resource files for the graph will come from the server that was just started
    from pyecharts.charts import Bar
    bar = Bar()
    ```
