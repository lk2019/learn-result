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

