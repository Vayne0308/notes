---
typora-root-url: image
---

## 什么是Nodejs

Node.js是一个Javascript运行环境(runtime)，发布于2009年5月，由Ryan Dahl开发，实质是对Chrome V8引擎进行了封装。Node.js对一些特殊用例进行优化，提供替代的API，使得V8在非浏览器环境下运行得更好。

* Node不是一个Web服务器，它本身并不能做任何事情。它无法像Apache那样工作。如果你希望它成为一个HTTP服务器，你必须借助它内置库自己编写
* Node.js只是计算机上执行代码的另一种方式，它是一个简单的JavaScript Runtime。简单的说，Node.js 就是运行在服务端的 JavaScript。
* Node.js 是一个基于Chrome JavaScript 运行时建立的一个平台。Node.js是一个事件驱动I/O服务端JavaScript环境，基于Google的V8引擎，V8引擎执行Javascript的速度非常快，性能非常好。
## node.js的组成
#### 浏览器中的js的组成

- DOM: 文档对象模型
- BOM: 浏览器对象模型，window/history/location/navigator/screen
- ECMA Script(ES):语法规范

#### node中js的组成

* 没有DOM
* 少量的BOM，console、setTimeout、setInterval...
* 几乎包含所有的ES
## 异步代码执行机制
#### nodejs中事件轮询：分为六个阶段

* timers 定时器阶段
    * 回调队列，执行已经被 setTimeout() 和 setInterval() 的调度回调函数，全部执行完就自动去下一个阶段 
* 待定回调（pending callbacks）
    * 执行延迟到下一个循环迭代的 I/O 回调
* idle, prepare：仅系统内部使用
* poll 轮询阶段 
   *  回调队列（放置做完成I/O操作的回调函数）
   *  负责执行回调函数，当全部执行完毕：
      1. 如果前面设置过 setImmediate 函数
      2. 如果有定时器到点了
   *  满足以上两种情况中一种，才会去下一个阶段
   *  如果以上两种情况都没有满足。就在当前阶段停留，等待新的回调函数被添加进来
* check 检查阶段 
    * 回调队列（放置 setImmediate的回调函数）       
    * 负责执行setImmediate的回调函数（全部执行完就自动去下一个阶段）
* close callbacks 
   * 全部执行完就自动去timers阶段  
#### 宏任务和微任务    
js引擎会对异步代码进行优先级划分，优先级高先执行，优先级低后执行

* 微任务：
   * 1.特点：优先级高：
   * 2.微任务主要有： process.nextTick（立即执行函数） 、 promise.then().catch().finally() 、queueMicrotask...

  * 3.优先级最高：process.nextTick。 其他的顺序执行
* 宏任务：

  * 1.特点：优先级低：

  * 2.宏任务主要有：setTimeout、setImmediate、I/O...

  * 3.看事件轮询机制  
* 执行：先执行微任务，在执行宏任务

```js
Promise.resolve()
  .then(() => {
    console.log('promise 4');
  })

setImmediate(() => {
  console.log('setImmediate() 1');
})

setTimeout(() => {
  console.log('setTimeout() 2');
})

process.nextTick(() => {
  console.log('process.nextTick() 3');
})
/*
nodejs中执行顺序：
process.nextTick() 3
promise 4
setTimeout() 2
setImmediate() 1
*/

```
libuv库源代码:https://nodejs.org/zh-cn/docs/guides/event-loop-timers-and-nexttick/

轮询机制文章:https://github.com/libuv/libuv/blob/v1.x/src/unix/core.c)

## commonjs模块化
模块化：将一个大的js文件拆成多个小的js文件，最终通过某种语法组合在一起
模块: 一个js文件

#### 引入（其他模块）

- require(模块路径)
  - 模块路径的规则
    - 文件后缀名可以省略不写，如js、json;
    - 自定义模块（自己写的模块）的的模块路径必须以 ./ 或 ../ 开头，否则报错
    - nodejs的核心模块（别人的模块）的模块路径直接写模块名称（不能加 ./ 或 ../）

#### 暴露（当前模块的内容）

* exports
   * exports只能 exports.xxx = xxx
* module.exports
   * module.exports.xxx = xxx
   * module.exports = xxx 
* 模块最终暴露的是 module.exports 指向的值，exports只是module.export的一个引用（简写）而已
###### 引入模块

```js
// 引入module1
const module1 = require('./module1'); // { add }
// 引入module2
const module2 = require('./module2'); // count
// 引入module3.json
const module3 = require('./module3');
// nodejs自带的核心模块
const http = require('http');
console.log(module1.add(1, 2));
console.log(module2(2, 1));
console.log(module3);
```
###### module1.js文件

```js
//module1.js文件
function add(x, y) {
  return x + y;
}
// 暴露出去
exports.add = add;
```
###### module2.js文件

```js
//module2.js文件
function count(x, y) {
  return x - y;
}
// 暴露出去
module.exports = count;
```
###### module3.json文件

```js
{
  "name": "xiaowang",
  "age": 40
}
```
## package和npm
首先需下载[node](https://nodejs.org/zh-cn/)，下载完成后进行安装，检查是否安装成功node,window在cmd控制台中输入node -v,回车出现版本号即安装成功。

#### 包 package

* package.json文件
  * name:包名（将来下载包输入的名称）
            1.包名要求不能有中文、大写。（只能小写英文、数字、下划线）
            2.包名不能与现有包名重复（不能叫jquery、react、vue）
  * version 版本号
  * scripts 运行项目的指令
  * dependencies 生产依赖
              jquery: 1.12.0  代表 版本必须是 1.12.0
              jquery: ^1.12.0 代表 版本必须是 1.12.x
              query: ~1.12.0 代表 版本必须是 1.x.x
  *  devDependencies 开发依赖

```js
//package.json
{
  "name": "xxx",
  "version": "1.0.0",
  "description": "",
  "main": "01.helloNode.js",
  "dependencies": {
    "bootstrap": "^4.4.1",
    "lodash": "^4.17.15",
    "jquery": "^1.12.4",
    "zepto": "^1.2.0"
  },
  "devDependencies": {},
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```
## 包管理器
#### 包管理器 npm
###### 下载安装包

* npm install/i xxx@x.x.x  下载指定版本包
* npm i xxx 下载最新版本的包
   * 创建node_modules，将下载的包放进去
   * 将下载的包添加当前目录的package.json中依赖中
   * 创建package-lock.json，是一个下载缓存文件，能让第二次下载更快
* npm i xxx -D/--save-dev 下载并添加到开发依赖 
* npm i xxx -g 全局安装 --> 默认路径 C:\Users\xxx\AppData\Roaming\npm，为了作为指令使用
* npm i  下载当前目录package.json中所有依赖包
###### 删除包

* npm remove/r xxx
###### 创建package.json

* 新建package.json
* npm init 自定义
* npm init -y   创建全选默认值的package.json 
>###### 输入指令：
>
>* npm config set registry https://registry.npm.taobao.org
>* 作用：将下载地址改成国内淘宝镜像服务器地址（优点：下载速度快，没有被墙的风险）
>* 只需设置一次，以后无需重复操作   
#### 包管理器 yarnnpm 
###### 安装yarn（下载速度快于npm）

* npm i yarn -g
###### 下载

* yarn add xxx 下载并添加到生产依赖
* yarn add xxx --dev  下载并添加到开发依赖
* yarn global add xxx 全局安装
  * yarn 下载当前目录package.json中所有依赖包
###### 删除

* yarn remove xxx  
>###### 输入指令：
>
>* npm config set registry https://registry.npm.taobao.org
>  * 作用：将下载地址改成国内淘宝镜像服务器地址（优点：下载速度快，没有被墙的风险）
>  * 只需设置一次，以后无需重复操作

******
* 在vscode中下载包管理器，需在下载包的文件下右键==>在终端打开，然后输入相应命令下载
* 在webstrom中下载包管理器，点击webstrom左下角的Terminal/ctrl+F12打开终端输入命令
## nodejs的核心模块
#### nodejs中的函数
* 模块化的所有模块默认都被包裹了一层看不见的函数
* 可在node.js中运行:console.log(arguments.callee.toString())
 * callee 是 arguments 对象的一个属性。它可以用于引用该函数的函数体内当前正在执行的函数
```
function (exports, require, module, __filename, __dirname) {}
    exports 用来暴露
    require 用来引入
    module  module.exports 用来暴露
    __filename 当前模块的绝对路径（文件绝对路径）
    __dirname  当前模块的文件夹绝对路径（文件夹绝对路径）
```
#### path核心模块
* 这个模块专门用来处理文件路径问题
* 需要通过require()引入
###### 相对路径 path.join() 
###### 绝对路径 path.resolve()
```js
//引入path核心模块
const path = require('path');

//相对路径 path.join() 
const filePath1 = path.join('a','/b','../c','d.js')
console.log(filePath1);  //a\c\d.js

//绝对路径 path.resolve()
const filePath2 = path.resolve(__dirname,'a','/b','../c','d.js')
console.log(filePath2);  //C:\Users\Desktop\nodejs\a\c\d.js

```
#### buffer核心模块
* 缓冲器，用来存储二进制数据
* 不需要引入，可以直接访问使用，他是全局的(global.Buffer)
* 特点：
   * 大小固定
   * 存储内容大小一字节
  * buffer是global上的属性

###### Buffer.alloc()  返回一个指定大小的新建的的已初始化的Buffer
###### Buffer.allocUnsafe() 返回一个指定大小的新建的未初始化的  Buffer，由于Buffer 是未初始化的，因此分配的内存片段可能包含敏感的旧数据
###### Buffer.from()  返回buffer，将数据类型（数组/字符串）转换成buffer数据存储
```js
// 创建buffer容器
const buf1 = Buffer.alloc(10);
const buf2 = Buffer.allocUnsafe(10);
console.log(buf1);  // <Buffer 00 00 00 00 00 00 00 00 00 00>
console.log(buf2);  // <Buffer 68 67 cd 0e 0f 02 00 00 01 00>

// buf2是一个伪数组
console.log(buf2[0]);   //232
console.log(buf2.length);  //10

/*
utf8
  英文字符 占 1字节
  中文字符 占 3字节
      
  1 byte(字节) = 8 bit （位）
  1 kb = 1024 byte
  1 mb = 1024 kb
  1 gb   1 tb
*/
const buf3 = Buffer.from('你好');
console.log(buf3); // <Buffer 68 65 6c 6c 6f 20 61 74 67 75 69 67 75>
console.log(buf3.length); // 6

console.log(buf3.toString()); // 你好

```
#### fs(file system)核心模块
* 用来对文件进行操作（读/写）
* 需要通过require（）引入模块
###### fs.openSync(path[, flags, mode]) 同步写入

 * 打开文件
        * fs.openSync(path[, flags, mode])
          path 文件路径
          flags 对文件进行操作（读/写）
              可选值：会有默认值 'r'
               'w'  写入
               'r'  读取
               'a'  追加
          mode 设置文件的权限（只读/可读可写..）
              可选值：会有默认值 0o666
              0o111 文件可执行
              0o222 文件可写入
              0o444 文件可读取
              0o666 文件可读、可写
             返回值：文件描述符（代表打开的文件）  
 * 写入内容
        * fs.writeSync(fd, string[, position[, encoding]])
             fd 文件描述符
             string 要写入的字符串内容
             position 从文件的那个位置开始写入  0
             encoding 写入文件内容的编码方式   utf-8
 * 关闭文件
        * fs.closeSync(fd)
```js
//引入fs模块
const fs = require('fs');
//打开文件
const fd = fs.openSync('./a.txt','w',0o666);
console.log(fd);   //3

//写入内容
const result = fs.writeSync(fd,'你好吗')；
console.log(result);   // 9 写入内容的字节长度

//关闭文件
fs.closeSync(fd);
```
###### fs.open(path[, flags, mode]) 异步写入

* 打开文件
     * fs.open(path[, flags, mode, callback])
        path 文件路径
        flags 对文件进行操作（读/写）
            可选值：会有默认值 'r'
            'w'  写入
            'r'  读取
            'a'  追加
        mode 设置文件的权限（只读/可读可写..）
            可选值：会有默认值 0o666
            0o111 文件可执行
            0o222 文件可写入
            0o444 文件可读取
            0o666 文件可读、可写
         返回值：文件描述符（代表打开的文件）  
         callback:
              error: 如果打开文件失败了，就会是错误内容。 如果打开文件成功了，就是null
              fd
              nodejs有错误优先机制: 要求开发者先处理异步代码的错误，再做其他事
* 写入内容
     * fs.write(fd, string[, position[, encoding], callback])
* 关闭文件
     * fs.close(fd, callback)
```js
// 回调函数方案
const fs = require('fs');
// 1. 打开文件
fs.open('c.txt', 'w', (error, fd) => {
  //console.log(error); // null
  if (!error) {   // 没有错误
    console.log('文件打开成功~');
    // 2. 写入内容
    fs.write(fd, '你好', (err) => {
      if (!err) {
        console.log('文件写入成功~');
      } else {
        console.log(err);
      }
      // 3. 关闭文件 --> 不管写入成功/失败，都要关闭
      fs.close(fd, (err) => {
        if (!err) {
          console.log('文件关闭成功');
        } else {
          console.log(err);
        }
      })
    })
  } else {
    // 有错误
    console.log(error);
  }
}) 
```
```js
 //使用promise方案
const fs = require('fs');
const promise = new Promise((resolve, reject) => {
  // 执行 打开文件 异步操作
  fs.open('c.txt', 'w', (err, fd) => {
    if (!err) {
      // 将promise对象的状态改成 成功状态
      resolve(fd);
    } else {
      // 将promise对象的状态改成 失败状态
      reject(err);
    }
  })
})

promise
  .then((fd) => {
    // 说明文件打开成功， 要写入文件
    return new Promise((resolve, reject) => {
      fs.write(fd, '你好', (err) => {
        if (err) {
          console.log('文件写入失败', err);
        }
        resolve(fd);
      })
    })
  })
  .then((fd) => {
    //关闭文件 
    return new Promise((resolve, reject) => {
      fs.close(fd, (err) => {
        if (!err) {
          resolve()
        } else {
          reject(err);
        }
      })
    })
  })
  .then(() => {
    console.log('全部完成');
  })
  .catch((err) => {
    console.log(err);
  })
  
```
* async函数
   * 是generator语法糖
   * 用 async 取代 
   * 用 await 取代 yield  

 ```js
 generator： 
    function* () {
      yield xxx;
    }
 ```

```js
async function fn() {
  // 只有遇到promise对象，才会暂停
  console.log(111);
  // await关键字遇到初始化状态的promise对象，会暂停
  // 当promise对象变成成功状态时，继续往下执行
  // 当promise对象变成失败状态时，会报错，终止函数的执行（退出函数）
  await new Promise((resolve, reject) => {
    // setTimeout(() => {
    //   resolve('error');
    // }, 3000)
  })
  console.log(222);
  return 'success';
}
// async函数返回值就是一个promise
const promise = fn();

// promise对象特点：如果处理了失败的回调（有catch），就不会报错，会触发catch
// 如果没有处理失败的回调（没有catch），就报错
promise
  .then((value) => {
    // async函数成功的返回值看 整个函数的返回值
    console.log('then', value);
  })
  .catch((err) => {
    // async函数失败的返回值看 reject(reason)
    console.log('catch', err);
  })
```

```js
// 解决异步回调地狱的方案： async + promise
const fs = require('fs');
async function writeFile() {
  // 打开文件
  const fd = await new Promise((resolve, reject) => {
    // 执行 打开文件 异步操作
    fs.open('c.txt', 'w', (err, fd) => {
      if (!err) {
        // 将promise对象的状态改成 成功状态
        resolve(fd);
      } else {
        // 将promise对象的状态改成 失败状态
        reject(err);
      }
    })
  })

  // 写入内容
  await new Promise((resolve, reject) => {
    fs.write(fd, '沛华~~', (err) => {
      if (err) {
        console.log('文件写入失败', err);
      }
      resolve();
    })
  })

  // 关闭文件
  await new Promise((resolve, reject) => {
    fs.close(fd, (err) => {
      if (!err) {
        resolve()
      } else {
        reject(err);
      }
    })
  })

}

const p = writeFile();

p.then(() => {
  console.log('全部执行完了~');
}).catch((err) => {
  console.log(err);
})
```
###### fs.writeFile() 简单文件写入(一般写入小文件)

```js
const fs = require('fs');
fs.writeFile('d.txt', '你好', (err) => {
  if (!err) {
    console.log('文件写入成功');
  } else {
    console.log(err);
  }
})
```
###### fs.readFile() 异步地读取文件的全部内容

*   `path`[<string>](http://nodejs.cn/s/9Tw2bK)|[<Buffer>](http://nodejs.cn/s/6x1hD3)|[<URL>](http://nodejs.cn/s/5dwq7G)|[<integer>](http://nodejs.cn/s/SXbo1v)文件名或文件描述符。
*   `options`[<Object>](http://nodejs.cn/s/jzn6Ao)|[<string>](http://nodejs.cn/s/9Tw2bK)

    *   `encoding`[<string>](http://nodejs.cn/s/9Tw2bK)|[<null>](http://nodejs.cn/s/334hvC)**默认值:**`null`。
    *   `flag`[<string>](http://nodejs.cn/s/9Tw2bK)参阅[支持的文件系统标志](http://nodejs.cn/s/JjbY8n)。**默认值:**`'r'`。
*   `callback`[<Function>](http://nodejs.cn/s/ceTQa6)

    *   `err`[<Error>](http://nodejs.cn/s/qZ873x)
    *   `data`[<string>](http://nodejs.cn/s/9Tw2bK)|[<Buffer>](http://nodejs.cn/s/6x1hD3)


```js
const fs = require('fs');

fs.readFile('a.txt', (err, data) => {
  if (!err) {
    console.log(data.toString());
  } else {
    console.log(err);
  }
})
```
###### fs.createWriteStream(path) 流式写入(写入大文件)

* 返回值是一个可写流，返回: <fs.WriteStream>
```js
const fs = require('fs');

// 返回值是一个可写流
const ws = fs.createWriteStream('e.txt');

// on绑定的事件是持久事件
// once绑定的事件是一次性事件
ws.once('open', () => {
  console.log('可写流打开/创建');
})

ws.once('close', () => {
  console.log('可写流关闭');
})

// 写入内容
ws.write('锄禾日当午');
ws.write('汗滴禾下土');
ws.write('谁知盘中餐');
ws.write('粒粒皆辛苦');

// 手动关闭可写流
ws.end();
```
###### fs.createReadStream(path)

```js
const fs = require('fs');

/*
  一旦创建可读流，就会立即读取一次，默认为64kb大小
  直到读取的内容被消费，才会读取下一次
    - 事件 data
    - pipe
*/
const rs = fs.createReadStream('C:\\Users\\Desktop\\demo\\简单流式写入.mp4');
const ws = fs.createWriteStream('a.mp4');

/* rs.once('close', () => {
  console.log('可读流关闭了~');
  ws.end();
})

ws.once('close', () => {
  console.log('可写流关闭了~');
})

// 可读流当全部读取完毕后，会自动关闭
rs.on('data', (chunk) => {
  // chunk 就是可读取每次读取的文件内容
  // console.log(chunk); // 65536 --> 64 * 1024 byte --> 64 kb
  ws.write(chunk);
}) */

rs.pipe(ws);
```
#### http核心模块

###### 学习更多=>查看nodejs中的http模块文档

###### http.createServer((request, response) => { }) 服务器

* request 请求信息：客户端发送给服务端的信息
* response 响应信息：服务端响应给客户端的信息
```js
/*
  http - nodejs核心模块
    服务端: http.createServer()
    客户端: http.request()

  querystring - nodejs核心模块
    用来解析查询字符串参数
*/
//引入模块
const http = require('http');
const querystring = require('querystring');

/*
  问题: 每次修改服务器代码，需要重启服务器才能生效
  解决：
    npm i nodemon -g
    nodemon xxx (nodemon会自动监视文件，一旦文件发生变化，会自动重启服务器)
*/
// 创建服务
const server = http.createServer((request, response) => {
  // 处理请求、返回响应~
  /*
    request 请求信息：客户端发送给服务端的信息
    response 响应信息：服务端响应给客户端的信息
  */
  // 处理请求
  // console.log(request.url); // /?username=jack&password=123
  const qs = request.url.split('?')[1];
  const result = querystring.parse(qs);
  console.log(result); // { username: 'jack', password: '123' }

  // 设置响应头（告诉客户端的内容）
  // response.setHeader('Content-Type', 'text/plain;charset=utf-8');
  response.setHeader('Content-Type', 'text/html;charset=utf-8');
  // 返回响应
  response.end('<h1>欢迎访问nodejs服务器</h1>');
})

// 启动: 监听端口号 (1 ~ 65535) 
// 一般3位数以下端口号被系统服务占用了，一般不用
// 一般使用4位数以上：3000 3030 4000 8000 8080...
// localhost / 127.0.0.1 代表本机  
// 192.168.2.147
server.listen(3000, (err) => {
  if (!err) console.log('服务器启动成功~ 请访问：http://localhost:3000');
  else console.log(err);
})
//启动： node 当前文件 回车
//终止： ctrl+c 
```
###### http.request() 客户端

```js
const http = require('http');

// 创建请求
// 查询字符串 querystring  ?username=jack&password=123
// 以问号开头，key=value，多个key/value用&连接
const request = http.request('http://localhost:3000?username=jack&password=123', {
  method: 'GET'
}, (res) => {
  let responseData = '';
  // console.log(res); // 可读流
  res.on('data', (chunk) => {
    // console.log(chunk); // <h1>欢迎访问nodejs服务器</h1>
    responseData += chunk.toString();
  }).on('close', () => {
    // 可读流关闭了
    // 数据读取完毕
    console.log(responseData);
  })
})

// 发送请求
request.end();
```
## 数据库
* 数据库（DataBase）是按照数据结构来组织、存储和管理数据的仓库
* 我们的程序都是在内存中运行的，一旦程序运行结束或者计算机断电，程序运行中的数据都会丢失。所以我们就需要将一些程序运行的数据持久化到硬盘之中，以确保数据的安全性。而数据库就是数据持久化的最佳选择。说白了，数据库就是存储数据的仓库。
* 数据库的分类
 * 关系型数据库（RDBS）
   代表有：MySQL、Oracle、DB2、SQL Server...
   特点：关系紧密，都是表
 * 非关系型数据库（NoSQL）
   代表有：MongoDB、Redis...
   特点：关系不紧密，有文档，有键值对
#### mysql数据库
#### 安装

* 服务器
   下载MySQL Server==>点击安装==>下一步直到finsh ==>下一步==>到达character set时，选择第三个，character set为utf-8 ==> 下一步，直到set the security options，设置账号密码 ==> Execute，直到四个√全中则安装成功，否则重装重试
* 可视化界面 mysql-workbench-community

##### 操作

* 创建连接
  1、打开可视化界面，检查mysql是否打开，打开任务管理器，查看MySQL是否运行，未运行就启动
  2、在可视化界面中MySQL Connections中点击加号创建连接，新建连接名，然后测试连接，输入密码，连接成功后点击OK进行连接
  3、双击刚创建的连接，进入连接

* 创建数据库

 * 创建数据库：点击左上角的+圆柱体即创建库，输入数据库名

 * 查看数据库：在输入sql语句界面输入：show databases；==> 选中输入的代码，点击输入界面左上角的闪电符号运行代码，查看所有数据库（--空格表示注释）

 * 切换需要操作数据库：输入use 数据库名 ==> 选中输入的代码，点击输入界面左上角的闪电符号运行代码 

     ![1](/1.bmp)

 * 点击左上角的+表格即创建库里面的表，输入表名

 * 添加表内的内容，Column Name(数据名)、Datatype（数据存储类型）、pk（主键）、NN（非空）、UQ(唯一)、AI（自增）

 * Apply 创建完成

* CRUD增删改查 

 * C -create 增
   1、在可视化界面输入：

     ```
     insert into 数据库表名(username,`password`) value  ('xiaoming', 123); 
     //由于password为关键字使用模板字符串将其包裹住
     ```
   2、选中输入的代码，点击输入界面左上角的闪电符号运行代码添添内容 

 * R - read 查
       * 查看数据库中所有表数据：
         1、在可视化界面输入

     ```
     	select * from 数据库表名;
     ```
        2、选中输入的代码，点击输入界面左上角的闪电符号运行代码添添内容 
       * 查看数据库中指定列数据：在可视化界面输入

     ```
     select username，`password` from 数据库表名;
     ```
       * 查看数据库中所需数据(where后添加查询条件)：在可视化界面输入

     ```
     select * from 数据库表名 where id=1;
     ```
       * 根据xx进行排序，默认是顺序：在可视化界面输入

     ```
     //desc是倒序
      select * from 数据库表名 order by id desc;
     ```
       * 分页查询 

     ```
     //limit 限制每次查询多少数据，查找第一页
         select * from 数据库表名 limit 2;
     //limit 限制每次查询多少数据，查找第二页
         select * from 数据库表名 limit 2 offset 2;
     //limit 限制每次查询多少数据，查找第三页
         select * from 数据库表名 limit 2 offset 4;
     ```

 * U-update 改
   1、在可视化界面输入：

   ```
   update 数据库表名 set `password`=`1234` where   username = 'xiaoming';
   ```
   2、选中输入的代码，点击输入界面左上角的闪电符号运行代码

 * D -delete 删(一般不操作)
     1、在可视化界面输入：

  ```js
  delete from 数据库 where id = 1；
   //软删除，定义标记status为2即删除
  //右键表Alt Table 添加status默认值为1，需要删除时改变status为2 
  update users set status=2 where username ='xiaoming';
  select * from users where status =1;
  ```
​      2、选中输入的代码，点击输入界面左上角的闪电符号运行代码

##### Mysql在nodejs中使用
###### 下载安装Mysql

* 进入npm官网查询Mysql，查看下载量及更新时间，选择下载量最多，最新 ，使用Mysql2
* 在vscode中打开需要终端，运行npm init -y，初始化包文件，以保证下载的包文件会存在生产依赖中，再运行npm i mysql2，下载安装mysql

###### 操作

######  学习更多=>查看<https://www.npmjs.com/package/mysql2>文档

* 1.引入mysql

    ```
    const mysql = require('mysql2');
    ```

* 2.创建连接 （连接上本地的mysql服务）
    ```js
    const config = {
      host: 'localhost', // 域名
      port: 3306, // 端口号
      user: 'root', // 用户名
      password: 'root', // 密码
      database: 'test' // 数据库名称
    }
    const connection = mysql.createConnection(config);
    ```

* 3.对数据库进行操作
    ```js
    connection.query(
      //操作同mysql的CRUD操作一致
      `select * from users`,
      `insert into users(username, password) values ('xiaoming', 123)`,
      function (err, result, fileds) {
        /*
          err 就是nodejs错误优先机制，代表错误原因
          result 就是查询结果
          fields 表的列数据（一般用不上）
        */
        // console.log(err, result, fileds);
        if (!err) {
          console.log(result);
        } else {
          console.log(err);
        }
      }
    )
    ```

* 4.断开数据库连接

    ```
    connection.end(); //也可以在终端中ctrl+c进行断开
    ```
##### sequelize操作mysql
###### 下载安装sequelize包

* 在vscode中打开需要终端，运行npm init -y，初始化包文件，以保证下载的包文件会存在生产依赖中，再运行npm install --save sequelize，下载安装sequelize
######  操作

>中文文档： https://github.com/demopark/sequelize-docs-Zh-CN
>getting-strated(入门操作)：https://github.com/demopark/sequelize-docs-Zh-CN/blob/master/getting-started.md
* 1.引入sequelize

    ```
    const Sequelize = require('sequelize');
    ```
* 2.创建实例对象：连接数据库

  ```js
  const sequelize = new Sequelize('test', 'root', 'root', {
      //第一个参数标识数据库名，第二三个参数表示数据库账号和密码
      host: 'localhost',
      dialect: 'mysql'    // 要连接数据库
    })
  ```
* 3.测试连接

    ```js
     sequelize
        .authenticate()
        .then(() => {
            console.log('连接成功');
         })
        .catch(err => {
            console.error('连接失败:', err);
       });
    ```
* 4.通过实例对象，创建表
    ```js
    // sequelize会默认给表添加 createdAt updatedAt
    const Article = sequelize.define('article', {
    // 第一个参数是创建表的名字，最终创建的表是复数形式
    // 第一个参数是对象，表中列数据
      title: {
        type: Sequelize.STRING, // 类型是字符串
        allowNull: false, // 非空
      },
      content: {
        type: Sequelize.STRING, // 类型是字符串
        allowNull: false, // 非空
      },
      userId: {
        type: Sequelize.INTEGER,
      }
    });
    ```
* 5.检查表创建是否成功（执行同步）   

    ```js
    // force: true：如果数据库存在Article表，会强制删除，再创建
    // 此方法只能执行一次，创建完表后就没有用途了
    Article.sync({
        force: true
      })
      .then(() => {
        console.log('创建成功');
      })
      .catch(err => {
        console.error('创建失败:', err);
      }); 
    //可在mysql可视化界面中，右键refresh All 更新数据，查看表是否创建成功
    ```
* 6.操作数据

    ```js
     !(async () => {
        // 创建一条文章数据
        const result = await Article.create({
            title: '标题444',
            content: '内容444',
            userId: 4
        })
        // 查询一条数据
        const result = await Article.findOne();
        // 查询所有数据
        const result = await Article.findAll({
          // 查询条件
          where: {
              userId: 1
           },
           // 排序，倒序
           order: [
             ['id', 'DESC']
           ],
           // 限制查找的数量
           limit: 2,
           // 从第几条开始查找
           offset: 2,
           // 只查找指定列的数据
           attributes: [
            'title', 'content'
           ]
         });
        //查询其中每一条数据，使用map方法
        console.log(result.map((article) => {
            return article.dataValues; //返回创建的数据
        }));
         //修改数据
         const result = await Article.update({
              title: '标题222'
         }, {
          where: {
            title: '标题111'
           }
         })
        console.log(result);
     })()
    ```
#### mysql的联表查询  
##### 在mysql中操作
* 1.打开mysql Workbench(mysql可视化界面)

* 2.选择数据库中需要联表查询的表单，右键选择Alter Table，进入表单Table界面

* 3.选择表单Table界面下方的Foreign Keys进行外接，在Foreign Keys Name中输入外接的表内需要连接的名称，Referenced Table中选择需要外接的表单

* 4.在选择表单Table界面右侧的Column中选择当前表单的字段，在Referenced Column中选择需要关联表单的字段(注意：关联的字段的Datatype类型需要一致否则无效)

* 5.在选择表单Table界面最右侧的Foreign Key Options,选择CASCADE（表单当前表单更新/删除，关联表单也更新/删除）

* 6.点击Apply完成操作

    ![1576497639(1)](/1576497639(1).png)

* 7.在可视化界面输入，以下代码检查联表查询

    ```js
    use test;   
    select * from users;
    select * from articles;
    select * from articles where title='标题111' ;
    -- 联表查询
    -- inner join users 将users表加入一起查询
    -- on (users.id = articles.userId) 
    select * from articles inner join users on (users.id = articles.userId) where title='标题111' ;
    -- 查询需要的内容
    select articles.id, articles.title, articles.content, users.username from articles 
    inner join users on (users.id = articles.userId) where title='标题111' ;
    ```
##### 使用sequelize进行联表查询
* 1.在vscode中引入sequelize包

    ```
    const Sequelize = require('sequelize');
    ```
* 2.创建连接
  ```js
  const sequelize = new Sequelize('test', 'root', 'root', {
      host: 'localhost',
      dialect: 'mysql',
       // 一般线上环境使用，连接池
      pool: {     // 创建连接池
        max: 5,   // 最大5个连接
        min: 0,   // 最小
        acquire: 30000,   // 如果报错超过30s，就会重新连接
        idle: 10000 // 如果10s连接没有使用，就会自动断开连接
        }
    })
  ```
* 3.通过 sequelize 创建表

    ```js
    const Article = sequelize.define('article', {
      title: {
        type: Sequelize.STRING,
        allowNull: false     //非空
      },
      content: {
        type: Sequelize.STRING,
        allowNull: false
      },
      userId: {
        type: Sequelize.INTEGER
      }
    })
    //第二张表
    const User = sequelize.define('user', {
      username: {
        type: Sequelize.STRING,
        allowNull: false
      },
      password: {
        type: Sequelize.STRING,
        allowNull: false
      }
    })
    ```
* 4.建立联系

    ```js
    // Article属于User --> 能通过Article查找User
    Article.belongsTo(User, {
        // 设置外键 Article.userId --> User.id
        foreignKey: 'userId'
    });
    // User拥有Article --> 能通过User查找Article
    User.hasOne(Article, {
        foreignKey: 'userId'
    })
    ```
* 5.创建表(会删除之前表，创建新表) --> 会删除之前所有数据
    ```js
    Article.sync({
      force: true
    })
        .then(() => {
            console.log('Article创建成功');
        })
        .catch((err) => {
            console.log('Article创建失败', err);
        });
    
    User.sync({
          force: true
    })
        .then(() => {
            console.log('User创建成功');
        })
        .catch((err) => {
            console.log('User创建失败', err);
        }) 
    ```
* 6.对表进行操作
    ```js
    !(async () => {
      // 创建表数据(在数据库user中创建xiaoming用户的表内容)
      const user1 = await User.create({
            username: 'xiaoming',
            password: 123
      })
      const user1Id = user1.dataValues.id;
      // 创建表数据(在数据库user中创建laoli用户的表内容)
      const user2 = await User.create({
            username: 'laoli',
            password: 123
      })
      const user2Id = user2.dataValues.id;
      //创建表数据(在数据库Article中创建四个文章表内容）
      await Article.create({
        title: '标题111',
        content: '内容111',
        userId: user1Id
      })
      await Article.create({
        title: '标题222',
        content: '内容222',
        userId: user1Id
      })
      await Article.create({
        title: '标题333',
        content: '内容333',
        userId: user2Id
      })
      await Article.create({
        title: '标题444',
        content: '内容444',
        userId: user2Id
      })
    ```
* 7.联表查询
  ```js
  // 当步骤4为:Article属于User --> 能通过Article查找User
  //    Article.belongsTo(User, {
          // 设置外键 Article.userId --> User.id
  //        foreignKey: 'userId'
  //    });
  
  //联表查询
  const result = await Article.findAll({
    attributes: [
      'title',
      'content',
    ],
    where: {
      title: '标题111'
    },
    // 关联user，一起查找
    include: [{
      model: User,
      attributes: ['username'],
    }]
  }) 
  console.log(result.map((article) => {
    let obj = {};
    obj.article = article.dataValues;
    obj.user = article.dataValues.user.dataValues;
    delete article.dataValues.user;
    return obj;
  })); 
  })()   //对表进行操作的结束符
  ```

    ```js
    //当步骤4为：User拥有Article --> 能通过User查找Article
    //    User.hasOne(Article, {
    //        foreignKey: 'userId'
    //    })
  
    //联表查询
    const result = await User.findAll({
          attributes: [
            'username',
          ],
          where: {
            id: '1'
          },
          include: [{
            model: Article,
            attributes: ['title', 'content'],
          }]
        })
        console.log(result.map((user) => {
            const userData = user.dataValues
            userData.article = userData.article.dataValues;
            return userData;
        }));
      })()  //对表进行操作的结束符
    ```

## http协议
#### http协议是什么
协议是指计算机通信网络中两台计算机之间进行通信所必须共同遵守的规定或规则。
HTTP（hypertext transport protocol）协议也叫超文本传输协议，是一种基于TCP/IP的应用层通信协议，这个协议详细规定了浏览器和万维网服务器之间互相通信的规则。
客户端与服务端通信时传输的内容我们称之为报文。
HTTP就是一个通信规则，这个规则规定了客户端发送给服务器的报文格式，也规定了服务器发送给客户端的报文格式。客户端发送给服务器的称为“请求报文”，服务器发送给客户端的称为“响应报文”。

* 一个超文本传输协议(基于TCP/IP协议位于应用层协议)

* 作用：用来规定客户端和服务端通信的规则  

* 通信的具体内容，称为报文

 * 请求报文
   * 请求方式：GET/POST/PUT/DELETE/OPTIONS       
   >#### 常见的get和post请求方式
   >
   >GET请求：
   >①浏览器输入地址发送请求 
   >②html 所有标签都是 GET 请求 
   >③form 表单可以发送 GET/POST 请求
   >POST请求：除了form表单/ajax 以外，其他请求默认都是 GET 请求
   >
   >####  get/post请求的区别
   >
   >①请求参数位置不一样
   >    GET请求请求参数（查询字符串参数）位于 请求首行（地址栏可见）
   >    POST请求请求参数(请求体参数)位于 请求主体(地址栏不可见)
   >②安全性不一样
   >    GET请求较低(参数地址栏可见)
   >    POST请求相对较高(参数地址栏不可见)
   >③GET请求默认被浏览器缓存起来(第二次会走缓存)
   >    POST请求默认不被缓存
   >④请求参数的长度不一样（过去有，现代浏览器没有这个区别）
   >    GET请求请求参数位于请求首行，而浏览器对地址栏输入地址长度是有限制的，长度有限
   >    POST请求参数位于请求体。理论上长度无限
   >结论：
   >    如果要传输敏感数据（如：用户名/密码、用户信息..），一般使用POST
   >    如果传输不是敏感数据，就用GET  
    * 内容类型：

      * text/html

      * text/css

      * application/javascript

      * application/json

      * applicaion/x-www-form-urlencoded       

* 响应报文

    * 响应状态码
      * 1xx 请求还需要进一步处理（请求未完成）
      * 2xx 请求成功 200
      * 3xx 请求重定向 301 302 304
      *  4xx 客户端错误 401 403 404
      *  5xx 服务端错误 500
```js
//简单的服务器
const http = require('http');

const server = http.createServer((request, response) => {

  response.setHeader('Content-Type', 'application/json;charset=utf-8');

  response.end(JSON.stringify({ title: 'aaa', content: 'bbb' }));

});

server.listen(3000, err => {

if (!err) console.log('服务器启动成功：http://localhost:3000');

else console.log(err);

});
```
#### fidder工具
  Fiddler是一个http协议调试代理工具，使用它我们可以抓取网页的所有请求与响应，也就是咱们俗称的抓包
* 使用

    * 打开软件，点击Capturing自动抓取包

    * 运行服务器，在Fiddler工具中找到抓取的内容，点击，查看右侧的第二行的Inspectors及第三行的Raw和下侧的Raw

    * 第三行的Raw的内容为请求报文，下侧的Raw为响应报文

    ```js
    //请求报文内容
    GET http://localhost:3000/ HTTP/1.1
    Host: localhost:3000
    Connection: keep-alive
    Upgrade-Insecure-Requests: 1
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.70 Safari/537.36
    Sec-Fetch-User: ?1
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,\_/\_;q=0.8,application/signed-exchange;v=b3
    Sec-Fetch-Site: none
    Sec-Fetch-Mode: navigat
    Accept-Encoding: gzip, deflate, br
    Accept-Language: zh-CN,zh;q=0.9   Cookie: weibo.sid=x90B5ZEA0757pugF0fPVL2bYEbkZrslS; weibo.sid.sig=umGVwHzgpSeaamtCEHJPBfvhs2o
     请求报文组成
    1. 报文首行
       GET http://localhost:3000/ HTTP/1.1
       ① GET 请求方式/类型 GET(查)/POST(增)/PUT(改)/DELETE(删)/OPTIONS
       ② 最常用的 GET POST
       http://localhost:3000/ 请求地址
       HTTP/1.1 协议名/版本号
    2. 报文头部
       Host: localhost:3000    //服务器主机名端口号
       Connection: keep-alive   //保持长（持续）连接
       Upgrade-Insecure-Requests: 1  // 允许使用 https 协议
        User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.70 Safari/537.36   //用户代理：浏览器内核信息
        Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,\_/\_;q=0.8,application/signed-exchange;v=b3  //浏览器能够接受的文件（数据）类型
        text/html     //html文件类型
        application/javascript    //js文件类型
        text/css     //样式文件类型
        image/webp image/png image/jpg ...  //图片文件类型
        application/json      //json数据类型
        application/x-www-form-urlencoded   //采用 form 表单传输数据的类型
        application/xml;q=0.9    //代表前面这个类型优先级=0.9
        Accept-Encoding: gzip, deflate, br   //浏览器接受的文件压缩格式
        Accept-Language: zh-CN,zh;q=0.9      //浏览器接受的语言
     3. 空行
        隔开报文主体   
        ......    //此处空行
     4. 报文主体
       POST 请求参数。。   Cookie: weibo.sid=x90B5ZEA0757pugF0fPVL2bYEbkZrslS; weibo.sid.sig=umGVwHzgpSeaamtCEHJPBfvhs2o    //会话控制的方案
        //不重要的
        Sec-Fetch-User: ?1
        Sec-Fetch-Site: none
        Sec-Fetch-Mode: navigate
    
        ````
         //响应报文内容
            HTTP/1.1 200 OK
            Content-Type: text/plain;charset=utf-8
            Date: Mon, 16 Dec 2019 02:29:29 GMT
            Connection: keep-alive
            Content-Length: 30
    
            http 服务器返回了响应~~
        响应报文的组成
        1.报文首行
            HTTP/1.1 200 OK   //协议名/版本号 响应状态码
                1xx 代表请求还需要进一步处理（请求处理中..）
                2xx 代表请求成功（响应成功） 200
                3xx 代表请求重定向（请求资源我这里没有，去其他服务器找）
                    301 请求重定向，永久重定向
                    302 请求重定向，临时重定向
                    304 请求重定向到缓存中(协商缓存)
                4xx 代表客户端错误
                    404 资源找不到
                    401 没有权限访问该资源
                    403 禁止访问
                5xx 代表服务端错误
                    500 服务器内部错误
        2. 报文头部
             Content-Type: text/plain;charset=utf-8  //内容类型：（浏览器接收到，就会对应解析）
            Date: Mon, 16 Dec 2019 02:29:29 GMT    //响应时间
            Connection: keep-alive
            Content-Length: 30     //报文体长度（字节）
        3. 空行     //隔开报文主体   
            ......    //此处空行
        4. 报文主体     //服务器响应的数据
             http服务器返回了响应~~
    ```

#### 案例：通过服务器访问html页面
````js
//方案1：直接将html返回响应

const http = require('http');  //引入http

const server = http.createSearver((req,res)=>{

  res.setHeader('Content-Type', 'text/html');
  //通过res.end() 快速返回响应
  res.end(`<!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>练习</title>
  </head>
  <body>
    <h1>服务器练习页面</h1>
  </body>
  </html>`); 
})

server.listen(3000,err =>{
    if(!err) console('服务器启动成功：http://localhost:3000');
    else console.log(err);
})
````
```js
//方案2：使用fs模块

//在当前文件夹新建public文件夹存放index.html

const http = require('http');
const fs = require('fs');

const server = http.createSearver((req,res)=>{
    res.setHeader('Content-Type', 'text/html');
    /*fs.readFile('./public/index.html', (err, data) => {
        if (!err) {
        // 将读取内容给响应返回
            res.end(data);
        } else {
            console.log(err);
        }
    /*
    //fs的流式读取更方便简洁
    const rs = fs.createReadStream('./public/index.html')
    rs.pipe(res);
    */
    })

 server.listen(3000,err =>{
    if(!err) console('服务器启动成功：http://localhost:3000');
    else console.log(err);
})
```
#### 案例：通过服务器访问html、css、js
```js
//在当前文件夹新建public文件夹存放html、css、js

const http = require('http');
const fs = require('fs');

const server = http.createSearver((req,res)=>{
    // 请求路径
    const url = req.url;
    
    if (url === '/') {
        // 返回html页面
        res.setHeader('Content-Type', 'text/html');
        const rs = fs.createReadStream('./public/index.html');
        rs.pipe(res);
  } elseif (url === '/css/index.css') {
        // 返回css文件
        res.setHeader('Content-Type', 'text/css');
        const rs = fs.createReadStream('./public/css/index.css');
        rs.pipe(res);
  } elseif (url === '/favicon.ico') {
        // 返回网站小图标
        res.setHeader('Content-Type', 'image/x-icon');
        const rs = fs.createReadStream('./public/favicon.ico');
        rs.pipe(res);
  } elseif (url === '/js/index.js') {
// 返回js文件
        res.setHeader('Content-Type', 'application/javascript');
        const rs = fs.createReadStream('./public/js/index.js');
        rs.pipe(res);
  }
})

 server.listen(3000,err =>{
    if(!err) console('服务器启动成功：http://localhost:3000');
    else console.log(err);
})
```
## express

Express 是一个基于 Node.js 平台的极简、灵活的 web 应用开发框架，它提供一系列强大的特性，帮助你快速创建各种 Web 和移动设备应用
简单来说Express就是运行在node中的用来搭建服务器的模块。
#### 下载：
* npm i express --save   安装express并添加到依赖项 
#### 使用
```
//引入express
const express = require('express');
//创建app应用对象（express的方法都在应用对象上）
const app = express();
//设置路由
//get代表接收一个get请求，'/' 代表请求的地址/路径
app.get('/',(req,res)=>{
    /*
    //较为麻烦，还需设置文件类型，可直接通过res.send()操作
    res.set('Content-Type','text/html;charset=utf-8');
    res.end('express服务器返回的响应')；
    */
    res.send('express服务器返回的响应');
})
//输入 http://localhost:3000/aaa 会返回一个aaa响应
app.get('/aaa',(req,res)=>{
    res.send('aaa');
})
//监听端口号 启动服务
app.listen(3000,err=>{
    if(!err) console.log('服务器启动成功：http://localhost:3000');
    else console.log(err);
})

```
#### 路由route

###### 学习更多访问：express中文网=>API参考手册（<http://www.expressjs.com.cn/4x/api.html>)

* 是什么route？
    路由是指如何定义应用的端点（URIs）以及如何响应客户端的请求。
    路由是由一个 URI、HTTP 请求（GET、POST等）和若干个句柄组成的。

    * 一个定义请求地址、接受请求、返回响应的方式

    * 一种key/value映射关系

* 路由的组成：

    * 请求方式:    GET/POST/PUT/DELETE/OPTIONS      

 * 请求路径
   * 一对一     '/'  根路径 --> http://localhost:3000/
    ```
    '/css/index.css' ==> http://localhost:3000/css/index.css
    ```
   * 一对多     '/xxx/:id'
    ```
    '/post/:id' ==> http://localhost:3000/post/123456  http://localhost:3000/post/abcd ...
    ```

 * 回调函数(句柄函数 / 钩子函数)：用来处理请求、返回响应

    * request（请求对象：客户端给服务器）

      * req.url 获取请求路径

        ```
        '/'
        /css/index.css
        ```

      * req.headers 获取请求头信息(请求报文头部) 

      * req.params 获取地址栏(报文首行)的params参数

        ```
        GET http://localhost:3000/
        ```

      * req.query 获取GET请求的查询字符串参数

      * req.body 获取POST请求的请求体的参数（默认情况下，express框架不解析请求体数据，所以获取永远undefined）

    * response(响应对象: 服务器给客户端)
      返回响应：（以下方法只能使用一个，不能同时返回两次响应）

      * res.end() 快速返回响应(响应不做任何处理，直接返回)
      * res.send() 根据响应的内容，设置响应头Content-type字段，在返回响应
      * res.json() 将响应的内容转换成json数据返回
      * res.sendFile() 返回文件(绝对路径)，客户端会打开显示
      * res.download() 返回文件，客户端会自动下载成文件
      * res.redirect() 请求重定向到新的网址
      * res.set() 设置响应头   

```js
    // 引入express
    const express = require('express');

    const path = require('path');
    app.get('/', (req, res) \=> {

    // res.set('Content-Type', 'text/html;charset=utf-8');
    // res.end('express服务器返回的响应');
    // console.log(req.url); // /?username=jack&age=18
    // console.log(req.query); // { username: 'jack', age: '18' }
    // console.log(req.headers);
    // res.send('express服务器返回的响应!!!');
    // res.json({
    //   name: 'xiaoming',
    //   age: 40
    // })
    // const filepath = path.resolve(\_\_dirname, './public/index.html');
    // res.sendFile(filepath);
    // res.download(filepath);
      res.redirect('http://www.baidu.com');
    });

    app.get('/post/:id', (req, res) \=> {
    // 获取id  --> 请求params参数
      console.log(req.params); // { id: '123456879' }
      res.send('id');
    });

    // 监听端口号 启动服务
    app.listen(3000, err \=> {
        if (!err) console.log('服务器启动成功：http://localhost:3000');
        else console.log(err);
    });
```
#### 中间件middleware
* 中间件是什么？ 
   * 中间件（Middleware）是一个函数，它可以访问请求对象（request）, 响应对象（response）和 web 应用中处于请求-响应循环流程中的中间件，一般被命名为 next 的变量。
* 组成：
   * request 和Route的req一模一样。 请求对象
   * response 和Route的res一模一样。 响应对象
   * next 调用堆栈中的下一个中间件 
* 中间件默认能接受处理所有请求
* 一次请求默认只能触发一个中间件函数  
* 服务器执行流程：route和middleware
   * 首先，服务器启动时，会用数组收集所有的路由和中间件[route, middleware...]
   * 当有请求访问服务器时，服务器就会遍历数组来处理请求、返回响应
   * 先取出第一个
       * 如果是路由, 看请求方式和请求路径是否完全匹配，如果匹配上就执行回调函数，请求就到此终止（后面的就不执行了），如果有一个不匹配，就看下一个函数
       * 如果是中间件，就立即执行中间件回调函数，如果内部调用了next方法，就执行下一个，如果没有，请求到此终止（后面的就不执行了）
       * 如果都没有匹配上呢？ 返回 404   Cannot GET /aaa
```js
const express = require('express');
const app = express

// 中间件能接受处理所有请求
app.use((req, res, next) => {
  console.log(111);
  // 一般next放最后调用的
  next();  // 调用下一个中间件函数
  next();// 重复调用失效
  console.log(222);
});

app.use((req, res, next) => {
  console.log(333);
  next(); // 调用下一个中间件函数
  console.log(444);
});

app.use((req, res, next) => {
  console.log(555);
  res.send('这是中间件返回响应');
}); 

//服务端输出 111 333 555 444 222
//客户端响应 这是中间件返回响应
  
app.use((req, res, next) => {
    // 路由公共代码放进去
  next();
});

app.get('/login', (req, res) => {
  res.send('路由返回响应');
});

app.get('/register', (req, res) => {
  res.send('路由返回响应');
});

app.listen(3000, err => {
    if (!err) console.log('服务器启动成功：http://localhost:3000');
    else console.log(err);
});
```
* 作用：提取路由的公共代码，用来复用
* 中间件应用：
   * 内置中间件：express框架内置的中间件。
     * express.urlencoded() 解析POST请求体数据
       * 解析form表单提交的参数
       * content-type：applicaion/x-www-form-urlencoded
     * express.json() 用来解析POST请求体参数
       * 解析json数据
       * content-type：applicaion/json                
     * express.static() 向外暴露服务器的静态资源
   * 应用级中间件：用户自己开发的中间件,用来复用代码
   * 第三方中间件：社区开发者开发的中间件
       * cookie-parser
   * 路由器中间件：分类管理route
       * express.Router
   * 错误处理中间件 处理错误
     * app.use((err, req, res, next) => {})
```js
//内置中间件
const express = require('express');
const app = express();

// 用来解析POST请求体数据
app.use(express.urlencoded({ extended: true }));

app.post('/', (req, res) => {  //需创建from表单进行post请求
  console.log(req.body); // 获取请求体参数  { username: 'xiaoming', password: '133' }
  res.send('服务器返回响应~');
});

app.listen(3000, err => {
    if (!err) console.log('服务器启动成功：http://localhost:3000');
    else console.log(err);
});
```
```js
// from表单HTML
<!DOCTYPEhtml>
<html lang="en">
    <head>
        <meta charset="UTF-8>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>form</title>
    </head>
    <body>
        <form action="http://localhost:3000" method="POST">
            用户名: <input type="text" name="username">
            密码: <input type="password" name="password">
            <input type="submit">
        </form>
    </body>
</html>

//打开页面输入表单请求，客户端响应 服务器返回响应~，服务器返回 请求体参数  { username: 'xiaoming', password: '133' }
```
#### 案例：通过中间件访问html、css、js
```js
//在当前文件夹新建public文件夹存放html、css、js
//通过内置中间件的express.static()方法向外暴露服务器的静态资源
const express = require('express');
const app = express();

// 将 public 文件夹下面所有向外暴露出去
app.use(express.static('public'));

app.listen(3000,err =>{
    if(!err) console('服务器启动成功：http://localhost:3000');
    else console.log(err);
})
//可以输入http://localhost:3000/index.html运行
```

#### 案例：登录注册
* 前端：登录注册页面
* 服务器：路由
```js
 <!--登录界面 在新建文件夹public中创建login.html文件-->
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>登录</title>
</head>

<body>
  <h1>登录</h1>
  <!-- 
    action 请求地址/路径 
    method 请求方式
   -->
  <form action="http://localhost:3000/login" method="POST">
    用户名: <input type="text" name="username"> <br>
    密码: <input type="password" name="password"> <br>
    <input type="submit" value="登录">
  </form>
</body>

</html>
```
```js
<!--注册界面 在新建文件夹public中创建register.html文件-->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>注册</title>
</head>
<body>
  <h1>注册</h1>
  <!-- 
    action 请求地址/路径 
    method 请求方式
   -->
  <form action="http://localhost:3000/register" method="POST">
    用户名: <input type="text" name="username"> <br>
    密码: <input type="password" name="password"> <br>
    确认密码: <input type="password" name="rePassword"> <br>
    手机号: <input type="text" name="phone"> <br>
    <input type="submit" value="注册">
  </form>
</body>
</html>
```
```js
/*
    //服务器 server.js
    const express = require('express');
    const User = require('./db/model/user');

    const app = express();
    // 内置中间件：用来解析POST请求体参数
    app.use(express.urlencoded({ extended: true }));
    
    //服务器接受登录请求 
    app.post('/login', async (req, res) => {
      // 1. 获取用户提交的表单数据
      const { username, password } = req.body;
      // 2. 表单校验
      const usernameReg = /^\w{5,15}$/; // 只能是英文、数字、下划线，长度为 5 - 15
      const passwordReg = /^\w{5,15}$/; // 只能是英文、数字、下划线，长度为 5 - 20

      if (!usernameReg.test(username)) {
        // 用户名校验失败 - 提示错误
        res.send('用户名不符合规范，只能是英文、数字、下划线，长度为 5 - 15');
        return;
      }

      if (!passwordReg.test(password)) {
        // 密码校验失败 - 提示错误
        res.send('密码不符合规范，只能是英文、数字、下划线，长度为 5 - 20');
        return;
      }
      try {
        // 3. 去数据库中查询用户是否存在
        const user = await User.findOne({
          attributes: ['username', 'password'],
          where: {
            username
          }
        });

        if (!user) {
          res.send('用户名不存在');
          return;
        }
        // 4. 判断密码是否正确
        if (user.dataValues.password === password) {
          res.send('登录成功');
        } else {
          res.send('密码错误');
        }
      } catch (e) {
        console.log(e);
        res.send('网络异常，登录失败');
      }
    });
    /*
      服务器接受注册请求
    */
    app.post('/register', async (req, res) => {
      // 1. 获取用户提交的表单数据
      // console.log(req.body); // 默认请求体不解析
      const { username, password, rePassword, phone } = req.body;
      /*
        {
          username: 'laofu',
          password: '123',
          rePassword: '123',
          phone: '1111111111111'
        }
      */
      // 2. 对用户的数据进行正则校验
      // 创建正则规则
      const usernameReg = /^\w{5,15}$/; // 只能是英文、数字、下划线，长度为 5 - 15
      const passwordReg = /^\w{5,15}$/; // 只能是英文、数字、下划线，长度为 5 - 20
      const phoneReg = /^(13[0-9]|15[012356789]|166|17[3678]|18[0-9]|14[57])[0-9]{8}$/;

      if (!usernameReg.test(username)) {
        // 用户名校验失败 - 提示错误
        res.send('用户名不符合规范，只能是英文、数字、下划线，长度为 5 - 15');
        return;
      }

      if (!passwordReg.test(password)) {
        // 密码校验失败 - 提示错误
        res.send('密码不符合规范，只能是英文、数字、下划线，长度为 5 - 20');
        return;
      }

      if (!phoneReg.test(phone)) {
        // 手机校验失败 - 提示错误
        res.send('手机不符合规范');
        return;
      }

      // 3. 密码和确认密码的校验
      if (password !== rePassword) {
        res.send('两次输入密码不一致，请重新输入');
        return;
      }

      // 凡是异步代码都可能出错，在async函数中一旦出错就会退出函数
      // 导致客户端没有接受到响应，一直转
      // 这样不好，希望即是出错，也要返回一个错误响应

      try {
        // 4. 判断用户名是否已存在
        const user = await User.findOne({
          attributes: ['username'],
          where: {
            // 对象的简写
            username
          }
        });
        /*
          找到了，返回值 { dataValues }
          没有找到, 返回值 null
        */
        if (user) {
          // 找到了
          res.send('用户名已存在');
          return;
        }
        // 5. 将用户数据存储到数据库中
        const result = await User.create({
          username,
          password,
          phone
        });
        console.log(result);
        // 6. 返回响应：注册成功
        res.send('注册成功');
      } catch (e) {
        console.log(e);
        // 说明以上异步代码出错了
        res.send('网络异常，注册失败');
      }
    });

    app.listen(3000, err => {
      if (!err) console.log('服务器启动成功: http://localhost:3000');
      else console.log(err);
    });
*/


//优化-使用中间件复用代码
const express = require('express');
const User = require('./db/model/user');

const app = express();

// 内置中间件：用来解析POST请求体参数
app.use(express.urlencoded({ extended: true }));

// 使用中间件复用代码 --> 应用级中间件
app.use((req, res, next) => {
  // 下面路由公共代码提取

  const { username, password, rePassword, phone } = req.body;
  // 创建正则规则
  const usernameReg = /^\w{5,15}$/; // 只能是英文、数字、下划线，长度为 5 - 15
  const passwordReg = /^\w{5,15}$/; // 只能是英文、数字、下划线，长度为 5 - 20
  const phoneReg = /^(13[0-9]|15[012356789]|166|17[3678]|18[0-9]|14[57])[0-9]{8}$/;

  // 判断请求是登录/注册
  const isRegister = req.url === '/register';

  if (!usernameReg.test(username)) {
    // 用户名校验失败 - 提示错误
    res.send('用户名不符合规范，只能是英文、数字、下划线，长度为 5 - 15');
    return;
  }

  if (!passwordReg.test(password)) {
    // 密码校验失败 - 提示错误
    res.send('密码不符合规范，只能是英文、数字、下划线，长度为 5 - 20');
    return;
  }

  if (isRegister && !phoneReg.test(phone)) {
    // 手机校验失败 - 提示错误
    res.send('手机不符合规范');
    return;
  }

  // 3. 密码和确认密码的校验
  if (isRegister && password !== rePassword) {
    res.send('两次输入密码不一致，请重新输入');
    return;
  }

  next();
});

/*
  服务器接受登录请求
*/
app.post('/login', async (req, res) => {
  // 1. 获取用户提交的表单数据
  const { username, password } = req.body;

  try {
    // 3. 去数据库中查询用户是否存在
    const user = await User.findOne({
      attributes: ['username', 'password'],
      where: {
        username
      }
    });

    if (!user) {
      res.send('用户名不存在');
      return;
    }
    // 4. 判断密码是否正确
    if (user.dataValues.password === password) {
      res.send('登录成功');
    } else {
      res.send('密码错误');
    }
  } catch (e) {
    console.log(e);
    res.send('网络异常，登录失败');
  }
});
/*
  服务器接受注册请求
*/
app.post('/register', async (req, res) => {
  // 1. 获取用户提交的表单数据
  const { username, password, phone } = req.body;

  // 凡是异步代码都可能出错，在async函数中一旦出错就会退出函数
  // 导致客户端没有接受到响应，一直转
  // 这样不好，希望即是出错，也要返回一个错误响应

  try {
    // 4. 判断用户名是否已存在
    const user = await User.findOne({
      attributes: ['username'],
      where: {
        // 对象的简写
        username
      }
    });
    /*
      找到了，返回值 { dataValues }
      没有找到, 返回值 null
    */
    if (user) {
      // 找到了
      res.send('用户名已存在');
      return;
    }
    // 5. 将用户数据存储到数据库中
    const result = await User.create({
      username,
      password,
      phone
    });
    console.log(result);
    // 6. 返回响应：注册成功
    res.send('注册成功');
  } catch (e) {
    console.log(e);
    // 说明以上异步代码出错了
    res.send('网络异常，注册失败');
  }
});

app.listen(3000, err => {
  if (!err) console.log('服务器启动成功: http://localhost:3000');
  else console.log(err);
});

```
```js
/*
//数据库 需在创建文件夹db(datebase)中创建文件sequelize.js

// 引入
const Sequelize = require('sequelize');

// 创建连接
// Sequelize不能创建数据库。所以需要我们手动在图形化界面（workbentch）创建数据库
const sequelize = new Sequelize('exec', 'root', 'root', {
  host: 'localhost',
  dialect: 'mysql'
});

// 测试连接
// 只要测试一次即可
sequelize
  .authenticate()
  .then(() => {
    console.log('连接成功');
  })
  .catch(() => {
    console.log('连接失败');
  });

/ 定义表
const User = sequelize.define('user', {
  username: {
    type: Sequelize.STRING, // 字符串类型
    allowNull: false, // 非空
    unique: true // 唯一的
  },
  password: {
    type: Sequelize.STRING, // 字符串类型
    allowNull: false // 非空
  },
  phone: {
    type: Sequelize.STRING,
    allowNull: false // 非空
  }
});

// 执行同步，才会真正创建表
// 会将sequelize定义的表全部创建（将上一个表删除，再重新创建）
// 此方法只能执行一次，创建完表后就没有用途了~
sequelize
  .sync({ force: true })
  .then(() => {
    console.log('执行同步成功');
  })
  .catch(() => {
    console.log('执行同步失败');
  });
*/

//优化-模块化
/*因为测试连接和执行同步只执行一次，因此将上面的数据库文件进行模块化
把只执行一次的代码单独抽取出来生成一个单独的模块
1.在已创建的db(datebase)文件夹中创建文件synic.js
因为synic.js文件中需要使用到sequelize对象，因此需在sequelize将sequelize暴露出(module.exports = sequelize;),synic.js文件中需引入sequelize
*/
// 引入  由于sequelize模块是自定义的，因此在引入时需在前加 ./
const sequelize = require('./sequelize');

// 将表的定义引入 -- 就会加载里面代码 
require('./model/user');

// 测试连接
// 只要测试一次即可
sequelize
  .authenticate()
  .then(() => {
    console.log('连接成功');
  })
  .catch(() => {
    console.log('连接失败');
  });

// 执行同步，才会真正创建表
// 会将sequelize定义的表全部创建（将上一个表删除，再重新创建）
// 此方法只能执行一次，创建完表后就没有用途了~
sequelize
  .sync({ force: true })
  .then(() => {
    console.log('执行同步成功');
  })
  .catch(() => {
    console.log('执行同步失败');
  });


/*
由于sequelize.js文件中的创建表可能会创建多个表，因此将创建表代码单独生成一个模块
2.在已创建的db(datebase)文件夹中创建文件model存储表，在model文件下创建表user.js
*/
// sequelize是通过npm下载的包
const Sequelize = require('sequelize');
// ../sequelize是我们自定义的包
const sequelize = require('../sequelize');

// 定义表
const User = sequelize.define('user', {
  username: {
    type: Sequelize.STRING, // 字符串类型
    allowNull: false, // 非空
    unique: true // 唯一的
  },
  password: {
    type: Sequelize.STRING, // 字符串类型
    allowNull: false // 非空
  },
  phone: {
    type: Sequelize.STRING,
    allowNull: false // 非空
  }
});

module.exports = User;
/*
3.最终db(datebase)文件夹中sequelize.js文件代码
*/
// 引入
const Sequelize = require('sequelize');

// 创建连接
// Sequelize不能创建数据库。所以需要我们手动在图形化界面（workbentch）创建数据库
const sequelize = new Sequelize('exec', 'root', 'root', {
  host: 'localhost',
  dialect: 'mysql'
});

// 将sequelize暴露出去
module.exports = sequelize;

/*4.最后node运行sync.js文件创建表
    node运行server.js文件启动服务器
    由于目前还不能进行服务器启动注册页面，因此需在vscode中打开register.html
    检查是否注册成功：在数据库中，可视化界面输入select * from users;
*/
```
## MVC

* 一种服务器常用的架构模式
   * M - Model 数据层(数据库)
   * V - View 视图层(页面)
   * C - Controller 控制层()

```
/*其中上面案例中的public即为view,
//新建controller文件
*/
```
```
完成单一职责、模块化功能

## 文件目录

- exec/ 项目根目录
  - ## 文件目录

- exec/ 项目根目录
  - controller/ 放置 通过数据库来生成最终返回响应的数据的 函数
    - user.js
  - db/ 放置数据库代码
    - model/ 放置数据库中表
      - user.js
    - sequelize.js
    - sync.js
  - middlewares/ 放置应用级中间件（复用路由的代码）
    - regVerify.js
  - model/ 放置 返回成功/失败数据 的类
    - user.js
  - services/ 放置 操作数据库 函数
    - user.js
  - views/ 放置 页面
    - login.html
    - register.html
  - server.js
  - db/ 放置数据库代码
    - model/ 放置数据库中表
      - user.js
    - sequelize.js
    - sync.js
  - middlewares/ 放置应用级中间件（复用路由的代码）
    - regVerify.js
  - model/ 放置 返回成功/失败数据 的类
    - user.js
  - routers/ 放置 登录/注册路由 函数
    - user.js
  - services/ 放置 操作数据库 函数
    - user.js
  - views/ 放置 页面
    - login.html
    - register.html
  - server.js

```
```
 //controller/user.js文件 放置通过数据库来生成最终返回响应的数据的函数
 /**
 * @description 通过操作数据库，生成要返回响应的数据（成功/失败）
 */
const { getUserInfo, addUser } = require('../services/user');
const { SuccessModal, ErrorModal } = require('../model');

// 一般 1/2参数直接写参数
const login = async (username, password) => {
  try {
    // 去数据库中查询用户是否存在
    const user = await getUserInfo(username);

    if (!user) {
      return new ErrorModal({
        errCode: 1,
        message: '用户名不存在'
      });
    }
    // 判断密码是否正确
    if (user.dataValues.password === password) {
      return new SuccessModal({
        errCode: 0,
        data: '登录成功'
      });
    } else {
      return new ErrorModal({
        errCode: 2,
        message: '密码错误'
      });
    }
  } catch (e) {
    console.log(e);
    return new ErrorModal({
      errCode: 3,
      message: '网络异常，登录失败'
    });
  }
};

// 3个参数以上写对象
const register = async ({ username, password, phone }) => {
  try {
    const user = await getUserInfo(username);

    if (user) {
      // 找到了
      return new ErrorModal({
        errCode: 4,
        message: '用户名已存在'
      });
    }

    await addUser({ username, password, phone });

    return new SuccessModal({
      errCode: 0,
      data: '注册成功'
    });
  } catch (e) {
    console.log(e);

    return new ErrorModal({
      errCode: 3,
      message: '网络异常，登录失败'
    });
  }
};

module.exports = {
  login,
  register
};

```
```
/*db/ 放置数据库代码
    - model/ 放置数据库中表
      - user.js
*/
/**
 * @description 定义user表
 */
// sequelize是通过npm下载的包
const Sequelize = require('sequelize');
// ../sequelize是我们自定义的包
const sequelize = require('../sequelize');

// 定义表
const User = sequelize.define('user', {
  username: {
    type: Sequelize.STRING, // 字符串类型
    allowNull: false, // 非空
    unique: true // 唯一的
  },
  password: {
    type: Sequelize.STRING, // 字符串类型
    allowNull: false // 非空
  },
  phone: {
    type: Sequelize.STRING,
    allowNull: false // 非空
  }
});

module.exports = User;




/*
- db/ 放置数据库代码
    - sequelize.js
*/
/**
 * @description 连接数据库
 */
// 引入
const Sequelize = require('sequelize');

// 创建连接
// Sequelize不能创建数据库。所以需要我们手动在图形化界面（workbentch）创建数据库
const sequelize = new Sequelize('exec', 'root', 'root', {
  host: 'localhost',
  dialect: 'mysql'
});

// 将sequelize暴露出去
module.exports = sequelize;



/*
- db/ 放置数据库代码
    - sync.js
*/
/**
 * @description 测试连接，创建表（只要一次）
 */
// 引入sequelize
const sequelize = require('./sequelize');

// 将表的定义引入 -- 就会加载里面代码
require('./model/user');

// 测试连接
// 只要测试一次即可
sequelize
  .authenticate()
  .then(() => {
    console.log('连接成功');
  })
  .catch(() => {
    console.log('连接失败');
  });

// 执行同步，才会真正创建表
// 会将sequelize定义的表全部创建（将上一个表删除，再重新创建）
// 此方法只能执行一次，创建完表后就没有用途了~
sequelize
  .sync({ force: true })
  .then(() => {
    console.log('执行同步成功');
  })
  .catch(() => {
    console.log('执行同步失败');
  });
```
```
/*
- middlewares/ 放置应用级中间件（复用路由的代码）
    - regVerify.js
*/
/**
 * @description 正则校验的中间件函数（应用级中间件）
 */

// 默认找模块时，如果模块名叫index.js，可以省略不写
const { ErrorModal } = require('../model');

function regVerify(req, res, next) {
  // 下面路由公共代码提取

  const { username, password, rePassword, phone } = req.body;
  // 创建正则规则
  const usernameReg = /^\w{5,15}$/; // 只能是英文、数字、下划线，长度为 5 - 15
  const passwordReg = /^\w{5,15}$/; // 只能是英文、数字、下划线，长度为 5 - 20
  const phoneReg = /^(13[0-9]|15[012356789]|166|17[3678]|18[0-9]|14[57])[0-9]{8}$/;

  // 判断请求是登录/注册
  const isRegister = req.url === '/register';

  // 定义错误对象
  const message = {};

  if (!usernameReg.test(username)) {
    // 用户名校验失败 - 提示错误
    message.usernameErr =
      '用户名不符合规范，只能是英文、数字、下划线，长度为 5 - 15';
  }

  if (!passwordReg.test(password)) {
    // 密码校验失败 - 提示错误
    message.passwordErr =
      '密码不符合规范，只能是英文、数字、下划线，长度为 5 - 20';
  }

  if (isRegister && !phoneReg.test(phone)) {
    // 手机校验失败 - 提示错误
    message.phoneErr = '手机不符合规范';
  }

  // 3. 密码和确认密码的校验
  if (isRegister && password !== rePassword) {
    message.rePasswordErr = '两次输入密码不一致，请重新输入';
  }

  const length = Object.keys(message).length;
  if (length) {
    // 有错误
    const err = new ErrorModal({
      errCode: 5,
      message
    });
    res.json(err);

    return;
  }

  next();
}

module.exports = regVerify;
```
```
/*
- model/ 放置 返回成功/失败数据 的类
    - user.js
*/
/**
 * @description 定义成功/失败响应的类
 */

class BaseModal {
  constructor({ errCode, data, message }) {
    /*
      errCode 错误代码： 成功：0  失败：1, 2 , 3 ...
      data 成功的数据
      message 失败的原因
    */
    this.errCode = errCode;

    if (data) {
      this.data = data;
    }

    if (message) {
      this.message = message;
    }
  }
}

class SuccessModal extends BaseModal {
  constructor({ errCode, data = {} }) {
    super({ errCode, data }); // 调用父类的constructor
  }
}

class ErrorModal extends BaseModal {
  constructor({ errCode, message = '' }) {
    super({ errCode, message }); // 调用父类的constructor
  }
}

module.exports = {
  SuccessModal,
  ErrorModal
};
```
```
/*
- model/ 放置 返回成功/失败数据 的类
    - user.js
*/
/**
 * @description 路由器中间件 - 封装登录/注册路由
 */
const express = require('express');
const { login, register } = require('../controller/user');
const regVerify = require('../middlewares/regVerify');

const Router = express.Router;
const userRouter = new Router();

// 使用中间件复用代码 --> 应用级中间件
userRouter.use(regVerify);
/*
  服务器接受登录请求
*/
userRouter.post('/login', async (req, res) => {
  const { username, password } = req.body;
  const result = await login(username, password);
  res.json(result);
});
/*
  服务器接受注册请求
*/
userRouter.post('/register', async (req, res) => {
  // 1. 获取用户提交的表单数据
  const { username, password, phone } = req.body;
  const result = await register({ username, password, phone });
  res.json(result);
});

module.exports = userRouter;
```
```
/*
- services/ 放置 操作数据库 函数
    - user.js
*/
/**
 * @description 定义操作数据库的方法
 */

const User = require('../db/model/user');

const getUserInfo = async username => {
  const user = await User.findOne({
    attributes: ['username', 'password'],
    where: {
      // 对象的简写
      username
    }
  });
  return user;
};

const addUser = async ({ username, password, phone }) => {
  const result = await User.create({
    username,
    password,
    phone
  });
  return result;
};

module.exports = {
  getUserInfo,
  addUser
}
```
```
/*
- views/ 放置 登录页面
    - login.html
*/
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>登录</title>
</head>

<body>
  <h1>登录</h1>
  <!-- 
    action 请求地址/路径 
    method 请求方式
   -->
  <form action="http://localhost:3000/login" method="POST">
    用户名: <input type="text" name="username"> <br>
    密码: <input type="password" name="password"> <br>
    <input type="submit" value="登录">
  </form>
</body>

</html>




/*
- views/ 放置 注册页面
    - register.html
*/
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>注册</title>
</head>

<body>
  <h1>注册</h1>
  <!-- 
    action 请求地址/路径 
    method 请求方式
   -->
  <form action="http://localhost:3000/register" method="POST">
    用户名: <input type="text" name="username"> <br>
    密码: <input type="password" name="password"> <br>
    确认密码: <input type="password" name="rePassword"> <br>
    手机号: <input type="text" name="phone"> <br>
    <input type="submit" value="注册">
  </form>
</body>

</html>
```
```
/*
- server.js
*/
/**
 * @description 主模块
 */
const express = require('express');
const userRouter = require('./routers/user');

const app = express();

// 内置中间件：用来解析POST请求体参数
app.use(express.urlencoded({ extended: true }));

// 应用 路由器中间件
app.use(userRouter);

app.listen(3000, err => {
  if (!err) console.log('服务器启动成功: http://localhost:3000');
  else console.log(err);
});
```
## 加密之md5 (与sha1类似)

* 一种消息摘要加密算法
  * 不可逆的方式加密（理论上通过密文没办法破解明文）
  * 同样的明文加密后输出同样的密文
* 在npm中查询md5查看文档

* 在node中下载md5(代码：npm i md5)

* 使用：md5(需要加密的内容)

```
/*
- services/ 放置 操作数据库 函数
    - user.js
*/
/**
 * @description 定义操作数据库的方法
 */
const md5 = require('md5');
const User = require('../db/model/user');

const getUserInfo = async username => {
  const user = await User.findOne({
    attributes: ['username', 'password'],
    where: {
      // 对象的简写
      username
    }
  });
  return user;
};

const addUser = async ({ username, password, phone }) => {
  const result = await User.create({
    username,
    password: md5(password), // 加密
    phone
  });
  return result;
};

module.exports = {
  getUserInfo,
  addUser
};



//controller/user.js文件 放置通过数据库来生成最终返回响应的数据的函数
/**
 * @description 通过操作数据库，生成要返回响应的数据（成功/失败）
 */
const md5 = require('md5');
const { getUserInfo, addUser } = require('../services/user');
const { SuccessModal, ErrorModal } = require('../model');

// 一般 1/2参数直接写参数
const login = async (username, password) => {
  try {
    // 去数据库中查询用户是否存在
    const user = await getUserInfo(username);

    if (!user) {
      return new ErrorModal({
        errCode: 1,
        message: '用户名不存在'
      });
    }
    // 判断密码是否正确
    // user.dataValues.password是数据库中密文
    // password是用户填写的明文
    // md5 同样的明文加密后输出同样的密文
    if (user.dataValues.password === md5(password)) {
      return new SuccessModal({
        errCode: 0,
        data: '登录成功'
      });
    } else {
      return new ErrorModal({
        errCode: 2,
        message: '密码错误'
      });
    }
  } catch (e) {
    console.log(e);
    return new ErrorModal({
      errCode: 3,
      message: '网络异常，登录失败'
    });
  }
};

// 3个参数以上写对象
const register = async ({ username, password, phone }) => {
  try {
    const user = await getUserInfo(username);

    if (user) {
      // 找到了
      return new ErrorModal({
        errCode: 4,
        message: '用户名已存在'
      });
    }

    await addUser({ username, password, phone });

    return new SuccessModal({
      errCode: 0,
      data: '注册成功'
    });
  } catch (e) {
    console.log(e);

    return new ErrorModal({
      errCode: 3,
      message: '网络异常，登录失败'
    });
  }
};

module.exports = {
  login,
  register
};

```

##  session

实现注册成功返回登录界面，注册失败返回成功界面

登录后才能访问用户中心的方案(session和jwt)

#### cookie

1. cookie是什么?
     本质上是一个 存储在浏览器端的 key/value文本
2. 作用:
     解决会话控制（http协议无状态问题） 
       存储少量的数据
3. 工作流程图
    ![cookie](cookie.png)
    1. cookie的使用
          客户端
          	document.cookie （基本不用）
           服务端
    2. 设置
         res.cookie(key, value, options)
    3. 获取
         cookie-parser 第三方中间件：用来解析cookie数据
         req.cookies（默认没有值，需要通过中间件解析）
    4. 删除
         res.clearCookie(key)
4. 缺点：
  5. 存储容量小  大小和数量有限制（一个网址 只能存 20 个左右，大小为 4kb ）   
  6. 安全性较低  因为数据是直接存储在客户端
  7. 传输流量大  cookie每次发送请求都会全部携带上   

```
const express = require('express');
const cookieParser = require('cookie-parser');

const app = express();

app.use(cookieParser());

app.get('/', (req, res) => {
  // 设置cookie
  // res.cookie('user', 'admin'); // 会话cookie （关闭浏览器就自动删除）

  /* res.cookie('user', 'admin', {
    // 持久化cookie
    maxAge: 1000 * 3600 * 24 * 7, // 过期时间7天
    httpOnly: true // 只能在服务端获取，客户端不能获取
  }); */

  // 获取
  console.log(req.cookies); // { user: 'admin' }

  // 删除
  // res.clearCookie('user');

  // 返回响应
  res.send('携带cookie的响应');
});

app.listen(3000, err => {
  if (!err) console.log('服务器启动成功');
  else console.log(err);
});
```
#### session

* 打开express官网=>资源=>中间件=>session和cookie parse查看文档/npm中的express-session查看文档

* 在文档Compatible Session Stores中找到connect-redis库的使用

* 安装redis connect-redis express-session(npm install redis connect-redis express-session)

* 工作流程图

  ![session](/session.png)
```
//server.js文件
/**
 * @description 主模块
 */
const express = require('express');
const session = require('express-session');
const RedisStore = require('connect-redis')(session);
const redisClient = require('./redis');
const userRouter = require('./routers/user');
const uiRouter = require('./routers/ui');

const app = express();

// 内置中间件：用来向外暴露静态资源
app.use(express.static('public'));
// 内置中间件：用来解析POST请求体参数
app.use(express.urlencoded({ extended: true }));

// 配置session
app.use(
  session({
    store: new RedisStore({
      // 存储session的数据库
      client: redisClient,
      ttl: 7 * 24 * 3600 // session数据过期时间 7天
    }),
    secret: '3r^nY1Tm&&UNMHAP', // 参与session_id加密参数
    resave: false, // 如果session数据没有修改，就不会重新存储
    saveUninitialized: false, // 如果session没有数据，就不会存储
    cookie: {
      maxAge: 7 * 24 * 3600 * 1000,
      httpOnly: true
    }
  })
);
```

## redis数据库
为了方便session能够持久化存储，由于redis数据库（内存数据库）的数据既存在内存中也存在磁盘中，正常使用时从内存中读取，一旦服务器关闭，磁盘中数据生效，待重启服务器时，会将磁盘中的数据存在内存中，因此读取速度比mysql快。正因为数据存储在内存中，因此一般不存储大数据只存储少量的用户户数据。
#### 基本安装

1. 解压压缩包，放在一个没有中文的路径下
2. 将压缩包目录添加为环境变量
3. 运行redis-server，开启redis服务
4. 运行redis-cli，开启连接redis服务

#### 基本指令

1. set key value 设置
2. get key 获取
3. keys * 列举所有

#### 配置为window服务

1. 来到redis安装目录
2. 在cmd中，输入 `redis-server --service-install redis.windows.conf --loglevel verbose`
3. 打开任务管理器 - 服务。 手动打开redis服务
## ajax
#### AJAX是什么？

AJAX 全称为Asynchronous Javascript And XML，就是异步的 JS 和 XML。
通过AJAX可以在浏览器中向服务器发送异步请求。
AJAX 不是新的编程语言，而是一种使用现有标准的新方法。
#### XML简介

XML 可扩展标记语言。
XML 被设计用来传输和存储数据。
XML和HTML类似，不同的是HTML中都是预定义标签，而XML中没有预定义标签，全都是自定义标签，用来表示一些数据。
```
//比如说我有一个学生数据：
    name = "孙悟空" ; age = 18 ; gender = "男" ;   
用XML表示：
    <student>
        <name>孙悟空</name>
        <age>18</age>
        <gender>男</gender>
    </student>
    
//现在已经被JSON取代了
//用JSON表示：
{"name":"孙悟空","age":18,"gender":"男"}
```
#### AJAX的工作原理

Ajax的工作原理相当于在用户和服务器之间加了一个中间层(Ajax引擎)，使用户操作与服务器响应异步化。

#### AJAX的特点

* 1 AJAX的优点
 * 可以无需刷新页面而与服务器端进行通信。
 * 允许你根据用户事件来更新部分页面内容。
* 2 AJAX的缺点
 * 没有浏览历史，不能回退
 * 存在跨域问题
 * SEO不友好
#### AJAX的使用

* 核心对象
    XMLHttpRequest，AJAX的所有操作都是通过该对象进行的。
* 使用步骤
     * 创建XMLHttpRequest对象
        var xhr = new XMLHttpRequest();
     * 设置接受响应的回调函数（事件）
        xhr.onreadystatechange = function () { }
     * 设置请求信息
        xhr.open(method, url);
        //可以设置请求头，一般不设置
        xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
     * 发送请求
        xhr.send(body)  //get请求不传body参数，只有post请求使用
     * 接收响应

     ```
      //xhr.responseXML 接收xml格式的响应数据
         //xhr.responseText 接收文本格式的响应数据
     
         xhr.onreadystatechange = function (){
             if(xhr.readyState == 4 && xhr.status == 200){
                 var text = xhr.responseText;
                 console.log(text);
             }
         }
     ```
* 解决IE缓存问题
     * 问题：在一些浏览器中(IE),由于缓存机制的存在，ajax只会发送的第一次请求，剩余多次请求不会在发送给浏览器而是直接加载缓存中的数据。
     * 解决方式：浏览器的缓存是根据url地址来记录的，所以我们只需要修改url地址即可避免缓存问题
        xhr.open("get","/testAJAX?t="+Date.now());
* AJAX请求状态
    xhr.readyState 可以用来查看请求当前的状态
        0: 对应常量UNSENT，表示XMLHttpRequest实例已经生成，但是open()方法还没有被调用。
        1: 对应常量OPENED，表示send()方法还没有被调用，仍然可  以使用setRequestHeader()，设定HTTP请求的头信息。
        2: 对应常量HEADERS_RECEIVED，表示send()方法已经执行，并且头信息和状态码已经收到。
        3: 对应常量LOADING，表示正在接收服务器传来的body部分的数据，如果responseType属性是text或者空字符串，responseText就会包含已经收到的部分信息。
        4: 对应常量DONE，表示服务器数据已经完全接收，或者本次接收已经失败了
```
//public文件的ajax.js   get请求
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>ajax</title>
</head>

<body>
  <button id="btn">按钮</button>
  <script>
    document.getElementById('btn').onclick = function () {
      // 发送ajax请求
      /*
        1. 创建xhr对象
        2. 设置接受响应的回调函数（事件）
        3. 设置请求信息
        4. 发送请求
      */
      // 1. 创建xhr对象
      const xhr = new XMLHttpRequest();
      // 2. 设置接受响应的回调函数（事件）
      xhr.onreadystatechange = function () {
        /*
          当 readyState 发生变化时，触发的事件
          readyState值代表请求的不同的阶段
            0：请求初始化阶段，xhr刚刚创建
            1：send方法还没调用（还没有发送请求），还可以设置请求信息
            2：send方法已经调用了（已经发送请求），并接受到了部分响应（响应首行 --> 响应状态码 和响应头 --> 其他信息）
            3：接受到了部分响应体数据（如果响应体较小，就全部接受完毕）
            4：全部接受完毕响应体数据

          问题：跨域
            Access to XMLHttpRequest at 'http://localhost:3000/ajax?username=jack&password=123' from origin 'http://127.0.0.1:5500' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
          解决：不要使用vscode打开前端页面，使用服务器打开
        */
        // console.log(xhr.readyState);

        // xhr.readyState === 4 && xhr.status >= 200 && xhr.status <= 299
        // xhr.status >= 200 && xhr.status <= 299 && xhr.readyState === 4 
        if (xhr.readyState === 4 && xhr.status >= 200 && xhr.status <= 299) {
          // 响应成功 并 全部接受到了响应数据
          console.log(xhr.responseText);
        }
      }
      // 3. 设置请求信息（请求方式、请求路径、请求参数、请求头信息...）
      // GET请求参数：查询字符串
      // xhr.open(请求方式, 请求路径?查询字符串参数, 同步false/异步true)
      /*
        GET请求默认会被浏览器缓存，
          chrome/firefox 走协商缓存，仍然会访问服务器，由服务器告诉客户端走缓存 304
          ie 走强制缓存，直接读取缓存，不会访问服务器
        问题：ie 走强制缓存，会导致接受不到最新的数据
        解决：在请求参数上加上随机数/时间戳(让每次请求不一样)
      */
      xhr.open('GET', 'http://localhost:3000/ajax?username=jack&password=123&date=' + Date.now());  
      // 4. 发送请求
       xhr.send() ;
      console.log('全部代码执行完了~');
    }
  </script>
</body>
</html>


//server.js
const express = require('express');
const app = express();

app.use(express.static('public'));  //可使用lochost3000/ajax.html访问

// 客户端发送请求到路由中。
app.get('/ajax', (req, res) => {
  console.log(req.query);
  // console.log('服务器接受到请求了222~');
  res.send('hello ajax3333');
});

app.listen(3000, err => {
  if (!err) console.log('服务器启动成功');
  else console.log(err);
});
```
```
//public文件的ajax.js   post请求
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>ajax</title>
</head>

<body>
  <button id="btn">按钮</button>
  <script>
    document.getElementById('btn').onclick = function () {
      // 发送ajax请求
      /*
        1. 创建xhr对象
        2. 设置接受响应的回调函数（事件）
        3. 设置请求信息
        4. 发送请求

      */
      // 1. 创建xhr对象
      const xhr = new XMLHttpRequest();
      // 2. 设置接受响应的回调函数（事件）
      xhr.onreadystatechange = function () {
        /*
          当 readyState 发生变化时，触发的事件
          readyState值代表请求的不同的阶段
            0：请求初始化阶段，xhr刚刚创建
            1：send方法还没调用（还没有发送请求），还可以设置请求信息
            2：send方法已经调用了（已经发送请求），并接受到了部分响应（响应首行 --> 响应状态码 和响应头 --> 其他信息）
            3：接受到了部分响应体数据（如果响应体较小，就全部接受完毕）
            4：全部接受完毕响应体数据

          问题：跨域
            Access to XMLHttpRequest at 'http://localhost:3000/ajax?username=jack&password=123' from origin 'http://127.0.0.1:5500' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
          解决：不要使用vscode打开前端页面，使用服务器打开
        */
        // console.log(xhr.readyState);

        // xhr.readyState === 4 && xhr.status >= 200 && xhr.status <= 299
        // xhr.status >= 200 && xhr.status <= 299 && xhr.readyState === 4 
        if (xhr.readyState === 4 && xhr.status >= 200 && xhr.status <= 299) {
          // 响应成功 并 全部接受到了响应数据
          console.log(xhr.responseText);
        }
      }
      // 3. 设置请求信息（请求方式、请求路径、请求参数、请求头信息...）
      // GET请求参数：查询字符串
      // xhr.open(请求方式, 请求路径?查询字符串参数, 同步false/异步true)
      /*
        GET请求默认会被浏览器缓存，
          chrome/firefox 走协商缓存，仍然会访问服务器，由服务器告诉客户端走缓存 304
          ie 走强制缓存，直接读取缓存，不会访问服务器
        问题：ie 走强制缓存，会导致接受不到最新的数据
        解决：在请求参数上加上随机数/时间戳(让每次请求不一样)
      */
      xhr.open('POST', 'http://localhost:3000/ajax');
      // 发送POST请求必须设置请求头
      /* 模拟form表单发送POST
      // xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
      // 发送json格式POST请求
      xhr.setRequestHeader('Content-Type', 'application/json');
      // 4. 发送请求
      // xhr.send(body) body就是post请求的请求参数
      // xhr.send('username=jack&password=123');
      xhr.send(JSON.stringify({
        username: 'jack',
        password: 123
      }));

      console.log('全部代码执行完了~');
    }
  </script>
</body>

</html>


//server.js
const express = require('express');
const app = express();

app.use(express.static('public'));
// 只能解析 form表单的POST请求
app.use(express.urlencoded({ extended: true }));
// 解析json POST请求
app.use(express.json());

// 客户端发送请求到路由中。

app.post('/ajax', (req, res) => {
  console.log(req.body); // { username: 'jack', password: '123' }
  res.send('hello ajax3333');
});

app.listen(3000, err => {
  if (!err) console.log('服务器启动成功');
  else console.log(err);
});

```
#### jQuery中的AJAX

* get请求
     $.get(url, [data], [callback], [type])
        url:请求的URL地址。
        data:请求携带的参数。
        callback:载入成功时回调函数。
        type:设置返回内容格式，xml, html, script, json, text, _default。
* post请求
    $.post(url, [data], [callback], [type])
        url:请求的URL地址。
        data:请求携带的参数。
        callback:载入成功时回调函数。
        type:设置返回内容格式，xml, html, script, json, text, _default。
```
!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>jquery中ajax</title>
</head>

<body>
  <button id="btn">按钮</button>
  <script src="https://cdn.bootcss.com/jquery/1.12.3/jquery.min.js"></script>
  <script>
    // 相当于 DOMContentLoaded 事件： 等所有DOM加载完毕
    // onload 事件： 等所有资源加载完毕
    $(function () {
      // ready事件

      $('#btn').click(function () {
        // 发送ajax请求
        /* $.ajax({
          method: 'GET', // 请求方式
          url: 'http://localhost:3000/ajax', // 请求路径
          data: { // 请求参数
            username: 'jack',
            password: 123
          },
          success: function (data) { // 请求成功的回调函数
            console.log(data); // 服务器响应的数据
          },
          error: function (err) {
            console.log(err);
          }
        }) */

        /* $.ajax({
          method: 'POST', // 请求方式
          url: 'http://localhost:3000/ajax', // 请求路径
          headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
          },
          data: { // 请求参数
            username: 'jack',
            password: 456
          },
          success: function (data) { // 请求成功的回调函数
            console.log(data); // 服务器响应的数据
          },
          error: function (err) {
            console.log(err);
          }
        }) */

        /* $.ajax({
          method: 'POST', // 请求方式
          url: 'http://localhost:3000/ajax', // 请求路径
          headers: {
            'Content-Type': 'application/json'
          },
          data: JSON.stringify({ // 请求参数
            username: 'jack',
            password: 789
          }),
          success: function (data) { // 请求成功的回调函数
            console.log(data); // 服务器响应的数据
          },
          error: function (err) {
            console.log(err);
          }
        }) */
        
        //简单方式，一般忽略失败
        /* $.get('http://localhost:3000/ajax', {
          username: 'jack',
          password: 456
        }, (data) => {
          console.log(data);
        }) */

        // 默认form方式发送
        $.post('http://localhost:3000/ajax', {
          username: 'jack',
          password: 789
        }, (data) => {
          console.log(data);
        })
      })
    })
  </script>
</body>

</html>
```

#### web socket









## 模块化

#### 模块化

 模块化:把一个庞大的js文件中每个功能拆分成多个功能,每个功能形成一个js文件,最终使用特定的语法引入这些js文件,此时形成模块化

  nodejs内部会帮助我们把每个js文件变成对应的一个模块

1.模块化有一个主文件(入口文件):index.js/main.js/app.js

 所有的模块都要通过入口文件来进行加载

2.模块化:模块的定义和引入模块

3.每个模块内部的数据都是私有的,外部是不可见的,想要让外部使用,必须要暴露出去



### CommonJS

模块定义:定义模块,并暴露出去,语法:module.exports或者exports

  引入模块:在某个js文件(某个模块)引入其他的模块,语法: const 变量名=require(路径)

#### 引入 :const 变量名=require(路径)

#### 暴露:module.exports或者exports

```
module1.js文件中
function add (x, y) {
  return x + y
}
// 向外暴露出去
module.exports = add

module2.js文件中
function sub (x, y) {
  return x - y
}
// 暴露出去
exports.sub = sub

index.js文件中
// 引入模块
const m1 = require('./module1')
const m2 = require('./module2')
console.log(m1) //[Function: add]
console.log(m2) // { sub: [Function: sub] }
console.log(m1(10, 20)) 
console.log(m2.sub(100, 20))
```

```
 * 总结:
 * module.exports怎么用都可以
 * exports只能exports.xxx=xxx使用
 * 为什么?
 * js模块最终向外暴露的值是module.exports,而exports是module.exports的简写/引用而已
 * 解释:
 * 此时m--module ,e---exports
 * module.exports最开始是一个空对象
 * const m={
 *  e:{}
 * }
 * exports是module.exports的引用
 * let e=m.e 
 * 相当于给module.exports.a=123
 * e.a=123
 * 如果e=123,那么指向就改变啦
 * 下面的是可以的
 * m.e.a=234
 * 总结:
 * 如果只要暴露一个内容:module.exports=xxx--->xxx-------->最常用
 * 如果要暴露多个内容: exports.xxx=xxx->{xxx}
 * 其他方式:---->es6的对象简写语法
 * module.exports={xxx}--------->多的时候这种比较好
 * 注意问题: require(路径可以省略.js后缀名字)，但是路径中的相对路径必须要写, ./ 不能省略
 * 模块分三种:
 * 1. 自己定义的，引入路径必须以./或者../ 这种开头的
 * 2.nodejs自带的:直接写名称即可
 * 3.第三方的-->npm 下载的
```

#### CommonJS可以直接在服务端执行

```
在终端中:node index.js 即可看到效果
```

#### CommonJS不能直接在浏览器端执行,如果需要则可以安装Browserify

```
在浏览器端使用模块化
当前目录commonJS中src目录和build目录及index.html文件
index.html 文件中使用script标签引入build目录中的built.js文件
下载安装
npm install browserify -g 
执行命令
browserify src/index.js -o build/built.js
此时build目录中的built.js文件中就有了编译后的文件
在index.html文件中
<script src="./build/built.js"></script>
```

##### 注意

```
 * ES6模块中不能直接在后台执行,也不能直接在浏览器端执行,如果要在浏览器端执行则需要编译
 * babel 
 * 
 * babel做了什么事?
 * 将ES6语法编译成commonjs模块化语法
 * 将ES6其他语法编译成ES5或ES5以下的语法
 * 
 * 还需要经过browserify 将commonjs模块化语法编程浏览器能识别的语法
 * browserify build/app.js -o build/built.js
```





### ES6模块化规范

#### 引入:import

1.引入默认暴露:import add from './module1.js'

2.引入分别暴露:import {} from './module2.js'

3.引入统一暴露:import Person from './module3.js'

#### 暴露:export

1.默认暴露:export default add

2.分别暴露:export const num1=10

3.统一暴露:export {name,age}



#### 例子

```
module1.js文件中
// 定义模块,并暴露出去
// 默认暴露
export default {
  name: 'jack'
}

module2.js文件中
// 定义模块,并暴露
// 分别暴露
export const num1 = 10
export const num2 = 20

module3.js文件中
// 定义模块,并暴露
const age = 18
const sex = '男'
export {
  sex,
  age
}
```



```
app.js文件中
// 引入默认暴露模块
import Person from './module1'
// 引入分别暴露模块
import { num1, num2 } from './module2'
// import * as A from './module2.js'   这种方式属于重命名
// import { num1 as b, num2 } from './module2.js'
// 引入统一暴露模块
import { sex, age } from './module3'
// 使用相关模块中的内容
console.log(Person.name)
console.log(num1, num2)
console.log(sex, age)
as语法主要解决重命名的问题,避免命名冲突
```





#### ES6模块不能在服务器端直接执行也不能直接在浏览器端直接执行

#### ES6在浏览器端执行

1.babel编译 网址:[https://babel.docschina.org/](https://babel.docschina.org/)

#### Babel 是一个 JavaScript 编译器

Babel 是一个工具链，主要用于在旧的浏览器或环境中将 ECMAScript 2015+ 代码转换为向后兼容版本的 JavaScript 代码



![img](01babel编译.png)



![img](02babel的使用.png)



先初始化package.json包,然后下载安装babel

![img](02babel指令的含义.png)

具体步骤如下:

```
第一步:
npm init -y 初始化一个package.json包(目录名称不能有中文)
npm install --save-dev @babel/core @babel/cli @babel/preset-env
第二步:配置
在根目录中创建一个.babelrc文件,注意,配置文件中不能写注释的,运行babel的时候执行对应的配置文件
{
  "presets":[
    "@babel/preset-env"
  ]
}
将es6的模块化语法编译成浏览器能够识别的语法
第三步:执行指令
使用 npx babel src -d build 将src目录下所有的文件编译后输出到build目录下
如果要在浏览器中使用则需要安装browserify
还需要经过browserify 将commonjs模块化语法编程浏览器能识别的语法
browserify build/app.js -o build/built.js,然后在index.html文件中引入这个js文件才可以

也使用以下内容在项目的根目录中创建名为 babel.config.js 的配置文件
```

![img](03配置babel.png)



```
babel配置有三种方式:
babel.config.js方式
.babelrc方式
package.json方式

```

![img](04配置babel方式1.png)

![img](04配置babel方式2.png)

![img](04配置babel方式3.png)



### 模块发展史



### AMD

```
module1.js文件中
// 定义模块---当前模块是一个没有依赖其他模块的模块
define(function(){
  function add (x,y){
    return x+y
  }
  // 向外暴露
  return add
})

module2.js文件中
// 定义模块--当前模块依赖其他模块
define(['m1'],function(m1){
  const result=m1(10,20)
  // 暴露出去
  return result
})

main.js文件中
配置
// 模块配置
require.config({
  baseUrl: './src', // 基础路径
  paths: {
    'm1': 'module1', // 'm1' 这个模块的路径是 './module1'
    'm2': 'module2'
  }
});
// 主模块
require(['m2'], function (m2) {
  console.log(m2)
});
index.html文件中
以上内容配置完毕后,去CDN去下载require文件,然后在index.html中进行script的配置
<script src="./src/require.min.js" data-main="./src/main.js"></script>

```



### CMD

```
module1.js文件中
define(function (require, exports, module) {
  function add (x, y) {
    return x + y
  }
  // 暴露出去
  module.exports = add
})

module2.js文件中
define(function (require, exports, module) {
  // 引入
  const add = require('./module1')
  // 暴露出去
  module.exports = add(10, 50)
})

main.js文件中
define(function (require, exports, module) {
  const result = require('./module2')
  console.log(result)
})
index.html文件中
  <script src="./src/sea.js"></script>
  <script type="text/javascript">
    seajs.use('./src/main.js')
  </script>

```









