## 如何安装

### pyecharts

**pip 安装**
```shell
$ pip install pyecharts
```

**源码安装**
```shell
$ git clone https://github.com/pyecharts/pyecharts.git
$ cd pyecharts
$ pip install -r requirements.txt
$ python setup.py install
```

### selenium

> 使用 selenium 是为了生成图片文件，如若没有这个需求可跳过本步骤

```shell
$ pip install selenium
```

selenium 安装后需要进行配置，这部分内容网上有很多文章介绍，就不在这里赘述了。


## 5 分钟上手

首先开始来绘制你的第一个图表
```python
from pyecharts import Bar

bar = Bar("我的第一个图表", "这里是副标题")
bar.add("服装", ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"], [5, 20, 36, 10, 75, 90])
# bar.print_echarts_options() # 该行只为了打印配置项，方便调试时使用
bar.render()    # 生成本地 HTML 文件
```
![guide-0](https://user-images.githubusercontent.com/19553554/35103909-3ee41ba2-fca2-11e7-87be-1a3585b9e0fa.png)

* ```add()```  
    主要方法，用于添加图表的数据和设置各种配置项
* ```print_echarts_options()```  
    打印输出图表的所有配置项
* ```render()```  
    默认将会在根目录下生成一个 render.html 的文件，支持 path 参数，设置文件保存位置，如 render(r"e:\my_first_chart.html")，文件用浏览器打开。

**Note：** 可以按右边的下载按钮将图片下载到本地，如果想要提供更多实用工具按钮，请在 `add()` 中设置 `is_more_utils` 为 True

```python
from pyecharts import Bar

bar = Bar("我的第一个图表", "这里是副标题")
bar.add("服装", 
        ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"], [5, 20, 36, 10, 75, 90],
        is_more_utils=True)
bar.render()
```
![guide-1](https://user-images.githubusercontent.com/19553554/35104150-f31e1b7c-fca2-11e7-81cf-a12bf1629e02.png)


### 使用主题

自 0.5.2+ 起，pyecharts 支持更换主体色系。下面是跟换为 'dark' 的例子：

```python
from pyecharts import Bar

bar = Bar("我的第一个图表", "这里是副标题")
bar.use_theme('dark')
bar.add("服装", ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"], [5, 20, 36, 10, 75, 90])
bar.render()
```
![guide-2](https://user-images.githubusercontent.com/4280312/39617664-79789878-4f78-11e8-9f0e-c3a2c371b6cb.png)

pyecharts 支持另外 5 个主体色系，[请移步到主题色系获取更多配置信息](zh-cn/themes)。


### Pandas&Numpy 简单示例

如果使用的是 Numpy 或者 Pandas，可以参考这个示例

![pandas-numpy](https://user-images.githubusercontent.com/19553554/35104252-3e36cee2-fca3-11e7-8e43-09bbe8dbbd1e.png)

**Note：** 使用 Pandas&Numpy 时，整数类型请确保为 int，而不是 numpy.int32

**当然你也可以采用更加酷炫的方式，使用 Jupyter Notebook 来展示图表，matplotlib 有的，pyecharts 也会有的**

**Note：** 从 v0.1.9.2 版本开始，废弃 ```render_notebook()``` 方法，现已采用更加 pythonic 的做法。直接调用本身实例就可以了。

比如这样

![notebook-0](https://user-images.githubusercontent.com/19553554/35104153-f6256212-fca2-11e7-854c-bacc61eabf6f.gif)

还有这样

![notebook-1](https://user-images.githubusercontent.com/19553554/35104157-fa39e170-fca2-11e7-9738-1547e22914a6.gif)

如果使用的是自定义类，直接调用自定义类示例即可

![notebook-2](https://user-images.githubusercontent.com/19553554/35104165-fe9765da-fca2-11e7-8126-920158616b99.gif)

更多 Jupyter notebook 的例子请参考 [notebook-use-cases](https://github.com/pyecharts/pyecharts-users-cases)。可下载后运行看看。

如需使用 Jupyter Notebook 来展示图表，只需要调用自身实例即可，同时兼容 Python2 和 Python3 的 Jupyter Notebook 环境。所有图表均可正常显示，与浏览器一致的交互体验，这下展示报告连 PPT 都省了！！
