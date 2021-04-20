## 时间戳相关

注意，以下所说的时间戳指的是UNIX时间戳（以秒为单位），时间字符串为`yyyy-MM-dd HH:mm:ss`格式

### 获得当前时间字符串

```sql
mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2020-10-23 21:50:32 |
+---------------------+
1 row in set (0.00 sec)
```

### 获得当前时间戳

通过`unix_timestamp`将时间字符串转为时间戳

```sql
mysql> select unix_timestamp(now());
+-----------------------+
| unix_timestamp(now()) |
+-----------------------+
|            1603461186 |
+-----------------------+
1 row in set (0.00 sec)
```

### 时间戳转时间字符串

通过`from_unixtime`将时间戳转为时间字符串

```sql
mysql> select from_unixtime(unix_timestamp(now()));
+--------------------------------------+
| from_unixtime(unix_timestamp(now())) |
+--------------------------------------+
| 2020-10-23 21:54:02                  |
+--------------------------------------+
1 row in set (0.00 sec)
```

兜兜转转套娃套回来了