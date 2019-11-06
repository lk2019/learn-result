## 第五天总结以及学习  
  ### 泛型  
    泛型，也可以称之为模板，一般来说，如果定义一个any类型，那么返回相同类型的返回值就很难实先，而使用泛型，也就是identity函数，就可以
  定义返回值类型与传入参数类型相同，例如：  
  function identity<T>(arg:T):T{  
    return arg;
  }  
  这个例子，我们给identity函数增加了一个类型变量T。T帮我们传入捕获到的类型，之后就可以使用这个类型，并且把T当作返回值，这样，就可以实现
  函数参数与返回值类型相同了。
   #### 泛型函数使用的两种方法
   （1）let output = identity<string>("mystring);  
   (2) let oupput = identity("mystring");
  ### 泛型变量
    在使用泛型函数时，如果我们需要打印参数的长度，如果传入的是number类型，可能就会报错，这时我们可以将T改成T类型的数组形式，例如：
    funvtion identity<T>(arg:Array<T>):Array<T>{
        console.log(arg.length);
        return arg;
    }
  ### 泛型类型
    (1)泛型接口:
        interface GenericIdentityFn{
            <T>(arg:T):T
         }
         
         function identity<T>(arg:T):T{
            return arg;
         }
         
         let myIdentity:GenericIdentityFn = identity;
     (2)泛型类:
     class GenricNumber<T> {
        zeroValue: T;
        add: (x:T,y：t)=> T;
        }
     let mygenericNumber = new GenericNumber<Number>();
     mygenericNumber.Value=0;
     mygenericNumber.add=function(x,y){return x+y;}
   ### 枚举
   #### 数字枚举
     enum Direction{
        Up=1,
        Down,
        left,
        right
     }
     这时 down为2，left为3，right为4，如果up不设值，则up从0开始，如果left设为100，则up为0，down为1，right为101
     
   #### 字符串枚举
    enum Direction{
        Up="Up",
        Dowm="Down",
        Left="Left",
        Right="Right",
    }
    字符串不存在自增长，但是字符串枚举可以序列化。
   #### 异构枚举
     enum booleanandstring{
    No=0,
    Yes="YES“
   }
   #### 计算的常量成员
     每个枚举成员都带有一个值，它可以是常量或计算出来的。当满足如下条件时，枚举成员为常量成员：
   （1）是枚举的，并且第一个成员没有初始化器，这种情况下被赋予0；
   （2）不带有初始化器切之前枚举为一个数字常量，这时候其后面的枚举成员在其值上+1，
   *（3）枚举成员使用了常量枚举表达式初始化，常量枚举表达式，可详细查找ts中文手册
   
   #### 联合枚举与枚举成员类型
     存在一种特殊的非计算的常量枚举成员的子集：字面量枚举成员。字面量枚举成员是指不带有初始值的常量枚举成员，或者是值被初始化
     为
     （1）任何字符串字面量
     （2）任何数字
     （3）使用一元运算符的数字
   #### 反向映射
     数字枚举成员具有反向映射，从枚举值到枚举名字，例如：
     enum Enum{
        A
     }
     let a=Enum.A;
     let nameofA=Enum[a
     ];
   #### const枚举
     const只能使用常量枚举表达式，且不同于常规，他们在编译阶段会被删除
   #### 外部枚举
     外部枚举是用来藐视以及存在的枚举类型的形状
     例如：
     
     declare enum Enum{
        A=1,
        B,
        C
     }
## 总结 
  在是用reactts中所遇到的问题，在实现table表的固定列和表头中存在的问题，以及使用react实现的方法，
  （1）第一个难点，css实现，首先，第一种，是将要固定的列和头进行浮动，盖住原来的表，经过调试css样式
  完成表的遮盖
  第二种思路，在css样式，position：sticky可以完成这种方案，再设置优先级即可
  这里实现的是第一种方案，附第一代源代码（未修改版）
  react：
    import React from "react";
    import "./demo5.css"
    
    
    
    
    export default class extends React.Component {
    
        constructor(props){
            super(props)
            this.state = {
            }
        }
    
        componentDidMount= () =>{
            window.addEventListener('scroll',this.scrollEvent);
        }
        handleScroll = (event) =>{
    
            let ctx = this;
            let clientHeight = ctx.refs.bodyBox.clientHeight; //可视区域高度
            let scrollTop  = ctx.refs.bodyBox.scrollTop;  //滚动条滚动高度
            let scrollleft = ctx.refs.bodyBox.scrollLeft; //滚动内容高度
            ctx.refs.right_div2.scrollTop=scrollTop;
            ctx.refs.left_div2.scrollTop=scrollTop;
            ctx.refs.main_div1.scrollLeft=scrollleft;
            console.log(clientHeight);
            console.log(scrollTop);
            console.log(scrollleft);
     }
    
    
        renderLeft = (columns) => {
            return (
                <React.Fragment></React.Fragment>
            )
        }
        renderRight = (columns) => {
            return (
                <React.Fragment></React.Fragment>
            )
        }
        renderMain = (columns) => {
            return (
                <React.Fragment></React.Fragment>
            )
        }
        render(){
            const leftColumns=[
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
                }
            ]
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
            const rightColumns=[
                {
                    title: 'Action',
                    key: 'operation',
                    fixed: 'right',
                    width: 100,
                    render: () => <a>action</a>,
                }]
            const data = [];
            for (let i = 0; i < 100; i++) {
                data.push({
                    key: i,
                    name: `Edrward ${i}`,
                    age: 32,
                    address: `London Park no. ${i}`,
                });
            }
            return (
    
                <div className="container-fluid" onScroll={this.handleScroll} >
                    <div className="left_div" >
                        <div className='left_div1'>
                            <table className="left_table1" >
                                <tbody>
                                <tr>
                                    {leftColumns.map((item,index,arr)=>{
                                        return (
                                            <td key={item.dataIndex}>{item.title}</td>
                                        )
                                    })}
                                </tr>
                                </tbody>
                            </table>
                        </div>
                        <div className="left_div2" ref="left_div2">
                            <table className="left_table2">
                                <tbody>
                                {data.map((item,index,arr)=>{
                                    return (
                                        <tr key={"left_div2"+index}>
                                            <th key ={"left_div2"+typeof(item)+index}>{index}</th>
                                        </tr>
                                    )
                                })}
                                </tbody>
                            </table>
                        </div>
                    </div>
                    <div className="right_div"  >
                        <div className="right_div1">
                            <table className="right_table1">
                                <tbody>
                                <tr>
                                    {rightColumns.map((item,index,arr)=>{
                                        return (
                                            <td key={"right_div"+index}>{item.title}</td>
                                        )
                                    })}
                                </tr>
                                </tbody>
                            </table>
                        </div>
                        <div className="right_div2" ref="right_div2">
                            <table className="right_table2" >
                                <tbody>
                                {data.map((item,index,arr)=>{
                                    return (
                                        <tr key={"right_div2"+index}>
                                            <th key ={"right_div2"+typeof(item)+index}>{index}</th>
                                        </tr>
                                    )
                                })}
                                </tbody>
                            </table>
                        </div>
                    </div>
                    <div className="main_div" >
                        <div className="main_div1" ref="main_div1">
                            <table className="main_table1">
                                <tbody>
                                <tr>
                                    {columns.map((item,index,arr)=>{
                                        return (
                                            <td key={"main_table1"+index}>{item.title}</td>
                                        )
                                    })}
                                </tr>
                                </tbody>
                            </table>
                        </div>
                        <div className="main_div2"   ref="bodyBox">
                            <table className="main_table2">
                                <tbody>
                                {data.map((item,index,arr)=>{
                                    return (
                                        <tr key={"main_table2"+typeof(index)+index}>
                                            {arr.map((item1,index1,arr1)=>{
                                                return (
                                                    <td key={"main_table1"+typeof(index1)+index1}>{item1.address}</td>
                                                )
                                            })}
                                        </tr>
                                    )
                                })}
                                </tbody>
                            </table>
                        </div>
                    </div>
                    {/* {this.renderMain(columns)}
                  {this.renderLeft(leftColumns)}
                  {this.renderRight(rightColumns)} */}
    
    
                </div>
    
    
    
            )
        }
    }
  css样式（未修改版）：
      .container-fluid {
          position: relative;
          width: 550px;
          overflow: hidden;
      }
      
      .left_div1 {
          width: 100%;
          z-index: 1000;
      }
      
      .left_div2 {
          z-index: 1000;
          width: 100%;
          height: 384px;
          overflow: hidden;
      }
      
      .right_div1 {
          width: 100%;
          height: 20px;
      }
      
      .right_div2 {
          width: 100%;
          height: 384px;
          overflow: hidden;
      }
      
      .main_table2 {
          /**width和max-width一起写，手机浏览器打开也能固定长度**/
          width: 880px;
          max-width: 880px;
      }
      
      .main_div1 {
          margin-left: -20px;
          display: block;
          z-index: 10;
          width: 100%;
          overflow: hidden;
          padding-right: 17px;
      }
      
      .main_table1 {
          width: 880px;
      }
      
      .main_div2 {
          width: 100%;
          overflow: auto;
          height: 400px;
      }
      
      .left_div {
          z-index: 1000;
          position: absolute;
          min-width: 70px;
          display: block;
          background-color: #ffffff;
      }
      
      .right_div {
          background-color: #ffffff;
          position: absolute;
          right: 0px;
          min-width: 100px;
          z-index: 1000;
          margin-right: 17px;
      }
      
      .main_div {
          position: relative;
          display: block;
          overflow: hidden;
          width: 100%;
      }
  
  这里附上ant design实现的方法
        const dataSource = [
        {
          key: '1',
          name: '胡彦斌',
          age: 32,
          address: '西湖区湖底公园1号',
        },
        {
          key: '2',
          name: '胡彦祖',
          age: 42,
          address: '西湖区湖底公园1号',
        },
      ];
      
      const columns = [
        {
          title: '姓名',
          dataIndex: 'name',
          key: 'name',
        },
        {
          title: '年龄',
          dataIndex: 'age',
          key: 'age',
        },
        {
          title: '住址',
          dataIndex: 'address',
          key: 'address',
        },
      ];
      
      <Table dataSource={dataSource} columns={columns} />;
  
  
