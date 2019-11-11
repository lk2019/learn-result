## Symbols介绍
### 从es6开始，symbol就成为了一个新的原生类型
#### symbol是通过symbol构造函数创建的，他是不可改变且唯一的。
    let sym2=Symbol("key");
    let sym3= Symbol("key");
    sym2===sym3;
    最后返回值时false
    symbol也可以被用作对象属性的键
    let sym = Symbol();
    let obj = {
        [sym]:"value"
    };
    
    console.log(obj[sym]);
    symbol也可以与计算出的属性名声明相结合来声明对象的属性和类成员
## Iterators和Generators
### 可迭代行
#### 当一个对象实现了Symbol.iterator函数负责返回供迭代的值
    for of语句
    let someArray = [1,"string",false];
    for(let entry of someArray){
        console.log(entry);
    }
    for of vs for in语句
    for of 和 for in都可以迭代一个列表，但是用来迭代的值不同，for in 迭代的是对象的键的列表，for of是迭代的键对应的值
    let list = [4,5,6]
    for(let i in list){
        console.log(i); (0 , 1 , 2)
    }
    for(let i of list){
        console.log(i);  (4 , 5 , 6)
    }
    
## 模块
### 导出
#### 导出声明
    export interface stringValidator{
        isAcceptable(s:string):boolean;
    }
#### 导出语句
    class zipcodeValidator implements StringValidator {
        isAcceptable(s:string){
            return s.length === 5 && numberRegexp.test(s);
        }
    }
    
    export {zipcodeValidator
    }
#### 重新导出
    export * from ".//"
### 导入
    import from ".//"
    
## 命名空间
    随着许多验证器的加入，就需要一种手段来组织代码，以便于在记录他们类型的同时还不用担心与其他对象产生命名冲突，一般会把验证器包裹
    到一个命名空间内
    namespace
## 声明合并
### 合并接口
    interface box{
        height:number;
        width:number;
    }
    interface Box{
        scale:number;
    }
    
    let box:Box = {height:5,width:6,scale:10}
### 合并命名空间
    namespace Animals{
        export class lkq{}
    }
    namespace Animals {
        export interface Legged { numberOfLegs:number;}
        export class Dog()
    }
