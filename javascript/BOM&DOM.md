### BOM,DOM以及客户端检测
##### BOM
###### window对象
- 全局作用域
- 窗口位置 screenLeft ，screenTop,screenX,screenY
- 窗口大小 innerWidth,innerHeight,outerWidth,outerHeight
- window.open()
- 超时调用setTimeOut(),间歇调用setInterval()
- 系统对话框 alert(),confrim(),prompt()

###### location对象
- 查询字符串参数
<img src='http://osz5qtl3g.bkt.clouddn.com/js-location.png'/>
- 位置操作
```
local.assign()
local.herf=''
local.location=''
```

###### navigator对象
- 检测插件
navigator.plugins
- 注册处理程序
此处省略
###### screen对象
###### hiostory对象
```
history.go()
history.length
```

##### 客户端检测
- 能力检测
- 怪癖检测
- 用户代理检测 navigator.userAgent
- 检测方式

##### DOM
###### node类型
- 节点检测	nodeType/nodeName/nodevalue
- 节点关系	childNodes
- 节点操作	addpendChild/removeChild/replaceChild/cloneNode

###### Document类型
- 文档信息	URL/domain/referrer
- 查找元素	getElmentById/getElmentByTagName/getElementsByName
- 文档写入	wirte，writeln，open，close

###### Element类型
- 特性函数	setAttribute/getAttribute
- 创建元素	createElement

###### Text类型
###### Comment类型
###### CDATASection类型
###### DocumentType类型
###### DocumentFragment类型
###### Atrr类型
##### BOM扩展
###### 选择符API
- document.querySelector//返回匹配的第一个元素
- document.selectorAll//返回匹配的所有元素
- mactchSelector//匹配返回true 否则返回true
###### 元素遍历
- childElementCount
- firstElementChild
- lastElementChild
- previousElementSibling
- nextElementsibling

###### HTML5
- getElementByClassName
- add/remove/contains/toggle 类操作
- focus/hasfocus 焦点有关函数

###### 专有扩展
- 文档模式 doctype

##### DOM2，DOM3
###### DOM变化
###### 样式
###### 遍历
使用NodeItxerator/TreeWalker 进行深度遍历
范围





