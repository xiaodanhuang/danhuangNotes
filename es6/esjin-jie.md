#### 一.symbol

###### 一.概述

为了防止对象属性名称的冲突，在es6中引入新的数据结构symbol

```
let s=symbol("s")//Symbol生成的是原始类型得值，而不是对象，所以不能用new
console.log(s)//Symbol(s)
let s1 = Symbol("fool");
let s2 = Symbol("fool");
console.log(s1==s2)//false
console.log(s1===s2)//false
```

###### 二.Symbol.prototype.description- es2019

```
let s1 = Symbol("fool");
console.log(s1.description)//fool
```

###### 三.作为属性名称的Symbol

```
//实例可参考消除魔法字符串，ps:魔法字符串，在代码之中多次出现、与代码形成强耦合的某一个具体的字符串或者数值
let myName=Symbol("name");
let myMotherName=Symbol("name")
let obj={}
obj[myName]="danhuang";//Symbol作为属性名称的时候不能用点运算符
obj[myMotherName]="xiaohua"
console.log(obj)//{ [Symbol(name)]: 'danhuang', [Symbol(name)]: 'xiaohua' }
```

###### 四.Symol作为属性名称的遍历

```
let myName=Symbol("name");
let myMotherName=Symbol("name")
let obj={}
obj[myName]="danhuang";
obj[myMotherName]="xiaohua"
let attr=Object.getOwnPropertySymbols(obj)//方法返回数组
console.log(attr)//[ Symbol(name), Symbol(name) ]
```

###### 五.Symbol.for\(\) SymbolKeyFor\(\)

```
//Symbol.for() key值若存在，不再重新创建
let s1=Symbol.for("fool")
let s2=Symbol.for("fool")
console.log(s1==s2,s1===s2)//true true

//SymbolKeyFor(),方法返回一个已登记的 Symbol 类型值的key。
let s1=Symbol.for("fool")
console.log(Symbol.keyFor(s1))//fool
```

###### 六.内置的 Symbol 值

```

```

#### 二.数据结构之map set

###### 1.set 无重复数据的集合 键值和键名相等

```
let s = new Set();
[1,1,2,2,3,3,4,4].map(item=>s.add(item))//set 加入值的时候不会进行类型转换
console.log(s)//Set { 1, 2, 3, 4 }
let s = new Set([1,2,3,3,4,"4"]);//Set { 1, 2, 3, 4, '4' }
console.log(s.size)//5
s.delete(1)//Set { 2, 3, 4, '4' }
s.has('4')//true
s.clear();//Set {}

//遍历 keys()：返回键名的遍历器 values()：返回键值的遍历器 entries()：返回键值对的遍历器 forEach()：使用回调函数遍历每个成员
```

###### 2.WeakSet 无重复数据的集合且键值为对象,无法遍历，没有size属性

```
let s = new WeakSet();
let obj={}
s.add(obj)
console.log(s)
```

###### 3.map 键值对的集合

```
let s = new Map();
s.set('name',"danhuang")
s.set('sex',"female")
console.log(s.size)//2
s.get('name')//danhuang
s.has('name')//true
s.delete('name')//true
s.clear()//Map {}
//遍历 keys():返回键名的遍历器 values():返回键值的遍历器。entries():返回所有成员的遍历器。forEach():遍历 Map 的所有成员。

//与其他类型转换
let s = new Map();
s.set('name',"danhuang")
s.set('sex',"female")
console.log([...s])//[ [ 'name', 'danhuang' ], [ 'sex', 'female' ] ] //map转数组
function mapToObj(map){
    let obj={}
    for(let [value,key] of map){
        obj[key]=value
    }
    return obj
}
function objToMap(obj){
    let map=new Map();
   for(let k of Object.keys(obj)){
       map.set(k,obj[k])
   }
    return map
}
let obj=mapToObj(s)
let map=objToMap(obj)
console.log(obj,map)//{ danhuang: 'name', female: 'sex' } Map { 'danhuang' => 'name', 'female' let s = new Map();
s.set('name',"danhuang")
s.set('sex',"female")

let arr=[...s]
console.log(arr)//[ [ 'name', 'danhuang' ], [ 'sex', 'female' ] ]
console.log(new Map(arr)) //Map { 'name' => 'danhuang', 'sex' => 'female' }
function mapToObj(map){
    let obj={}
    for(let [value,key] of map){
        obj[key]=value
    }
    return obj
}
function objToMap(obj){
    let map=new Map();
   for(let k of Object.keys(obj)){
       map.set(k,obj[k])
   }
    return map
}
let obj=mapToObj(s)
let map=objToMap(obj)
console.log(obj,map)//{ danhuang: 'name', female: 'sex' } Map { 'danhuang' => 'name', 'female' => 'sex' }
function mapToJson(map){
    return JSON.stringify([...map])
}
function JsonToMap(json){
    return objToMap(JSON.parse(json))
}
console.log(mapToJson(map))//[["danhuang","name"],["female","sex"]]
console.log(JsonToMap(mapToJson(map)))//Map { '0' => [ 'danhuang', 'name' ], '1' => [ 'female', 'sex' ] }
```

###### 4.WeakMap 只接受键名为对象

```
//WeakMap只有四个方法可用：get()、set()、has()、delete()。
```

#### 三.proxy

###### 1.概述

用于修改某些操作的默认行为。Proxy 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写。

2.get ,set

```
let person={name:'danhuang'}
var proxy = new Proxy(person, {
    get(target, propertyKey, receiver) {
        console.log('GET ' + propertyKey);
        return target[propertyKey];
    },
    set(target,key,value){
        if(key in target){
            console.log('modify')
        }else{
            console.log('add')
        }
        return value
    }
});
console.log(proxy.name)//danhuang
console.log(proxy.sex="female")//female
```

3.Proxy.revocable\(\)

4.this 问题

#### 四.reflect

1.概述

reflect 让Object操作都变成函数行为。

2.静态方法

* Reflect.apply\(target, thisArg, args\)
* Reflect.construct\(target, args\)
* Reflect.get\(target, name, receiver\)
* Reflect.set\(target, name, value, receiver\)
* Reflect.defineProperty\(target, name, desc\)
* Reflect.deleteProperty\(target, name\)
* Reflect.has\(target, name\)
* Reflect.ownKeys\(target\)
* Reflect.isExtensible\(target\)
* Reflect.preventExtensions\(target\)
* Reflect.getOwnPropertyDescriptor\(target, name\)
* Reflect.getPrototypeOf\(target\)
* Reflect.setPrototypeOf\(target, prototype\)

#### 五.promise对象

1.概述

异步编程的解决方案

```
const getJSON = function(url) {
    const promise = new Promise(function(resolve, reject){
        const handler = function() {
            if (this.readyState !== 4) {
                return;
            }
            if (this.status === 200) {
                resolve(this.response);
            } else {
                reject(new Error(this.statusText));
            }
        };
        const client =  new XMLHttpRequest();
        client.open("GET", url);
        client.onreadystatechange = handler;
        client.responseType = "json";
        client.setRequestHeader("Accept", "application/json");
        client.send();

    });

    return promise;
};

getJSON("https://baidu.com").then(function(json) {
    console.log('Contents: ' + json);
}).catch((function(error) {
    console.log('false');
})).finally(function(){console.log("end")});//false end
```

#### 六.Iterator

1.概述

遍历器（Iterator）就是这样一种机制。它是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署 Iterator 接口，就可以完成遍历操作（即依次处理该数据结构的所有成员）。

Iterator 的作用有三个：一是为各种数据结构，提供一个统一的、简便的访问接口；二是使得数据结构的成员能够按某种次序排列；三是 ES6 创造了一种新的遍历命令`for...of`循环，Iterator 接口主要供`for...of`消费。

#### 七.generator

1.概述

Generator 函数是 ES6 提供的一种异步编程解决方案

```
function *helloworldGenerator(){
    yield 'hello';
    yield 'world';
    return 'finish'
}
let hw =helloworldGenerator()
console.log(hw.next()) //{ value: 'hello', done: false }
console.log(hw.next())//{ value: 'world', done: false }
console.log(hw.next())//{ value: 'finish', done: true }
console.log(hw.next())//{ value: undefined, done: true }
```

#### 八.async

#### 九.class

```
class Person{
    constructor(name,sex){
        this.name=name;
        this.sex=sex
    }
    getName(){
        return this.name
    }
    setName(name){
        this.name=name
    }

}
class  Friends  extends Person{
    constructor(name,sex,whos){
        super(name,sex);
        this.whos=whos
    }
    getWhos(){
        this.whos.whos
    }

}
let danhuang=new Friends("danhuang",'female','mango')
console.log(danhuang.getName())
danhuang.setName("xiaodanhuang")
console.log(danhuang)//Friends { name: 'xiaodanhuang', sex: 'female', whos: 'mango' }
```



