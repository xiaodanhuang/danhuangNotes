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

高阶组件（HOC）是 React 中用于复用组件逻辑的一种高级技巧。HOC 自身不是 React API 的一部分，它是一种基于 React 的组合特性而形成的设计模式。 高阶组件是一个函数，参数是一个组件，返回一个新的组件。

**组件是将 props 转换为 UI，而高阶组件是将组件转换为另一个组件。**



