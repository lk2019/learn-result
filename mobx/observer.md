## @observer
observer可以将react组件转换为Mobx组件。它用Mobx.autorun将render函数包裹，就确保了任何依赖数据的更新都可以触发渲染。
### 给无状态组件添加
    import {observer} from "mobx-react";
   
    const Timer = observer(({ timerData }) =>
       <span>Seconds passed: { timerData.secondsPassed } </span>
    );
### observer使用原则
+ 所有使用可观察数据渲染的组件。
