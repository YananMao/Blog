# Array-like object 和iterable object

## 1Array-like object

类数组对象是什么呢?简单的说,就是这个对象不是数组,但是他有length属性,并且可以通过数字索引来访问.

```
let array_like_object = {};
const num = 10;
for(let i=0; i < len; i++) {
	array_like_object[i]=i
}
array_like_object.length = num;
```

这样我们就创建了一个类数组对象