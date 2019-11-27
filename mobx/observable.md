## observable
*********
参数可以是JS原始类型、引用、纯对象、类实例、数组和map。 
**** 
+ 当value是map时，返回observable map
+ 当value是数组，返回observable Array
+ 当value是一个无原型对象，返回observable Object
+ 当value是一个有原型的对象，返回Boxed Observable。
***
+ 当要创建一个动态属性对象时，使用map
+ 使用@overvable时，需要启用装饰器语法
+ 创建的可观察的数据结构是有传染性的。
