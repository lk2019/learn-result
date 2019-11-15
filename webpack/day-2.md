## 入口
### 单个入口简写
    const config = {
        entry:{
            main:"./path/to/my/entry/file.js"
        }
    };
    
### 对象语法
    const config = {
      entry: {
        app: './src/app.js',
        vendors: './src/vendors.js'
      }
    };
    这两个依赖图彼此完全分离、互相独立.
    
## 输出
    const config = {
    output :{  
        filename : "bundle.js",
        path:'/home/proj/public/assets'
    }  
    };
    使用 CDN 和资源 hash 的复杂示例：
   
    config.js
   
    output: {
     path: "/home/proj/cdn/assets/[hash]",
     publicPath: "http://cdn.example.com/assets/[hash]/"
    }
## 模式
### 用法
    mode选项：
    module.exports = {
        mode:'production'
    };
    
## 配置
    webpack很少有配置相同的，一般webpack可以做到以下事情：
        （1）通过require（）导入其他文件
        （2）通过require（）使用npm工具函数
        （3）使用js控制流表达式如？：
        （4）对常用值使用常量或变量
        （5）编写并执行函数来生成部分配置
    需要避免的问题：
        使用webpack命令行接口，应该使用自己的命令行接口，或者使用--env，访问命令行接口参数。
        导出不确定值
        编写很长的配置
        
    基本配置：
        webpack.config.js
         
        var path = require('path');
        
        module.exports = {
            mode:'development',
            entry:'./foo.js',
            output:{
                path:path.resolve(_dirname,'dist'),
                filename:'foo.bundle.js'
            }
        };
        
   
