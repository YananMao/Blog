#  Array-like object 和iterable object

## 一、Array-like object

类数组对象是什么呢?简单的说,就是这个对象不是数组,但是他有length属性,并且可以通过数字索引来访问.

```
let array_like_object = {};
const num = 10;
for(let i=0; i < len; i++) {
	array_like_object[i]=i
}
array_like_object.length = num;
```

这样我们就创建了一个类数组对象.

常用的类数组对象主要有:

### 1 arguments

```
var test = function(){
	console.log(arguments);
}
test(1,2,3);
```

![9.0](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/9.0.png)

### 2 NodeList

