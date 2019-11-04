## 第三天学习加总结  
  类：
    ts的类与es6的类大体相同，这里简单介绍一下  
    （1）类的声明以及使用：  
    class Greeter {  
        greeting: string;  
        constructor(message: string) {  
            this.greeting = message;  
        }  
        greet() {  
            return "Hello, " + this.greeting;  
        }
    }  
    
    let greeter = new Greeter("world");  
    这里是new了一个greeter类的实例  
    创建了一个新对象，并初始化  
    （2）类的继承  
    class Animal {
        move(distanceInMeters: number = 0) {
            console.log(`Animal moved ${distanceInMeters}m.`);
        }
    }
    
    class Dog extends Animal {  
        bark() {  
            console.log('Woof! Woof!');  
        }  
    }  
    
    js中类的继承一般是bind函数继承 或者使用原型链继承  
    
    （3）类的私有，公有，保护  
    私有：pravite  不能在声明它的类的外部访问  
    公有：public（默认）  可以自由的访问程序里定义的成员  
    保护：protected成员在派生类中仍然可以访问  
    readonly修饰符  
        只读属性必须在声明时或构造函数里被初始化。  
    参数属性  ：
        参数属性可以方便地让我们在一个地方定义并初始化一个成员  例如  
        class Animal {  
            constructor(private name: string) { }  
            move(distanceInMeters: number) {  
                console.log(`${this.name} moved ${distanceInMeters}m.`);  
            }  
        }  
    （4）存取器：  
    把赋值取值操作用get和set来完成  
    例如：  
    class Employee {  
        private _fullName: string;  
    
        get fullName(): string {  
            return this._fullName;  
        }  
    
        set fullName(newName: string) {  
            if (passcode && passcode == "secret passcode") {  
                this._fullName = newName;  
            }  
            else {  
                console.log("Error: Unauthorized update of employee!");  
            }  
        }  
    }  
    （5）静态属性和抽象：  
    静态属性为static  
    抽象类做为其它派生类的基类使用。 它们一般不会直接被实例化  
    （6）构造函数 
    在js中，new一个实例分为4步：  
    1.创建一个空实例  
    2.bind函数完成绑定  
    3.原型链查找  
    4.如果找到，返回这个变量，没找到，则新建这个实例  
    ts中，的实例如下：  
    class Greeter {  
        greeting: string;  
        constructor(message: string) {  
            this.greeting = message;  
        }  
        greet() {  
            return "Hello, " + this.greeting;  
        }  
    }  
    
    let greeter: Greeter;  
    greeter = new Greeter("world");  
    console.log(greeter.greet());  
    当它被编译成js时，会编译成下面的例子：  
    let Greeter = (function () {  
        function Greeter(message) {  
            this.greeting = message;  
        }  
        Greeter.prototype.greet = function () {  
            return "Hello, " + this.greeting;  
        };  
        return Greeter;  
    })();  
    
    let greeter;  
    greeter = new Greeter("world");  
    console.log(greeter.greet());  
    
## 今日总结
    在css中，尊在一个position：sticky属性，是根据relative和fixed所结合的，  
    用这个属性，一般可以完成table中的固定列，position：sticky中，生效的条件总结：
    （1）父元素为overflow：visble  
    （2）自身需要设定top，bottom，left以及right，优先级为top》bottom，left》right  
    当然  这是原生方法实现table的固定列，在ant design文档中，存在一个<Table>，  
    其中将column中的fixed改为left或right，就可以实现固定列  
    如下例子（该例子参考ant design中文文档）：
    import { Table } from 'antd';  
    
    const columns = [  
      {   
        title: 'Full Name',  
        width: 100,  
        dataIndex: 'name',  
        key: 'name',  
        fixed: 'left',  
      },  
      {  
        title: 'Age',  
        width: 100,  
        dataIndex: 'age',  
        key: 'age',  
        fixed: 'left',  
      },  
      {  
        title: 'Column 1',  
        dataIndex: 'address',   
        key: '1',  
        width: 150,  
      },  
      {  
        title: 'Column 2',  
        dataIndex: 'address',  
        key: '2',  
        width: 150,  
      },  
      {  
        title: 'Column 3',  
        dataIndex: 'address',  
        key: '3',  
        width: 150,  
      },  
      {  
        title: 'Column 4',  
        dataIndex: 'address',  
        key: '4',   
        width: 150,  
      },   
      {  
        title: 'Column 5',  
        dataIndex: 'address',  
        key: '5',  
        width: 150,  
      },  
      {  
        title: 'Column 6',  
        dataIndex: 'address',  
        key: '6',  
        width: 150,  
      },   
      {  
        title: 'Column 7',  
        dataIndex: 'address',  
        key: '7',  
        width: 150,  
      },  
      { title: 'Column 8', dataIndex: 'address', key: '8' },  
      {  
        title: 'Action',  
        key: 'operation',  
        fixed: 'right',  
        width: 100,  
        render: () => <a>action</a>,  
      },  
    ];  
    
    const data = [];  
    for (let i = 0; i < 100; i++) {  
      data.push({  
        key: i,  
        name: `Edrward ${i}`,  
        age: 32,  
        address: `London Park no. ${i}`,  
      });  
    }  
    
    ReactDOM.render(  
      <Table columns={columns} dataSource={data} scroll={{ x: 1500, y: 300 }} />,  
      mountNode,  
    );  
    
