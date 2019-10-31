##第一天总结##
    1.了解ts所学知识，例如：在reactjs中，一般存在一个类型检测接口，例如proptypes，而在ts中，ts的每一个类型声明都存在有一个类型检测。
    例如：
    function greeter（person：string）{
            return “Hello，” + person；
    }
    2.ts中存在接口，这个接口与我们在java中所学的接口类似，一般接口只完成数据类型的声明。
    3.类与接口可以相互协作，类完成数据类型定义，类完成实现功能。
    4.数据类型（与js作对比）：
    ts：
    （1）布尔： let isDone：boolean=false；
    （2）数字
    （3）字符串：这里要说到的是
    不光可以使用普通字符串，而且还可以使用模板字符串，比如说：
    let name：string=‘Gene’；
    let age：number=37；
    let sentence：string=‘hello，my name is ${name}’
    这种模板字符串可以通过${}来使用
    （4）数组
    普通数组：let list：number[] =[1,2,3];
    数组泛型: let list:Array<number> = [1,2,3]
    (5)元组Tuple
    元组相当于是可以存不同数据类型的数组，例如可以let x:[string,number]
    但是数据类型需要一一对应   如果x=[10,'luo']，就会报错
    （6）枚举
    enum，跟c++，java所学的enum类型似乎并没有区别，都是从下标0开始记位，当然，存在记位的就向后顺延。
    （7）任意类型
    let arr：any
    就可以跟js中的var arr一样
    （8）空值
    void类型，表示空值，当没有返回值时，会显示空值。
    （9）null和undefined
    默认情况下null和undefined是所有类型的子类型。 就是说你可以把null和undefined赋值给number类型的变量。
    （10）NEVER
    表示永远都不存在的值。never类型是任何类型的子类型，也可以赋值给任何类型；然而，没有类型是never的子类型或可以赋值给never类型（除了never本身之外）。
    即使any也不可以赋值给never。
    （11）类型断言
    类型断言是告诉编译器你在知道数据实体的时候强制告诉编译器你没有错误，跟强制转换类型应该差不多。
##总结今日经验##
    （1）flex布局中，一般三栏布局为
    .parent{
        width：200px
        display:flex;
    }
    .left{
         width:...px;
    }
    .mid{
        flex:1;
    }
    .right{
        width:...px
    }
        但是如果.mid中的数据远远超过父元素的宽度时怎么办，我当时当然第一时间想到的就是BFC解决，似乎bfc并不能完成（可能是我太菜了，不会）
    总结结果，最后用到
    .mid{
        flex:!;
        width：0；
        overflow:hidden;
    }
    在mid的子元素中添加数据
    （2）浮动布局中 left mid right都设置浮动，且设置定长  触发BFC，不会撑开宽度，但是这种写法似乎很多人都不提倡，可用性太低。
    （3）树形展开，还需学习。
    （4）持续学习ant design和ts中，并继续了解react
