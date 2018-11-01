### ife设计学院第一天之过渡
#### 课程目标
- 熟悉 CSS3 过渡子属性
- 通过 JavaScript 触发过渡效果
- 理解语义化，合理地使用 HTML 标签来构建页面

#####  css过渡是元素从一种样式逐渐改变为另一种的效果。
```
transition：简写属性
transition-property：应用过渡的属性名称
transition-timing-function：过渡效果的事时间曲线
transition-delay：过渡延迟
```
##### 过渡时间曲线属性值
- linear	规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)）。
- ease	规定慢速开始，然后变快，然后慢速结束的过渡效果（cubic-bezier(0.25,0.1,0.25,1)）。
- ease-in	规定以慢速开始的过渡效果（等于 cubic-bezier(0.42,0,1,1)）。
- ease-out	规定以慢速结束的过渡效果（等于 cubic-bezier(0,0,0.58,1)）。
- ease-in-out	规定以慢速开始和结束的过渡效果（等于 cubic-bezier(0.42,0,0.58,1)）。
- cubic-bezier(n,n,n,n)	在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值。

[example地址](https://codepen.io/xiaodanhuang/pen/KRqaNg)

###### 2018年5月3日
-正在实习的蛋黄

