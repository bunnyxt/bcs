## vsftpd

## 安装vsftpd

```shell
sudo apt-get install vsftpd
```

### 启动服务
```shell
service vsftpd start
```

### 添加运行访问的用户

新建文件`/etc/vsftpd.user_list`，用于存放允许访问ftp的用户
```shell
sudo vim /etc/vsftpd.user_list
```

添加用户名，一行一个

建议新建一个用户uftp专门用来连接ftp

### 修改配置文件

编辑配置文件
```shell
sudo vi /etc/vsftpd.conf
```

打开注释（即去掉行首的`#`）
```shell
write_enable=YES 
```

添加信息（即在文件尾部添加以下三行）
```shell
userlist_file=/etc/vsftpd.user_list 
userlist_enable=YES 
userlist_deny=NO 
```

### 其他

FileZilla连接配置中选`SFTP`

ref: [在Ubuntu16.04下配置VSFTPD](https://blog.csdn.net/xiangwanpeng/article/details/54427557)