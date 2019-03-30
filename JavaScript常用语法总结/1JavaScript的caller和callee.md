---
typora-copy-images-to: ..\pictures
---

关于JavaScript的caller和callee：

```
function outerFunction(){
	innerFunction('test');
	// caller是函数的属性，返回调用当前函数的函数
	// 如果当前函数是在顶层，未被调用，返回null
	console.log('outerFunction的caller:\n',outerFunction.caller);
}
function innerFunction(arg1,arg2){
	console.log('innerFunction的caller:\n',innerFunction.caller);
	// callee是arguments的属性，实参传给哪个函数，就返回哪个函数
	console.log('innerFunction的arguments的callee：\n',arguments.callee);
	// 一个函数的length属性是形参的个数
	console.log('innerFunction的的长度: ',innerFunction.length);
	// arguments的长度是实参
	console.log('innerFunction的arguments的长度: ',arguments.length);
}
outerFunction();
```

浏览器打印结果：

![1.0](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/1.0.png)





