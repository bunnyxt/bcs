## ~/.bashrc配置

### 每次SSH连接后配置不自动生效

在`/etc/profile`文件中添加`source ~/.bashrc`

### alias

```shell
alias ll='ls -lh'  #alias ll='ls -alF'
```

### 环境变量

```shell
export PATH="<path-you-want-to-add>:${PATH}"
```

### PS1

PS1是命令行提示符，详细的参数含义参考[命令提示符](https://wangdoc.com/bash/prompt.html)

这里记录一个师兄给我们的挺好用的PS1

```shell
export PS1='${debian_chroot:+($debian_chroot)}\n\[\e[1;32m\][\t \[\e[1;32m\]\u@\[\e[1;35m\]\h:\[\e[36m\]$PWD]\[\e[0m\]\$ '
```

ref: [命令提示符](https://wangdoc.com/bash/prompt.html)