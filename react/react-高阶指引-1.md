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
大多数React应用都会使用webpack这类的构件工具来打包文件。打包是将文件引入并合并到一个单独文件的过程，最终形成一个bundle。

