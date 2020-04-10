#### 

#### 原型

原型（prototype）是函数的属性名称。此属性指向一个对象。这个对象的用途是包含可以由特定类型的所有实例共享的属性和方法。

##### constructor

prototyp.constructor 指向函数

##### \_prototype\_

实例对象通过\_proto\_指向构造函数的prototype。

##### 继承

* 原型链继承

    function father(father_name){
        this.father_name=father_name;
    }
    father.prototype.sayName=function(){
        console.log(`father_name:${this.father_name} child_name:${this.name}`)
    }
    function child(name){
        this.name=name;
    }
    child.prototype=new father;
    child.prototype.constructor=child;

* 借用构造函数继承

    function father(father_name){
        this.father_name=father_name;
    }
    father.prototype.sayName=function(){
        console.log(`father_name:${this.father_name} child_name:${this.name}`)
    }
    function child(father_name,name){
        this.name=name;
        father.call(this,father_name)
    }

* 组合继承

    function father(father_name){
        this.father_name=father_name;
    }
    father.prototype.sayName=function(){
        console.log(`father_name:${this.father_name} child_name:${this.name}`)
    }
    function child(father_name,name){
        this.name=name;
        father.call(this,father_name)
    }
    child.prototype=new father;
    child.prototype.constructor=child;

* 原型式继承

```
function object(o){
    function F(){}
    F.prototype=o;
    return new F()
}
var obj={
    name:'danhang'
}
var a=object(father);
```

* 寄生式继承

```
function =object(o){
    function F(){}
    F.prototype=o;
    return new F()
}
var obj={
    name:'danhang'
}

function createO(obj){
    var o = object(obj);
    o.age=13;
    return o
}
var a= createO(obj);
```

* 寄生组合式继承

    function father(father_name){
        this.father_name=father_name;
    }
    father.prototype.sayName=function(){
        console.log(`father_name:${this.father_name} child_name:${this.name}`)
    }
    function createO(o){
        function F(){}
        F.prototype=o;
        return new F()
    }
    function inheritPrototype(child,father){
        var prototype=createO(father.prototype)
        prototype.sayChildName=function(){
            console.log(this.name)
        }
        prototype.constructor=child;
        child.prototype=prototype;
    }
    function child(father_name,name){
        father.call(this,father_name);
        this.name=name;
    }
    inheritPrototype(child,father)

##### es6实现继承

类似寄生组合式继承

#### 补充:创建对象的方式

* 工厂模式

```
function createPerson(name){
    var o=new Object();
    o.name=name;
    return o
}
```

* 构造函数模式

```
 function Person(name){
    this.name=name;
}
```

* 原型模式

```
function Person(){}

Person.prototype.sayName=function(){
    console.log(this.name)
}
Person.prototype.name='mango';
```

* 组合模式

```
function Person(name){
    this.name=name;
}

Person.prototype.sayName=function(){
    console.log(this.name)
}
```

* 动态原型模式

```
function Person(name){
    this.name=name;
    if( typeof  this.sayName !='function'){
        Person.prototype.sayName=function(){
            console.log(this.name)
        }
    }
}
```

* 寄生构造函数模式

```
function Person(name){
    var o=new Object();
    o.name=name;
    o.sayName=function(){
        console.log(this.name)
    }
    return o
}
```

* 稳妥构造函数模式

```
function Person(name){
    var o=new Object();
    o.sayName=function(){
        console.log(name)
    }
    return o
}
```



