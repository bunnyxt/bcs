# Python

* [Ubuntu安装Python](ubuntu-install-python.md)
* [Jupyter保存当前会话](jupyter-save-session.md)
* [set相关技巧](set.md)
* [pandas相关操作](pandas.md)

## 字符串处理
### 替换字符串中的反斜杠
```python
s = "abc\ndef"
s = eval(repr(s).replace('\\', '\\\\'))
```

直接对s进行replace无效，不会处理转义符号本身，需要使用repr()函数转换。repr()可以将字符串转换为python的原始字符串（即忽视各种特殊字符的作用），然后再使用eval()函数将原始字符串转换为正常的字符串，不使用eval()输出的字符串会带有''引号。

ref: [Python替换字符串中的反斜杠\\](https://blog.csdn.net/LeonTom/article/details/89703912)
