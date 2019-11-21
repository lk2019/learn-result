## state Hook   
### 声明state变量
    import React,{useState} from 'react',
    funcition Example(){
        const [count,setCount] = useState(0)
    }
    useState的参数:
    唯一的初始state就是参数，可以用数字、字符串来赋值，不一定是对象，如果要存储两个变量，调用两次setstate。
    usestate的返回值：
    返回当前state和更新的state。
### 更新setcount
    <button onClick = {() => { setCount(count+1)}}>click me </button>
## effect hook
    在effect hook中可以进行副作用操作，比如数据获取，设置订阅以及更改reactDom等等。
    effect可以当做componentDidMount,componentDidUpdate,componentWillUnmount三个函数看到。
    useeffect会在每次渲染后都执行。
    当需要清除时，一般会这样:
    useEffect(() =>{
        function handleStatusChange(status){
            setIsOnline(status.isOnline);
        }
        
        ChatAPI.subscribeToFriendStatus(props.friend.id,handleStatusChange);
        return funciton cleanup(){
            ChatAPI.unsubscribeToFriendStatus(props.friend.id,handleStatusChange);
        }
    })
    
### HOOK规则
    只在最顶层调用HOOK
    只在react函数中使用hook
    最重要的是，hook可以在调用其他函数hook，这样解决了react只能用props来完成组件的信息传递。
