## store
    redux只存在一个store
    一般增加store  let store = createStore(todoApp)
### 数据流
    redux是严格的单项数据流，一般生命周期存在以下四个步骤：
        1调用store.dispatch(action)
        2.redux store传入reducer函数
        3.根reducer把多个reducer合并成单一state树
        4.store保存reducer返回完整state树
## 完成todolist
   [入门的todolist ](https://github.com/lk2019/redux-todolist)  
