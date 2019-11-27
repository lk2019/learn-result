## @observable
装饰器可以被es7以上版本或ts使用，让类属性变为可以观察的。
import {observable} from "MobX";

class OrderLine {
    @observable price = 0;  
    @observable amount = 1;  

   constructor(price) {  
        this.price = price;  
    }

   @computed get total() {    
        return this.price * this.amount;  
    }  
}  
如果你使用的是 typescript ，请开启 --experimentalDecorators 这一构建工具标记，并在 tsconfig.json 中将 experimentalDecorators 设置为 true
