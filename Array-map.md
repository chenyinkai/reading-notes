# Array.map()

> 创建一个新的数组，元素为之前数组每一项调用方法后的返回值

## 语法

```javascript
let newArray = arr.map((currentValue, index, array) => {
  // Return element for newArray
})
// 或者
let newArray = Array.prototype.map.call(arr, (currentValue, index, array) => {})
```

有 3 个参数：

* `currentValue` 当前处理中的元素
* `index` 当前处理中元素的索引
* `array` 原数组本身

## demo

```javascript
// simple demo
const arr1 = [1, 2, 3]
console.log(arr1.map(val => val * val)) // [1,4,9]
console.log(arr1.map(Math.sqrt))
console.log(Array.prototype.map.call(arr1, val => val * val))

// 将 kvArray 输出为 [{1:10},{2,20},{3,30}]
const kvArray = [
  {
    key: 1,
    value: 10
  },
  {
    key: 2,
    value: 20
  },
  {
    key: 3,
    value: 30
  }
]

let kvArrayTest = kvArray.map((val, i) => {
  let obj = {}
  obj[val.key] = val.value
  return obj
})
console.log(kvArrayTest)

// 和字符串的应用
console.log(Array.prototype.map.call('HelloWorld', val => val.charCodeAt(0)))
```

## code

```javascript
// 下面的语句返回什么呢:
['1', '2', '3'].map(parseInt)
// 你可能觉的会是[1, 2, 3]
// 但实际的结果是 [1, NaN, NaN]

// 通常使用parseInt时,只需要传递一个参数.
// 但实际上,parseInt可以有两个参数.第二个参数是进制数.
// map方法在调用callback函数时,会给它传递三个参数:当前正在遍历的元素, 元素索引, 原数组本身.
// 第三个参数parseInt会忽视, 但第二个参数不会,也就是说,
// parseInt把传过来的索引值当成进制数来使用.从而返回了NaN.

function returnInt(element) {
  return parseInt(element, 10)
}
```
