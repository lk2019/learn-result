## 事件处理
### react元素的事件处理和DOM元素的很相似，但是有一点语法上的不同
    react命名采用驼峰式
    JSX语法需要传入一个函数作为事件处理函数
    在react中不能通过返回false来阻止默认行为，而是需要显示的使用prevenDefault。
    react一般不需要使用addEventListener为已创建的DOM元素添加监听器，只需要在元素初始渲染的时候添加监听器就行。
    在JSX回调函数中的this，在js中，class默认不会绑定this，所以一般需要绑定this。
### 向事件处理程序传递参数
    两种方法:
    (1) onClick={(e) => this.deleteRow(id,e)}
    (2) onclick={this.deleteRow.bind(this.id)}
## 条件渲染
### react中的条件渲染和js中的一样，使用js运算法if或者条件运算符去创建元素来表现当前的状态，然后让react根据它们来更新UI
    例如：
        function Greeting(props){
            const isLoggedIn = props.isLoggedIn;
            if(isLoggedIn){
                return <UserGreeting/>
            }
            return <GuetGreeting/>
        }
        
## 元素变量
    react可以使用变量来存储元素。它可以帮助你有条件地渲染组件的一部分，而其他的渲染部分并不会因此而改变
### 与运算符&&
    通过与运算符包裹代码，可以在JSX中嵌入任何表达式，它可以很方便的进行元素渲染。
### 三目运算符
    三木运算符也是一种内联条件渲染的方法
### 阻止组件渲染
    在有时候，我们希望能隐藏组件，即使它已经被渲染，如果要完成这个操作，我们可以让render方法直接返回null
## 列表&key
    react中，将数组转化为元素列表的过程与map相似
### 渲染多个组件
    可以使用map，例如：
        const listItems = numbers.map((number) =>{
            <li>{number}</li>
        })
### 基础列表组件
    我们可以把上述例子变成一个基础组件来完成渲染，但是这时就会出现一个key值
## key
    key值是帮助react来识别哪些元素改变了，所以一般会给数组中的每一个元素赋予一个确定的标识，key最好使用独一无二的值来使用，
    需要注意的是，key值只需要在兄弟节点间唯一
## 表单
### 受控组件
    在react中，可变状态通常保存在组件的state中，并且只能通过使用setstate来更新
    我们可以把两者结合起来，使react的state成为“唯一数据源”。渲染表单的react组件
    还控制着用户输入过程中表单发生的操作。被react以这种方式控制取值。
    
### textarea标签
    在HTML中，<textarea>元素通过其子元素定义其文本
### select标签
    html中，select创建下拉列表标签。
## 状态提升
    如果我们希望两个组件的输入框的数据可以同步，这时候就需要状态提升，也就是将多个组件中需要共享的state上移动到共同父组件中
        
     
