## Reducer
    reducer指定应用状态变化如何响应actions并发送到store。
### reducer处理
    reducer不能操作：
    1.修改传入参数
    2、执行有副作用的函数
    3.调用非纯函数。
    function todoApp(state = initalState,action){
        switch(action.type){
            case SET_VISIBILITY_FILITER:
                return Object.assign({},state,{
                    visibilityFilter:action.filiter
                })
            default:
                return state
        }
    }
