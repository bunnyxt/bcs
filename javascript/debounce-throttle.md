## 防抖与节流

### 防抖（debounce）

在事件被触发`n`秒后再执行回调函数，如果在这`n`秒内事件又被触发，则重新计时。

```javascript
function debounce(func, delay) {
    return function (...args) {
        let that = this;
        clearTimeout(func._debounceTimeoutId);
        func._debounceTimeoutId = setTimeout(function () {
            func.call(that, ...args)
        }, delay);
    };
}
```

### 节流（throttle）

在事件触发后`n`秒内若再次（多次）触发事件，则除了第一次触发后的回调函数立刻执行外，其余的回调函数都等到第一次事件触发`n`秒后再执行（且只执行一次）。

举例：酒吧畅饮套餐规定，两次续杯之间间隔时间不少于20分钟，那么如果在8:00点了一杯畅饮，8:05喝完了，这时候再去要续杯的话是不给续的（酒吧会记录下但不会立刻理睬）。同理，8:10、8:15的时候去要续杯，酒吧都不会理睬，直到8:20酒吧才会把第二杯酒给我。注意：不论8:00到8:20之间我跟酒吧要了多少次续杯，8:20的时候我只能得到一杯续杯。另外，即使我8:20没有去跟酒吧要续杯，酒吧也会把续杯给我，因为之前我要过了，酒吧已经记录下来了，所以不需要我8:20的时候再去说一遍要续杯。

```javascript
function throttle(func, threshhold) {
  let last, deferTimer;
  return function (...args) {
    let that = this;
    let now = +new Date;
    if (last && now < last + threshhold) {
      clearTimeout(deferTimer);
      deferTimer = setTimeout(function () {
        last = +new Date;
        func.call(that, args);
      }, last + threshhold - now);
    } else {
      last = now;
      func.call(context, args);
    }
  };
}
```