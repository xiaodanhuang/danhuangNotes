阅读摘要：

* ##### context
* ##### error boundaries
* ##### Refs转发
* ##### Fragments
* ##### 高阶组件

#### context

跨层级的数据传递（地区偏好/UI主题）

        const ThemeContext = React.createContext({
            theme:'light',
            toggleTheme:()=>{}
        })
        function Button(props) {
            return (
                <button className={`btn ${'btn-' + props.theme}`}>button</button>
            )
        }

        function ThemeButton() {
            return (
                <ThemeContext.Consumer>
                    {
                        ({theme,toggleTheme}) =>
                        <div>
                            <Button theme={theme}></Button>
                            <button onClick={toggleTheme}>toggle theme</button>
                        </div>
                    }
                </ThemeContext.Consumer>
            )
        }
        class Input extends React.Component{
            constructor (){
                super();
                Input.contextType=ThemeContext//this.context 来消费最近 Context 上的那个值
            }
            render(){
                return (
                    <input className={['input','input-'+this.context].join(' ')}/>
                )
            }
        }

        class App extends React.Component {
            constructor(props) {
                super()
                this.state = {
                    theme: 'dark'
                }
            }

            toggleTheme = () => {
                console.log(1)
                this.setState(preState => (
                    {
                        theme: preState.theme === 'light' ? 'dark' : 'light'
                    }
                ))
            }
            render() {
                return (
                    //Provider 的 value 值发生变化时，它内部的所有消费组件都会重新渲染
                    <div>
                        <ThemeContext.Provider value={{theme:this.state.theme,toggleTheme:this.toggleTheme}}>
                            <ThemeButton/>
                        </ThemeContext.Provider>
                        <Input/>
                    </div>
                )
            }
        }
        ReactDOM.render(<App/>, document.getElementById('root'))

#### error boundaries

可以捕获并打印发生在其子组件树任何位置的 JavaScript 错误，并且，它会渲染出备用 UI

错误边界无法捕获以下场景中产生的错误：事件处理，异步，服务端渲染，自身抛出的错误。

```
     class ErrorBoundary extends React.Component{
        constructor(){
            super();
            this.state={
                has_error:false
            }
        }
        static getDerivedStateFromError(error) {
            // 更新 state 使下一次渲染能够显示降级后的 UI
            return { has_error: true };
        }
        render(){
           if(this.state.has_error){
               return (
                   <div>报错了，兄弟</div>
               )
           }
           return this.props.children
        }
     }
    class Error extends React.Component{
        constructor(){
            super()
            this.state={
                user:null
            }
        }
        render(){
            return(
                <div>{this.state.user.name}</div>
            )
        }
    }
ReactDOM.render(<ErrorBoundary><Error/></ErrorBoundary>, document.getElementById('root'))
```

#### Refs转发

我们用ref绑定元素，refs转发又是啥子意思哦？ 将ref转发给其子组件

```
    const Input = React.forwardRef((props, ref) => (
        <input ref={ref}/>
    ));

    class App extends React.Component {
        constructor() {
            super()
            this.myRef = React.createRef();
        }

        focus = () => {
            console.log(this.myRef.current.focus())

        }

        render() {
            return (
                <div>
                    <Input ref={this.myRef}/>
                    <button onClick={this.focus}>聚焦</button>
                </div>
            )
        }
    }
```

#### Fragments

React 中的一个常见模式是一个组件返回多个元素。Fragments 允许你将子列表分组，而无需向 DOM 添加额外节点。

```
    class App extends React.Component {
        constructor() {
            super()
            this.state={
                list:['苹果','橙子']
            }
        }

        render() {
            return (
                <React.Fragment>
                    {
                        this.state.list.map((item,index)=><li key={index}>{item}</li>)
                    }
                </React.Fragment>
            )
        }
    }
```

#### 高阶组件

高阶组件（HOC）是 React 中用于复用组件逻辑的一种高级技巧。HOC 自身不是 React API 的一部分，它是一种基于 React 的组合特性而形成的设计模式。 高阶组件是一个函数，参数是一个组件，返回一个新的组件。它的作用是能实现代码复用和逻辑抽象、对state和props进行抽象和操作、对组件进行细化（如添加生命周期）、实现渲染劫持等。

**组件是将 props 转换为 UI，而高阶组件是将组件转换为另一个组件。**

关于高阶组件能解决的问题可以简单概括成以下三个方面：

* 抽取重复代码，实现组件复用，常见场景：页面复用。
* 条件渲染，控制组件的渲染逻辑（渲染劫持），常见场景：权限控制。
* 捕获/劫持被处理组件的生命周期，常见场景：组件渲染性能追踪、日志打点。

通常情况下，实现高阶组件的方式有以下两种:

* 属性代理\(Props Proxy\)
  * 返回一个无状态（stateless）的函数组件
  * 返回一个 class 组件
* 反向继承\(Inheritance Inversion\)

> 属性代理

1. 操作props&通过 props 实现条件渲染

```
// 返回一个无状态的函数组件
function HOC(WrappedComponent) {
  const newProps = { type: 'HOC' };
  return props => <WrappedComponent {...props} {...newProps}/>;
}

// 返回一个有状态的 class 组件
function HOC(WrappedComponent) {
  return class extends React.Component {
    render() {
      const newProps = { type: 'HOC' };
      return this.props.is_show?<WrappedComponent {...this.props} {...newProps}/>:<div>不展示</div/>;
    }
  };
}
```

通过属性代理方式实现的高阶组件包装后的组件可以拦截到父组件传递过来的props

    2. 抽象state

需要注意 ⚠️的是，通过属性代理方式实现的高阶组件无法直接操作原组件的state，但是可以通过props和回调函数对state

进行抽象。️

```
function HocChildren(props){
    return (<div>{props.type}:{props.name} <input onChange={props.onChange}/></div>)
}
function  Hoc (HocChildren){
    return class HocContainer extends React.Component{
        constructor(props){
            super();
        }
        onChange=(e)=>{
            console.log(e.target.value)
        }
        render(){
            const new_props={type:'hoc',onChange:this.onChange}
            return  <HocChildren{...this.props}  {...new_props}/>
}
```

   3.获取 refs 引用，获取原组件的 static 方法，用其他元素包裹传入的组件

```
class User extends React.Component{
    constructor(){
        super();
    }
    static sayHello () {
        console.error('hello world'); // tslint:disable-line
    }
    render(){
        return (
            <div>
                <div>{this.props.name}</div>
                <div>{this.props.age}</div>
                <input
                    ref={input => {
                        if (this.props.inputRef) {
                            this.props.inputRef(input); // 调用父组件传入的ref回调函数
                        }
                    }}
                />
            </div>
        )
    }
}
function  Hoc (HocChildren){
    let inputElement;
    return class HocContainer extends React.Component{
        constructor(){
            super();
        }
        focus=()=>{
           inputElement.focus()
        }
        sayHello=()=>{
           HocChildren.sayHello()
        }
        render(){
            return  (
                <div>
                    <HocChildren
                        {...this.props}
                        name="芒果" age={2}
                        inputRef={(el) => { inputElement = el; }}
                    />
                    <button onClick={this.focus}>子组件聚焦</button>
                    <button onClick={this.sayHello}>子组件的静态方法</button>
                </div>
            )
        }
    }
}
```



