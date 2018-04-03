###函数表达式
###### 函数表达式的特征
```
var sayName=function (name){console.log(name)}
```
###### 函数实现递归
- 函数通过名字调用自身函数也可用arguments.callee代替

###### 使用闭包定义私有变量
- 闭包是有权访问另一个函数作用域中变量的函数
- 闭包只能取得函数中任何变量的最后一个值
```
function createFunctions(){
	var result = new Array();
	for (var i=0; i < 10; i++){
		result[i] = function(){
		return i;
		};
	}
	return result;
}
function createFunctions(){
	var result = new Array();
	for (var i=0; i < 10; i++){
		result[i] = function(num){
		return function(){
		return num;
		};
	}(i);
	}
	return result;
}
```
- 立即执行函数可以模仿块级作用域