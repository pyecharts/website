**Q:为什么安装后还是无法 import Bar,Line 等图形**

A: 请检查是否将测试文件命名为 pyecharts.py，如若是请重命名该文件。

**Q:使用 pyinstaller 的单文件模式打包后无法加载 js 等静态文件？**

A: 目前 pyecharts 暂时未开放这部分的 API，没有考虑到打包后的资源文件路径的兼容问题。建议使用文件夹/多文件模式。
如果确实需要使用单文件模式，可参考 [《Python打包工具》](https://kinegratii.github.io/2016/04/23/python-package/) 这篇文章了解相关原理后进行源码修改。

**Q: 如何离线安装 pyecharts？**

A: TODO
