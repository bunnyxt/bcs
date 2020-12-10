## 终端指令

### 清除Mac OS文件系统的附加属性

出现问题：提示`项目xxx已被 OS X 使用，不能打开`，常出现在移动硬盘内，文件呈灰色，打不开

```shell
xattr -c <filename>  # clear <filename> file extended attributes
xattr -c *.*  # clear extended attributes of all files in current folder
```

ref: [mac 移动硬盘文件灰色，项目“XXX”已被OS X使用，不能打开](https://www.jianshu.com/p/a4533888a2a2)
