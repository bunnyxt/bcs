## 跳过第一行输出文本文件

### tail -n +k

-n +k即从正数第k行开始一直读到文件尾，故-n +2就是从第二行开始输出

```shell
seq 1 5 | tail -n +2
```

输出结果
```
2
3
4
5
```

### awk NR / FNR

NR和FNR是awk内置变量，分别对应文件中已处理的输入记录数和当前文件中已处理的记录数。当要处理的文件只有一个时，FNR和NR的作用相同

所以，要只显示除过第一行的其他所有行，指定NR != 1或者FNR != 1即可

```shell
seq 1 5 | awk 'NR != 1 { print }'
```

或者使用FNR

```shell
seq 1 5 | awk 'FNR != 1 { print }'
```

输出结果同上

### sed -n p

sed命令的-n参数的作用是使sed命令不产生输出

sed的替换命令中p标记的作用是打印与替换替换命令中指定的模式匹配的行

-n参数和p标记结合使用，就可以打印出与指定模式匹配的行

2,$表示从第二行到最后一行

```shell
seq 1 5 | sed -n '2,$p'
```

也可以指定不需要打印的行，使用!p标记

```shell
seq 1 5 | sed -n '1!p'
```

输出结果同上

### sed d

sed的删除命令d，通过指定行区间，用来删除文本流中的特定行

删除第一行的话就是1d


```shell
seq 1 5 | sed '1d'
```

输出结果同上

ref: [使用不同的命令打印文本中除过第一行的所有行](https://blog.csdn.net/swinfans/article/details/82823478)
