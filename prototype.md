# 原型和原型链

## 原型

* 所有的引用类型（数组、对象、函数），都具有对象特性，即可自由扩展属性(null除外)
* 所有的引用类型（数组、对象、函数），都有一个__proto__属性，属性值是一个普通的对象
* 所有的函数，都有一个prototype属性，属性值也是一个普通的对象
* 所有的引用类型（数组、对象、函数），__proto__属性值指向它的构造函数的prototype属性值

```js
// 要点一：自由扩展属性
var obj = {}; obj.a = 100;
var arr = []; arr.a = 100;
function fn () {}
fn.a = 100;

// 要点二：__proto__
console.log(obj.__proto__);
console.log(arr.__proto__);
console.log(fn.__proto__);

// 要点三：函数有 prototype
console.log(fn.prototype)

// 要点四：引用类型的 __proto__ 属性值指向它的构造函数的 prototype 属性值
console.log(obj.__proto__ === Object.prototype)
```

```js
// 构造函数
function Foo(name, age) {
    this.name = name
}
Foo.prototype.alertName = function () {
    alert(this.name)
}
// 创建示例
var f = new Foo('zhangsan')
f.printName = function () {
    console.log(this.name)
}
// 测试
f.printName()
f.alertName()
```

执行 `f.alertName()` 时，`f` 对象上没有 `alertName` 属性，那么它会在它的 `__proto__`(即它的构造函数的 `prototype` 上)， `f.alertName()` 相当于执行 `Foo.prototype.alertName`

## 原型链

> 接以上实例

```js
f.toString()
```

`f` 本身没有 `toString()`, `f.__proto__(Foo.prototype)`也没有 `toString()`, 那么继续往上查找 `f.__proto__.__proto__` 即 `Foo.prototype.__proto__` 即 `Object.prototype`, 在这里找到了 `toString`, 因此 `f.toString` 最终对应到了 `Object.prototype.toString`