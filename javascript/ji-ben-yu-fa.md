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

1.转换为string -调用toString\(\)，ps :不影响原变量







