## Ubuntu安装Python

去官网[https://www.python.org/downloads/](https://www.python.org/downloads/) 找到需要下载的版本（这里以[3.7.8](https://www.python.org/downloads/release/python-378/)为例）

在最下面Files中选择第一个`Gzipped source tarball`，鼠标右键复制下载链接

打开Linux终端，使用`wget`下载该文件

```shell
wget https://www.python.org/ftp/python/3.7.8/Python-3.7.8.tgz
```

解压文件

```shell
tar -zxvf Python-3.7.8.tgz
```

使用make编译

```shell
./configure --prefix=/usr/local
make && make install
```

注意这里的**--prefix指定安装目录**，默认应该是`/usr/local`（make install需要sudo），何老师组服务器上是装在`/data1/usr/LiuJY/software`里

如果自定义了安装目录，则需要添加到环境变量PATH中，以方便直接调用程序。何老师组的服务器上添加的PATH是`/data1/usr/LiuJY/software/bin`（即安装目录/bin）

> [!NOTE]
>
> 为了覆盖`/usr/local`中可能已经安装了的默认的python，设置环境变量时，需要把我们自定义的PATH放在已有的PATH之前，即`export PATH="/data1/usr/LiuJY/software/bin:$PATH"`

ref: [Linux（Ubuntu）系统安装Python](http://c.biancheng.net/view/4162.html)