## set相关技巧

`set`是一个无序不重复元素集，通过`set([1, 2, 3])`构造，或者通过`{1, 2, 3}`构造。

### 列表去重

```python
>>> l = [1, 1, 1, 2, 2, 3]
>>> l = list(set(l))
>>> l
[1, 2, 3]
```

### 取并集

```python
>>> l1 = [1, 2]
>>> l2 = [1, 3]
>>> l = list(set(l1) | set(l2))
>>> l
[1, 2, 3]
```

### 取交集

```python
>>> l1 = [1, 2]
>>> l2 = [1, 3]
>>> l = list(set(l1) & set(l2))
>>> l
[1]
```

### 取差集

```python
>>> l1 = [1, 2]
>>> l2 = [1, 3]
>>> l = list(set(l1) - set(l2))
>>> l
[2]
>>> l = list(set(l2) - set(l1))
>>> l
[3]
```

ref: [python 并集union, 交集intersection, 差集difference](https://blog.csdn.net/lanyang123456/article/details/77596349)
