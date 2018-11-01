#css 标准盒模型以及IE盒模型
所有的HTML元素都可以看作是一个盒子，在css中，盒子模型是用来设计和布局使用的。
盒模型包括：边距，边框，填充，以及实际内容即margin border，padding,content
<img  height="300px"src="http://osz5qtl3g.bkt.clouddn.com/gitbook-css-boxModel.png"/>
###### margin外边距
清除边框外的区域
###### border
边框
###### padding
清除内容周围的区域
###### content
盒子的内容 如上图可知，
width以及height设置的是content的宽度和高度。所以因此可以得到：
````
标准元素实际宽度=width+左右padding+左右border
标准元素实际高度度=width+上下padding+上下border
```
```
在IE盒模型中：
width=左右padding+左右border+内容
hieght=上下padding+上下border+内容
```