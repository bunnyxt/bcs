## 空间占用检查

### 查看所有数据库占用空间大小

```sql
select
table_schema as '数据库',
sum(table_rows) as '记录数',
sum(truncate(data_length/1024/1024, 2)) as '数据长度(MB)',
sum(truncate(index_length/1024/1024, 2)) as '索引长度(MB)',
sum(truncate(data_length/1024/1024, 2)) + sum(truncate(index_length/1024/1024, 2)) as '总长度(MB)'
from information_schema.tables
group by table_schema
order by sum(data_length) desc, sum(index_length) desc
limit 10;
```

ref: [MySQL查看数据库表容量大小](https://blog.csdn.net/ystyaoshengting/article/details/103726237)

### 查看所有数据库中各表占用空间大小

```sql
select
table_schema as '数据库',
table_name as '表名',
table_rows as '记录数',
truncate(data_length/1024/1024, 2) as '数据长度(MB)',
truncate(index_length/1024/1024, 2) as '索引长度(MB)',
truncate(data_length/1024/1024, 2) + truncate(index_length/1024/1024, 2) as '总长度(MB)'
from information_schema.tables
order by data_length desc, index_length desc
limit 10;
```

ref: [MySQL查看数据库表容量大小](https://blog.csdn.net/ystyaoshengting/article/details/103726237)

可追加条件：
- 指定数据库名：`where table_schema='tdd'`

### 查看所有数据库中各索引占用空间大小

```sql
select 
database_name as '数据库', 
table_name as '表名', 
index_name as '索引名',
truncate(stat_value * @@innodb_page_size/1024/1024, 2) as '索引长度(MB)'
from mysql.innodb_index_stats
where stat_name = 'size' and index_name != 'PRIMARY'
order by `索引长度(MB)` desc
limit 10;
```

可追加条件：
- 指定数据库名：`where database_name='tdd'`
- 指定表名：`where table_name='tdd_video_record'`

注意：`index_name`为`PRIMARY`的索引是表自身，因此忽略。

ref: [How to figure out size of Indexes in MySQL](https://stackoverflow.com/questions/781873/how-to-figure-out-size-of-indexes-in-mysql)
