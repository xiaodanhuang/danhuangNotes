#### 

#### 一.注释

```js
// 单行注释

/*
 * 多行注释 
*/
```

#### 二.字面量，变量，标志符

###### 字面量不可变，一般不会直接使用 eg:1,2,3

###### 变量，用来保存字面量 可任意改变

###### 标志符，自主命名的就是标志符 ，驼峰命名 规则：1.字母，数字，\_,$.2.标志符不能以数字开头.3.标志符不能是js中关键字 ，保留字

```
//声明变量并赋值
var a=1;
console.log(a)
```

#### 三.数据类型

1.String

```js
var str="hello world"
typeof str//string
```

2.Number 包括整数和浮点数

```js
var num=6
typeof num//number
NaN//not a number
Infinity//正无穷
console.log(135+23434564)//23434699 js中整数的运算可以保证精确
console.log(0.1+0.2)//0.30000000000000004 不精确
```

ps:进制

```
//十六进制
0x123//291
//八进制
0123//83 有些浏览器会当作8进制 有的当作十进制
//二进制
0b11//3
```

3.Boolean 逻辑判断

```
true
false
typeof true//boolean
```

4.Null表示空对象

```
var a=null;
typeof a//object
```

5.Undefind变量未赋值

```
var b;
typeof b //undefined
```

6.Object

#### 四.强制类型转换

1.转换为string 

```
var a=1;

//调用toString()
console.log(a.toString)//ps :不影响原变量,null, undefined 没有toString()

//调用String()
console.log(String(a))
```

2.转换为Number

```
//使用Number()
console.log(Number("123"))//123
console.log(Number("786cgv"))// NAN
console.log(Number(""))//0
console.log(Number(true))//1
console.log(Number(null))//0
console.log(Number(undefined))//0

//专门字符串用parseInt(),parseFloat() 先转字符串再转换成number
console.log(parseInt("786cgv"))// 786
console.log(parseFloat("12.123cgv"))//12.123
console.log(parseFloat("12.123cgv"))//12.123
```

3.转换为boolean

```
//Boolean（ ） 
console.log(Boolean("-1"))//true 数字除 0 NAN 都为true
console.log(Boolean(""))//false  除空串都为
console.log(Boolean(0))//false
console.log(Boolean(undefined))//false
console.log(Boolean(null))//false 对象转换为true
```

#### 五.运算符

1.算数运算符：+  -   \*   /  %

```
console.log(2+NAN)//NAN  任何值+NAN 都是NAN
console.log("123"+"456") //123456 字符串+字符串为拼接
console.log(true+"456") //true456 任何值+字符串 先转字符串再相加
console.log("123"-1)//122 任何值-number 先转number再相减
console.log(2*undefined)//NAN 
console.log(3/2)//1.5
```

2.一元运算符+ -

```
console.log(1+ +"2"+3) // 6 
-true// -1 负 -其他类型 转换mber 变负
```





