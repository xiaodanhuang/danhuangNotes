#### 一.let 和const

```js
//let 块级作用域的声明 不存在变量提升
{
    let a=1
}
console.log(a)//a is not defined

//const 块级作用域定义常量 其值不能改变
const a=2;
```

#### 二.变量解构赋值 ps:\(只要等号右边的值不是对象或数组，就先将其转为对象\)

1.解构

```js
//数组的解构赋值
let [a,b,c]=[1,2]
console.log(a,b,c)//1 2 undefined
let [a,b=2,c=3]=[1,undefined,null]
console.log(a,b,c)//1 2 null

//对象的解构赋值
let { name,age}={age:"1",name:"danhuang"}
console.log(name,age)
let name;
({name}={name:"danhuang"})
console.log(name)//danhuang 已声明变量的解构赋值 需要加大括号

//字符串的解构赋值
let [a,b,c]="abc"
console.log(a,b,c)//a b c
let {length : len}="abc"
console.log(len)//3 类似数组的对象都有一个length属性

//数值和布尔值的解构赋值 
let {toString: s} = 123;
s === Number.prototype.toString // true

let {toString: s} = true;
s === Boolean.prototype.toString // true

//函数参数饿解构赋值
function add([x,y]){
    return x+y
}
console.log(add([1,2]))//3
```

2.用途

```
//交换变量的值
let [x,y]=[1,2];
[x,y]=[y,x]
console.log(x,y)//2 1

//从函数返回多个值以及函数参数的定义
function minAndMax([a,y,z]){
    let min=a<y?a:y<z?y:z
    let max=a>y?a:y>z?y:z
    return [min,max]
}
[min,max]=minAndMax([1,9,4])
console.log(min,max)//1,9

//提取 JSON 数据
let obj={
    name:"xiaodanhuang",
    age:16
}
let {name,age}=obj
console.log(name,age)//xiaodanhuang 16

//函数默认值
function ajax(url,{aync=true}){
    console.log(url,aync)
}
ajax("https://baidu.com",{}) //https://baidu.com true

//遍历数组

const map= new Map();
map.set("I","love")
map.set("my","mother")
for([key,key] of map){
    console.log(key,value)
}
/*
 *   I love
 *  my mother
*/

//输入模块的指定方法
const { SourceMapConsumer, SourceNode } = require("source-map");
```

#### 三.字符串的扩展

    //unicode表示法
    console.log("\u{78}")//

    //for of 遍历

    //模板字符串
    let name="danhuang"
    console.log(`哈哈${name}`)//哈哈danhuang

    //标签模板 
    alert`123`// 等同于alert(123)

    //新增的方法
    console.log(String.fromCodePoint(0x20BB7))// 𠮷 String.fromCodePoint()  Unicode 码点返回对应字符
    console.log(String.raw())



