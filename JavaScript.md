---
title: Javascript
aliases: [js, JS]
---

JavaScript 是主要用于 *Web* 的脚本语言。

## Array 数组

`push(newItem)` 将 newItem 添加至数组中  

`length` 属性返回数组的长度  

`delete array[index]` 动态删除数组元素

`join(分隔符)` 将元素组合成字符串  

`pop()` 弹出最后一个元素  

`concat()` 连接多个数组

## 字符串方法

```JavaScript
"hello".charAt(0); // "h"
"hello, world".replace("world", "mars"); // "hello, mars"
"hello".toUpperCase(); // "HELLO"
```

## 类型转换

- Number() 
- parseInt()
- parseFloat()

`isNaN()` 函数用于判断输入是否为 `NaN`

`isFinite()` 判断是否为有穷量

## Truthy 与 Falsy

Truthy 指的是在布尔值上下文中，转换后为真的值。Falsy 与之相对，是转换后为假的值。

Falsy 包括：
- false
- 0
- -0
- 0n
- ""
- null
- undefined
- NaN

其它不是 Falsy 的值都是 Truthy

## for 循环

- `for（value of iterable) {}` 语句可以迭代 `iterable` 中的元素

`for(property in object){}` 语句可以遍历对象中的属性。

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

### Interval

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

递归的 Timeout 可以保证每次运行之间的间隔是一样的，或者说代码结束与下一次代码开始的时间是一样的；而 Interval 只会保证 代码开始与下一次代码开始的时间一样，也就是说把代码执行的时间也算进时间间隔里了。

当代码执行的时间很**长**时，最好使用 `setTimeout()`


## Date() 
`date = new Date()` 创建一个 Date 对象

`date.toLocaleTimeString()` 可以返回一个当前时间的字符串。

## 全局对象 `Global` 的常用方法

`isNaN(value)` 判断 value 是不是 NaN  

`parseFloat(string)` 将 string 转换为 float

`parseInt(string)` 同上

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

## `instanceof` 

instanceof是Java中的二元运算符，左边是对象，右边是类；当对象是右边类或子类所创建对象时，返回true；否则，返回false。

## arguments 对象

arguments 对象在函数被调用时自动创建

arguments.length 返回调用函数时的实参个数

## 代码优化

在对象不再使用时赋予 `null` 可有助于减少内存占用

## 技巧

```JavaScript
//用于判断对象是否存在，若存在则执行后面的方法
var name = o && o.getName();

//用于缓存，若前面为真则不执行后面的语句
var name = cachedName || (cachedName = getName());
```

## DOM API

- [[Canvas]] 是常用于绘制动画的画布

### 滚动 

[window.scrollBy(x, y)][scrollBy]

滚动一定的距离，单位是像素。

[scrollBy]:https://developer.mozilla.org/zh-CN/docs/Web/API/Window/scrollBy


## 一些有意思的库

- [[Matter.js]]  一个 2d 的物理引擎