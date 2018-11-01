#css 定位
在css中使用定位可以将元素放到你想要放的位置。就像瓦匠可以将瓦放在自己想要放的位置。
###### float
float即浮动。故名思义，设置这个属性可以让元素向左或者向右浮动，设置了float的属性为浮动元素。此时浮动元素脱离普通文档流。浮动元素不仅影响自己，也会影响周围的元素对齐进行环绕。
float:left/right
```
<style>
    .content{
        float:left;
    }

</style>
<div class="content">youyouyou</div>
<span>hahahhah</span>
```
###### position
position位置，
1. static 默认值，没有定位
2. absolute 绝对定位，相对于static 定位意外的第一个父元素进行定位
3. relative 相对定位
4. fixed 相对于浏览器窗口进行定位
5. inherit继承

z-index:设置元素的堆叠顺序
###### display
常用的display属性值
1. none 元素不被显示
2. block 块级元素
3. inline 行内元素
4. inline-block行内块元素【自行百度】
5. table 块级表格
6. table-cell 表格单元格
7. table-row表格的行
8. table-column表格的列

###### overflow
指定如果内容溢出一个元素的框，会发生什么
1.visible 默认值，呈现在元素框外
2.hidden内容被修剪，外面的看不见
3.scroll 出现滚动条，不管有没有溢出都出现
4.auto 有溢出就出现滚动条，没有则不出现
5.inherit继承父元素的
