### 百度前端学院第二天笔记之HTMl5
#### HTML5是什么？
HTML5是HTML的最新的修订版本，就酱紫。氮素HTML5有好多有意思的特性。
##### HTML语义化
语义就是一定的含义。HTML是文本标记语言。为了让别人很好的看我们写的渣渣代码，也为了让HTML呈现出比较好的内容结构，代码结构。利于一下SEO，页为了其他设备解析。我们需要语义化。语义化就是少写一点没啥意义的元素。请多来点语义化的标签吧，吼吼吼。
##### H5的文档声明 <!DOCTYPE html>
一定别忘咯。HTML的文档模式有两种，标准模式以及混杂模式。混杂模式浏览器会按照自己的方式去解析HTML，酱紫是不对的。
##### 我觉得常用的语义以及结构元素
- article 定义页面独立的区域，用于论坛帖子，博客文章，新闻故事等等。
- aside 顾名思义，侧边栏
- commad 定义命令按钮
- details 描述文档或者某部分的细节
- dialog 对话框
- summary 标签包含details 元素的标题
- figure 独立的流内容
- figcaption 定义figure的标题
- footer 定义页脚
- header 定义页头
- mark 带有标记的文本
- nav 导航
- progress 定于任务进度
- section 定义文档的节
- time 定义日期时间

###### -2018年4月28日
正在实习的蛋黄
###### 马上下班咯，五一找时间更新嘿嘿🤗
#####图形
- canvas 画布
使用canvas元素可以在网页上绘制图像
- 内联SVG
可伸缩矢量图形

##### 媒体
- 视频 video
- 音频 audio

##### input新类型
- color
- datedatetime
- datetime-local
- email
- month
- number
- range
- search
- tel
- time
- url
- week

#####表单
##### web存储 
使用HTML5可以在本地存储用户的浏览数据。
- localStorage	没有时间限制的数据存储
- sessionstorage 针对一个session的数据存储
```
localStorage.setItem(key,value);
localStorage.getItem(key);
localStorage.removeItem(key);
localStorage.clear();
localStorage.key(index);
```
##### web SQL
##### 离线缓存
manifest 文件可分为三个部分：
- CACHE MANIFEST - 在此标题下列出的文件将在首次下载后进行缓存
- NETWORK - 在此标题下列出的文件需要与服务器的连接，且不会被缓存
- FALLBACK - 在此标题下列出的文件规定当页面无法访问时的回退页面（比如 404 页面）
```
<html manifest="demo.appcache">
```
##### web workers
web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行。
##### SSE
HTML5 服务器发送事件（server-sent event）允许网页获得来自服务器的更新。
##### websocket
WebSocket是HTML5开始提供的一种在单个 TCP 连接上进行全双工通讯的协议。等有时间写个例子...
###### -2018年5月2日
正在实习的蛋黄
###### 明天更新css🤗


