## webpack的概念
        webpack是现代js应用程序的静态模块打包器。当webpack处理应用
    时，他会递归地构建一个关系依赖图，其中包含应用程序需要的每个
    模块，然后最终打包成一个或多个bundle。
### 入口
        入口指示webpack应该使用哪个模块，来作为构建内部依赖图的开始。
    进入入口起点后，webpack会找出哪些模块和库是入口起点的依赖。
    可以通过在webpack配置entry属性，来指定一个入口起点。默认是"./src"
        看一个例子：
    module.exports = {
        entry:"./path/to/my/entry/file.js"
    };
    
### 出口
        告诉webpack在哪里输出所创建的bundles，以及如何命名这些文件，默认值为./dist
    我们可以通过在配置中指定一个output字段，来配置这些处理过程：
     const path = reqire('path');
     
     module.exports = {
        entry:""./path/to/my/entry/file.js,
        output : {
            path:path.resolve(_dirname,'dist'),
            filename:'my-first-webpack.bundle.js'
        }
     }
            这个示例，通过output.filename和output.path属性，来告诉webpack bundle的名称
        以及我们想要bundle生成到哪里.可能你想要了解在代码最上面导入的path模块是什么。
### loader
         loader负责处理非js文件。loader可以将所有类型的文件转换为webpack能处理的模块，然后利用webpack
     的打包能力，对他们进行处理。
     
        本质上，webpack loader将所有类型的文件，转换为应用程序的依赖图，可以直接用的模块。
     loader有两个目标：
         1.test，用于标识应该被对应的loader进行转换的文件。
         2.use属性，标识进行转换时，应该使用哪个loader。
        官网例子：
        const path = require('path');
        
        const config = {
            output :{
                filename : "my-first-webpack.bundle.js"
                
            },
            module:{
                rules:[
                    {test:/\.txt$/},use : "raw-loader"}
                ]
            }
        };
        module.exports = config;
            这个例子的意思就是，当你看到.txt的文件的时候，使用raw-loader转换一下
        切定义loader时，要定义在module.xxx里，不要单独定义。
        
### 插件
        插件可以用于执行范围更广的任务。插件的范围包括，从打包优化和压缩，一直到重新定义
    环境中的变量。插件接口可以用来处理各种各样的任务。
        使用插件，一般会使用require（），然后加到plugins数组中。多数插件可以通过选项来自定义
    也可以在一个配置文件中多次使用同一个插件，这时就需要使用new操作来创建实例。
        例子：
        const HtmlWebPlugin = require('html-webpack-plugin');
        const webpack = require('webpack');
        
        const config = {
            module:{
                rules:[ 
                    {test:/\.txt/,use : 'raw-loader'}
                 ]
            },
            plugins:[
                new HtmlWebpackPlugin({template:'./src/index.html'});
            ]
        };
        
        module.exports = config;
        
### 模式
        通过选择development和production之中的一个，来设置mode参数，你可以启动相应模式下的webpack
    内置的优化
     module.export = {
        mode : 'production'
     }
