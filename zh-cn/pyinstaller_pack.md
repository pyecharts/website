## pyinstaller 打包

### 开发者示例

**适用场景描述**
1. 需要将pyecharts应用于独立GUI软件/CS架构开发
2. pyinstaller打包，生成单文件可执行文件(.exe)
3. 呈现控件可支持HTML5相关交互，能正常支撑pyecharts基本互动控制

**当前生成环境信息，仅供参考（系统环境及 pyecharts 版本）**

> pyecharts: 1.7.1
> PyInstaller: 4.0
> cefpython3: 66.0
> wxPython: 4.1.0
> Python: 3.7.2
> Platform: Windows-10-10.0.17763-SP0


**流程步骤**
1. pyecharts资源文件`datasets`及`templates`整合至特定目录下（如打包目录下`./resources`文件夹）
![image](https://user-images.githubusercontent.com/37883510/91822530-8200cb00-ec6a-11ea-867f-58dcaf60a3cb.png)


2. 这一步分两种情况：
   ① 已有pyinstaller生成的`.spec`文件
   修改`datas`字段（追加or添加）
    ```python
    
    a = Analysis(['main.py'],
             pathex=['.\\'],
             binaries=[],
             datas=[('.\\resource\\datasets', 'pyecharts\\datasets\\.'), 
                    ('.\\resource\\templates', 'pyecharts\\render\\templates\\.')],
             hiddenimports=[],
             hookspath=[],
             runtime_hooks=[],
             excludes=[],
             win_no_prefer_redirects=False,
             win_private_assemblies=False,
             cipher=block_cipher,
             noarchive=False)
    ```
   元组中左侧元素为资源文件路径，右侧是打包后相对于临时文件夹路径拷贝位置。
   ② 无`.spec`文件
   cmd/bat脚本pyinstaller添加`--add-data`选项：
    ```bat
    pyinstaller --add-data=".\resource\datasets;pyecharts\datasets\." --add-data=".\resource\templates;pyecharts\render\templates\." -Fw main.py
    ```
   到这一步，初步解决了pyecharts相关资源缺失问题。但是我们辛苦绘出来的图片若要进一步显示到GUI上，仍需要继续努力！

3. cefpython3调用`cef.Initialize(settings=XXX)`配置初始化内容进行如下适配：
    ```python
    # import os, sys, wx etc.
    ...
    settings = {X: XXX}    # original setting dict()
    if getattr(sys, 'frozen', False):
        if wx.Platform == "__WXMSW__":
            settings.update(
                dict(resources_dir_path=sys._MEIPASS,
                     locales_dir_path=os.path.join(sys._MEIPASS, 'locales'), 
                     browser_subprocess_path=os.path.join(sys._MEIPASS, 'subprocess.exe'),
                     log_file=os.path.join(sys._MEIPASS, 'debug.log'))
            )
    cef.Initialize(settings=settings)
    ...
    ```
   这部分内容中`__WXMSW__`是wxPython的平台标识，可以参考[这里](https://zhuanlan.zhihu.com/p/141467076)对其他平台进行同样适配。

4. 编写`hook-cefpython3.py`文件，并添加到`.spec`文件的`hookspath`属性中。

   这里文件编写可以参考cefpython3的[官方文档](https://github.com/cztomczak/cefpython/blob/master/examples/pyinstaller/hook-cefpython3.py)，但是需要修改如下几个字段：
    ```python
    ...
    from PyInstaller.utils.hooks import get_package_paths
    ...
    CEFPYTHON3_DIR = get_package_paths("cefpython3")[1]
    ...
    def get_cefpython3_datas():
        ...
        # SPECIAL ATTENTION of this dot '.'!!!
        ret.append((os.path.join(CEFPYTHON3_DIR, filename),
                    "."))
    ...
    ```
   特别注意那个append字段里的点，在打包后运行时是临时文件夹`sys._MEIPASS`指代路径。官方示例文档中直接是空字符`""`，反正那个我是没直接跑起来... : P

   添加修改好的`hook-cefpython3.py`文件。（我依然是很懒的放到了`./resources`里）
   ①有`.spec`的文件配置
    ```python
    
    a = Analysis(
        ...
             hiddenimports=[],
             hookspath=['.\\resources\\hooks'],
        ...)
    ```
   ② 无`.spec`文件
   cmd/bat脚本pyinstaller添加`--additional-hooks-dir`选项：
    ```bat
    pyinstaller ... --additional-hooks-dir=".\resources\hooks" -Fw main.py
    ```
   然后运行`.bat`脚本or创建pipenv环境装好库文件敲指令等收菜即可。

**简单解释**

上述所有涉及到的配置部分其实是因为pyinstaller在打包后和未打包之前，原始库文件的层级关系和路径对应关系发生了改变导致的。（可参考pyinstaller官方项目里关于`'frozen'`的相关解释）


**references**
[issue #1698](https://github.com/pyecharts/pyecharts/issues/1698)
[issue #1653](https://github.com/pyecharts/pyecharts/issues/1653)
[issue #1625](https://github.com/pyecharts/pyecharts/issues/1625)
[issue #960](https://github.com/pyecharts/pyecharts/issues/960)
[cefpython](https://github.com/cztomczak/cefpython/tree/master/examples/pyinstaller)
[pyinstaller](https://pyinstaller.readthedocs.io/en/stable/feature-notes.html?highlight=frozen#solution-in-pyinstaller)
