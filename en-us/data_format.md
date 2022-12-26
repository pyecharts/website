## Python -> JSON

What pyecharts is essentially doing is serializing Echarts configuration items from Python dict to JSON format, so what data types pyecharts supports depends on what data types JSON supports.

The formatting of JSON in Python is as follows

```
Python JSON
------ ----
int, float number
str string
bool boolean
dict object
list array
```

This also means that when you pass data into pyecharts, you need to convert the data format to the native Python data format above. Most data analysis requires numpy/pandas, but numpy's numpy.int64/numpy.int32/... etc. do not inherit from `Python.int`.

**Q1: How do I convert? **

```python
# for int
[int(x) for x in your_numpy_array_or_something_else]
# for float
[float(x) for x in your_numpy_array_or_something_else]
# for str
[str(x) for x in your_numpy_array_or_something_else]
```

**Q2: Is there a more convenient way to convert? **

`Series.tolist()`

**Q3: Is there a reason why pyecharts doesn't have automatic conversions? **

pyecharts is a generic third-party library and we can't possibly care about all the usage scenarios of the developers. The conversion requires us to bring in `numpy/pandas`, two third-party libraries which are `too heavy`, so we leave this job to the developers.
