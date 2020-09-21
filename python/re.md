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
