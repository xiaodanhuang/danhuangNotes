#css背景
#####css背景是用来将网页这个房子的各种物品进行涂绘，无论是涂上油漆还是粘上壁纸都可以通过css背景去实现
<img width="50px" src="http://osz5qtl3g.bkt.clouddn.com/css_backgroud.jpg"/>
###### 1.background-color以及background-image
顾名思义，background-color就是背景颜色，background-image就是背景图片
```
p{
	background-color:pink;
}
div{
	background-iamge:url("url")；
}
```
###### 2.background-repeat
repeat,重复。这个属性的意思是设置背景重复。当我们使用background-image的时候，很可能用到这个属性。这个属性一共有三个取值：repeat-x,repeat-y,no-repeat
```
p{
	background-iamge:url("url")；
    background-repeat:repeat-x;水平平铺
    background-repeat:repeat-y;垂直平铺
    background-repeat:repeat-x;不平铺
}
```
###### 3.background-position
background-position设置背景起始位置。
###### 4. background-attachment
 background-attachment设置背景是否固定。值为 fixed以及scroll
```
p{
	background-iamge:url("url")；
    background-attachment：fixed;//固定
    background-attachment:scroll;//随元素滚动
}
```
###### 5.bacground
设置多个背景图像（并指定他们的位置）：
###### 6.background-size
设置背景大小
```
p{
	background-size:100px 100px;//设置背景图片高度和宽度
    background-size:50%	50% 相对于背景定位区域的百分比;
    background-size:cover;//完全覆盖背景定位区域的最小大小。
    background-size:contain;//保持图像的纵横比,将图像缩放成将适合背景定位区域的最大大小。
}
```
###### 7.background-clip
指定对象的背景图像向外裁剪的区域
指定背景绘制区域。
```
p{
	background-clip:border-content;
    background-clip:padding-content;
    background-clip:content-box-content;
}
```
###### 8.background-origin
设置或检索对象的背景图像计算background-position时的参考原点(位置)。
```
p{
	background-origin:border-content;
    background-origin:padding-content;
    background-origin:content-box-content;
}
```

background 6，7，8都是css3中的新增加的属性
###### 郝老师，请回答 background-clip background-origin区别
