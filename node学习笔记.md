# node学习笔记

## require

引入一个模块require("")  模块名必须以.或..开头



require()之后，不会引入模块中var定义带变量

但是可以引入exports.x="123";  定义的变量



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
```

