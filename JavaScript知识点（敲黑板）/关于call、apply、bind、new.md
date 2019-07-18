# new call apply bind的模拟实现

为什么把这几个放在一起呢？因为 感觉这几个都是可以修改this指向的，所以就把他们放一起了哈哈哈。

## 一 new

```javascript
// 手写new的实现
var newF = function(constructor,...args) {
  //为什么这里不用new Object（），因为现在是在模拟new的实现哇。。。
  let obj = Object.create(null);
  //这里为什么不用__proto__或者Object.setPrototypeOf()呢
  //因为__proto__属性不是所有的浏览器都支持，而且引入reflect就是为了可以把Object对象上一些属于语言内部（？）的方法都部署过来，所以感觉用reflect是一个更好的选择呢
  Reflect.setPrototypeOf(obj,constructor.prototype);
  let res = constructor.call(obj,...args);
  //如果调用newF返回的是一个对象，就返回这个对象
  if(res && (typeof res === 'object' ||typeof res === 'function')){
      return res
  }
  return obj
}
```

### tips：

1. ##### [Object.create()]( <https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/create>)

2. ##### 调用new的时候，如果返回一个对象就直接返回这个对象而不是返回我们新创建的这个对象哦

## 二、call

```javascript
// 手写call的实现
Function.prototype.call = function(ctx,...args){
  ctx = ctx || window;
  ctx.callFn = this;
  // es6
  // let result = ctx.callFn(...args);
  // 使用eval()
  // eval('ctx.callFn(arguments[0],arguments[1])')
  let args1 = [];
  for(let i=1,len=arguments.length;i<len;i++){
    args1.push(`arguments[${i}]`)
  }
  let result = eval(`ctx.callFn(${args1})`
  //函数调用完之后要删除该属性
  delete ctx.callFn;
  return result
}
```

### tips：

1. ##### 函数调用完之后要删除对应的属性哦

## 三、apply

```javascript
//手写apply的实现
Function.prototype.apply = function(ctx,arr){
  ctx = ctx || window;
  arr = arr || [];

  ctx.applyFn = this;
  let args = arr.map((val,index) => {
    return `arr[${index}]`
  })
  let res = eval(`ctx.applyFn(${args})`)
  delete ctx.applyFn;
  return res;
}
```

## 四、bind

```javascript
// 手写bind的实现
// 返回一个新的函数
// bind返回的函数可以当做构造函数使用，
Function.prototype.bind = function(ctx,...args){
    //如果调用bind的不是函数，报错
    if (typeof this !== "function") {
      throw new Error("Function.prototype.bind - what is trying to be bound is not 		callable");
    }
    
    
  //传入的ctx为null或者undefined时，this为window
  ctx = ctx || window;
  let self = this;
  let bound = function(...args1){
    // 作为构造函数时，this指向实例；普通函数时，this指向window
    return self.call(this instanceof bound? this:ctx,...args,...args1);
  }

  bound.prototype = Object.create(this.prototype);

  return bound;

}
```





