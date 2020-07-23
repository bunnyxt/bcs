## mysql-server

### 安装mysql-server
```shell
sudo apt-get install mysql-server
```

### 设置允许远程访问

编辑以下文件
```shell
sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
```

修改
```shell
bind-address           = 127.0.0.1
```

这一行为
```shell
bind-address           = 0.0.0.0
```
保存退出

重启服务
```shell
sudo service mysql restart
```

### 设置root用户允许远程访问

登陆mysql
```shell
mysql -u root -p
```

输入授权指令并使其立刻生效
```sql
grant all on *.* to root@'%' identified by '<root用户的密码>' with grant option;
flush privileges;
```

或者直接修改```mysql.user```表
```sql
use mysql;
update user set host = '%' where user = 'root';
```

可以通过以下指令查看是否修改完成
```sql
select host, user from user;
```

### 数据迁移

单表导出

```shell
mysqldump <db-name> -u <username> -p<password> --tables <table-name> > <table-name>.sql
```

运行导出的sql

```sql
source /path/to/your/file.sql
```
