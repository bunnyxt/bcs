# Linux

* [快捷键](shortcut.md)
* [~/.bashrc配置](bashrc.md)
* [跳过第一行输出文本文件](skip-first-line.md)
* [tail -f | grep](tail-f-grep.md)
* [scp路径中包含空格](scp-space-in-path.md)

## 常用命令的常见参数及用法

### sort

- `-t, --field-separator=SEP`，指定分割域（列）的字符为`SEP`，默认是空（空格、TAB等） 
- `-k, --key=KEYDEF`，指定按某个域和类型（`KEYDEF`）排序，例如`-k 2`就是按照第二列排序，完整格式解析见[《sort命令的k选项大讨论》-linux命令五分钟系列之二十七](http://roclinux.cn/?p=1472)
- `-n, --numeric-sort`，按数字大小（而不是字典序）排序
- `-h, --human-numeric-sort`，按人类可读新式的数字大小排序（例如2K、1G）
- `-r, --reverse`，反转排序结果（即从大到小）

例：

```shell
ls -lh | sort -k 5 -h -r | head
```

显示当前文件夹下的文件（长格式，人类可读形式的文件大小），按文件大小从大到小排序，显示前10条
