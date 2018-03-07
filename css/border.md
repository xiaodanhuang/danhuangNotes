#css border以及outline
border可以理解为一个元素的边框，outline就是一个元素的轮廓。
###### border 复合属性

```
 .content{
        width:200px ;
        height:200px;
        border:1px solid pink;//border-width, border-style,和border-color
    }
```
###### border-width,border-style,border-color
border-width设置边框的宽度，border-style设置边框的样式，border-color设置边框的颜色
```
.content1{
	width:200px;
    height:200px;
    border-width:2px 4px 6px 10px;
    border-style:solid dashed  double dotted;
    border-color:red orange yellow green ;
    }
```

###### border-x-width,border-x-styleborder-x-color
x可以取的值：top,right,bottom,left，即单独设置上，右，下，左的边框的样式。
###### border-x
x可以取的值：top,right,bottom,left,即设置上，右，下，左的复合样式
```
.content1{
        width:200px;
        height:200px;
        border-top:1px solid pink;
    }
```
###### outline即为轮廓，将元素理解为人的脸，我们常说的轮廓就是脸部的轮廓，那么outline就可以理解为元素最外的一圈，outline可以将元素包裹在一起。
```
.content{
        width:200px ;
        height:200px;
        border:1px solid pink;
        outline:1px dotted yellow;
    }
```
######  border-radius
设置边框的圆角弧度
######  border-image
设置边框的样式用图片来填充
###### box-shadow阴影
```
div
{
    box-shadow: 10px 10px 5px #888888;
}
```
