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

![3.0](..\pictures\3.0.png)

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

   ![3.2](..\pictures\3.2.png)

   ​	

   ##### c 数值转换：

   ###### 	Number( ):

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

   ​	![3.1](..\pictures\3.1.png)

   ###### 	parseInt( ):

   ​	把字符串转换为10进制整数，从前往后解析，可以指定把字符串按多少进制进行解析（详见

   [js进制转换]: 4js中进制转换.md）

   

2. String

3. Boolean

4. Undefined

5. Null

### 引用类型（Object）

