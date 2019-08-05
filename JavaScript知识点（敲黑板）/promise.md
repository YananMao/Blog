# 关于Promise

promise是es6引入的解决异步编程的对象，他有很多常见的用法。

## 1、Promise.all

input: 一个部署了iterator接口的对象promises

output：

1. 一个新的promise实例p
2. 当promises中的所有的promise实例的状态都变为fulfilled的时候，p也变为fulfilled，并且所有实例的返回值组成一个数组，传给p的回调函数
3. promises中有任意一个promise实例的状态变为rejected的时候，p也变为rejected，并且这个被rejected的实例的返回值传给p的回调函数。

```javascript
Promise.all = function(promises) {
	return new Promise( (resolve,reject)=> {
		// 传入的参数必须有iterator接口
		if(typeof promises[Symbol.iterator] === 'undefined'){
			reject('参数类型不对哦')
		}
		// 将输入的对象转换为数组
		promises = Array.from(promises);
		let number = promises.length;
		let count = 0;
		let res = [];
		for(let [index,promise] of promises.entries()){
			Promise.resolve(promise).then((value) => {
				res[index]=value;
				if(++count === number){
					resolve(res)
				}
			}).catch((error) => {
				reject(error)
			})
		}
	} )
}
```

## 2、promise.race

```javascript
Promise.race = function(promises){
	return new Promise((resolve,reject) => {
		if (typeof promises[Symbol.iterator] === 'undefined'){
			reject('输入的参数不对')
		}
		promises = Array.from(promises);
		for(let promise of promises){
			Promise.resolve(promise).then((value) => {
				resolve(value);
			}).catch((error) => {
				reject(error)
			})
		}
	})
}
```

