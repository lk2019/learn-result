## computed 计算值
+ 计算值是通过当前状态或是其他计算值计算出的。
+ 与autorun不一样的是，computed会生成新值，autorun会产生副作用。
### setters
+ setters不能直接改变计算值。
   
      class Foo {  
        @observable length: 2,  
        @computed get squared() {  
            return this.length * this.length;  
       }  
        set squared(value) {   
            this.length = Math.sqrt(value);  
        }  
      }  
+ 必须记住getter之后使用setter，否则一些TypeScript的版本会将同样的命名声明为两个属性
### 作为函数
+ computed可以作为函数被调用，使用.get来获得当前值，也可以使用.observe（callback）来观察变化。
### 支持第二个配置
可以传入name、context上下文、setter、compareStructural（默认false）

