## 无障碍辅助功能
  网络无障碍辅助功能是一种可以帮助所有人获得服务的设计和创造。无障碍辅助功能是使得辅助技术正确解读网页的必要功能。  
  ### WAI-ARIA
   jsx支持所有aria-*HTML属性。虽然大多数react的DOM变量和属性命名都使用驼峰式命名，单aria-*应该向在HTML中一样使用连带字符的命名法。  
    <input  
        type="text"
        aria-label={labelText}
        aria-required="true"
        onChange={onchangeHandler}
        value={inputValue}
        name="name"
    />
  ### 语义化的HTML
   语义化的HTML是无障碍辅助功能网络应用的基础。利用多种HTML元素来强化网站中的信息可以使我们获得无障碍辅助功能。  
   有时，语义化HTML会被破坏。比如当在JSX中使用<div>元素来实现React代码功能的时候，又或是在使用列表和HTML<table>时。在这种情况下，我们应该使用react Fragments来组合组件。
  ### 无障碍表单
  所以体验的HTML表单控制，例如<input>和<textarea>，都需要被标注来实现无障碍辅助功能。
## 代码分割
### 打包
  大多数React应用都会使用webpack这类的构件工具来打包文件。  
  打包是将文件引入并合并到一个单独文件的过程，最终形成一个bundle。  

### react.lazy
react.lazy和Suspense不支持服务器渲染，react.lazy函数能让你像渲染常规组件一样处理动态引入。例如：
    const OtherComponent = React.lazy(() => import("./otherComponent.))
## Context
在一个典型的 React 应用中，数据是通过 props 属性自上而下（由父及子）进行传递的，但这种做法对于某些类型的属性而言是极其繁琐的（例如：地区偏好，UI 主题），这些属性是应用程序中许多组件都需要的。Context 提供了一种在组件之间共享此类值的方式，而不必显式地通过组件树的逐层传递 props。
