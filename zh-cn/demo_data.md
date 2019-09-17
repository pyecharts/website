## Fixtures

部分示例可能会看到使用了 json 文件，如

```python
with open(os.path.join("fixtures", "weibo.json"), "r", encoding="utf-8") as f:
    j = json.load(f)
```

fixtures 文件夹位于 [example/fixtures](https://github.com/pyecharts/pyecharts/tree/master/example/fixtures)。

## 运行示例

如何运行 example 文件夹中的示例

```shell
$ git clone https://github.com/pyecharts/pyecharts.git
# 如果未安装 pyecharts 请执行该语句安装
# cd pyecharts && python install.py
$ cd pyecharts/example
$ python bar_example.py
# 使用浏览器打开 example/render.html 文件
```
