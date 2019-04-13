# 来扒一扒JavaScript中的Array

数组是在JavaScript中经常使用的一种数据类型，今天来看一看Array都有哪些操作吧。

## 一、判断一个数据是不是数组

都有哪些方法呢，让我来动一下我聪明的小脑袋来想一想。

```
let mao = [1,1];
let frame = document.createElement('iframe');
document.body.append(frame);
let frameArray = window.frames[0].Array(1,2,3);
console.log(`let mao = [1, 1];\t怎么判断mao是个数组呢？`);
console.log(`根据数组的构造函数是Array(),数组的原型是Array.prototype,有下面5种方法`)
console.log('%c1 constructor属性','color:red');
console.log(`mao.constructor === Array: ${mao.constructor === Array}`);
console.log('%c2 instanceof','color:red');
console.log(`mao instanceof Array: ${mao instanceof Array}`)
console.log('%c3 isPrototypeOf()','color:red');
console.log(`Array.prototype.isPrototypeOf(mao): ${Array.prototype.isPrototypeOf(mao)}`);
console.log('%c4 Object.getPrototypeOf()','color:red');
console.log(`Object.getPrototypeOf(mao) === Array.prototype: ${Object.getPrototypeOf(mao) === Array.prototype}`);
console.log('%c5 __proto__属性','color:red');
console.log(`mao.__proto__ === Array.prototype: ${mao.__proto__ === Array.prototype}`);
console.log(`但是这几种方法是存在风险的，这是因为使用构造函数和原型判断时，都假定当前的全局执行环境是唯一的，而如果网页上包含多个框架，就会存在多个全局执行环境，也就存在着多个版本的Array构造函数。\n我们现创建一个array实例\nlet frame = document.createElement('iframe');\ndocument.body.append(frame);\nlet frameArray = window.frames[0].Array(1,2,3);\n用上面的几种方法来检验一下看是否生效`);
console.log(`frameArray.constructor === Array: ${frameArray.constructor === Array}
frameArray instanceof Array: ${frameArray instanceof Array}
Array.prototype.isPrototypeOf(frameArray) === true: ${Array.prototype.isPrototypeOf(frameArray) === true}
Object.getPrototypeOf(frameArray) === Array.prototype: ${Object.getPrototypeOf(frameArray) === Array.prototype}
frameArray.__proto__ === Array.prototype: ${frameArray.__proto__ === Array.prototype}`)
console.log(`针对上面出现的问题，es5新增了Array.isArray()方法：\n`);
console.log('%c6 Array.isArray:','color:red');
console.log(`Array.isArray(mao): ${Array.isArray(mao)}
Array.isArray(frameArray): ${Array.isArray(frameArray)}
这种方法也有局限性就是并不是所有的浏览器都支持，emmmm
所以祭出终极大招，利用Object的原生toString方法`);
console.log('%c7 Object.prototype.toString()','color:red');
console.log(`Object.prototype.toString.call(mao) === "[object Array]": ${Object.prototype.toString.call(mao) === "[object Array]"}`);
console.log(`Object.prototype.toString.call(frameArray) === "[object Array]": ${Object.prototype.toString.call(frameArray) === "[object Array]"}`);
```

![8.0](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/8.0.png)

## 二、查找类

### 1、元素是否在数组里

​	我们现在已经可以判断一个对象是不是数组了，假设判断出一个对象是数组了，那怎么判断某个元素在不在这个数组里呢？

