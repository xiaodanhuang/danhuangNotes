### ife基础学院第3天之选择器
##### 选择器可以定位我们需要样式化的元素。我们可以讲HTML理解为一个房子的架构，css理解为对这个房子进行装修。在css中选择器可以理解为选择房子的某一个部分进行装修。例如我们要将门涂成粉色，代码如下：
```
.door{
	background:pink;
}
```
##### css中的各种选择器
###### 1.ID选择器
ID选择器就像我们的身份证一样，每个HTML元素只能有一个ID，通过ID选择器我们可以为此元素添加样式，并以 "#" 来定义。例如房子的前门我要涂成黄色，代码如下：
```
#front-door{
	background:yello;
}
```
###### 2.class选择器
class即为类，选中一类事物添加样式，并以 "." 来定义。例如房子的门涂成粉色，代码如上。
```
.door{
	background:pink;
}
```
###### 3.标签选择器
此选择器的标签就是html里面的标签。代码如下：
```
div{
	text-align:center;//文字居中
}
```
###### 4.通用选择器
*就是通用选择器，使用此选择器选中的是全部的元素，代码如下
```
*{
    margin: 0px auto;//居中
}
```
###### 5.子选择器以及后代选择器
子选择器选择的是一个元素的所有子元素。后代选择器选择的是一个元素的所有后代元素，子子孙孙都选择。
```
.house>div{
	//子选择器
}
.house div{
	//后代选择器
}
```
###### 6.直接兄弟选择器以及兄弟选择器
直接兄弟选择器选中的是一个元素后面的独一个兄弟，兄弟选择器选中的是所有兄弟。
```
.table+desk{
//桌子后面第一个椅子
}
.table~desk{
//桌子后面所有的椅子
}
```
###### 7. 伪类选择器[样式在特定状态下才被呈现到指定元素]
常见伪类：
锚点 :link,:hover,:active,:focus,:visited
表单元素：enabled、:disabled、:checked
结构伪类：
1,:nth-child(n)、:nth-last-child(n)、first-child、last-child、:only-child
2,:nth-of-type(n)、:nth-last-of-type(n)、:first-of-type、:last-of-type、:only-of-type
3,:root、:not、:empty、:target
###### 8.伪元素
:before ,:after
###### 9.属性选择器
```
[attribute]			用于选取带有指定属性的元素。
[attribute=value]	用于选取带有指定属性和值的元素。
[attribute~=value]	用于选取属性值中包含指定词汇的元素。
[attribute|=value]	用于选取带有以指定值开头的属性值的元素，该值必须是整个单词。
[attribute^=value]	匹配属性值以指定值开头的每个元素。
[attribute$=value]	匹配属性值以指定值结尾的每个元素。
[attribute*=value]	匹配属性值中包含指定值的每个元素。
```


