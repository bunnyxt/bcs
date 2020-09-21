## Jupyter保存当前会话

关闭jupyter notebook之后，笔记本内保存的变量会消失，需要从头重新运行。使用`dill`可以保存当前会话内的变量，解决此问题。

安装`dill`
```shell
pip install dill
```

存储当前会话
```python
import dill
dill.dump_session('env.db')
```

恢复会话
```python
import dill
dill.load_session('env.db')
```

ref: [How to pickle or store Jupyter (IPython) notebook session for later](https://stackoverflow.com/questions/34342155/how-to-pickle-or-store-jupyter-ipython-notebook-session-for-later)