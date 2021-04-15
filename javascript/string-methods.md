## 字符串相关操作

### slice

`slice()`方法提取某个字符串的一部分，并返回一个新的字符串，且不会改动原字符串，语法为`str.slice(beginIndex[, endIndex])`。其中`beginIndex`表示开始提取的索引，`endIndex`表示结束提取的索引（**不包括此位置，类似Python的切片**）（可选，如不提供则表示一直提取到字符串结束）。这两个索引都可以为负数，表示从右到左第几个位置（同Python的负索引）。

```javascript
> const str = 'The morning is upon us.';
undefined
> str.slice(4, 11);
'morning'
> str.slice(12);
'is upon us.'
> str.slice(-3, -1);
'us'
> str.slice(30);
''
> str.slice(0, -1);  // 可以用来去除字符串末尾的几个字符
'The morning is upon us'
```

ref: [String.prototype.slice()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/slice)
