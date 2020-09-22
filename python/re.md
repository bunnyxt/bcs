## 正则表达式

```python
import re
```

### 匹配与提取

- 匹配组：`(content)`
- 命名匹配组：`(?P<name>content)`
- 非匹配组：`(?:content)`

```python
s = '2013-01-31 19:29:40,【洛天依】前尘如梦「新年重制版」（By桜色妖精）,av456930'

match_obj = re.match('(\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}),(?P<title>\S+),av(?:\d+)', s)
if match_obj:
    print('pubdate', match_obj.group(1))
    print('title', match_obj.group('title'))
    # print('aid', match_obj.group(3))  # IndexError: no such group
```

### re.match与re.search

`re.match`只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回`None`；而`re.search`匹配整个字符串，直到找到一个匹配。

```python
s = 'hello world'

if re.match('hello', s):
    print('re.match find hello')  # ✅
if re.match('world', s):
    print('re.match find world')  # ❌

if re.search('hello', s):
    print('re.search find hello')  # ✅
if re.search('world', s):
    print('re.search find world')  # ✅
```

### re.findall与re.finditer

`re.findall`寻找字符串中所有匹配的子串，返回一个列表；而`re.finditer`返回的是一个迭代器，每次迭代返回`re.MatchObject`对象。

```python
s = 'Yamato 97200, Shimakaze 17900, Zao 40800'

s_number_list = re.findall('\d+', s)
print(s_number_list)  # ['97200', '17900', '40800']

s_number_iter = re.finditer('\d+', s)
for s_number in s_number_iter:
    print(s_numbe.group(0))  # iter print 97200 17900 40800
```

### re.MatchObject

各种匹配方法返回的对象（`re.findall`除外，这个方法直接返回列表）。

```python
obj = re.search('\d+', 'Hakuryu 63100')
print(obj.group())  # 63100
print(obj.start())  # 匹配开始的位置, 8
print(obj.end())  # 匹配结束的位置, 13
print(obj.span())  # 匹配 (开始,结束) 的位置元组, (8, 13)
```

ref: [Python 正则表达式](https://www.runoob.com/python/python-reg-expressions.html)
