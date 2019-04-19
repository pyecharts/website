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
![](https://user-images.githubusercontent.com/19553554/55897058-5bb03a80-5bf2-11e9-9ab8-7d6b5419b68b.png)


## 主题风格

### LIGHT

```pyhon
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.LIGHT))
```
![](https://user-images.githubusercontent.com/19553554/55897092-6cf94700-5bf2-11e9-8fa9-e7d880481a90.png)

### DARK

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.DARK))
```
![](https://user-images.githubusercontent.com/19553554/55897130-80a4ad80-5bf2-11e9-836d-748b15b260ce.png)

### CHALK

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.CHALK))
```
![](https://user-images.githubusercontent.com/19553554/55897251-bd70a480-5bf2-11e9-805e-6c0bd5e76b48.png)

### ESSOS

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.ESSOS))
```
![](https://user-images.githubusercontent.com/19553554/55897288-cfeade00-5bf2-11e9-8b45-1f8aa45a166b.png)

### INFOGRAPHIC

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.INFOGRAPHIC))
```
![](https://user-images.githubusercontent.com/19553554/55897310-dc6f3680-5bf2-11e9-921a-cc8981570378.png)

### MACARONS

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.MACARONS))
```
![](https://user-images.githubusercontent.com/19553554/55897352-ef820680-5bf2-11e9-8d4f-314c2abb40df.png)

### PURPLE_PASSION

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.PURPLE_PASSION))
```
![](https://user-images.githubusercontent.com/19553554/55897399-ff99e600-5bf2-11e9-9135-0a186f0acad5.png)

### ROMA

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.ROMA))
```
![](https://user-images.githubusercontent.com/19553554/55897419-0d4f6b80-5bf3-11e9-8314-f433ab1cca5c.png)

### ROMANTIC

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.ROMANTIC))
```
![](https://user-images.githubusercontent.com/19553554/55897475-2821e000-5bf3-11e9-9079-e8a6458900b2.png)

### SHINE

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.SHINE))
```
![](https://user-images.githubusercontent.com/19553554/55897502-366ffc00-5bf3-11e9-8492-ca9e162dafac.png)

### VINTAGE

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.VINTAGE))
```
![](https://user-images.githubusercontent.com/19553554/55897530-47b90880-5bf3-11e9-89d8-5466f0f7f3b1.png)

### WALDEN

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.WALDEN))
```
![](https://user-images.githubusercontent.com/19553554/55897553-556e8e00-5bf3-11e9-8146-67c3e4d30109.png)

### WESTEROS

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.WESTEROS))
```
![](https://user-images.githubusercontent.com/19553554/55897595-6a4b2180-5bf3-11e9-97b1-61b9c575af9e.png)

### WONDERLAND

```python
c = Bar(init_opts=opts.InitOpts(theme=ThemeType.WONDERLAND))
```
![](https://user-images.githubusercontent.com/19553554/55897678-8bac0d80-5bf3-11e9-9ca4-a85b3868cf81.png)


## 使用自己构建的主题

Echarts 提供了[主题构建工具](http://echarts.baidu.com/theme-builder/)，你可以从中构建喜欢的主题，假设你构建的主题文件为 `myTheme.js`。

使用自己构建的主题必须由开发者自己启动资源文件服务器，这部分内容请参考 **进阶话题-资源引用**，然后你需要进行以下步骤的操作

1. 将 `myTheme.js` 放入至 `pyecharts-assets/assets/themes` 文件夹。
2. 注册主题到 pyecharts
    ```python
    from pyecharts.datasets import register_files
    register_files({"myTheme": ["themes/myTheme", "js"]})
    ```
3. 使用主题
    ```python
    c = Bar(init_opts=opts.InitOpts(theme="myTheme"))
    ```
