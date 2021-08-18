# node学习笔记

## require

引入一个模块require("")  模块名必须以.或..开头



require()之后，不会引入模块中var定义带变量

但是可以引入exports.x="123";  定义的变量

```javascript
exports.x="123";  //暴露变量
exports.fn = function(){
    
}; //暴露函数
```



## 全局变量

定义变量的时候不加var a = 10;

直接写a = 10;   这时候定义的就是全局变量



全局变量用console.log(global.a)读出来    gloabal相当于javascript中的windows



## 模块

模块里全是局部变量

证明模块是一个函数



```javascript
// a=10;
// console.log(global.a);
console.log(arguments.callee + "");
console.log(arguments.length);
```



function (exports, require, module, \__filename, __dirname) 

函数有5个实参

exports 该对象用来将变量暴露或函数暴漏到外部

require 函数，用来引入外部的模块 

module 代表的是当前模块本身  module.exports == exports 这两个完全相等

\__filename 当前文件名称

__dirname 当前文件夹名称

## module.exports和exports

module.exports 是一个对象

exports是一个变量，指向了module.exports 

所以export只能通过exports.x = "";赋值

module.exports可以直接赋值一个{},也可以通过module.exports.x = "";赋值

## 包package

包结构

包实际上就是一个压缩文件，解压后还远为目录，符合规范的目录，应该包含如下文件

- package.json 描述文件

- bin 可执行二进制文件

- lib js代码

- doc 文档

- test 单元测试

   

  
