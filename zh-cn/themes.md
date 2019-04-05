
```python
from pyecharts import options as opts
from pyecharts.charts import Bar
from pyecharts.globals import ThemeType

def theme_default() -> Bar:
    c = (
        Bar()
        # 等价于 Bar(init_opts=opts.InitOpts(theme=ThemeType.WHITE))
        .add_xaxis(Faker.choose())
        .add_yaxis("商家A", Faker.values())
        .add_yaxis("商家B", Faker.values())
        .add_yaxis("商家C", Faker.values())
        .add_yaxis("商家D", Faker.values())
        .set_global_opts(title_opts=opts.TitleOpts("Theme-default"))
    )
    return c
```
![dark](https://user-images.githubusercontent.com/19553554/39868563-c136646a-548c-11e8-87c2-dbf7ae85e844.png)

默认主题的效果

![default](https://user-images.githubusercontent.com/19553554/39868566-c20b699e-548c-11e8-861f-5a1b063434c3.png)



## 主题风格

### LIGHT

```pyhon
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.LIGHT))
```

### DARK

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.DARK))
```

### CHALK
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.CHALK))
```

### ESSOS
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.ESSOS))
```

### INFOGRAPHIC
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.INFOGRAPHIC))
```

### MACARONS
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.MACARONS))
```

### PURPLE_PASSION
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.PURPLE_PASSION))
```

### ROMA
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.ROMA))
```

### ROMANTIC
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.ROMANTIC))
```

### SHINE
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.SHINE))
```

### VINTAGE
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.VINTAGE))
```

### WALDEN
```
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.WALDEN))
```

### WESTEROS
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.WESTEROS))
```

### WONDERLAND
```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.WONDERLAND))
```

## 使用自己构建的主题

Echarts 提供了[主题构建工具](http://echarts.baidu.com/theme-builder/)，你可以从中构建喜欢的主题，如 `myTheme.js`。然后 hack *echarts-themes-pypkg* 包。具体操作如下

1. cd 到你 Python 安装环境下的 `Lib/site-packages/echarts_themes_pypkg/resources` 目录下，具体路径因操作系统而异
2. 将 `myTheme.js` 放入到 `resources/echarts-themes-js` 文件夹下
3. 改动 `resources/registry.json` 文件

```
 "PINYIN_MAP": {
        "shine": "shine",
        ...
        "myTheme": "myTheme"    # 这行
    },
    "FILE_MAP": {
        "shine": "shine",
        ...
        "myTheme": "myTheme"    # 还有这行
    }
```
4. cd 到 notebook 安装环境下的 `jupyter/nbextensions/echarts-themes-js` 目录下，具体路径因操作系统而异
5. 将 `myTheme.js` 放入到 `echarts-themes-js` 文件夹下
6. 使用 `chart.use_theme("myTheme")`

**4、5 为可选项，如果不使用 notebook 的话可以忽略该步骤。**