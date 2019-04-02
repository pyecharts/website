### Grid3DOpts：三维笛卡尔坐标系配置项
> *class pyecahrts.options.Grid3DOpts*

```python
class Grid3DOpts(
    # 三维笛卡尔坐标系组件在三维场景中的宽度
    width: Numeric = 200,

    # 三维笛卡尔坐标系组件在三维场景中的高度。
    height: Numeric = 100,

    # 三维笛卡尔坐标系组件在三维场景中的深度。
    depth: Numeric = 80,

    # 是否开启视角绕物体的自动旋转查看。
    is_rotate: bool = False,

    # 物体自转的速度。单位为角度 / 秒，默认为10 ，也就是36秒转一圈。
    rotate_speed: Numeric = 10,

    # 旋转操作的灵敏度，值越大越灵敏。支持使用数组分别设置横向和纵向的旋转灵敏度。
    # 设置为0后无法旋转。
    rotate_sensitivity: Numeric = 1,
)
```

### Axis3DOpts：三维坐标轴配置项
> *class pyecharts.options.Axis3DOpts*

```python
class Axis3DOpts(
    data: Optional[Sequence] = None,

    # 坐标轴类型。可选：
    # 'value': 数值轴，适用于连续数据。
    # 'category': 类目轴，适用于离散的类目数据，为该类型时必须通过 data 设置类目数据。
    # 'time': 时间轴，适用于连续的时序数据，与数值轴相比时间轴带有时间的格式化，在刻度计算上也有所不同，
    # 例如会根据跨度的范围来决定使用月，星期，日还是小时范围的刻度。
    # 'log' 对数轴。适用于对数数据。
    type_: Optional[str] = None,

    # 坐标轴名称。
    name: Optional[str] = None,

    # 坐标轴名称与轴线之间的距离，注意是三维空间的距离而非屏幕像素值。
    name_gap: Numeric = 20,

    # 坐标轴刻度最小值。
    # 可以设置成特殊值 'dataMin'，此时取数据在该轴上的最小值作为最小刻度。
    # 不设置时会自动计算最小值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'。
    # 也可以设置为负数，如 -3）。
    min_: Union[str, Numeric, None] = None,

    # 坐标轴刻度最大值。
    # 可以设置成特殊值 'dataMax'，此时取数据在该轴上的最大值作为最大刻度。
    # 不设置时会自动计算最大值保证坐标轴刻度的均匀分布。
    # 在类目轴中，也可以设置为类目的序数（如类目轴 data: ['类A', '类B', '类C'] 中，序数 2 表示 '类C'。
    # 也可以设置为负数，如 -3）。
    max_: Union[str, Numeric, None] = None,

    # 坐标轴的分割段数，需要注意的是这个分割段数只是个预估值，最后实际显示的段数会在这个
    # 基础上根据分割后坐标轴刻度显示的易读程度作调整。
    # 在类目轴中无效。
    splitnum: Optional[Numeric] = None,

    # 强制设置坐标轴分割间隔。
    # 因为 splitNumber 是预估的值，实际根据策略计算出来的刻度可能无法达到想要的效果，
    # 这时候可以使用 interval 配合 min、max 强制设定刻度划分，一般不建议使用。
    # 无法在类目轴中使用。在时间轴（type: 'time'）中需要传时间戳，在对数轴（type: 'log'）中需要传指数值。
    interval: Optional[Numeric] = None,
    margin: Numeric = 8,
    textstyle_opts: Union[TextStyleOpts, dict, None] = None,
)
```

## Bar3D：3D柱状图

## Line3D：3D折线图

## Scatter3D：3D散点图

## Surface3D：3D曲面图
