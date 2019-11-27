## action
任何改变状态的代码都称为行为.
+ action可以接受name和fn两个参数，name是String，主要描述action的作用，fn是Function，是这个action的具体逻辑。
+ action的作用更多的是用来注释当前的操作
+ action只能影响正在运行的函数，而无法影响当前函数调用的异步操作
+ 如果你使用async function来处理业务，那么我们可以使用runInAction这个API来解决之前的问题。

