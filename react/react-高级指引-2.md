##  refs
refs创建过程:

1.我们通过调用 React.createRef 创建了一个 React ref 并将其赋值给 ref 变量。  
2.我们通过指定 ref 为 JSX 属性，将其向下传递给 <FancyButton ref={ref}>。  
3.React 传递 ref 给 forwardRef 内函数 (props, ref) => ...，作为其第二个参数。  
4.我们向下转发该 ref 参数到 <button ref={ref}>，将其指定为 JSX 属性。  
5.当 ref 挂载完成，ref.current 将指向 <button> DOM 节点  

## Fragments
用法:
class Columns extends React.Component {
  render() {
    return (
      <React.Fragment>
        <td>Hello</td>
        <td>World</td>
      </React.Fragment>
    );
  }
}
代表空组件

## flow
Flow 是一个针对 JavaScript 代码的静态类型检测器。Flow 由 Facebook 开发，经常与 React 一起使用。Flow 通过特殊的类型语法为变量，函数，以及 React 组件提供注解，帮助你尽早地发现错误。你可以阅读 introduction to Flow 来了解它的基础知识。

完成以下步骤，便可开始使用 Flow：

1.将 Flow 添加到你的项目依赖中。
2.确保编译后的代码中去除了 Flow 语法。
3.添加类型注解并且运行 Flow 来检查它们

### react生命周期
####挂载过程  

1.constructor()  
    初始化state和方法绑定，不进行可以不需要  
2.static getDerivedStateFromProps()  
     getDerivedStateFromProps 会在调用 render 方法之前调用，并且在初始挂载及后续更新时都会被调用。它应返回一个对象来更新 state，如果返回 null 则不更新任何内容。
     不推荐使用，会导致代码冗余，并使组件难以维护.
3.render()
      render() 方法是 class 组件中唯一必须实现的方法。render() 函数应该为纯函数，这意味着在不修改组件 state 的情况下，每次调用时都返回相同的结果，并且它不会直接与浏览器交互。
      
4.compoentDidMount()  
       componentDidMount() 会在组件挂载后（插入 DOM 树中）立即调用。依赖于 DOM 节点的初始化应该放在这里。如需通过网络请求获取数据，一般在这里请求。

###更新过程  
1.static getDerivedStateFromProps()
        和装载过程相同
2.shouldComponentUpdate()  
        根据 shouldComponentUpdate() 的返回值，判断 React 组件的输出是否受当前 state 或 props 更改的影响。默认行为是 state 每次发生变化组件都会重新渲染。
3.render()  
4.getSnapshotBeforeUpdate()  
        getSnapshotBeforeUpdate() 在最近一次渲染输出（提交到 DOM 节点）之前调用。它使得组件能在发生更改之前从 DOM 中捕获一些信息（例如，滚动位置）。此生命周期的任何返回值将作为参数传递给 componentDidUpdate()。
5.componentDidUpdate()  
        当组件更新后，可以在此处对 DOM 进行操作。如果你对更新前后的 props 进行了比较，也可以选择在此处进行网络请求。
### 卸载过程
1.componentWillUnmount()  
        componentWillUnmount() 会在组件卸载及销毁之前直接调用。在此方法中执行必要的清理操作，例如，清除 timer，取消网络请求或清除在 componentDidMount() 中创建的订阅等。
