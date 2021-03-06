#### 执行上下文&执行栈

##### 执行上下文-代码执行的环境 （动态的

执行上下文的类型

1. 全局执行上下文
2. 函数执行上下文
3. eval执行上下文

执行上下文的3个重要属性：

* 作用域链-由多个执行上下文的变量对象构成的链表就叫做作用域链

```
var scope = "global scope";
function checkscope(){
    var scope2 = 'local scope';
    return scope2;
}
checkscope();
```

执行过程如下：

1.checkscope 函数被创建，保存作用域链到 内部属性\[\[scope\]\]

```
checkscope.[[scope]] = [
    globalContext.VO
];
```

2.checkscope 函数执行，创建执行上下文，压入执行栈

3.拷贝作用域链到执行上执行上下文

4.创建活动变量，收集函数，变量以及函数参数

5.将活动变量添加到执行上下文的作用域头部

6.修改活动变量将scope2修改，返回scope2的值

7.出执行栈

##### 活动变量-arguments对象

```
function foo() {
    console.log(a);
    a = 1;
}

foo(); // ???

function bar() {
    a = 1;
    console.log(a);
}
bar(); // ???
```

第一题报错，因为a没有在函数执行上下文的活动对象中，根据作用域链往上找，全局也没有，所以报错

第二题输出1，a没有在函数执行上下文中。但是a=1执行后将a添加到全局执行上下文的活动变量里，所以输出为1

##### 执行栈-先进后出的数据结构，存储代码运行过程中创建的执行上下文。

当 JavaScript 引擎第一次遇到你的脚本时，它会创建一个全局的执行上下文并且压入当前执行栈。每当引擎遇到一个函数调用，它会为该函数创建一个新的执行上下文并压入栈的顶部。

引擎会执行那些执行上下文位于栈顶的函数。当该函数执行结束时，执行上下文从栈中弹出，控制流程到达当前栈中的下一个上下文。

##### 作用域：代码有权访问其他函数以及变量的权限。代码定义的时候就决定了

参考来源：[https://github.com/mqyqingfeng/Blog/issues/4](https://legacy.gitbook.com/book/xiaodanhuang/danhuangnotes/edit#)

#### 闭包

有权访问另一个函数作用域的活动对象的函数

题目指路：[https://juejin.im/post/58f1fa6a44d904006cf25d22\#heading-0](https://juejin.im/post/58f1fa6a44d904006cf25d22#heading-0)



