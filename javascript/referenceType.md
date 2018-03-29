###引用类型
###### Object类型
- Object创建方式
```
var a=new Object();//new一个
var b={}//字面量
```

###### Array类型
```
//创建数组
var a=new Array();
var b=[];

//数组的length不是只读性的
a.length=3;

//数组转字符串
a=[1,2,3,4]
a.toString()//"1,2,3,4"
a.toLocaleString()//"1,2,3,4"
a.join(",")//"1,2,3,4"

//栈方法
a.push(5);//[1, 2, 3, 4, 5]尾部添加
a.pop()//[1, 2, 3, 4]尾部删除

//栈方法
a.shift()//[2, 3, 4, 5]//头部删除
a.unshift(-1)//[-1, 2, 3, 4, 5]//头部添加

//重排序方法
a.reverse()//[5, 4, 3, 2, -1]降序排列
a.sort()//[-1, 2, 3, 4, 5]升序排列

//操作方法
a.concat(a)//[-1, 2, 3, 4, 5, -1, 2, 3, 4, 5]
a.slice(1,3)//[2, 3]
a.splice(0,2)//[3, 4, 5] 改变该数组
a.splice(0,0,1,2)//[1, 2, 3, 4, 5]

//位置方法
a.indexOf(3)//2
a.lastIndexOf(4)//3

//迭代方法
every
some
forEach
map
filter

//归并方法
reduce
reduceRight
```
###### Date类型
格式化时间自己玩去🌝
###### RegExp
```
g//全局匹配
i//不区分大小写
m//多行
```
###### Function类型
- 函数实际上是对象，函数名其实是指向函数的指针
- 重复涂一遍，米有函数重载
- 函数表达式和函数声明是有区别的，解析器优先解析函数声明
- 函数中有特殊的对象：arguments以及this对象，arguments.callee可以指向此函数

###### 基本包装类型
- Boolean,Number,String

###### 单体内置对象
- Global
```
//编码
unicodeURI()
encodeURIComponent()
//类似解析器
eval()
```

- Math
```
//最值方法
Math.min(1,2,3,4)//1
Math.max(1,2,3,4)//4
//舍入方法
Math.ceil(5.1)//6向上舍入
Math.round(5.1)//5向下舍入
Math.floor(5.1)//5四舍五入
//随机函数
Math.random
```
