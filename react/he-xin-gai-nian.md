阅读摘要：

* ##### React是什么？
* ##### JXS
* ##### 函数组件&类组件
* ##### state&props
* ##### 事件处理
* ##### 条件渲染
* ##### 列表 和key
* ##### 表单
* ##### 组合&继承
* ##### 生命周期

#### React是什么？

是一个用于构建用户界面的 JavaScript 库

```js
ReactDOM.render("hello world",document.getElementById("root"));
```

#### JSX 【 JavaScript 的语法扩展】

```js
const element = 
  <div className="content">
        <h1> Hello, world! </h1>
        <h1> hello jxs </h1>
  </div>
;
```

```
//经过babel的转换形成对象 通过 transform-react-jsx 调用react.createElement
var element = React.createElement("div", {
  className: "content"
}, React.createElement("h1", null, " Hello, world! "), React.createElement("h1", null, " hello jxs "));
```

#### 函数组件&类组件

```
//函数组件 数据通过props传递 本质是函数
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
//类组件 数据通过props传递 内部有state 生命周期 本质是es6的类
class Welcome extends React.Component  {
        constructor(props) {
            super(props)
        }
        render () {
            return (
                <div>{this.props.title} </div>
            )
        }
}
```

#### state&props

state：组件内部数据的维护使用state 可变 使用this.setState

props：父组件传递给子组件的数据**  在子组件中只读**

```
class Welcome extends React.Component  {
        constructor(props) {
            super(props)
            this.state={
                count:1
            }
        }
        addOne=()=>{
            this.setState(preState=>({count:preState.count+1}))
        }
        render () {
            return (
                <div>
                    {this.props.title}
                    {this.state.count}
                    <button onClick={this.addOne}>+1</button>
                </div>
            )
        }
    }
```

#### 事件处理

React 事件的命名采用小驼峰式，而不是纯小写。** class的方法默认不会默认绑定this 所以要处理一下**

```
<button onClick={this.addOne.bind(this,1,1}>+1</button>
<button onClick={(e)=>{this.addOne(1,1,e)}}>+1</button>
```

#### 条件渲染

if/三目运算符

```
function Time(props){
    if(props.status){
        return <div>{props.title}</div>
    }else{
        return <div>404</div>
    }
}
class Welcome extends React.Component  {
        constructor(props) {
            super(props)
            this.state={
                count:1
            }
        }
        addOne=()=>{
            this.setState(preState=>({count:preState.count+1}))
        }
        render () {
            return (
                <div>
                    {this.props.title}
                    {this.state.count}
                    {this.props.status?(<button onClick={this.addOne}>+1</button>):null}
                </div>
            )
        }
    }
```

#### 列表和key

React使用map进行遍历，key有利于React的diff ，之后对写React源码的时候再补充 为啥子要加key

```
 class Welcome extends React.Component {
        constructor(props) {
            super(props)
            this.state = {
                list: [
                    {id: 1, name: '香蕉'},
                    {id: 2, name: '葡萄'},
                    {id: 3, name: '草莓'},
                ]
            }
        }
        render() {
            return (
                <div>
                    {
                        this.state.list.map(item => (
                            <div key={item.id}>{item.name}</div>
                        ))
                    }
                </div>
            )
        }
    }
```

#### 表单

受控组件：表单数据是由 React 组件来管理

非受控组件：表单数据将交由 DOM 节点来处理

#### 组合&继承

使用一个特殊的children prop 来将他们的子组件传递到渲染结果中

组件可以直接引入（import）而无需通过 extend 继承它们

```
class Welcome extends React.Component {
        render() {
            return (
                <div>
                    { this.props.children}
                </div>
            )
        }
    }
```

#### 生命周期

![](/assets/生命周期.png)

v16.x

![](/assets/生命周期v6.png)



