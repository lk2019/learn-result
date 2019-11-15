## 第四天学习
   ### 函数
     (1)有名函数和匿名函数：
     与js所拥有的函数类型相同：
     function add(x, y) {
         return x + y;
     }

     let myAdd = function(x, y) { return x + y; };
     （2）函数类型：
     ts的函数类型，就是在声明时定义返回类型
     这与变量声明时相同  例如：
     function add（x:number,y:number）：number
     这种表示函数类型返回值一定时number类型
     函数类型包含参数类型和返回值类型
     在ts中，如果想写完整函数，需要这样写：
     let myAdd: (x:number, y:number) => number =
     function(x: number, y: number): number { return x + y; };

     （3）函数参数
     函数参数包含可选参数以及默认参数
     在函数参数：后加？ 就是可选参数
     在函数参数后=一个默认值就是默认参数
     默认参数可以定义任意位置，这与c++不同，但是在构建函数时，默认参数需要填写准确值或者undefined
     （4）剩余函数
     如果想操作多个参数时，js中，存在一个arguements，而在ts中，可以把所有参数集中到一起，用...来完成
     例如：
     function buildName(firstName: string, ...restOfName: string[]) {
       return firstName + " " + restOfName.join(" ");
     }

     let employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
     （5）this
     js中，搞清楚this是至关重要的一部分，修改this指针的方法，大概是，
     （1）new一个函数实例时，this指针指向实例
     （2）call，apply，bind时，this指针发生改变
     （3）如果一个函数中有this，但是它没有被上一级的对象所调用，那么this指向的就是window
     （4）如果一个函数中有this，这个函数有被上一级的对象所调用，那么this指向的就是上一级的对象。
     （5）如果一个函数中有this，这个函数中包含多个对象，尽管这个函数是被最外层的对象所调用，this指向的也只是它上一级的对象
      箭头函数：箭头函数的作用是保存函数创建时的this值，而不是调用时的值。
      （5）函数重载：
      方法是为同一个函数提供多个函数类型定义来进行函数重载。 编译器会根据这个列表去处理函数的调用。
      例如：let suits = ["hearts", "spades", "clubs", "diamonds"];

         function pickCard(x: {suit: string; card: number; }[]): number;
         function pickCard(x: number): {suit: string; card: number; };
         function pickCard(x): any {
             if (typeof x == "object") {
                 let pickedCard = Math.floor(Math.random() * x.length);
                 return pickedCard;
             }
             else if (typeof x == "number") {
                 let pickedSuit = Math.floor(x / 13);
                 return { suit: suits[pickedSuit], card: x % 13 };
             }
         }

         let myDeck = [{ suit: "diamonds", card: 2 }, { suit: "spades", card: 10 }, { suit: "hearts", card: 4 }];
         let pickedCard1 = myDeck[pickCard(myDeck)];
         alert("card: " + pickedCard1.card + " of " + pickedCard1.suit);

         let pickedCard2 = pickCard(15);
         alert("card: " + pickedCard2.card + " of " + pickedCard2.suit);
   ### 今日实习总结：实习任务未完成  在下一次一起总结


