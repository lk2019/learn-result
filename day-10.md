## Symbol 
    symbol从es6开始作为一个原始数据类型来定义的，Symbol值是通过symbol函数生成。
    symbol值得机制是保证每个属性的名字都是独一无二的，从根本上防止属性名的冲突。
## Set和Map
    set本身是一个构造函数，用来说生成Set的数据类型，使用add方法来加入成员，Set结构表明
    不会存在重复的值。
    Set的方法和属性：
        1.Set.prototype.constructor：构造函数，默认set函数
        2.Set.prototype.size:返回Set成员函数总数
        方法:
        add(value) 增加某个值
        delete(value)删除某个值
        has(value)是否存在这个值
        clear（）删除所有值
    map是实现了字符串-值得对于，是一种更加完善的hash结构实现
## proxy
    proxy用于修改某些操作的默认行为，在目标对象之前设一层拦截，外界对该对象的访问，都必须先经过
    这层拦截，可以称作代理器。
        var obj = new proxy({},{
            get : function (target,key,receiver){
                console.log("getting ${key}!")
                return Reflect.get(target,key,value,receiver);
            },
            set : function(target,key,value,receiver){
                console.log("setting ${key}!");
                return Reflect.set(target,key,value,receiver);
            }
        );
## promise
    promise是异步编程的一种方案，比回调函数和事件更加强大。
        promise存在两个特点：
            对象的状态不受外界影响。
            状态一旦改变，就不会再变。
        promise要掌握的两个方法
            promise.all
            promise.race
## async
    async是generator的语法糖，他同样是解决异步问题的，差别在于generator需要手动.next而async不需要
    async与await同用
