# JavaScript中的数据类型总结

使用 typeof 对数据类型进行判断：

```
console.log(typeof number: ${typeof 1});`
console.log(typeof string: ${typeof '6666'});`
console.log(typeof boolean: ${typeof true});`
console.log(typeof undefined: ${typeof undefined});`
console.log(typeof null: ${typeof null});`
console.log(typeof object: ${typeof {}});`
console.log(typeof function: ${typeof function(){}});`
```

控制台结果为：

![3.0](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/3.0.png)

### 基本类型

1. #### Number

   ##### a 数值类型： 整数 浮点数

   ##### b 数值范围：

   ###### 	min：Number.MIN_VALUE

   ###### 	max：Number.MAX_VALUE

   ​	超过这个范围，正数 Infinity，负数 -Infinity

   ##### C NaN(not a number):	

   ​	任何涉及到NaN的操作都返回NaN,NaN不跟任何数相等，NaN !== NaN

   ###### 	isNaN( ):

   ```
   console.log(`isNaN(1): ${isNaN(1)}`);
   console.log(`isNaN('11'): ${isNaN('11')}`);
   console.log(`isNaN('emoji'): ${isNaN('emoji')}`);
   console.log(`isNaN(true): ${isNaN(true)}`);
   ```

   ![3.2](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/3.2.png)

   ​	

   ##### d 类型转换：

   ###### 	Number( ):

   ​	把**所有的数据类型**转化为数值

   ```
   console.log(`Number('be happy'): ${Number('be happy')}`);
   console.log(`Number('0011'): ${Number('0011')}`);
   console.log(`Number('0x11'): ${Number('0x11')}`);
   console.log(`Number(''): ${Number('')}`);
   console.log(`Number(33): ${Number(33)}`);
   console.log(`Number(undefined): ${Number(undefined)}`);
   console.log(`Number(null): ${Number(null)}`);
   console.log(`Number({size:10}): ${Number({size:10})}`);
   console.log(`Number({}): ${Number({})}`);
   ```

   ​	![3.1](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/3.1.png)

   ###### 	parseInt( ):

   ​	把**字符串**转换为10进制整数，从前往后解析，**[可以指定把字符串按多少进制进行解析](https://github.com/YananMao/JavaScript-Grammars/blob/master/JavaScript%E5%B8%B8%E7%94%A8%E8%AF%AD%E6%B3%95%E6%80%BB%E7%BB%93/4js%E4%B8%AD%E8%BF%9B%E5%88%B6%E8%BD%AC%E6%8D%A2.md)**。

   ###### 	parseFloat():

   ​	把**字符串**转化为整数或者小数，从前往后解析，**不能指定把字符串按多少进制进行解析**。

   ##### e [进制转换](https://github.com/YananMao/JavaScript-Grammars/blob/master/JavaScript%E5%B8%B8%E7%94%A8%E8%AF%AD%E6%B3%95%E6%80%BB%E7%BB%93/4js%E4%B8%AD%E8%BF%9B%E5%88%B6%E8%BD%AC%E6%8D%A2.md)

2. #### String

   ##### a 类型转换

   ###### toString( ):

   可以将number，boolean，object(**除了null和undefined**)类型转换为数值类型。

   ```
   num=11;
   console.log(`num=11\nnum.toString(): ${num.toString()}`);
   console.log(`num.toString(2): ${num.toString(2)}\ntoString()方法可以把number类型的数据转换进制`);
   console.log(`true.toString(): ${true.toString()}`);
   console.log(`{test:'hhh'}.toString(): ${{test:'hhh'}.toString()}`);
   ```

   ![3.3](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/3.3.png)

   ###### String( ):

   可以把**所有的数据类型**转换为string。

   ```
   num=11;
   console.log(`num=11\nString(num): ${String(num)}\nString()方法不能进行进制转换`);
   console.log(`String(true): ${String(true)}`);
   console.log(`String({test:'hhh'}): ${String({test:'hhh'})}`);
   console.log(`String(null): ${String(null)}`);
   console.log(`String(undefined): ${String(undefined)}`);
   ```

   ![3.4](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/3.4.png)

3. #### Boolean

   ##### a 类型转换

   ###### Boolean( ):

   ```
   console.log(`Boolean(11): ${Boolean(11)}`);
   console.log(`Boolean(0): ${Boolean(0)}`);
   console.log(`Boolean(NaN): ${Boolean(NaN)}`);
   console.log(`Boolean(true): ${Boolean(true)}`);
   console.log(`Boolean(''): ${Boolean('')}`);
   console.log(`Boolean('hiahia'): ${Boolean('hiahia')}`);
   console.log(`Boolean(undefined): ${Boolean(undefined)}`);
   console.log(`Boolean(null): ${Boolean(null)}`);
   console.log(`Boolean({}): ${Boolean({})}`);
   ```

   ![3.5](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/3.5.png)

4. ##### Undefined

   一个变量声明了但是没有初始化

5. ##### Null

   **null表示一个空指针对象，所以typeof null === object**。

   如果一个准备用一个变量来表示对象，可以把它初始化为null。

### 引用类型（Object）

看下一个最简单的对象，他从Object（）继承了哪些属性：

```
let obj = new Object();
obj.name = 'mao';
obj.lovers = ['sherlock','messi','zht'];
obj.age = 23;
console.log(obj.__proto__);
console.log(`let obj = new Object();\nobj.name = 'mao';`)
console.log('%cconstructor:','color:red');
console.log(`obj.constructor: ${obj.constructor}`);
console.log('%chasOwnProperty:','color:red');
console.log(`obj.hasOwnProperty('constructor'): ${obj.hasOwnProperty('constructor')}\nobj.hasOwnProperty('name'): ${obj.hasOwnProperty('name')}`);
console.log('%cisPrototypeOf:','color:red');
console.log(`Object.prototype.isPrototypeOf(obj): ${Object.prototype.isPrototypeOf(obj)}\nObject.isPrototypeOf(obj): ${Object.isPrototypeOf(obj)}`);
console.log('%cpropertyIsEnumerable:','color:red');
console.log(`obj.propertyIsEnumerable('name'): ${obj.propertyIsEnumerable('name')}\nobj.propertyIsEnumerable('lovers'): ${obj.propertyIsEnumerable('lovers')}\nobj.propertyIsEnumerable('age'): ${obj.propertyIsEnumerable('age')}`);
console.log('%ctoLocaleString:','color:red');
console.log(`obj.toLocaleString(): ${obj.toLocaleString()}`);
console.log('%ctoString:','color:red');
console.log(`obj.toString(): ${obj.toString()}`);
console.log('%cvalueOf:','color:red');
console.log(`obj.valueOf(): ${obj.valueOf()}`);
```

![3.6](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/3.6.png)

![3.6](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/3.7.png)

to be continued~~