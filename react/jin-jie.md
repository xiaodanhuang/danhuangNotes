阅读摘要：

* ##### context
* ##### error boundaries

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



