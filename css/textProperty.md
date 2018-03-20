#文本属性
###### color 文本颜色
```
p{
	color:pink//字的颜色设置为粉色
}
```
###### direction
设置文本方向
```
p{
	direction:ltr;//从左到右
    direction:rtl;//从右到左
}
```
###### letter-spacing 字符间距
```
p{
	letter-spacing:2px;
	letter-spacing:-2px;
}
```
###### line-height 行高
行高不可为负值
```
p{
	line-height:20px
}
```
###### text-align 对齐方式
left:文字左对齐，center：文字居中，right：文字右对齐
###### text-decoration
1. overline:上划线
2. line-through 中间划线
3. underline：下划线

###### text-indent
首行缩进
```
p{
	text-indent:4px;
}
```
###### text-shadow 文本阴影
text-shadow: h-shadow v-shadow blur color;
1. h-shadow:水平阴影位置
2. v-shadow：垂直阴影位置
3. 模糊距离
4. 阴影颜色

```
p{
	text-shadow:2px 20px pink;
}
```
###### text-transform
1. capitalize首字母大写
2. uppercase全大写
3. lowercase全小写

###### vertical-align
1.text-top
2.text-bottom
3.middle

######  white-space  空白处理
1.normal空白自动忽略
2.pre 保留空白
3.nowrap 不换行
4.pre 保留空白 正常换行
5.pre-line 合并空白 保留换行符

###### word-spacing
```
p{ 
	word-spacing:30px;
}
```