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
order by sum(data_length) desc, sum(index_length) desc;
```

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
order by data_length desc, index_length desc;
```

可追加条件：
- 指定数据库名：`where table_schema='tdd'`
- 限制返回条数：`limit 10`
