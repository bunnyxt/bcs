## Ubuntu安装Java

去官网[https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)下载需要的jdk版本（这里以jdk8为例），选择`Linux x64 Compressed Archive`下载，文件名形如`jdk-8u261-linux-x64.tar.gz`。

下载完成后，解压该文件，得到文件夹`jdk1.8.0_261`
```shell
tar -zxvf jdk-8u261-linux-x64.tar.gz
```

将文件夹移动到某个地方，这里以`/usr/local/`为例
```shell
mv jdk1.8.0_261 /usr/local
```

之后添加以下环境变量
```shell
JAVA_HOME=/usr/local/jdk1.8.0_261
JRE_HOME=/usr/local/jdk1.8.0_261/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH
```

激活环境变量，完成。

可以通过`java -version`指令查看安装的版本，验证是否安装成功。

ref: [ubuntu安装Java环境](https://www.cnblogs.com/Yatces/p/10513701.html)