# DOM 扩展

## 选择符API

* `querySelector()` 返回匹配的第一个元素
* `querySelectorAll()` 返回一个 `NodeList`, 包含所有匹配的元素
* `matchsSelector()` 参数为 `CSS` 选择符，调用元素与该选择符匹配返回 `true`, 反之 `false`

```js
console.log(document.body.matchsSelector('body'))
```

## 元素遍历API

> `Element Traversal API` 新增5个属性(不含空白节点和注释节点)

* `childElementCount` 返回子元素的个数
* `firstElementChild` 返回第一个子元素
* `lastElementChild` 返回最后一个子元素
* `previousElementSibling` 返回前一个兄弟元素
* `nextElementSibling` 返回后一个兄弟元素

## 类名相关

> 新增 `classList` 属性  返回该节点所有的类名

定义了4个方法

* `add(value)` 添加类名
* `remove(value)` 删除类名
* `contain(value)` 检测是否包含类名
* `toggle(value)` 切换类名(存在则删除，不存在则添加)

## document 相关

### readyState 属性

> 判断文档是否加载完毕, 相当与我们借助 `onload` 事件判断

* `loading` 正在加载文档
* `complete` 文档加载完成

```js
if(document.readyState === 'complete'){
    // 文档加载完成，执行操作
}
```

### 兼容模式

判断浏览器渲染模式

```js
if(document.compatMode === 'CSS1Compat'){
    // 标准模式
} else {
    // 兼容模式 document.compatMode 为 BackCompat
}
```

## scrollIntoView()

使元素出现在可视窗口中。可用于解决 `ios中软键盘遮住表单的问题`
