## Action
    actiion的作用是把数据从应用传到store的有效载荷，也是store数据的唯一来源，一般我们会通过store.dispatch()来传递action，
### Action创建函数
    function addTODO(text){
        return {
            type:ADD_TODO,
            text
        }
    }
    派发action:dispatch(addTODO(text))  
    或:const boundAddtodo = text => dispatch(addTodo(text))
        boundAddtodo(text);
        
    
