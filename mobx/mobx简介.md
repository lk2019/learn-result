## mobx简单介绍
### 1.observable state 
    一般称之为可观察状态，支持js数据类型，可以让你的类属性可见。
### 2.computed values 计算值
    当相关的数据变化时，计算值会发生变化自动更新，
### 3.Reactions 反应
    一般是产生副作用的部分，例如打印到控制台，网络请求或者是递增地更新React组件树来修补DOM等。
### 与react组件配合
    一般可以把无状态函数变成响应式组件。
### 自定义reactions => autonun reaction when
### actions mobx处理事件
    可以用类似 Flux 的方式完成
    或者使用 RxJS 来处理事件
    或者用最直观、最简单的方式来处理事件 onClick={() => todo.finished = !todo.finished}
### state 状态
    一般是指数据。
### Derivations 衍生
    任何来源state并且不会再相互有影响的东西，可以以界面、衍生数据、后端多种形式存在。
    Computed values(计算值) - 它们是永远可以使用纯函数(pure function)从当前可观察状态中衍生出的值。
    Reactions(反应) - Reactions 是当状态改变时需要自动发生的副作用。需要有一个桥梁来连接命令式编程(imperative programming)和响应式编程(reactive programming)。或者说得更明确一些，它们最终都需要实现I / O 操作。
### Actions
    用来改变state的代码。用户事件、后端数据推送、预定事件等。
### 原则
    只支持单向数据流，触发action来改变state。
    
