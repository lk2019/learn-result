## autorun
+ Mobx.autorun是希望创建一个响应函数，一般如果你想使用一个可以自动运行的函数，但是又不想改变值或生成值时使用。
  
   
    var numbers = observable([1,2,3]);
    var sum = computed(() => numbers.reduce((a, b) => a + b, 0));
    
    var disposer = autorun(() => console.log(sum.get()));
    // prints '6'
    numbers.push(4);
    // prints '10'
    
    disposer();
    numbers.push(5);
