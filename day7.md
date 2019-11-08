## ts高级类型
### 交叉类型
    交叉类型就是可以将多个类型合并为一个类型，这里copy中文手册的例子：
    function extend<T,U>(first:T,second:U):T&U{
        let result = <T&U>{};
        for(let id in first){
            (<any>result)[id]=(<any>first)[id];
        }
        for (let id in second){
            if(!result.hasOwnProperty(id)){
                (<any>result)[id]=(<any>second)[id];
            }
        }
        return result;
    }
    
    class Person{
        constructor(public name : string){}
    }
    interface Loggable{
        log():void;
    }
    class ConsoleLogger implements Loggable{
        log(){}
    }
    var jim = extend(new Person("jim"),new ConsoleLogger());
    var n = jim.name;
    jim.log()
### 联合类型
    联合类型与交叉类型很有关联，但是使用不同。例如，有时我们需要一个函数传入number或者string，
    这是可以使用联合函数，例如：
    function pad（calue：string，padding：number|string）{...}
    这样的联合类型让我们代替了any作为参数检测，但是，如果一个值是联合属性，那么我们只能访问到此类型中所有类型的共有属性。
### 类型保护与区分类型
    当然，在上述联合类型中，我如果想确定是否是联合类型中的一个类型时怎么办？
    这时候，可以使用类型断言：
    let pet = getSmallPet();
    if((<fish>pet).swim){
        (<Fish>pet).swim();
    }
    else {
        (<Bird>pet).fly();
    }
#### 用户自定义的保护类型
    上述需要多次使用类型断言，但是自定义保护类型，可以在观察过一次后，就可以知道每个分支的类型，像这样：
    function isFish(pet : Fish|Bird):pet is Fish{
        return (<Fish>pet).swim !==undefined;
    }
    所以每当使用一些调用isFish时，ts会将变量缩减为那个具体的类型，只要类型兼容。
#### 可以为Null的类型
    ts和js一样，都存在null和undefined两种特殊的类型，null和undefined是所有其他类型的一个有效值，这也意味着我们无法阻止
    其他类型的值被赋为null，在ts中，--strictNullCheck可以解决这类错误：
    当我们声明一个变量时，它不会自动地包含null或者undefined。可以使用联合类型明确包含它们：
    let s = "foo"
    s=null;
    let sn:string|null="bar";
    sn=null;
    sn=undefined
#### 可选参数和可选属性
    使用--systrickNullChecks,可选参数会自动地加上|undefined：
    function f(x:number,y?:number){
        return x+(y||0);
    }
    f(1,2);
    f(1);
    f(1,undefined);
    f(1,null);
    当然，可选属性也会有同样的处理
#### 类型保护和类型断言
    可以为null的类型时通过联合类型实现，那么是你需要使用类型保护去除null。这与js里写的代码一致:
    function f(s:string|null):string{
        if(sn==null){
            return "default";
        }
        else{
            return sn;
        }
    }
#### 类型别名
    就是给一个类型起一个新名字。它有时和接口很香，但是可以作用于原始值，联合类型，元祖以及其他任何你需要手写的类型。例如：
    type Name = string;
    type NameResolver = Name | NameResolver;
    function getName(n:NameOrResolver):Name{
        if(type n === "string'){
            return n;
        }
        else {
            return n();
        }
    }
    
    类型别名也可以是泛型:
    type Comtainer<T>={value : T}
    
    类型别名与接口的区别:
    (1)接口创建了一个新名字，类型别名并不创建新名字
    （2）类型别名不能被extens和implements
    （3）如果无法通过接口来描述一个类型并且需要使用联合类型和元组类型时，这通常会使用类型别名。
#### 字符串字面量类型
    字符串字面量类型允许你指定字符串必须的固定值。实际运用中，字符串字面量类型可以和联合类型，类型保护和类型别名配合。
    例如：type lkq = "cai"|"niu"|"yiban"
    数字字面量类型和枚举成员类型也拥有着差不多的意思
#### 可辨识联合
    可以合并单例类型，联合类型，类型保护和类型别名来创建一个叫做可辨识联合的高级模式，它也称标签联合或者代数数据类型。可辨识联合有
    三个要素：
        （1）具有普通的单例类型属性-可辨识特征
        （2）一个类型别名包含了哪些类型的联合
        （3）此属性上的类型保护
    完整性检查：
    （1）--strictNullChecks
    (2)never
#### 多态的this
    多态的this类型表示的是某个包含类或接口的子类型。这被称为F-bounded多态性。它能很容易的表现连贯接口间的继承
