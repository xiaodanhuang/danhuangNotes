#### 一.概述

为了防止对象属性名称的冲突，在es6中引入新的数据结构symbol

```
let s=symbol("s")//Symbol生成的是原始类型得值，而不是对象，所以不能用new
console.log(s)//Symbol(s)
let s1 = Symbol("fool");
let s2 = Symbol("fool");
console.log(s1==s2)//false
console.log(s1===s2)//false
```

#### 

#### 二.Symbol.prototype.description- es2019

```
let s1 = Symbol("fool");
console.log(s1.description)//fool
```



#### 三.作为属性名称的Symbol

```
//实例可参考消除魔法字符串，ps:魔法字符串，在代码之中多次出现、与代码形成强耦合的某一个具体的字符串或者数值
let myName=Symbol("name");
let myMotherName=Symbol("name")
let obj={}
obj[myName]="danhuang";//Symbol作为属性名称的时候不能用点运算符
obj[myMotherName]="xiaohua"
console.log(obj)//{ [Symbol(name)]: 'danhuang', [Symbol(name)]: 'xiaohua' }
```

#### 四.Symol作为属性名称的遍历

```
let myName=Symbol("name");
let myMotherName=Symbol("name")
let obj={}
obj[myName]="danhuang";
obj[myMotherName]="xiaohua"
let attr=Object.getOwnPropertySymbols(obj)//方法返回数组
console.log(attr)//[ Symbol(name), Symbol(name) ]
```

#### 五.Symbol.for\(\) SymbolKeyFor\(\)

```
//Symbol.for() key值若存在，不再重新创建
let s1=Symbol.for("fool")
let s2=Symbol.for("fool")
console.log(s1==s2,s1===s2)//true true

//SymbolKeyFor(),方法返回一个已登记的 Symbol 类型值的key。
let s1=Symbol.for("fool")
console.log(Symbol.keyFor(s1))//fool

```

#### 六.内置的 Symbol 值

```

```



