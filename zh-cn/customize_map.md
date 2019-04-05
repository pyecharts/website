> 地图自定义篇：考虑到项目更好的通用性，以及更好可扩展性，所以决定对地图部分提供自定义模式。适用在 pyecharts v0.1.9.7 以后的版本。

> Echarts 官方地图下载地址 [download-map](http://echarts.baidu.com/download-map.html) 已经暂时关闭

## VERSION 0.5.7+

从 v0.5.7 开始，新增了 [echarts-cities-pypkg](https://github.com/pyecharts/echarts-cities-pypkg) 插件，扩展 Geo/Geoline 图的地理坐标数据。可以从指定的国家/地区中检索区域坐标。数据来自 [geonames.org](geonames.org), 总共包含了 [138,398](https://github.com/echarts-maps/echarts-cities-js) 个地区。具体的国家/地区映射表参照 [countries_regions_db.json](https://github.com/pyecharts/pyecharts/blob/master/pyecharts/datasets/countries_regions_db.json)。

安装扩展包

```shell
$ pip install echarts-cities-pypkg
```

## 如何制作自己的地图扩展

你需要做两个 Github 项目：一个是 npm 项目，提供所有的 javascript 脚本；另一个是 python 项目，把前一个项目变成可以用 pip 装的 python 包。

### npm 项目

这个项目首先必须是一个 npm 的项目，并已经启动 gh-pages 来提供地图库。如果未启动 gh-pages , 那么
你的 jupyter 用户不能把 ipynb 下载成 html ，因为下载之后地图将无法显示。

首先，你需要得到以下的项目：

```bash
$ pip install yehua
$ git clone https://github.com/echarts-maps/echarts-js-mobans.git
$ export YEHUA_FILE=/ABSOLUTE/PATH/TO/echarts-js-mobans/yehua.yml
```

然后你需要移步到你的工作文件夹，以 echarts-united-kingdom-js 为例子运行这个命令

```bash
$ yh
Yehua will walk you through creating a echarts-maps js package.
Press ^C to quit at any time.

project name: echarts-united-kingdom-js
description: UK maps for echarts
license: MIT
author: C.W.
All done!! project echarts-united-kingdom-js is created
```

文件已经产生了，让我们看看是哪些文件：

```bash
$ pyecharts-host:tmp chfw$ cd echarts-united-kingdom-js/
$ pyecharts-host:echarts-united-kingdom-js chfw$ ls
echarts-united-kingdom-js	package.json			registry.json
```

现在讲原理。一个 echarts-js 包需要以下的文件结构

```
+ echarts-united-kingdom-js
  + registry.json
  + package.json
  + echarts-united-kingdom-js
     + london.js
     + manchester.js
     + index.js
  + other files
```

在 registry.json 里，需要填写的东西是和 pyecharts 衔接的必要信息。
```
{
    "JUPYTER_URL": "/nbextensions/echarts-united-kingdom-js",
    "GITHUB_URL": "https://your.github.io/echarts-united-kingdom-js/echarts-united-kingdoms-js",
    "JUPYTER_ENTRY": "echarts-united-kingdom-js/index",
    "JS_FOLDER": "echarts-united-kingdoms-js",
    "PINYIN_MAP": {
        "伦敦": "lundun",
        "曼彻斯特": "manqiesite"
    },
    "FILE_MAP": {
        "lundun": "london",
        "manqiesite": "manchester"
    }
}
```

index.js 只为 jupyter notebook 而存在
```
define(["require", "exports"], function (require, exports) {
    "use strict";
    Object.defineProperty(exports, "__esModule", { value: true });
    var version = '1.0.0';
    function load_ipython_extension() {
        console.log("echarts-united-kingdom-js " + version + " has been loaded");
    }
    exports.load_ipython_extension = load_ipython_extension;
});

好了，在 echarts-united-kingdom-js 子文件夹里就需要放地图文件了。每放一个呢，请记住更新 PINYI_MAP 和 FILE_MAP。
```

### python 项目

首先，你需要得到以下的项目：

```bash
$ pip install yehua
$ git clone https://github.com/pyecharts/pypkg-mobans.git
$ export YEHUA_FILE=/ABSOLUTE/PATH/TO/pypkg-mobans/yehua.yml
```

然后你需要移步到你的工作文件夹，以 echarts-united-kingdom-pykg 为例子运行这个命令

```
$ yh
Yehua will walk you through creating a pyecharts pypkg package.
Press ^C to quit at any time.

project name: echarts-united-kingdom-pypkg
npm project name: echarts-united-kingdom-js
description: pyecharts map extension - united kingdom maps - python package
license: MIT
author: C.W.
contact email: wangc_2011@hotmail.com
github profile/organisation: chfw
copyright owner: C.W.
Cloning into 'mobans'...
remote: Counting objects: 214, done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 214 (delta 8), reused 12 (delta 5), pack-reused 198
Receiving objects: 100% (214/214), 30.31 KiB | 17.00 KiB/s, done.
Resolving deltas: 100% (126/126), done.
Templating CUSTOM_README.rst.jj2 to README.rst
Templating custom_setup.py.jj2 to setup.py
Templating requirements.txt.jj2 to requirements.txt
Templating tests/custom_requirements.txt.jj2 to tests/requirements.txt
Templating docs/source/conf.py.jj2 to docs/source/conf.py
Templating test.script.jj2 to test.sh
Templating _version.py.jj2 to echarts_united_kingdom_pypkg/_version.py
Templating gitignore.jj2 to .gitignore
Templating travis.yml.jj2 to .travis.yml
Templated 9 files.
Initialized empty Git repository in /private/tmp/echarts-united-kingdom-pypkg/.git/
Please review changes before commit!
```

这个时候，这个扩展包的骨架就已经做好了。我们现在做最后一步：

```bash
$ pyecharts-host:tmp chfw$ cd echarts-united-kingdom-pypkg/
$ git submodule add https://github.com/your/npm/project your_project_name_pypkg/resources
$ git submodule init
```

请把需要的文件加入 git, 然后做:

```bash
$ git commit
```

这样呢，这个包就可以放在 Github 上了。
