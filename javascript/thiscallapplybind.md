#### this

上回书说到 函数执行前的准备阶段会创建函数执行上下文，然后会确定this的指向。那么this是啥？

this是一个对象。他在创建后被绑定。全局函数中，this指向window。而函数通过对象调用的时候，this指向这个对象。

##### 如何确定this指向-谁调用就指向谁

1. 全局调用-this 指向全局
2. 对象调用函数  `obj.func()`指向对象。
3. call ,apply ,bind 指向函数第一个参数 ` func.bind(obj)`
4. 箭头函数-指向箭头函数外部最近的一个函数的this,没有就是全局对象。
5. 构造函数 -` new`this指向创建的对象
6. dom处理函数-this指向触发函数的dom元素

##### call和apply的区别

call和apply都是改变this用的。call接收参数列表。apply接收一个参数数组。

##### 实现call

```
Function.prototype.call=function(obj,...args){
    if(typeof obj !=='object') throw  new Error("非对象")
    obj.func=this;
    let result=obj.func(...args)
    delete obj.func
    return result;
}

Function.prototype.call=function(obj){
    if(typeof obj !=='object') throw  new Error("非对象")
    obj.func=this;
    let args=[]
    for(var i = 1, len = arguments.length; i < len; i++) {
        args.push('arguments[' + i + ']');
    }
    args=args.join(',')
    let result=eval('obj.func('+args+')')
    delete obj.func
    return result;
}
```

##### 实现apply

```
Function.prototype.Apply=function(obj,args){
    if(typeof obj !=='object') throw  new Error("非对象")
    obj.func=this;
    let result=obj.func(args)
    delete obj.func
    return result;
}
Function.prototype.Apply=function(obj,args){
    if(typeof obj !=='object') throw  new Error("非对象")
    obj.func=this;

    let result=obj.func(args)
    delete obj.func
    return result;
}
```

参考来源：[https://juejin.im/post/5907eb99570c3500582ca23c\#heading-4](https://juejin.im/post/5907eb99570c3500582ca23c#heading-4)

##### 实现bind

一个绑定函数也能使用new操作符创建对象：这种行为就像把原函数当成构造器。提供的 this 值被忽略，同时调用时的参数被提供给模拟函数。

```
Function.prototype.bind=function(context){
    var args=Array.prototype.slice.call(arguments,1);
    var self=this;
    var fNOP = function () {};
    var fbound= function(){
        let current_args=Array.prototype.slice.call(arguments);
        self.call(this instanceof self?this:context,...args.concat(current_args))
    }

    fNOP.prototype=  this.prototype;
    fbound.prototype=new fNOP
    return fbound
}
```





