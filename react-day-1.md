## jsx
### 在jsx中嵌入表达式
     const name = "Josh Perpz";
     const element = <h1>Hello,{name}</h1>;
### jsx防止注入攻击
    在react Dom渲染所有输入内容之前，都会进行默认转义，他可以确保在你的应用中，永远都不会注入那些并非自己明确编写的内容。
    const title = response.potentiallyMaliciousInput;
    const element - <h1>{title}</h1>
### 表示对象
    两个方法:
    (1)const element = (
        <h1 className="greeting">
            hello world!
        </h1>
    );
    const element = React.createElement(
        "h1",
        {class : "greeting"},
        "hello world!"
    )
### 将元素渲染为Dom
    <div id="root"></div>
    要将一个react元素渲染到DOM节点中，只需要把他们一起传入ReactDOM.render()
    const element = <h1>hello world!</h1>
    ReactDOM.render(element,document.getElementById('root'));
### 更新已渲染的元素
    一个计时器的例子：
        function tick(){
            <div>
                <h1>hello world!</h1>
                <h2>It is {new Date().toLocaleTimeString()}<./h2>
             </div>
        );
        ReactDOM.render(element,document.getElementById('root'));
        }
        setInterval(tick,1000)
        这个例子中，react只会更新它需要更新的部分。
## 组件&props
### 组件定义
    class wellkq extends React.Component{
        render(){
            return <h1>hello,{this.props.name}</h1>;
        }
    }
### 渲染组件
    当react元素为用户自定义组件时，它会将JSX所接收的属性转换为单个对象传递给组件，这个对象被称为props
    组件无论是使用函数声明还是class声明，都不能修改自身的props
    react虽然灵活，但是存在一个严格的规则：
    所有react组件都必须向纯函数一个保护他们的props不被更改
## 生命周期与state  
    官方例子，写一个时钟：
    class Clock extends React.component{
        constructor(props){
            super(props);
            this.state = {date: new Date()};
        }
        
        componentDidMount(){
            this.timerID = setInterval(
                ()=>this.tick(),1000
            );
        }
        
        componentWillUnmount(){
            clearInterval(this.timerID);
        }
        
        tick(){
            this.setState({
                date:new Date()
            });
        }
        
        render(){
            return (
                <div>
                    <h1>hello world</h1>
                    <h2>It is {this.state.date.toLocaleTimeString()}</h2>
                </div>
            )
        }
        
    }
