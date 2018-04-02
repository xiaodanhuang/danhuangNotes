###对象？
###### 理解对象
- 对象，无序属性的集合
- 属性类型：
	1. 数据属性：configurable,Enumerable,writable,value
	2. 修改属性特性请使用Object.defineProperty，Object.definePropertys
	3. 访问器属性：setter，getter,`_year`标记下划线表示只能通过对象方法进行访问
	4. 取读属性特性：Object.getOwnPropertyDescriptor

###### 创建对象
1. 工厂模式
```
function  createObj(name,age){
	var obj =new Object();
	obj.name=name;
	obj.age=age;
    obj.sayName=function (){console.log(this.name)}
	return obj
}
```
2. 构造函数模式
```
function Person(name,age){
	this.name=name;
	this.age=age;
    this.sayName=function (){console.log(this.name)}
}
```
3. 原型模式
```
function Person(){
	Person.prototype.name="danhuang"
	Person.prototype.age="age";
	Person.prototype.sayName=function (){console.log(this.age)}
	}
var person =new Person()
person.hasOwnProperty("name")//false 测试属性是在实例中还是原型中
```
4.组合使用构造函数以及原型模式方式
```
function Person(name,age){
	this.name=name;
	this.age=age;
}
Person.prototype={
constructor : Person,
	sayName:function(){
    		console.log(this.name)
		}
}
```
5.动态原型模式
```
function Person(name,age){
	this.name=name;
	this.age=age;
    if(typeof this.sayName!="function"){
    Person.prototype.sayName=function (){console.log(this.age)}
    }
}
```
6.寄生构造函数模式
```
function  Person(name,age){
	var obj =new Object();
	obj.name=name;
	obj.age=age;
    obj.sayName=function (){console.log(this.age)}
	return obj
}
```
7.稳妥构造函数模式
```
function  Person(name,age){
	var obj =new Object();
    obj.sayName=function (){console.log(name)}
	return obj
}
```
###### 继承对象
- 原型链
```
function SurperPerson(){this.name='danhuang'}
SurperPerson.prototype.getName=function(){ return this.name}
function Person(sex){this.sex=sex }
Person.prototype=new SurperPerson()
a =new Person('boy')
a.name//danhuang
```
- 借用构造模式
```
function SurperPerson(){this.name=['danhuang']}
function Person(){ SurperPerson.call(this);
}
a =new Person()
a.name.push('haha')//Person {name: Array(2)}
b=new Person()//Person {name: Array(1)}
```
- 组合继承模式
```
function SurperPerson(name){this.name=name}
SurperPerson.prototype.getName=function(){ return this.name}
function Person(name,age){ 
	SurperPerson.call(this,name);
	this.age=age
}
```
- 原型式继承
```
function createObj(obj){ function F(){}; F.prototype=obj; return new F()}
person={name:'danhuang', age:18,work:[]}
a =createObj(person)
a.work.push('web')
b=createObj(person)
b.work//["web"]
```
- 寄生继承
```
function createObj(obj){ 
var obj= Object(obj);
obj.sayhi=function(){console.log(obj.name)};
return obj}
obj={name:'danhuang',age:13}
```
- 组合寄生继承
```
function SurperPerson(name){this.name=name;this.color=[]}
SurperPerson.prototype.getName=function(){ return this.name};
function Person(name,age){ 
	SurperPerson.call(this,name);
    this.age=age;
	}
 Person.prototype=new SurperPerson();
 Person.prototype.construcor=Person;
 Person.prototyp.sayName=function(){console.log(this.name)}   
```

