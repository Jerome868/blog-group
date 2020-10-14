# 数组
> 数组（Array）是一种线性表数据结构。它用一组连续的内存空间，来存储一组具有相同类型的数据。

**线性表**
线性表就是数据排成像一条线一样的结构。每个线性表上的数据最多只有前和后两个方向。

**连续的内存空间和相同类型的数据**
正是因为这两个限制🚫，它才有了一个堪称“杀手锏”的特性：“随机访问”。但有利就有弊，这两个限制也让数组操作变得非常低效，比如想在数组中删除、插入一个数据，为了保证连续性，就需要做大量的数据搬移工作。

## 数组的属性
- Array.length length 是 array 的实例属性。返回或设置一个数组中的元素个数。
- Array.prototype[@@unscopables]

## 数组的方法
**Array.from()**
作用：从一个类似数组或可迭代对象创建一个新的，浅拷贝的数组实例。
```js
console.log(Array.from('foo'));
// expected output: Array ["f", "o", 'o']

console.log(Array.from([1, 2, 3], x => x + x));
// expected output: Array [2, 4, 6]
```
**Array.isArray()**
作用：判断参数是否为 Array
```js
Array.isArray([1, 2, 3]);
// true
```
instanceof 和 isArray
*档检测 Array 实例时，`Array.isArray` 优于 `instanceof`， 因为 Array.isArray 能检测 `iframes`*
Polyfill
```js
if(!Array.isArray) {
    Array.isArray = function(arg) {
        return Object.prototype.toString.call(arg) === '[object Array]'
    }
}
```
**Array.of()**
作用：创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或者类型。返回新的 `Array` 实例
`Array.of()` 与 `Array` 构造函数之间的区别在于处理整数参数。
```js
Array.of(7) // [7]
Array.of(1, 2, 3) // [1, 2, 3]

Array(7) // [ , , , , , , ]
Array(1, 2, 3) // [1, 2, 3]
```
**Array.prototype.concat()**
作用：合并两个或多个数组，并返回一个新数组
**Array.prototype.map(callbackfn, thisArg)**
