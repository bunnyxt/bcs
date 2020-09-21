## pandas相关操作

```python
import pandas as pd
```

### Cheat Sheet

![pandas_cheat_sheet](pandas_cheat_sheet.png)

### 按行遍历

```python
for index, row in df.iterrows():
    print('index %d, name %s, age %d' % (index, row['name'], row['age']))
```

### 多条件筛选

```python
df_filtered = df[(df['sex'] == 'male') & (df['age'] >= 18)]
```
