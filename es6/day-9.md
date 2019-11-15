## es6模块复习
### let和const
    const在声明后不允许再修改值
    let和const的命令只在代码块中有效
    例如：
    {
        var a=10;
        var b=1;
    }
    a // a is not defined
    b // 1
#### let不存在变量提升，一道经典问题:
    console.lof(foo);
    var foo=2;
    这时会输出undefined

    console.log(bar);// referenceError
    let bar = 2;
#### 暂时性死区
    var tmp = 123;
    if (true){
        tmp = "abc"; // ReferenceError
        let tmp;
    }
#### 不允许重复声明
    function func(){
        let a = 10;
        var a = 1;
    }// 这时会报错
#### 存在块级作用域
    {
        let tmp = ...;
    }
## 解构函数
    let [a,b,c]=[1,2,3];
    let [foo,[[baz],baz]]=[1,[[2],3];
    let [ , ,third]=["foo",'bar','baz']
    let [x,,y]=[1,2,3]
    let [head,...tail]=[1,2,3,4]
    let {foo,bar} = {foo:'aaa',bar'bbb'}
    let [a,b,c,d,e]="hello"
    函数参数也可解构
## 字符串的扩展
    es6开始已经支持\uxxxx的写法
#### 为字符串增加了遍历器接口
    for(let i of "foo"){
    }
#### "\u4e2d" = u+4e2d
## 正则的扩展
#### RegExp存在两种参数，第一种的第一个参数是字符串，第二个参数就表示正则式的修饰符
#### 第二种是，第一个参数是正则表达式，这是会返回一个正则式的拷贝，不允许出现第二个参数
## 函数的扩展
### 箭头函数
    箭头函数注意的几点：
    （1）函数体内的this指针，是定义时所在的对象，并不是使用时所在的对象
    （2）不可以当作构造函数，不可以使用new
    （3）不可以使用arguments对象，可以用rest参数代替
    （4）不可以使用yield命令
## 数组的扩展
### 扩展运算符
    let a1=[1,2];
    let a2=[..a];
### Array.from()
    将两类对象转为数组的形式
### Array.of()
    将一组值，转换为数组
### flat()
    将嵌套的数组拉平
### 会跳过空位的函数
    forEach().filter(),reduce(),every(),some()
    map()会跳过空位，但是会保留这个值
    join()和tostring()会把空位设置为undefined，undefined和null会处理成空字符串
## 对象的扩展
    super，会指向当前对象的原型对象
