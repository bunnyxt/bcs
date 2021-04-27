## scp路径中包含空格

本地路径中包含空格的话，直接在空格前加`\`转义即可，同`cp`对空格的处理，如下：

```shell
scp file\ with\ space.txt user@host:/path/to/destination
```

远端路径中包含空格的话，需要将远端路径（冒号`:`后面的部分）用双引号（`""`）包裹，并在空格前加`\\`转义，如下：

```shell
scp user@host:"/remote/path/to/file\\ with\\ space.txt" /path/to/destination
```

ref: [SCP and path with spaces? (another "waste of time issue")](https://blogs.oracle.com/joshis/scp-and-path-with-spaces-another-waste-of-time-issue)
