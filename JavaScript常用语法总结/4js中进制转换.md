# js中进制转换

**parseInt()可以将任M(M>=36)进制的数转换为10进制**

**toString()可以把10进制的数转换为N进制**

##### 通过这两个函数就可以实现任意两个进制间的转换

### parseInt(string,radius=10):

2<=rdius<=36(0-9,a-z)

```
console.log(`parseInt(111): ${parseInt(111)}`);
console.log(`parseInt(111,2): ${parseInt(111,2)}`);
console.log(`parseInt('12316712',5): ${parseInt('12316712',5)}`);
```

![4.0](..\pictures\4.0.png)

### toString(bool/number,radius = 10)

```
num1 = 111;
console.log(`num1 = 111;\nnum.toString(3): ${num1.toString(3)}`);
num2 = '111';
console.log(`num2 = '111';\nnum.toString(3): ${num2.toString(3)}`);
```

![4.1](..\pictures\4.1.png)