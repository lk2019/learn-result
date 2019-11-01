##  第二天学习
    ts变量声明：  
    ts存在有跟es6相同的变量声明  let  var  const以及解构声明、函数声明和扩展运算符声明（对象可枚举类型也可以通过扩展运算符声明）  
    ts接口：  
        (1)在声明接口完成后，函数调用时，类型检查器会检查接口中是否存在当前属性，仅检测当前需要检查的属性(接口中不仅限一个属性)  
        (2)可选属性，接口中可选属性就是在属性名字后加？  
        例如：  
        interface lkq{  
            clolr?:string;  
            index?:number;
            }  
         (3)只读属性  
         例如:  
         interface lkqnb{  
           readonly x:number;  
           readonly y:number;  
           }   
           
          与const的差别：  
          作为变量时用const  作为属性时用readonly  
          （4）函数类型：  
          接口也可以描述函数类型   
          （5）可索引类型  
          interface StringArray{  
            [index:number]:string;    
          }  
           
           let myArray: StringArray;  
           myArray = ["bob","lkq"];  
           
           let mystr:string = myArray[0];  
           ts同时支持字符串和数字索引  类似obj[]=target  
           
          
