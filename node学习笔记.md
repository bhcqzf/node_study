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

- package.json **描述文件**，必须有

- bin 可执行二进制文件

- lib js代码

- doc 文档

- test 单元测试

  

## npm包管理器

node package manager

npm完成第三方模块的发布、安装和依赖。借助npm node与第三方模块之间形成了很好的一个生态系统

npm -v   查看npm版本

npm  version 查看所有模块的版本

npm search  搜索包

npm install 包名   默认安装到当前的文件夹中   简写  npm i

npm install -g 包名 （全局安装包，一般都是一些工具）

npm install 包名 --save 会储存到json中（其实现在不加save也会添加）

npm install 下载所有依赖包

npm init 初始化一个package环境

npm remove 移除包

### 设置国内源和cnpm

```shell
#设置国内源
npm config set registry https://registry.npm.taobao.org
#安装cnpm
npm install -g cnpm --registry=https://registry.npm.taobao.org
```



## buffer(缓冲区)

buffer的结构和数组很像，操作的方法也和数组类似

js本身的数组性能较差

数组中不能存储二进制文件

buffer可以存储二进制文件,都是以二进制存储的，但是会以16进制显示

```javascript
var str = "hello world ";
var buf = Buffer.from(str);
console.log(buf);

//创建一个指定大小的buffer
//buffer的构造方法都废弃了
var buf2 = new Buffer(10);
console.log(buf2.length);
//下面这个没废弃
var buf2 = Buffer.alloc(10);
console.log(buf2);
//buffer的大小一旦确定无法改变
```

```javascript
/*
	Buffer.from(str) 将一个字符串传华为buffer
	Buffer.alloc(size) 创建一个指定大小的Buffer
	Buffer.alloUnsafe(size) 创建一个指定大小的Buffer，但可能包含敏感数据
*/
```

## 文件系统 File System

fs模块中所有的操作都有两种形式可供选择

同步和异步

同步文件系统会阻塞程序的运行，也就是除非操作完毕，否则不会向下执行代码

异步文件系统不会阻塞程序的运行，而是在操作系统完成时，通过回调函数将结果返回
