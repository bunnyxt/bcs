## tail -f | grep

对日志记录做多次grep过滤输出，格式如下：

```shell
tail -f xxx.log | grep --line-buffer yyy
```

因为管道`|`是全缓冲的，一般来说`buffer_size`为4096，有些是8192。不管具体值多少，只有buffer_size满了，才会看到输出。当`grep`带上了`--line-buffer`的时候，每输出一行，就刷新一次，即可实现对日志文件实时输出的筛选。

ref: [tail -f 多次grep过滤输出](https://www.quwenqing.com/read-134.html)
