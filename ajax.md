# XMLHttpRequest

```js
let xhr = new XMLHttpRequest()
xhr.onreadystatechange = function() {
  if (xhr.readyState === 4) {
    if (xhr.status === 200) {
        alert(xhr.responseText)
    }
  }
}
xhr.open('GET', url, false)
xhr.send()
```

> `readyState`

* 0 -代理被创建，但尚未调用 open() 方法。
* 1 -open() 方法已经被调用。
* 2 -send() 方法已经被调用，并且头部和状态已经可获得。
* 3 -下载中， responseText 属性已经包含部分数据。
* 4 -下载操作已完成