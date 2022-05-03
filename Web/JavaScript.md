---
title: Javascript
aliases: [js, JS]
---

JavaScript 是主要用于 *Web* 的脚本语言。

## Number

`.toFix(n)`: 保留 n 位小数点  

## Array 数组

### 属性
属性|描述
---|---
`length` |数组的长度  

### 方法

方法|描述
---|---
`concat()`| 连接多个数组
`delete array[index]` |动态删除数组元素
`fill(x)`|用 x 填充数组
`join(分隔符)` |将元素组合成字符串  
`pop()` |弹出最后一个元素  
`push(newItem)`| 将 newItem 添加至数组中  

## 字符串

```js
const x = 'world';
console.log('hello ${x}');  //可以这样在字符串中插入变量
```

### 方法

```JavaScript
"hello".charAt(0); // "h"
"hello, world".replace("world", "mars"); // "hello, mars"
"hello".toUpperCase(); // "HELLO"
```

`.trim()`: 删除两端空白

## 类型转换

- `Number()`
- `parseInt()`
- `parseFloat()`

## 类型判断

- `isNaN()` 函数用于判断输入是否为 `NaN`

- `isFinite()` 判断是否为有穷量

## Truthy 与 Falsy

Truthy 指的是在布尔值上下文中，转换后为真的值。Falsy 与之相对，是转换后为假的值。

Falsy 包括：
- `false`
- `0`
- `-0`
- `0n`
- `""`
- `null`
- `undefined`
- `NaN`

其它不是 Falsy 的值都是 Truthy

## for 循环

- `for（value of iterable) {}` 语句可以遍历 `iterable` 中的元素

- `for(property in object){}` 语句可以遍历对象中的**属性**。

## switch ... case 语句

```javascript
switch(a) {
    case 1: // 继续向下
    case 2:
        eatIt();
        break;
    default:
        doNothing();
}
```

## 输入

```js
const line = readline();  //将输入的一行字符串存入 line
const array = readline().split(' ').map(Number);  //这样可以将输入的数组存入 array
```

## 异步函数

### setTimeout

`setTimeout(func,t)` 

`setTimeout` 中的函数可以这样传入

```javascript
let myGreeting = setTimeout(sayHi, 2000, 'Mr. Universe');
```

`setTimeout()` 会返回一个用于取消延时的标志，设置了延时程序后可以通过该引用名取消

```javascript
clearTimeout(myGreeting);
```

### setInterval

interval 是每隔一定时间重复执行的函数

`setInterval(fun, time)` 用于设置定时
`clearInterval(intervalName)` 用于取消定时

### 递归的 setTimeout

```javascript
setTimeout(function mytf() {

	//执行的代码

	setTimeout(mytf, 100);
},100);
```

### Timeout or Interval?
递归的 Timeout 可以保证每次运行之间的间隔是一样的，或者说代码结束与下一次代码开始的时间是一样的；而 Interval 只会保证 代码开始与下一次代码开始的时间一样，也就是说把代码执行的时间也算进时间间隔里了。

当代码执行的时间很**长**时，最好使用递归的 `setTimeout()`


## Date() 
`date = new Date()` 创建一个 Date 对象

`date.toLocaleTimeString()` 可以返回一个当前时间的字符串。

## 异常处理

``` javascript
try{
// 要运行的代码
}
catch(e){
// 处理异常的代码
}
finally{
// try 完总会运行的代码
}
```

`throw <Error>` 抛出错误, 可被父级 catch

## DOM API

- [[Canvas]] 是常用于绘制动画的画布

### 滚动 

[window.scrollBy(x, y)][scrollBy]

滚动一定的距离，单位是像素。

[scrollBy]:https://developer.mozilla.org/zh-CN/docs/Web/API/Window/scrollBy

## 从服务器获取数据

有两种方法：
- XmlHttpRequest(XHR)
- fetch

XHR 是较传统的兼容性更好的方法，而 fetch 是更现代的方法。fetch 还用到了优雅的 Promise 语法。

## arguments 对象

arguments 对象在函数被调用时自动创建

arguments.length 返回调用函数时的实参个数

## 技巧

```JavaScript
//用于判断对象是否存在，若存在则执行后面的方法
var name = o && o.getName();

//用于缓存，若前面为真则不执行后面的语句
var name = cachedName || (cachedName = getName());
```

## 代码优化

在对象不再使用时赋予 `null` 可有助于减少内存占用

## 一些有意思的库

- [[Matter.js]]  一个 2d 的物理引擎