> pyecharts 内置提供了 10+ 种不同的风格，另外也提供了便捷的定制主题的方法。

默认主题的效果
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


## 主题风格

### LIGHT

```pyhon
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.LIGHT))
```

### DARK

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.DARK))
```

### WHITE

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.WHITE))
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
