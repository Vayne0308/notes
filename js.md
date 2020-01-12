付铭

18618176338

# 第一天，JavaScript 课堂笔记

## 1 JavaScript简介

### 1.1 JavaScript是什么？

* 是一门编程语言

### 1.2 编程语言

* 编程语言就是人与计算机交流的语言

* 图灵完备性(一切可计算的问题都能计算)，所以说HTML和CSS不能算作编程语言

### 1.3 编程语言分类

* 机器语言

  ```
  0101010001110000111000011
  ```

* 汇编语言

  ```
  SET 1
  ```

* 高级语言

  * 编译型语言	;先编译，再运行； 如 Java、C、C++ ... 运行效率更高
  * 解释型语言   ;边编译，边运行； 如JavaScript、PHP、Python...    开发效率更高

### 1.4 JavaScript能做什么

* 浏览器端JS，页面特效（表单验证、各种特效）
* 手机App （ios 编程语言 OC和swift；  安卓：Java）（js开发混合App，一键打包到安卓、ios、windowsphone）
* 游戏（页游，代替flash）
* 后端开发（nodejs）

### 1.5 JavaScript的特点

* 是一种脚本语言
* 是一种解释型语言；  解释器是浏览器或Node；
* 是动态语言，数据自动分配类型，声明变量无需指定类型；（弱类型； 数据类型可以自动转换 ）
*  静态语言，声明变量指定类型；（强类型：数据类型不可以自动转换）
* 基于对象的编程语言（面向对象）

### 1.6 浏览器端JavaScript 组成

* ECMAScript 基本语法 （使用ES的编程语言：JavaScript、ActionScript）
* BOM （浏览器对象模型） 浏览器提供的一系列API啊（使用代码直接调用的方法）
* DOM （文档对象模型）HTML文档提供的一系列API



## 2 JavaScript最基本语法

### 2.1 JS的三种书写方式

* 内联式 `<button onclick="JS代码">`

* 嵌入式 `<script>JS代码</script>`

* 外部导入 `<script src="JS文件地址"></script>`

  ```html
  <body>
      <!--JS按照顺序执行-->
  
      <!--内联式-->
      <button onclick="alert('啊，好疼')">我是一个按钮</button>
  
      <!--嵌入-->
      <!--type属性可以省略 默认就是text/javascript-->
      <script type="text/javascript">
          alert('今天天气真好');
      </script>
  
      <!--外部导入-->
      <!--导入和嵌入的代码不要写一起，只会执行导入-->
      <script src="main.js"></script>
  </body>
  ```

  

### 2.2 注释

* 单行注释  `//`
* 多行注释 `/*  */`

### 2.3 指令结束符

* 每一行代码都是一条指令，需要一个结束符

* JS的指令结束符是 `;`或者换行符

### 2.4 内容输出（输出运算结果，调试代码）

- JS代码按照顺序执行

* 以弹框的形式 `alert(内容)` 中断代码的执行
* 以弹框的形式`prompt(内容)`用户输入框
* `confirm(内容)`未知
* 控制台输出 `console.log(内容)`, 不影响页面
* 在页面输出`document.write(内容)`



## 3 变量

#### ① 直接量

​	把数据直接用

#### ② 什么是变量？

​	把数据取个名字
​	变量存储数据的容器，有名字

### 3.1 数据和直接量

* 计算器运算的就是数据，计算中用到的数据会存储到内存中
* 数据如果直接取用，支撑位直接量 `console.log(100)`

### 3.2 变量

- 声明变量， 把数据赋值给变量名

* 把数据取个名字，放在内存中
* 通过变量名取到数据

### 3.3 定义变量

- var 变量名 = 值;

```html
<script>
        // 声明变量， 把数据赋值给变量名
        
        var age = 108;
        var username = '小丽丽';
        var backgroundColor = '#f90';
        var $var = '小燕燕';

        /*
        静态类型的语言，声明变量指定数据的类型
        char name = '小';
        int age = 200;
        
        JS是动态语言，数据自动分配类型，
        */

        console.log(username);
        console.log(age + 10);
        console.log(age - 190);
</script>

```

### 3.4 变量名的命名规范

* 包含数字、字母、下划线 和 $,且不能以数字开头。
* 变量名不能是关键字和保留字*（ JS中具有特殊意义的单词是关键字当前JS版本没有特殊意义，不保证将来JS版本有没有特殊意义，称之为保留字）*
* 变量名要取得有意义 
* 如果变量名有多个单词组成，推荐使用小驼峰命名法



### 3.5 JavaScript交换两个变量的值（案列练习）

```html
    <script>
        // 声明两个变量
        var number1 = 100;
        var number2 = 200;
        console.log(number1, number2);

       方法一：
        // 交换两个变量的值 使用第三个变量
        var number3 = number1;   // number3是 100
        number1 = number2; // 此时number1 = 200
        number2 = number3; //此时number2 = 100
        console.log(number1, number2);
        
	   方法二：
       // 交换两个变量的值 不使用第三个变量（前提：两个变量都是数字）
        number1 = number1 + number2;  // number1 = 300;
        // 交换之后 number2的值 = 和 - number2
        number2 = number1 - number2;  // number2 = 100;
        // 交互之后的 number1的值
        number1 = number1 - number2;  // number1(300) - number2(100)

        console.log(number1, number2);
    </script>
```



## 4 数据类型

### 4.1 JavaScript数据类型的划分

#### ① 原始类型

* Number   数值
* String  字符串
* Boolean  布尔值    true(真)/false（假）
* Null  空
* Undefind  未定义

#### ② 对象类型

* Array（数组，数据）详细介绍在第五天1 数组 Array
* Object
* Function
* RegExp
* Error
* Math
* Date
* ..........

### 4.2 数据类型检测函数

```
typeof()
```



### 4.3 Number数值类型

#### ①  整型 （整数）

* 十进制表示
* 八进制表示 `010`  (不推荐)
* 十六进制表示  `0xf90`

#### ②  浮点 （小数）

* 直接写小数
* 科学计数法，表示较大的数；`2.3e3`
* 浮点的精度问题（十进制小数转为二进制小数，大部分无法精确转换；整数不存在这个问题）

#### ③ JS中数值的范围

* 5e324 ~ 1.7976931348623157e+308	
* 如果超过范围，会表示为 Infinity	或者 -Infinity	

#### ④ 特殊的数值 NaN

* NaN是number类型，是一个数值
* 特点1：NaN与任何数进行任何运算结果都是NaN
* 特点2：NaN与任何数都不相等，包括自己
*  强制把其他类型的数据转为Number类型的时候，是在转不动转为NaN

#### ⑤ 数值相关的运算符

```
+  -  *  /  %
```

#### ⑥ 相关函数

```
isNaN()   判断数据是否是NaN， 是返回true，否则返回false
isFinite（） 判断数据是否在范围内，在范围内返回true，否则false
```

```html
<script>
        /*
          十进制
           0 1 2 3 4 5 6 7 8 9 10 11 12 ...

        * 二进制：
            0 1 10 11 100 101 110 111 1000 1001 ...

           八进制
           0 1 2 3 4 5 6 7 10 11 12 13 14 15 16 17 20 .

           十六进制
           0 1 2 3 4 5 6 7 8 9 a b c d e f 10 11 12 ... 1f 20 21....
           #ff9900
        *
        *
        * */

        // 整数
        // 使用十进制表示
        var num1 = 30;
        console.log(num1);
        // 使用八进制表示 严格模式不支持8进制表示
        var num2 = 020; // 声明整数的时候，如果以0开头，会认为是8进制表示
        console.log(num2);
        // 使用十六进制表示
        var num3 = 0x10; // 声明整数的时候，如果以0x开头，会认为是16进制表示
        console.log(num3);
        console.log('');

        // 浮点数（小数） 整形和浮点内部存储是由区别的
        // 直接写
        var num4 = 34.45;
        console.log(num4);
        var num5 = 3.14e4;  // 3*10^2
        console.log(num5);
        console.log('');

        // 浮点数的精度问题
        console.log(1+2);
        console.log(0.1+0.2);
        console.log('');

        // JS中数值的可表示范围
        var num6 = 4.56e877;
        console.log(num6);
        var num7 = -4.56e877;
        console.log(num7);
        var num8 = 4.56e-877;
        console.log(num8); //0
        console.log('');

        console.log(100 % 3);
        console.log('');

        // JS中特殊一个数值  NaN   not a number
        // 被动产生， 强制把其他类型的数据转为Number类型的时候，是在转不动转为NaN
        var num9 = NaN;
        console.log(num9);
        console.log(typeof(num9));
        // 特点1； NaN与任何数进行任何运算，结果仍然是NaN
        console.log(num9 + 100);
        console.log(NaN * 0);
        // 特点2：与任何数都不相等(包括自己)
        console.log(2 == 2);
        console.log(NaN == NaN);
        console.log('');

        //相关函数
        console.log(isNaN(num9));
        console.log(isNaN(num8));

        console.log(isFinite(num1));  //true 没有超过范围
        console.log(isFinite(num7)); // false 表示超出范围

</script>
```



### 4.4 字符串类型

#### ① 定义字符串

* 使用单引号或者双引号，没有区别
* 单引号不要嵌套单引号；双引号，同理； 如果非要嵌套对引号进行转义 `\'` `\"`

#### ② 转义字符

```
\n  表示换行符
\r  表示回车符
\t  水平制表符 tab
\uXXXX 四位十六进制表示unicode字符串
\xXX 两位十六进制表示拉丁字符
```

#### ③ 字符串连接符 +



### 4.5 undefined类型

- 变量没有给值的时候数值会变成undefined

- 函数中属性没有给值的时候数值会变成undefined





# 第二天，JavaScript 课堂笔记

## 1 数据类型转换

### 1.1 强制转换（显示转换）

#### ① 转换函数

强制转换，需要重新赋值（定义变量），例如下面代码：

```html
<script>
        // 把字符串转为 Number
        var a = 'hello, 小莉莉';
        var n = Number(a); //要转什么类型就写什么。
        console.log(typeof(n), n);
</script>
```

```
Number()	把其他类型数据转为Number类型
parseInt()	
parseFloat()

String()  	把其他类型数据，转为Stirng

Boolean()   把其他类型的数据转为布尔值
```

#### ② 其他类型数据转为 Number 规则

```
其他类型数据转为数值类， 使用Number()函数
	字符串：  纯数字字符串 转为对应数字、
	十六进制：0xaf、 科学计算法：2e3， 也是纯数字
	空字符串转为0， 其他都是NaN
	
	布尔值： true->1  false->0
	null： 转为 0
	undefined: 转为 NaN
	
其他类型数据转为数值类， 使用parseInt()和parseFloat函数
	用于从字符串中提取数字，其他类型的数据都是转为NaN
	以数字开头或者纯数字，可用从字符串中提取数字部分；
	空字符转为NaN
	
	parseInt和parseFloat二者区别：
	parseInt获取小数点之后，提取整数；parseFloat提取浮点数
```

#### ③ 其他类型数据转为 String 规则

```
数字转为字符串： 原样转换， 十六机制和科学计数法表示的数字转换后是十进制的数字
其他类型，原样转换输出
```

#### ④ 其他类型数据转为 Boolean 规则

```
数字转为布尔值： 0/Nan转为false；其他都是true
字符串转为布尔值：  空字符串转为false， 其他都是true
null 转为 flase
undefined 转为 false
```



### 1.2 自动转换（隐式转换）（弱类型语言可以进行自动转换）

在某种运算环境下，数据自动转换类型

```
数字的运算环境， 表达式中有数字运算符： + - * / % ++ --
字符串的运算环境， 表达式中有连接符 +(字符串连接符)，且一边是字符串， 另外边的数据肯定自动转为字符串
布尔值的运算环境， 条件判断的时候 if (数据)  数据会自动转为布尔值
```



## 2 表达式

```
表达式是JS中的一个短语，有运算结果
变量赋值也是表达式
原始表达式： 变量、直接量
复杂的表达式： 运算符把原始表达式组合复杂表达式
有些表达式产生副作用，副作用是改变了操作数的值； 又没有副作用由运算符决定；
```

```html
<script>
        var a = 100; //变量赋值也是表达式
        var b = 200;

        a; // 表达式
        100; //表达式

        a + b;
        a + 100 / 45 % b;

        // 副作用 把变量的值给改变了
        a - b;  //没有副作用
        a = 500; //表达式 有副作用
        a ++; //有副作用

</script>
```



## 3 运算符分类

### 3.1 按照操作数

```
一元运算符/一目运算符			++ / --  -b -100
二元运算符/二目运算符			大部分运算符都是二元	
三元运算符/三目运算符			?:比较运算符
```



### 3.2 按照功能

```
算术运算符 	
标记运算符
关系运算符	
逻辑运算符	
位运算符
赋值运算符
其他运算符
```



## 4 运算符详解

### 4.1 算术运算符

```
+	加号
-	减号
*	乘号
/	除号
%	取余
++	累加自增
--	累减
+	正号
-	负号
```

### 4.2 关系运算符（比较运算符）

```
>  大于
>= 大于等于
< 小于
<= 小于等于
== 相等
!=  不等
===  全等
!==  不全等

in 运算符	判断某个属性是否属于某个对象
instanceof 运算符	判断某个对象是否是某个构造函数的实例,(在第7天② 判断构造函数)
```

```html
<script>
        //比大小 数字和数字
        console.log(100 > 20);
        console.log(100 <= 20);
        console.log('');

        // 布尔值比较 转为 数字
        console.log(20 > true);  //true  true转为1
        console.log(-100 < false);  // true false 转为0
        console.log(true > false);  // true
        console.log('');

        //字符串
        // 字符串可以进行比较 无需转为数字
        // 比的是字符对应的ascii码
        console.log('a' < 'b');  //true
        console.log('A' > 'a');  // false
        console.log('abc' > 'd'); //false
        console.log('a' > 2);  //false 字符串跟数字比， 字符串转为数字
        console.log('');
        console.log('');
        console.log('');

        // 等于比较
        // ==  ===
        console.log(100 == 100);
        console.log(100 == '100'); //自动转换类型
        console.log(false == 0);  //自动转换
        console.log('true' == true); //都转为数字进行比较
        console.log(100 != 10);
        console.log(NaN != NaN); // true
        console.log('');

        // ===  不会进行类型转换
        // 先判断类型，再判断值
        console.log(100 === 100);
        console.log(100 === '100');
        console.log(true !== 1); //true

</script>
```



### 4.3 逻辑运算符

```
&&	逻辑与AND 并且
||	逻辑或OR 或者
!	逻辑非 取反 一元, 先转布尔值再取反
```

```
逻辑运算符表达式结果
运算前会把操作数转换为布尔值再进行比较（并没有真正的转，只是看如果转换成布尔值会是true还是false）（自己添加）
	
	逻辑非，表达式结果是布尔值
	
	逻辑与，表达式结果是一种一个操作数的值
		第一个操作数成立，表达式结果就是第二个操作数；
		第一个操作不成立，表达式结果就是第一个操作数；
		如果第一个条件成立还会判端第二个条件是否成立；如果第一个条件不成立没有必要再判断第二个条件
		
	逻辑或，表达式结果是一种一个操作数的值
		第一个操作数成立，表达式结果就是第一个操作数的值
		第一个操作数不成立，表达式结果就是第二个操作数的值
		如果第一个条件成立没有必要判断第二个条件，如果第一个条件不成立继续判断第二个条件
```

```html
<script>
        // && 逻辑与 两个都为真结果才是真 两个条件都满足
        console.log(true && false);  //false
        console.log(true && true);
        console.log(false && false);
        console.log('');

        // || 逻辑或 只有一个为真结果就是真  只要满足一个条件
        console.log(true || false);
        console.log(true || true);
        console.log(false || false);
        console.log('');

        // ! 取反  真变为假  假变为真  一元运算符  ！构成的表达式计算结果是布尔值
        console.log(!true);
        console.log(!false);
        console.log(!100);
        console.log(!'');
        console.log(!null);
        console.log('');

        // && 和 || 通常会组成更复杂的表达式， 一般会组合关系表达式
        var age = 23;
        // 要求年龄大于等于18岁 并且 小于等于 60岁
        console.log(age >= 18  && age <= 60);
        // 要求年龄<18岁 或者 年龄 大于60岁
        console.log(age < 18 || age > 60);
        console.log('');

    
        // 逻辑运算符组成表达式， 表达式结果
        // 逻辑非 ！ 表达式结果一定是布尔值
        // 逻辑与和逻辑或 && || 表达式结果 不一定； 表达式的结果是其中一个操作数的值

    
        // 逻辑与 表达式的结果；  如果第一个操作数成立那么总体结果就是第二个操作数的值；
    	//如果第一个操作数不成立，结果是第一个操作数的值
        console.log(200 && 0);
        console.log(200 && 100);
        console.log(0 && 400);
        //console.log('' && 600);
        console.log(null && undefined);
        console.log('');

        // 逻辑或 表达式结果： 如果第一个操作成立，取第一个操作数的值；
    	//如果第一个操作数不成立取取第二个操作数的值
        console.log(100 || 200);
        console.log('' || '啦啦啦');
        console.log('');

        var a = 100;
        console.log(a++ && a--);  // 101
        console.log(a); // 100

        console.log(--a || --a); // 99
        console.log(a); // 99

</script>
```



### 4.4 位运算符(了解)

```
&	按位与
|	按位或
^	按位异或
~	按位取反
<<	左移
>>	右移
```



### 4.5 赋值运算符

```html
=  赋值
+=
-=
*=
/=
%=
(以下了解)
<<=
>>=
&=
|=
^=
```

```html
<script>
    
		累加0开始，累*的1开始
    
        var age = 78;
 
        //修改age 变量的值， 改为原来的值+10
        //age = age + 10;
        age += 10; //上面的简写 age = age + 10;
        console.log(age); // 88

        age -= 5; // age = age - 5
        console.log(age); // 83

        age *= 2; // age = age * 2;
        console.log(age); // 166

        age %= 3;  // age = age % 3
        console.log(age);//1

        age &= 2; // age = age & 2;
        console.log(age); // 0

        // 表达式整体的值 就是重新计算后变量的值
        console.log(age += 20);

    </script>
```



### 4.6 其他运算符

```
① + 字符串连接符
② , 逗号运算符	
③ void 忽略运算符
④ typeof  用于数据类型判断 一元运算符
⑤ delete 删除对象中的属性 一元运算符（未学）
⑥ ?: 一个三元运算符， 比较运算符

```

```html
<body>
    <a href="http://www.atguigu.com">某大型互联网公司</a>
    <br>
    <a href="">某大型互联网公司</a>
 
    <!--让超链接失效-->
    <a href="javascript:void(0)">拉拉顺丰到付</a>
    <a href="javascript:">拉拉顺丰到付</a>
    <a href="javascript:;">拉拉顺丰到付</a>
    <br>
    <!--没有herf属性就不是超链接了-->
    <a>拉拉顺丰到付</a>


    <script>
        // 同时定义多个变量
        // var username = '小丽丽';
        // var age = 18;
        // var sex = 'undefined';

        // 使用一个var关键字 定义多个变量
        var username = '小李地理', age = 19, sex = 'male';
        console.log(username, age, sex);
        console.log('');

        // typeof 数据类型判断
        var num = 234;
        console.log(typeof(num)); //使用typeof函数
        console.log(typeof num); //运算符

</script>
```

#### 三元运算符:

```html
<script>
        /*
        操作数 ? 操作数 : 操作数
        条件 ？ 值1 : 值2

        表达式的结果： 条件满足表达式结果是值1，条件不满足表达式结果是值2
         */

        // 输入成绩
        var sorce = 61;

        //计算结果
        var res =  sorce >= 60 ? '及格' : '不及格';
        console.log(res);
        console.log('');

        var age = 30;

        var r = age >= 18 && age <= 60 ? age++ + ++age : --age - age ++;  // 99 - 99

        console.log(r); // 62
        console.log(age); // 32
</script>
```



## 5 运算符优先级

```
先 乘除 后 加减。
一元运算符优先级比较高
一元运算符 > 普通二元运算符 > 三元 > 赋值 > ,最低
() 可以提高优先级
```

![](D:\尚硅谷资料\02尚硅谷0908面授javascript\JS-课堂笔记\图例\运算符优先级.png)





# 第三天，JavaScript 课堂笔记

## 1 语句

```
语句就是编程语言中的一个整句
;或者换行是语句结束符
表达式语句：语句可以有表达式组成，一个表达式也是个语句；
复合语句：可以使用花括号把多个语句组成一个复合语句
编程语言中专门有一类 流程控制语句 流程流程
```

![](D:\尚硅谷资料\02尚硅谷0908面授javascript\JS-课堂笔记\图例\语句.png)

## 2 流程控制结构

```
顺序结构
	代码从上到下执行
	JS语句本身就是顺序结构
	
分支结构
	根据逻辑条件的判断，执行不同的代码
	可以使用条件语句来实现分支结构

循环结构
	类似的运算重复执行多次
	可以使用循环语句来实现循环结构
```



## 3 分支结构（条件语句）

### 3.1 单向分支

```js
if (条件) {
    语句；
}
语句； // 不论前面的分支是否执行，都会执行
```

#### ①判断逻辑条件

```html
<script>

        //判断逻辑条件
        //if (true) {
        //if (100) { //可以自动转换
        if (100 > 20) { //表达式 比较表达式
            // 只有条件成立了，才会执行
            console.log('啊。我执行了');
            console.log('啊。我也执行了');
        }

        // 语句
        // 在分支语句的外面， 不论分支条件是否成立， 都会执行
        console.log('哈哈哈，我在这');
</script>
```

#### ②案列

```html
<script>

        // 用户输入年龄
        // 如果年龄<18 给一个警告提示

        // 获取用户的输入
        var input = prompt('请输入您的年龄：'); //输入框，可以获取用户的输入

        //所有用户的输入，不论输入的是什么，类型都是字符串
        //console.log(input, typeof(input));

        // 判断用户输入的年龄是否<18
        if (input < 18) {
            alert('由于您未成年，请慎重访问！'); //警告框
        }

</script>
```

![](D:\尚硅谷资料\02尚硅谷0908面授javascript\JS-课堂笔记\图例\01单向分支.png)



### 3.2 双向分支

```js
if (条件) {
    语句1;
} else {
	语句2;
}    
语句3；   // 不论前面的分支是否执行，都会执行
```

#### ①判断逻辑条件

```html
<script>
        //判断逻辑条件

        //if (true) { //表达式 比较表达式
        if (false) { //表达式 比较表达式
            console.log('条件成立');
        } else {
            console.log('条件不成立');
        }

        // 语句
        // 在分支语句的外面， 不论分支条件是否成立， 都会执行
        console.log('哈哈哈，我在这');
</script>
```

#### ②案列1

```html
<script>

        //让用户输入年龄
        // 判断用户输入的年龄格式是否正确

        // 获取用户输入
        var input = prompt('请输入您的年龄：');

        // 判断用户输入的年龄格式是否正确， 年龄必须是数字
        // 如果用户输入的不是纯数字，成立
        //if (isNaN(input)) {
        // 用户输入的是非数字或者空字符串
        if (isNaN(input) || input === '') {
            alert('请输入正确的年龄');
        } else {
            alert('您的年龄是'+input+', 欢迎访问！');
        }

</script>
```

#### ②案列2

```html
<script>
        /*
        * 用户输入成绩
        * 判断 及格还是不及格， 把结果弹框弹出来；
        * */
        //获取用户输入
        var sorce = prompt('请输入您的成绩：');
        //判断是否及格
        if (sorce >= 60) {
            alert('恭喜，你及格了');
        } else {
            alert('恭喜，你不及格');
        }
</script>
```



![](D:\尚硅谷资料\02尚硅谷0908面授javascript\JS-课堂笔记\图例\02双项分支.png)



### 3.3 嵌套分支

```js
if (条件) {
    语句;
    if (条件) {
        if （） {
            
        }
    } else {
        
    }
} else {
    if （） {
        
    }
}
```

#### 案列1

```html
<script>

        /*
        * 让用户输入年龄
        * 判断年龄的格式是否正确，
        * 如果格式是正确，再判断是否成年
        * */

        // 获取用户输入
        var input = prompt('请输入您的年龄：');

        // 判断用户输入的年龄格式是否正确
        if (isNaN(input) || input === '') {
            alert('请输入正确的年龄！');
        } else {
            // 说明用户输入的年龄格式是正确的
            // 判断用户是否是未成年
            if (input < 18) {
                alert('未成年人请谨慎访问！');
            }
        }
</script>
```

#### 案列2

```html
<script>
        /*
        * 90-100 优秀
        * 80-90 良好
        * 70-80 中等
        * 60-70 刚及格
        * <60   不及格
        * */

        // 获取用户输入的成绩
        var sorce = prompt('请输入您的成绩：');

        if (sorce <= 100) {
            //如果成绩>=90
            if (sorce >= 90) {
                alert('同志，你很优秀！');
            } else {
                //成绩是小于90
                // 找出>=80
                if (sorce >= 80) {
                    alert('同志，你也不错，良好！');
                } else {
                    // 成绩小于 80
                    // 找出 >= 70
                    if (sorce >= 70) {
                        alert('同志，你比较中等，继续努力！');
                    } else {
                        // 成绩是小于 70
                        // 找出 >= 60
                        if (sorce >= 60) {
                            alert('同志，你刚及格，快做不成同志了！');
                        } else {
                            // 成绩 < 60 的
                            // 成绩>=0才是有效
                            if (sorce >= 0) {
                                alert('你不是我们的同志！');
                            } else {
                                alert('成绩无效!成绩不能为负数');
                            }
                        }
                    }
                }
            }
        } else {
            alert('你这么牛逼，都超过100了，成绩无效！');
        }

</script>
```

![](D:\尚硅谷资料\02尚硅谷0908面授javascript\JS-课堂笔记\图例\03嵌套分支.png)

![](D:\尚硅谷资料\02尚硅谷0908面授javascript\JS-课堂笔记\图例\03嵌套分支.png)

### 3.4 多向分支 elseif

```js
if (条件) {
    
} else if (条件) {
    
} else if (条件) {
    
} else if (条件) {
    
} else {
    
}
```

```
什么时候用嵌套分支？什么时候用多项分支？
	如果多个判断条件都是对一个变量（值，表达式）进行判断， 这种情况使用多项分支；
	如果多个判断条件是针对不同的变量(值,表达式)进行的判断， 这种情况使用 嵌套分支；
```

#### 类似多项分支案列1

```html
    <script>
        /*
        * 90-100 优秀
        * 80-90 良好
        * 70-80 中等
        * 60-70 刚及格
        * <60   不及格
        * */

        // 获取用户输入的成绩
        var sorce = prompt('请输入您的成绩：');

        if (sorce >= 90 && sorce <= 100) {
            alert('同志，你很优秀！');
        }

        if (sorce >= 80 && sorce < 90) {
            alert('同志，你还不错，良好');
        }

        if (sorce >= 70 && sorce < 80) {
            alert('同志，你中等水平！');
        }

        if (sorce >= 60 && sorce < 70) {
            alert('同志，你危险了，刚及格！');
        }

        if (sorce >= 0 && sorce < 60) {
            alert('你不是我的同志！');
        }

    </script>
```

#### 案列2

```html
<script>
        /*
        * 90-100 优秀
        * 80-90 良好
        * 70-80 中等
        * 60-70 刚及格
        * <60   不及格
        * */

        // 获取用户输入的成绩
        var sorce = prompt('请输入您的成绩：');

        if (sorce > 100) {
            alert('你这么牛逼，都超过100了，成绩无效！');
        } else if (sorce >= 90) {  // sorce >= 90 && sorce <= 100
            alert('同志，你很优秀！');
        } else if (sorce >= 80) {  // sorce >= 80 && sorce < 90
            alert('同志，你也不错！');
        } else if (sorce >= 70) {   // sorce >= 70 && sorce < 80
            alert('同志，你也行吧！');
        } else if (sorce >= 60) {   // sorce >= 60 && sorce < 70
            alert('同志，你危险了！');
        } else if (sorce >= 0) {    // sorce >= 0 && sorce < 60
            alert('你已经不是我们的同志了！');
        } else {
            alert('输入的成绩无效！');
        }

    </script>
```

#### 案列3

```html
<script>
        /*
        * 90-100 优秀
        * 80-90 良好
        * 70-80 中等
        * 60-70 刚及格
        * <60   不及格
        * */

        // 获取用户输入的成绩
        var sorce = prompt('请输入您的成绩：');

        // 执行判断
        if (sorce < 0) {
            alert('成绩无效，请重新输入！');
        } else if (sorce < 60) {
            alert('你不是我们的同志！');
        } else if (sorce < 70) {
            alert('同志，你很危险!');
        } else if (sorce < 80) {
            alert('同志，加油');
        } else if (sorce < 90) {
            alert('同志，你也不错！');
        } else if (sorce <= 100) {
            alert('同志，你很优秀!');
        } else {
            alert('成绩无效，请重新输入！');
        }
</script>
```



#### 多向分支+嵌套分支案例

```html
<script>
        /*
        * 我去加油
        * 输入油号，油量
        * 如果是92油，价格5元/L, 如果油量超过40L，按照4元/L
        * 如果是95油，价格6元/L, 如果油量超过40L，按照5元/L
        * 只有92和95
        * */

        // 获取用户输入
        var oilN = prompt('请输入您要加的油号：'); //油号
        var oilL = prompt('请输入你要加的油量：'); //油量

        //如果油量输入的不合乎规范，设置油量的默认值是0
        // if (isNaN(oilL)) {
        //     oilL = 0;
        // }
        //转为三元运算符
        oilL = isNaN(oilL) ? 0 : oilL;


        // 判断
        if (oilN === '92') { //加的92号油
           /* if (oilL > 40) {
                alert(oilN * 4);
            } else {
                alert(oilN * 5);
            }*/
            var price = 5; //定义单价默认5元
            if (oilL > 40) {
                price = 4; //如果油量>40, 修改单价
            }
            //输出花费
            alert('你本次92号汽油消费共计：'+price*oilL+'元');

        } else if (oilN === '95') { //加的95号油
            var price = 6; //定义单价 默认6元
            if (oilL > 40) {
                price = 5; //修改价格
            }
            //输出花费
            alert('你本次95号汽油消费共计：'+price*oilL+'元');
        } else {
            alert('本加油站只有92号和95号汽油！你换一家吧');
        }
    </script>
```



### 3.5 多向分支 switch ... case

```js
switch (表达式) {
        case 表达式可能的值: 语句; break; 
        case 表达式可能的值: 语句; break;
        case 表达式可能的值: 语句; break;
        case 表达式可能的值: 语句; break;
        case 表达式可能的值: 语句; break;
    	default:语句; 
}
```

```
case所列举的值都不是表达式的值，default才执行  default可以不写；
break会跳出分支，不写break，会继续执行后面其他case里面（不进行判断）的语句，直到 遇到break；
```

```
swich...case 和 else if 适合不同的应用场景
	switch ... case: 适合根据某个表达式值的不同，来进行不同的操作； 表达式等于某个值的时候进行某些操作； 不适合范围判断；
	else if 适合根据表达式范围的不同，来进行某种操作； 
```

#### ①判断逻辑条件

```html
<script>
        //获取用户的年龄
        var age = 2;
        switch (age) {
            case 1: console.log('我今年1岁了'); break;
            case 2: console.log('我今年2岁了'); break;
            case 3: console.log('我今年3岁了'); break;
            case 4: console.log('我今年4岁了'); break;
            case 5: console.log('我今年5岁了'); break;
            default: console.log('我今年不知道几岁');
        }
        console.log('');


        age = 20;
        switch (age) {
            //case 1: console.log('我今年1岁了');console.log('我喜欢吃奶'); break;
            case 1:
                console.log('我今年1岁了');
                console.log('我喜欢吃奶');
                break;
            case 2:
                console.log('我今年2岁了');
                console.log('我喜欢吃奶粉');
                break;
            case 3:
                console.log('我今年3岁了');
                console.log('我喜欢吃烧烤');
                break;
            default:
                console.log('我不知道几岁了');
                console.log('我什么都喜欢吃');
        }
        console.log('');

        //break的作用
        // break的作用就是跳出分支结构， 不再执行后面的语句
        age = 2;
        switch (age) {
            case 1:
                console.log('我今年1岁了');
            case 2:
                console.log('我今年2岁了');
            case 3:
                console.log('我今年3岁了');
            default:
                console.log('我不知道几岁了');
        }
        console.log('');

        // break 的妙用
        age = 2;
        switch (age) {
            case 1:
            case 2:
            case 3: console.log('我是个婴幼儿！'); break;
            case 4:
            case 5:
            case 6:
            case 7:
            case 8: console.log('我是个儿童！'); break;
            case 9:
            case 10:
            case 11:
            case 12: console.log('我是个少年少女'); break;
            default: console.log('我长大了');
        }

</script>
```

#### ②案列1

```html
<script>
        /*
        * 用户输入出生的年份（公元纪年） 1976
        * 判断用户的生肖
        * */
        /*
        *  鼠    牛   虎   兔   龙   蛇   马  羊    猴   鸡   狗   猪  鼠
        *  2020  2021                                                2032
        *  %12
        *  4     5    6    7    8    9    10  11   0    1    2    3   4
        *
        * */

        // 获取用户的输入
        var year = prompt('请输入您的出生年份(公元纪年)：');

        //定义变量 保存用户的生肖
        var animal;

        switch (year % 12) {
            case 0: animal = '猴'; break;
            case 1: animal = '鸡'; break;
            case 2: animal = '狗'; break;
            case 3: animal = '猪'; break;
            case 4: animal = '鼠'; break;
            case 5: animal = '牛'; break;
            case 6: animal = '虎'; break;
            case 7: animal = '兔'; break;
            case 8: animal = '龙'; break;
            case 9: animal = '蛇'; break;
            case 10: animal = '马'; break;
            case 11: animal = '羊'; break;
            default: animal = '驴';
        }

        alert('经过缜密计算，您的生肖是：' + animal);


        /**
         *  if (age % 12 === 0) {
         *      animal = '猴';
         *  } else if (age % 12  === 1) {
         *      animal = '鸡'
         *  } else if (age % 12  === 2) {
         *      animal = '狗'
         *  } else if (age % 12  === 3) {
         *      animal = '猪'
         *  } else if (age % 12  === 4) {
         *      animal = '鼠'
         *  }
         *  ......
         *  很明显，不如switch case 简单
         *
         *
         * */
    </script>
```



### 3.6 分支注意点(分支和三元运算符区别)

```
分支和三元运算符区别：
	三元运算符每种情况只能有一条语句； 分支结构每种情况可以有多条语句。
	三元运算符组成是一个表达式，适合于根据不同条件取不同的值；  分支结构适合根据不同的条件干任何事情
```

```html
<script>
        var age = 9;

        age >= 18 ? console.log('成年了') : console.log('未成年');
        // 上下两种写法，等价的

        if (age >= 18) {
            console.log('成年了');
            // console.log('我可以去网吧');
            // console.log('我可以开房');
        } else {
            console.log('未成年');
        }

        /*
        *  ① 三元运算符组成的是表达式； 双向分支是一种条件语句；
        *  ② 三元运算符每种情况只能写一个表达式（操作数）三元运算符每一种情况只能写一条语句；双向			 	分支每种情况可以写多条语句.
        *  ③ 三元运算符更多的是用于取值；三元运算符主要用于根据条件取两个值里的一个；
        * */

    </script>
```



```
如果分支结构里的{}内只有一条语句，{}可以省略 (但是不建议省略)
	if (条件)
		语句
		
	if (条件)
		语句
	else
		语句
		
		
	if (条件) 语句;
```



####  简易的计算机案列

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JS</title>
    <style>
        input {
            width: 300px;
            line-height: 30px;
        }
        #box {
            width: 400px;
            min-height: 200px;
            padding: 20px;
            box-sizing: border-box;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
    加数1：<input type="text" id="num1">
    <br>
    加数2：<input type="text" id="num2">
    <br>
    <button onclick="add()">相加</button>
    <br>
    <div id="box"></div>

    <script>
        // 定义声明函数 实现两个数相加
        // 函数内的代码 调用才能执行
        function add() {
            //获取div元素
            var div = document.getElementById('box');

            //获取input元素
            var input1 = document.getElementById('num1');
            var input2 = document.getElementById('num2');

            // 获取用户输入的内容 并转为数字
            var num1 = parseFloat(input1.value);
            var num2 = parseFloat(input2.value);

            // 如果用户输入的不是数字内容
            if (isNaN(num1) || isNaN(num2)) {
                alert('加数1和加数2必须是一个数字')
            } else {
                // 对两个加数进行相加
                var sum = num1 + num2;
                //把计算结果输出到div标签内
                box.innerHTML = sum;
            }

        }

        /*
        * JS获取HTML标签，变为一个JS的对象
        *   document.getElementById()
        *
        * 通过元素对象获取属性
        *   dom.属性名
        *
        *  给双标签元素设置内容
        *   dom.innerHTML
        * */

    </script>
</body>
</html>
```





# 第四天，JavaScript 课堂笔记

## 1 循环结构（循环语句）

### 1.1 while 循环

```js
while (条件表达式) {
    循环语句;
}

```

#### ①循环逻辑条件

```html
    <script>
        // 输出100次 hello world
        //循环标记变量
        var i = 0;
        //循环  循环条件（满足条件，才能执行{}中的语句）
        while (i < 100) {
            //输出内容
            console.log('hello world', i);
            //循环标记变量 自增
            i ++;
        }
    </script>
```



### 1.2 do ... while 循环

```js
do {
	循环语句
} while (条件表达式);
```

#### ①循环逻辑条件

```html
<script>
        // 输出100次 hello world

        // 定义循环标记变量
        var i = 0;

        // 执行循环
        do {
            //输出内容
            console.log('hello world', i);
            //循环标记标签自增
            i ++;
        } while (i < 100);

    </script>
```

```
while循环和do...while的区别：
	① while循环先判断再执行语句； do...while第一次先执行后面的循环需要判断
	② do...while比while少了一次判断
	③ 只有循环次数超过0次（明确的知道会发生循环）， while和do...while的循环体语句和判断条件是一模一样的
```



### 1.3 for 循环

```js
for (循环标记变量的定义; 循环条件; 循环标记标量的变化) {
    循环语句;
}
```

```html
<script>
        //输出100次 hello world
        for (var i = 0; i < 100; i ++) {
            console.log('hello world', i);
        }

        console.log('');
        // 输出100次 hello 圆圆 ；  i不从0开始， 从100开始，让i的值递减
        for (var i = 100; i > 0; i --) {
            console.log('hello, 圆圆', i);
        }
        console.log('');


        // for循环 拆解
        //造成死循环
        /*for (;;) {
            console.log('哈哈哈哈');
        }*/

        // 循环标记标签定义在外面
        var i = 0;
        for (;i < 10; i ++) {
            console.log('hello, 翠翠');
        }
        console.log('');

        // 循环标记变量，和循环标记变量的变化 都不写在()内
        var i = 10;
        for (; i > 0;) {
            console.log('hello 小红红', i);
            i --;
        }

    </script>
```

```
for适合的应用场景：
	程序员明确知道循环次数
	
while和do...while 适合无法明确循环多少次
	循环读取文件中每一行的内容
```

#### ②-案例-输出0-100之间所有的偶数1

```html
<script>
        //0-100之间所有的偶数

        // for
        for (var i = 0; i <= 100; i ++) {
            if (i % 2 === 0) {
                console.log(i);
            }
        }
        console.log('');

        // while
        var i = 0;
        while (i <= 100) {
            if (i % 2 === 0) {
                console.log(i);
            }
            i ++;
        }
        console.log('');

        // do...while
        var i = 0;
        do {
            if (i % 2 === 0) {
                console.log(i);
            }
            i ++;
        } while (i <= 100);

    </script>
```



#### ②-案例-输出0-100之间所有的偶数2

```html
    <script>
        //0-100之间所有的偶数
        // 代码结构更简单；循环次数少了一半
        for (var i = 0; i <= 100; i += 2) {
            console.log(i);
        }
        console.log('');

        // 输出 0-100之间的奇数
        for (var i = 1; i <= 100; i += 2) {
            console.log(i);
        }
        console.log('');


        // 0-10之间所有偶数的和
        var sum = 0;
        for (var i = 0; i <= 10; i += 2) {
            sum += i; //sum = sum + i;
        }
        console.log(sum);

    </script>
```



#### ③-案列-以下是嵌套循环

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>循环</title>
    <style>
        table {
            margin-bottom: 20px;
            width: 800px;
            border-collapse: collapse;
        }
        td {
            padding: 10px;
            border: 1px solid #999;
        }
    </style>
</head>
<body>
    <script>
        // 循环输出表格，指定6行，10列
        document.write('<table>');
        for (var i = 0; i < 6; i ++) {
            document.write('<tr>');
            for (var j = 0; j < 10; j ++) {
                document.write('<td></td>');
            }
            document.write('</tr>');
        }
        document.write('</table>');

        // while循环 输出表格，输出4行，6列
        document.write('<table>');
        var i = 0;
        while (i < 4) {
            document.write('<tr>');
            var j = 0;
            while (j < 6) {
                document.write('<td></td>');
                j ++;
            }
            document.write('</tr>');
            i ++;
        }
        document.write('</table>');


        // do while 循环 5行5列
        document.write('<table>');
        var i = 0;
        do {
            document.write('<tr>');
            var j = 0;
            do {
              document.write('<td></td>');
              j ++;
            } while (j < 5);
            document.write('</tr>');
            i ++;
        } while (i < 5);
        document.write('</table>');

    </script>
</body>
</html>
```



#### ③-案列-九九乘法表1

```html
 <script>
        document.write('<table>');
        for (var i = 1; i <= 9; i ++) {
            document.write('<tr>');
            for (var j = 1; j <= i; j ++) {
                document.write('<td>'+j+'&times'+i+'='+(i*j)+'</td>');
                //document.write('<td>'+j+'&tiems'+i+'='+(i*j)+'<td>')
            }
            document.write('</tr>');
        }
        document.write('</table>');
    </script>
```



#### ③-案列-九九乘法表2

```html
<script>
        //九九乘法表 塔尖在左下面
        document.write('<table>');
        for (var i = 9; i >= 1; i --) {
            document.write('<tr>');
                for (var j = 1; j <= i; j ++) {
                    document.write('<td>' + j + '&times' + i + '=' + (j * i) + '</td>');
                }
            document.write('</tr>');
        }
        document.write('</table>');
    </script>
```



#### ③-案列-九九乘法表3

```html
 <script>
        //九九乘法表 塔尖在右上
        document.write('<table>');
        for (var i = 1; i <= 9; i ++) {
            document.write('<tr>');
            //输出空的单元格
            for (var j = 1; j <= (9-i); j ++) {
                document.write('<td class="empty"></td>');
            }
            // 输出内容
            for (var j = 1; j <= i; j ++) {
                document.write('<td>' + j + '&times' + i + '=' + (i * j) + '</td>');
            }

            document.write('</tr>');
        }
        document.write('</table>');

        document.write('<br>');
        document.write('<br>');
        document.write('<br>');
        document.write('<br>');

        //另外一种思路 塔尖在右上
        document.write('<table>');
        for (var i = 1; i <= 9; i ++) {
            document.write('<tr>');
            for (var j = 1; j <= 9; j ++) {
                if (j <= (9-i)) {
                    document.write('<td class="empty"></td>');
                } else {
                    document.write('<td>' + j + '&times;' + i + '=' + (i*j) + '</td>');
                }
            }
            document.write('</tr>');
        }
        document.write('</table>');
     
     
     //另外一种思路 塔尖在右上(正确的)
        document.write('<table>');
        for (var i = 1; i <= 9; i ++) {
            document.write('<tr>');
            for (var j = 1; j <= 9; j ++) {
                if (j <= (9-i)) {
                    document.write('<td class="empty"></td>');
                } else {
                    var num = j - (9-i);
                    document.write('<td>' + num + '&times;' + i + '=' + (i*num) + '</td>');
                }
            }
            document.write('</tr>');
        }
        document.write('</table>');
    </script>
```

#### ③-案列-九九乘法表4

```html
<script>
        //九九乘法表 塔尖在右下
        document.write('<table>');
        for (var i = 9; i >= 1; i --) {
            document.write('<tr>');
            //空的单元格
            for (var j = 1; j <= (9-i); j ++) {
                document.write('<td class="empty"></td>');
            }
            // 有内容的单元格
            for (var j = 1; j <= i; j ++) {
                document.write('<td>' + j + '&times;' + i + '=' + (i * j) + '</td>');
            }

            document.write('</tr>');
        }
        document.write('</table>');

        // 另一种思路
        document.write('<br>');
        document.write('<br>');
        document.write('<br>');
        document.write('<br>');

        document.write('<table>');
        for (var i = 9; i >= 1; i --) {
            document.write('<tr>');
            for (var j = 1; j <= 9; j ++) {
               if (j <= (9-i) ) {
                   document.write('<td class="empty"></td>')
               } else {
                   document.write('<td>' + j + '&times;' + i + '=' + (i*j) + '</td>');
               }
            }
            document.write('</tr>');
        }
        document.write('</table>');
    </script>
```

#### ④-强化练习-打印100–200之间所有能被3或者7整除的数

```html
    <script>
        //打印100–200之间所有能被3或者7整除的数
        for (var i = 100; i <= 200; i ++) {
             //判断能为被3或者7整除
            if (i % 3 === 0 || i % 7 === 0) {
                console.log(i);
            }
        }
    </script>
```



#### ⑤-强化练习-打印三位数位上有3或者7的数字

```html
<script>
        /***
         * 625
         */

        //打印三位数位上有3或者7的数字
        for (var i = 100; i <= 999; i ++) {
            // 从每个数字里面 获取百位数、十位数、个位数
            var h = parseInt(i / 100); //获取了百位上的数
            var n = i % 100; //十位和个位部分  25
            var t = parseInt(n / 10); //获取十位的部分
            var o = n % 10; // 获取各位部分
            // 判断不论哪一位的数字，只有有3或者7
            if (h === 7 || h === 3 || t === 7 || t === 3 || o === 7 || o === 3) {
                console.log(i);
            }
        }

    </script>
```



#### ⑥-强化练习-计算100的阶乘    1*2....*100

```html
<script>
        // 100阶乘
        var res = 1;
        for (var i = 100; i >= 1; i --) {
            res *= i;
        }

        console.log(res);
    </script>
```



#### ⑦-强化练习-求100-999之间的水仙花数。abc =a^3+b^3+c^3

```html
<script>
        // 获取 100到999之间的水仙花数
        for (var i = 100; i <= 999; i ++) {
            //分别获取每一位的数
            var h = parseInt(i / 100); //百分上的数
            var t = parseInt(i%100 / 10); // 十位上的数
            var o = i%10; // 各位上的数
            // 判断是否是水仙花数
            if (i === h*h*h + t*t*t + o*o*o) {
                console.log(i);
            }
        }
    </script>
```

#### ⑧-输出100-200之间所有的素数（质数）（只能被1和自身整除的数）

```html
<script>
        //输出100-200之间所有的素数（质数）（只能被1和自身整除的数）
        for (var i = 100; i <= 200; i ++) {
            //定义一个变量表示是否是质数
            var tag = true;
            //判断是否是个质数
            for (var j = 2; j < i; j ++) {
                if (i % j === 0) {
                    tag = false; //证明i已经不是质数了
                    break;  //后面的循环都没有必要了
                }
            }
            // 判断tag
            if (tag) {
                console.log(i);
            }
        }

    </script>
```



## 2 跳转语句

```
break	跳出整个循环，结束循环
continue	跳出本次循环，下一次循环继续
```

```html
<script>
        // 循环输出 0-5；
        for (var i = 0; i <= 5; i ++) {
            //判断 当i的值是3的时候，跳出循环
            if (i === 3) {
                break;  // 跳出整个循环。让整个循环结束
            }
            console.log(i);
        }

        console.log('');
        console.log('');
        console.log('');

        // 循环输出 0-5；
        for (var i = 0; i <= 5; i ++) {
            //判断 当i的值是3的时候，跳出循环
            if (i === 3) {
                continue; // 跳出本次循环，下一次循环继续
            }
            console.log(i);
        }

    </script>
```



## 3 with语句

```js
with (document) {
    write('hello,燕燕<br>');
    write('hello,燕燕<br>');
    write('hello,燕燕<br>');
    write('hello,燕燕<br>');
}
```

```html
 <script>
        document.write('hello,world<br>');
        document.write('hello,world<br>');
        document.write('hello,world<br>');
        document.write('hello,world<br>');

        //使用with来简写
        with (document) {
            write('hello,燕燕<br>');
            write('hello,燕燕<br>');
            write('hello,燕燕<br>');
            write('hello,燕燕<br>');
        }

        //write('hello, 丽丽');

        with (console) {
            log('OK');
            log('OK');
            log('OK');
            log('OK');
        }

    </script>
```



## 4 练习

```
1. 九九乘法表 4种
2. doc上的练习
3. 强化练习  求1!+2!+3!+...+20!的值

```



二、 强化练习
	打印100–200之间所有能被3或者7整除的数
	打印三位数位上有3或者7的数字
	计算100的阶乘    1*2....*100   
	求100-999之间的水仙花数。abc =a^3+b^3+c^3		

​		

三、 强化练习二
	输出100-200之间所有的素数（质数）（只能被1和自身整除的数）



# 第五天，JavaScript 课堂笔记

## 第四天的练习(案列)

#### ①使用for循环输出8行5列的一个表格，内容注意隔行颜色。

```html
<script>
        document.write('<table>');
        for (var i = 0; i < 8; i ++) {
            if (i%2 === 0) { //偶数
                document.write('<tr>');
            } else {
                // 奇数
                document.write('<tr bgcolor="#ccc">');

            }

            for (var j = 0; j < 5; j ++) {
                document.write('<td>江南美景</td>');
            }
            document.write('</tr>');
        }
        document.write('</table>');
    </script>
```

#### ②使用循环<h1>---<h6>输出标

```php+HTML
    <script>
       for (var i = 1; i <= 6; i ++) {
           document.write('<h' + i + '>才饮长沙水，又食武昌鱼</h' + i + '>');
       }
    </script>
```



#### ③求1!+2!+3!+...+20!的值

```html
    <script>
        //定义变量，记录最终结果
        var res = 0;

        // 循环1到20
       for (var i = 1; i <= 2; i ++) {
           // 定义变量，记录i的阶乘
           var num = 1;
            //循环
           for (var j = 1; j <= i; j ++) {
               num *= j;
           }
           // 累加
           res += num;
       }
        console.log(res);
    </script>
```



#### ④循环输出1到50的值，要求每次循环只能输出一个值，每输出10个换一行。

```html
<script>
       for (var i = 1; i <= 50; i ++) {
           //如果i的值是小于10的，前面拼接一个0
           var number = i < 10 ? '0' + i : i;
           //输出数字
           document.write(number + ' ');
           // 判断如果i能够被10整除，后面输出换行
           if (i % 10 === 0) {
               document.write('<br>');
           }
       }
    </script>
```



#### ⑤使用*号写出等腰三角形

```html
   <script>

        for (var i = 0; i < 5; i ++) {
            // 输出空格
            for (var j = 0; j < 4-i; j ++) {
                document.write('&nbsp;');
            }
            // 计算星星的数量
            var num = i * 2 + 1;
            // 输出 *
            for (var j = 0; j < num; j ++) {
                document.write('*');
            }

            document.write('<br>');
        }

    </script>
```





## 1 数组 Array

### 1.1 数组的概念

- 数组是值的有序集合；
- 数组的没个值称之为“元素”
- 每个元素都一个索引，通过索引可以访问这个元素
- 数组索引从0开始
- 数组的元素可以是任意类型
- 数组元素的个数足最大是 2^32-2



### 1.2 创建数组(声明数组)

- [] 数组直接量 （推荐）
- Array() 数组函数

```
数组命名 = [] 这种写法，结构简单；[]里面的内容都是数组元素;逗号隔开
数组命名 = Array() 如果只有一个参数且该参数是数字，那么数字表示数组的长度，数组元素是空。
		如果参数不止一个，或只有一个但类型是字符串；参数都会变为数组的元素。
```

```html
<script>
        // 定义数组  直接量 []
        // 定义咱班所有的姓名组成的集合
        var nameList = ['曹操', '诸葛亮', '刘备', '吕布', '小燕燕'];

        //定义由数字组成的数组
        var numList = [112,232,34,34234,3434,3434,121,112,112,112];

        //数组的元素各种类型都有
        var list = ['孙悟空', 100, true, false, '猪八戒', [1, 2, 3]];

        console.log(nameList);
        console.log(numList);
        console.log(list);
        console.log('');

        // 定义数组，使用Array函数
        var list1 = Array(10, 20, 30);
        console.log(list1);

        var list2 = Array(30);
        console.log(list2);

        var list3 = Array('小芳芳');
        console.log(list3);

        var list4 = [12];
        console.log(list4);

        //alert(nameList)

    </script>
```



### 1.3 读写数组元素

```
通过 [索引] 来读取数组元素
nameList[12]
nameList[2] = 100;
```

```html
<script>
        // 定义个数组
        var nameList = ['刘奶奶', '牛奶奶', '王奶奶', '李姥姥','王大爷'];

        // 读取数组中指定某个元素的值
        console.log(nameList[2]);

        // 修改某个元素的值
        nameList[4] = '李大爷';

        console.log(nameList);
    </script>
```



### 1.4 稀疏数组

```
数组内有内容的元素的索引没有连续，这样的数组称之为稀疏数组
JS要求数组中的元素索引必须是连续的。如果给了索引值很大的元素赋值。而中间的索引没有赋值；会把没赋值的元素补全，但是元素内容undefined; 也是稀疏数组
```



### 1.5 遍历数组（迭代）

```html
for (var i = 0; i < arr.length; i ++) {
    arr[i]
}

//for in循环
fro (var i in arr) {
    arr[i]
}

 <script>
        // 定义数组
        var nameList = ['刘姥姥', '欧阳姥姥', '上官姥姥', '爱新觉罗姥姥', '完颜姥姥'];

        // 数组本质上也是个对象， 有一个length属性，可以获取数组的长度
        console.log(nameList.length);

        // 读取数组中的每一个元素
        for (var i = 0; i < nameList.length; i ++) {
            console.log(nameList[i], i);
        }
        console.log('');


        // 提供了一种遍历数组的方式 for ... in
        for (var i in nameList) {
            console.log(nameList[i], i);
        }

    </script>
```



### 1.6 数组元素的添加和删除

#### ① 添加元素

```
[] 指定索引，指定下一个索引（避免成为稀疏数组或者修改了其他元素的值）
[数组长度]  把数组长度作为索引；因为没添加元素之前，数组的最大索引就比长度-1
arr.push(新元素)  在数组的最后面添加一个元素
arr.unshift(新元素)  在数组的最前面添加一个元素
arr.splice(位置, 0, 新元素)  在指定的位置插入一个元素
```

#### ② 删除元素

```
① 强制设置数组的length属性，如果设置的length值与原来小，会删除后面想元素 删除一个 arr.legnth -= 1
② arr.pop() 删除数组中最后一个元素
③ arr.shift() 删除数组中第一个元素；剩下的元素自动调整索引
④ arr.splice(位置, 1) 指定位置，删除一个元素； 剩下的元素自动调整索引；
```

```html
<script>
        // 定义数组
        var nameList = ['刘姥姥', '欧阳姥姥', '上官姥姥', '爱新觉罗姥姥', '完颜姥姥'];
        console.log(nameList);

        // 添加元素
        //nameList[2] = '伊丽莎白姥姥'; 修改了其他元素的值
        //nameList[21] = '伊丽莎白姥姥';  //变为稀疏数组 不好
        nameList[5] = '伊丽莎白姥姥';
        console.log(nameList);

        // 添加元素 数组的长度刚好与数组的下一个索引相同
        nameList[nameList.length] = '维多利亚姥姥';
        console.log(nameList);

        // push()  向数组中追加一个元素，在数组的后面追加一个元素
        nameList.push('黑山姥姥');
        console.log(nameList);

        // 在数组的前面追加一个元素 unshift
        nameList.unshift('路易姥姥');
        console.log(nameList);

        // 指定位置 插入一个元素
        nameList.splice(3, 0, '玛格丽特姥姥');
        console.log(nameList);
        console.log('');



        // 删除数组中的某个元素
        console.log(nameList);
        // 删除元素，修改数组的长度
        //nameList.length = 9;
        //删除最后一个元素
        nameList.length -= 1;  // nameList.length = nameList.length - 1;
        console.log(nameList);

        // pop 删除数组中的最后一个元素
        nameList.pop();
        console.log(nameList);

        // shift 删除数组中第一个元素 删除了第一个元素之后，后面的元素重新排列
        nameList.shift();
        console.log(nameList);

        // 指定位置删除元素  删除元素后，剩下的元素自动调整索引
        nameList.splice(2, 1);
        console.log(nameList);

        // 使用delete运算符 删除元素
        delete nameList[5]; //会造成稀疏数组
        console.log(nameList);

    </script>
```



### 1.7 数组方法

```
会影响数组本身：
	push() 	数组最后添加一个元素
	unshift()	数组最前面添加一个元素
	splice(位置, 要删除的数量，新元素)  	添加元素、删除元素、替换元素
	pop()	删除数组的最后一个元素
	shift()	删除数组从第一个元素
	reverse()	翻转数组
	sort()	数组排序

不影响数组本身，靠返回值计算结果
	join（） 把数组合并为字符串
	slice(start, end)  截取数组中一部分，返回一个新数组; end指定的索引不会被截取，end可以省略（一致截取到最后）
	concat() 数组合并

```

```html
<script>
        var nameList = ['刘姥姥', '欧阳姥姥', '上官姥姥', '爱新觉罗姥姥', '完颜姥姥'];
        console.log(nameList);

        //把数组拼接成字符串
        var msg = nameList.join();
        console.log(msg, typeof(msg));
        console.log('');

        // nameList.pop();// 删除数组的最后一个元素 pop对数组对象产生影响
        // console.log(nameList);

        //截取数组中的一部分
        var smallList = nameList.slice(1, 4); //无法改变数组本身
        console.log(nameList);
        console.log(smallList);
        console.log('');

        // 合并  无法对数组产生影响
        var res = nameList.concat([100,200,300,400]);
        console.log(res);
        console.log('');

        // 替换掉数组总某个元素
        nameList.splice(1, 1, '斯密斯姥姥');
        console.log(nameList);
        console.log('');

        // 数组 会影响数组本身的值；
        nameList.reverse();
        console.log(nameList);
        console.log('');

        //数组排序
        var numList = [23, 4, 12, 56,100, 91, 289];
        console.log(numList);
        numList.sort();
        console.log(numList);

        document.write(nameList);
        document.write('<br>');
        document.write(nameList.toString());

        console.log('');
        console.log(nameList);
        console.log(nameList.slice(1));

    </script>
```



### 1.8 类数组对象/伪数组对象(未学)

```
具有数组的特性，但却不是数组的一类对象
```



### 1.9 字符串具有数组的特性

```
字符串可以通过 [] 取到指定的字符，只能取值无法修改；
字符串属性 .length可获取字符串的长度（字符的个数）
字符串可以向数组那样遍历
```

```html
<script>
        var msg = 'hello,小艳艳，米好啊';

        // 一个汉字、一个标点、一个字母都是一个字符
        console.log('字符串的长度：'+msg.length);

        // 遍历字符串
        // 字符串同样可以通过索引获取指定的字符
        console.log(msg[0]);

        for (var i = 0; i < msg.length; i ++) {
            console.log(msg[i]);
        }

        console.log('');
        for (var i in msg) {
            console.log(msg[i]);
        }

        // 不能修改每个字符的值
        msg[1] = '夷';
        console.log(msg);

    </script>
```

### 2.0数组的案列

```html
<script>
        // 把某个人各科的成绩记录到数组中
        var sorces = [78, 67, 23, 19, 29, 16, 9];

        // 计算 总成绩，平均分，最高分，最低分

        var sum = 0; //总成绩
        var max = sorces[0]; //定义最大值 默认值是数组的第一个元素
        var min = sorces[0]; // 定义最小值 默认值是第一个元素的值

        // 遍历数组
        for (var i = 0; i < sorces.length; i ++) {
            sum += sorces[i];
            // 如果元素的值比max大，就修改max的值=元素的值
            if (sorces[i] > max) {
                max = sorces[i];
            }
            // 如果元素的值小于min,就设置min的值=元素的值
            if (sorces[i] < min) {
                min = sorces[i]
            }
        }

        var avg = sum / sorces.length; //平均分

        console.log('这位同学的总成绩是：'+sum);
        console.log('这位同学的平均分: '+avg);
        console.log('这位同学单科最高分: '+max);
        console.log('这位同学单科最低分: '+min);
    </script>
```



## 2 函数

### 2.0 函数的定义

```
把一块代码合到一起取个名字
让代码可以重复利用， 提高代码重用性
```

```
提高代码重用性
提高代码可维护性
提高代码可扩展性
```

```js
function 函数名(参数) {
    代码
    [return 返回值]
}
```



### 2.1 函数的组成（声明函数）

```
函数名， 命名规则同变量名
函数体， 函数内容
参数，   分为形参和实参
返回值， 函数调用表达式的结果
```



### 2.2 函数调用和返回值

```
返回值是函数调用表达式的结果   demo()的结果就是demo函数的返回值
在函数体内写return 值； 设置返回值
如果函数体内没有写return，函数默认返回undefined
return除了设置返回值外，还可以结束函数的执行，return后面的代码没用
```

```
什么样的函数需要写返回值？
	如果函数的作用是进行某种计算，得到的计算结果最后以返回值的形式返回
	
什么样的函数不需要返回值？
	函数的功能是实现某个具体的操作（界面操作），无需返回值
```

```
函数调用：
	函数名() 才是调用； 直接使用函数名是对函数整体的引用
	
	var a = demo();   //a的值就是demo()函数的返回值
	var b = demo;   // b的值就是函数本身， demo函数并不会被调用；b也变为了函数
```

### 函数案列

```html
<script>
        /**
         * 演示函数
         * @return 返回值
         */
        function demo(){
            return 100; //返回值是100
        }

        // 如果不写return，默认值是undefind
        function demo1(){
            var a = 200;
        }

        // 函数调用
        // 控制台输出 函数调用表达式
        console.log(demo());

        // 输出 demo1
        console.log(demo1());

        var a = demo() +200;
        console.log(a);

        console.log('');


        function demo2(){
            console.log('ok');
            return 200;  //会结束函数的执行
            console.log('不ok');
        }
        // 只调用没有返回值
        demo2();

        // 有返回值
        // console.log(demo2());
        console.log('');

        function demo3(){
            console.log(200);
        }

        console.log(demo3());


        console.log('');

        function demo4(){
            var a = 200;
            var b = 100;
            return ;
            console.log(a+b);
        }

        console.log(demo4());
        console.log('');

        /***
         * 定义一个函数，计算两个数的和
         * @param a number
         * @param b number
         * @return 返回a和b的和
         *
         */
        function sum(a, b) {
            return a + b;
        }
    </script>
```

```html
<script>
       function demo(){
           console.log('demo');
           return 100;
       }

       demo;
       demo();

       var a = demo;
       var b = demo();

       console.log(a);  //a的结果是整个函数
       console.log(b); //100

        a(); //a可以调用

        // demo是函数名， 本质上就是个变量名；
        console.log(alert);

        console.log(typeof(demo)); //function
        console.log(typeof(alert)); // funcion

        console.log(typeof(demo())); // number


        console.log(alert()); //输出的alert()的返回值

    </script>
```

```html
<script>
        function demo(){
            return 100+200;
        }

        console.log(demo() + demo()); //600
        console.log(demo+200);  //字符串拼接
        console.log(demo*200);  //NaN

    </script>
```



## 3 作业练习

#### ①封装函数， 接受一个参数； 输出*组成的等腰三角形，参数指定多少行

```html
<script>

        /**
         * 输出*组成的等腰三角形
         * @param rows number 三角形的行数
         */
        function printTriangle(rows) {
            for (var i = 0; i < rows; i ++) {
                var rowContent = '';
                // 内容添加空格
                for (var j = 0; j < rows-1-i; j ++) {
                    rowContent += ' ';
                }
                //内容里面添加*
                for (var j = 0; j < i*2+1; j ++) {
                    rowContent += '*';
                }
                console.log(rowContent);
            }
        }

        printTriangle(15);

        printTriangle(8);

        printTriangle(20);

        console.log(printTriangle(10));

    </script>
```



#### ②自己封装函数，实现数组的翻转；（不能用reverse）

```html
<script>

        /**
         * 翻转数组
         * @param arr Array 需要翻转的数组
         * @return newArr 翻转好的数组
         */
        function reverseArr(arr) {
            //定义新数组
            var newArr = [];
            // 遍历arr，从最后一个开始取
            for (var i = arr.length-1; i >= 0; i --) {
                newArr.push(arr[i]);
            }
            //返回值翻转好的数组
            return newArr;
        }

        var list = [100, 200, 300, 400, 500];
        console.log(list);

        console.log(reverseArr(list));

    </script>
```



#### ③自己封装函数。实现数组排序（选做）；（纯数字排序）

```html
1,冒泡排序
<script>

        // 定义数组
        var numbers = [12, 34, 2, 7, 345, 123, 8];
        console.log(numbers);

        for (var k = 0; k < numbers.length; k ++) {
            //比较 比到最后一个元素，结果保证 最后一个元素是所有元素里最大的
            for (var i = 0; i < numbers.length-k-1; i ++) {
                //紧挨着两个元素，如果前面元素的值比后面元素的值大，进行交换
                if (numbers[i] > numbers[i+1]) {
                    //执行交换
                    var tmp = numbers[i]; //临时存储
                    numbers[i] = numbers[i+1];
                    numbers[i+1] = tmp;
                }
            }
        }

        console.log(numbers);

    </script>

2,冒泡排序封装函数
 <script>

        /**
         * 进行排序
         * @params arr Array 需要进行排序的数组
         * @params isUp boolean 是否从大到小； 默认值是false（从小到大）
         * @return 排好序的数组
         */
        function sortArr(arr, isUp) {
            // 数组遍历
            for (var i = 0; i < arr.length; i ++) {
                // 进行比较。把最大的元素搞到最后面取
                for (var j = 0; j < arr.length-1-i; j ++) {
                    // 先判断是从大到小还是从小到大
                    if (isUp) { //从大到小
                        //如果前面的元素比后面的小，进行交换
                        if (arr[j] < arr[j+1]) {
                            var temp = arr[j]; //第三方变量
                            arr[j] = arr[j+1];
                            arr[j+1] = temp;
                        }
                    } else { //从小到大
                        //如果前面的元素比后面的大，进行交换
                        if (arr[j] > arr[j+1]) {
                            var temp = arr[j]; //第三方变量
                            arr[j] = arr[j+1];
                            arr[j+1] = temp;
                        }
                    }
                }
            }
            // 把排好序的数组返回
            return arr;
        }

        var numbers = [10, 23, 3, 100, 4, 234, 1];

        console.log(numbers);

        console.log(sortArr(numbers, true));
        console.log(sortArr(numbers, false));

    </script>


3,冒泡排序函数嵌套
<script>
        /**
         * @params arr Array 需要进行排序的数组
         * @params isUp boolean 是否从大到小； 默认值是false（从小到大）
         * @return 排好序的数组
         */
        function sortArr(arr, isUp) {
            // 数组遍历
            for (var i = 0; i < arr.length; i ++) {
                // 进行比较。把最大的元素搞到最后面取
                for (var j = 0; j < arr.length-1-i; j ++) {
                    // 先判断是从大到小还是从小到大
                    if (isUp) { //从大到小
                        //如果前面的元素比后面的小，进行交换
                        if (arr[j] < arr[j+1]) {
                            exchange();
                        }
                    } else { //从小到大
                        //如果前面的元素比后面的大，进行交换
                        if (arr[j] > arr[j+1]) {
                            exchange();
                        }
                    }
                }
            }
            // 把排好序的数组返回
            return arr;

            // 交换
            function exchange(){
                var temp = arr[j]; //第三方变量
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }

        var numbers = [10, 23, 3, 100, 4, 234, 1];

        console.log(numbers);

        console.log(sortArr(numbers, true));
        console.log(sortArr(numbers, false));
        console.log(sortArr(numbers));

    </script>
```



# 第六天，JavaScript 课堂笔记

## 1 定义函数的三种方式

- function关键字方式/字面量方式

  ```js
  function 函数名() {
      
  }
  function 函数名(参数) {
      
  }
  ```

- 表达式方式

  ```js
  var 函数名 = function(){
     
  }
  var 函数名 = function(参数) {
      
  }
  ```

- Function构造函数方式

  ```js
  var 函数名 = new Function('函数体');
  var 函数名 = new Function('参数', '函数体')
  ```

  

## 2 函数的参数问题

### 2.1 形参和实参

- 形参： 声明函数的时候，给的参数， 类似于变量名；在声明函数的时候，参数是没有值；
- 实参：调用函数是给的参数； 实参会按照顺序赋值给形参；

```html
<script>

        /**
         * 定义函数实现两个数据相加
         */
        function add(num1, num2) {
            // 函数在定义的时候，给的就是形参
            // 形参类似于变量，在函数体内可以使用形参； 形参的值是未知；
            return num1 + num2;
        }

        // 调用函数时，给的参数就是实参；
        // 实参会按照顺序赋值给形参； 形参只有在函数被调用的时候才会有值；
        console.log(add(100, 200));

        // 每一次调用函数，函数内的代码都会执行一次
        // 每一次调用的时候，给的实参不同，形参的值也不同
        console.log(add(34, 56));
        console.log('');

        // 形参和实参的数量
        // 正常情况下，保证实参数量=形参数量

        function demo(a, b) {
            console.log(a);
            console.log(b);
            console.log('');
        }

        // 调用
        //实参数量=形参数量
        demo(100, 'hello');
        // 实参数量>形参数量; 多出来的实参，废了；
        demo('hello', '你好', 200);
        // 实参数量<形参数量; 有的形参没有对应的实参，取默认值undefined
        demo(250);

    </script>
```



### 2.2 形参的默认值(参数的默认值)

```
JS函数允许形参有默认值，有默认值的形参，在调用函数的时候，可以没有与之对应的实参！

如何实现形参的默认值？
旧版语法：
	判断形参的值，是否是undefined，如果是undefined说明函数调用的时候没有给值，可以设置默认值
	function demo(a,b) {
		if (b === undefined) {
			b = 默认值
		}
	}
	
新版语法：
	function demo(a, b=默认值) {
	
	}
	
注意： 有默认值的形参一定要放在后面！
```

```html
 <script>

        // JS可以允许函数的参数有默认值的
        // 如果参数有默认值，调用函数时可以没有与之对应的实参；

        // 如何设置参数的默认值

        // 旧版语法
        // 参数b有默认值，默认值小莉莉
        function demo(a, b) {
            //判断如果 b没有传递参数
            if (b === undefined) {
                b = '小莉莉'; //给b设置默认值
            }
            console.log(a+'和'+b+'一起跳舞');
        }
        demo('小燕燕', '小莉莉');
        demo('小燕燕');
        demo('小燕燕', '曹操');
        console.log('');

        // 新版语句 ES6+ ES2015
        //参数name2设置一个默认值
        function fn(name1, name2='小莉莉') {
            console.log(name1+'和'+name2+'一起跳舞');
        }
        fn('曹操', '孙悟空');
        fn('曹操');
        console.log('');

        // 有默认值的参数的位置问题
        // 设置a有默认值
        // 有默认值的参数，一定要放在后面；
        function f(a='曹操', b) {
            console.log(a+'和'+b+'一起跳舞');
        }

        f('孙权');

    </script>
```



### 2.3 arguments（获取所有的参数）

```
arguments只能在函数内使用
arguments是一个类数组对象，具有数组的一些个性
arguments可以获取所有的实参； 获取实参：①用形参；②使用arguments
可以用来定义可变参数数量的函数：如计算所有参数和，取参数中的最大值，取参数中的最小值，求所有参数平均数..
```

```html
<script>

        /**
         * 计算所有参数的和
         @return 所有参数的和
         */
        function sum() {
            // arguments 对象（类数组对象）
            // console.log(arguments);

            var res = 0; //计算素所有元素的和
            // 遍历arguments
            for (var i = 0; i < arguments.length; i ++) {
                res += arguments[i];
            }
            // 把计算结果返回
            return res;
        }

        console.log(sum(100, 200));
        console.log(sum(100, 200, 1000,1123, 234234, 2342, 234234,234234));
        console.log('');

        /**
         * 取所有参数里面的最大值
         */
        function max() {
            //设置遍历 默认值的最大值
            var res = arguments[0];
            // 循环比较
            for (var i = 0; i < arguments.length; i ++) {
                if (arguments[i] > res) {
                    res = arguments[i];
                }
            }
            // 返回结果
            return res;
        }
        console.log(max(1,2,3,4121,1123));
        console.log('');

        /*
        * 从所有参数里面取最小值
        * */
        function min() {
            var res = arguments[0];
            for (var i = 0; i < arguments.length; i ++) {
                if (arguments[i] < res) {
                    res = arguments[i];
                }
            }
            return res;
        }
        console.log(min(1,2,3,4121,1123));
        console.log('');

        // splice(index, number, ele, ele1, ele2, ele3...)
        var numbers = [10,20,30,40];
        console.log(numbers);
        numbers.splice(2, 1, '刘姥姥', '马姥姥', '大姥姥', '小姥姥');
        console.log(numbers);


    </script>
```



## 3 作用域

### 3.1 变量的作用域

```
变量的可作用范围，变量只有在自己的作用域下才会生效
函数会产生作用域
```

### 3.2 作用域分类

- **局部作用域**； 函数内定义的变量的作用域就是局部作用域；这样的变量称之为**局部变量**。
- **全局作用域：** 在函数外面定义的变量的作用域是全局作用域；这样的变量称之为**全局变量**。
- **块级作用域**： 在代码块中定义的变量的作用域是块级作用域；这样的变量称之为**块级变量**。 **ES6才支持** 

```
局部变量 只能在定义变量的函数内使用；
全局变量 任意地方都可以使用。
```

```html
 <script>
        var num = 200; //就是全局变量

        function demo() {
            var a = 200;
            console.log(a);  // a的作用域就是 demo函数
            console.log(num); // num的作用域是 全局
        }

        function fn(){
            var b = 300; //声明一个局部变量，作用域fn函数
            console.log(b);
            console.log(num);
            // console.log(a); // 报错 a的作用域是demo函数
        }

        // 调用函数
        demo();
        fn();

        console.log(num);
        // console.log(a);  报错，因为a变量的作用范围仅限于demo函数
        //console.log(b); // 报错 变量的b的作用域仅限于 fn 函数
        console.log('');


        var n = 400; //全局变量
        function add() {
            var n = 500; //局部变量
            console.log(n);
        }

        add(); //输出 500
        console.log(n); //400
    </script>
```



### 3.3 作用域链

```
当使用某个变量的时候
	先从本作用域寻找，找到了停止；找不到就向上层作用域寻找；
	上层作用域找到了，停止；找不到，继续向上上层作用域；
	一直到全局作用域；
	如果都没有找到，报错！
```

> 注意： 变量的作用域只与函数定义的位置有关；与函数调用的位置无关！

```html
 <script>
       var n = 100; //全局变量
       var num = 200;

        function fn(){
            var num = 0;

            function fn1() {
                var num1 = 1;
                function fn2(){
                    var num2 = 2;
                    console.log(num2); //2
                    console.log(num1); //1
                    console.log(num); // 0
                    console.log(n); // n;
                }
                fn2();
            }

            fn1();

        }

        fn();

        //fn1(); //fn1的作用域 fn

    </script>
```

```html
<script>
        var num = 10;
        function fun() {
            var num = 20;
            fun2(); //变量的作用域只与函数定义的位置有关；与函数调用的位置无关
        }

        function fun2() {
            console.log(num);  // 10
        }

        fun();

        // fun函数不是 fun2的上层作用域；
        // fun2的上层作用域是全局

    </script>
```



## 4 变量提升和函数提升

```
变量提升：
	JS会把变量的声明提升到本作用域的最前面。（只有声明，没有值）
	
函数提升：
	JS会把函数连声明带值提升到本作用域的最前面。 函数可以在函数声明之前调用。
	只有字面量方式（function关键字方式）声明的函数才能函数提升！
	表达式方式声明的函数，只能变量提升！
```

```
预编译（预解释）： 在正式执行代码之前，会把变量和函数的声明提升最前；
```

```
函数提升的优先级更高！！！
```

#### ①变量提升

```html
<script>
       var num = 100;
       function demo(){
           console.log(num);  // undefined
           var num = 200; //声明局部变量
           console.log(num); // 200
       }
       demo();
       console.log(num); // 100
       

       console.log('');
       console.log(n);
       var n = 1000;
       console.log(n);
       console.log('');

       var a = 1; // 全局变量a
       function fn() {
           console.log(a); // 1
           a = 200; //这不是声明 加var关键字才是声明；
           console.log(a); // 200
       }
       fn();
       console.log(a); // 200
    </script>
```

#### ②函数提升

```html
<script>
        console.log(a);  // undefined
        console.log(fn); // 函数提升，不但提升了声明，带着值也提升；
        fn(); //可以调用
        console.log(demo); //变量提升，提升了变量的声明，没有值
        // demo(); 无法调用

        var a = 100;
        // 字面量方式声明
        function fn() {
            console.log('我是fn');
        }
        // 表达式方式声明
        var demo = function(){
            console.log('我是demo');
        };


        console.log('');
        fn();
        demo();
    </script>
```

#### ③var的注意事项

```html
<script>
        /*
        * JS在严格模式下，不写var声明变量报错！！！！
        *
        * 要求：声明变量一定加 var
        * */

        function fn() {
            // console.log(num); //没有提升 报错
            num = 100; // 函数内不使用var声明的变量是全局（隐式全局变量）
            console.log(num);
        }

        fn();  // 输出 100
        console.log(num); // 报错

    </script>
```

#### ④提升相关面试题

```html
<script>
        /*
        alert(a); // 报错
        a = 0;  //没有声明
         */

       /* alert(a);   //undefined
        var a = 0;
        alert(a); // 0*/

       /* alert(a);  // 输出了函数体
        var a = '我是变量'; //声明了一个变量
        function a(){ alert('我是函数') }  //声明了一个函数; 函数提升 全提升了
        alert(a); // 我是变量*/

       /* alert(a); // 函数体
        a++;
        alert(a); // NaN
        var a = '我是变量';
        function a(){ alert('我是函数') }
        alert(a) // 我是变量*/

        console.log(a);  //  undefined
        var a = 0;
        console.log(a);  // 0
        function fn(){
            console.log(a);  // undefined
            var a = 1;
            console.log(a);   // 1
        }
        fn();
        console.log(a); // 0

    </script>
```



## 5 练习

```
1， 定义函数，实现把稀疏数组变为不稀疏数组；
2， 定义函数，获取某个值在数组中第一次出现的位置，如果没有这个值，返回-1
3， 定义函数，获取某个值在数组中最后一次出现的位置，如果没有这个值，返回-1
4， 日历生成器。

```

#### ①定义函数，实现把稀疏数组变为不稀疏数组；

```html
<script>
        //声明数组
        var list = [10,20, 100 ,30,40];
        list[23] = 100;
        list[26] = 200;
        console.log(list);

        // 把数组变为不稀疏的
        var list1 = normalArray(list);
        console.log(list1);
        console.log('');


        /**
         * 实现把稀疏数组变为不稀疏
         * @param arr 需要处理的数组
         * @return 返回处理好的数组
         */
        function normalArray(arr){
            //创建一个空数组
            var newArr = [];
            //遍历旧数组
            for (var i = 0; i < arr.length; i ++) {
                //判断元素的值是否是undefined，不是undefined，加入到新数组
                if (arr[i] !== undefined) {
                    newArr.push(arr[i]);
                }
            }
            // 返回新数组
            return newArr;
        }
</script>
```



#### ②定义函数，获取某个值在数组中第一次出现的位置，如果没有这个值，返回-1

```html
<script>
		/***
         * 返回值某个值在数组中，第一个出现的位置，不存在返回-1
         * @param data 需要查找的值
         * @param arr  数组
         * @return 返回值第一次在数组中出现的位置(索引)
         */

        //声明数组
         var list = [10,20, 100 ,30,40];

         // 验证某个值在数组中的位置
         console.log(indexOfArray(100, list));
        function indexOfArray(data, arr) {
            //声明变量，标记值的所以
            var index = -1;
            // 遍历数组
            for (var i = 0; i < arr.length; i ++) {
                // 判断元素是否与data相等
                if (arr[i] === data) {
                    index = i; //修改index的值
                    break; //结束循环
                }
            }
            //返回位置
            return index;
        }

 // 另一种写法
        /*function indexOfArray(data, arr) {
            // 遍历数组
            for (var i = 0; i < arr.length; i ++) {
                // 判断元素是否与data相等
                if (arr[i] === data) {
                    return i;
                }
            }
            //返回位置
            return -1;
        }*/

</script>
```



#### ③定义函数，获取某个值在数组中最后一次出现的位置，如果没有这个值，返回-1

```html
<script>
		/***
         * 返回值某个值在数组中，最后一次出现的位置，不存在返回-1
         * @param data 需要查找的值
         * @param arr  数组
         * @return 返回值最后一次在数组中出现的位置(索引)
         */
        //声明数组
         var list = [10,20, 100 ,30,40];

         // 验证某个值在数组中的位置
         console.log(lastIndexOfArray(30, list));
        function lastIndexOfArray(data, arr) {
            // 定义变量，标记位置
            var index = -1;
            // 循环
            for (var i = arr.length-1; i >= 0; i --) {
                if (arr[i] === data) {
                    index = i;
                    break;
                }
            }
            //返回值
            return index;
        }
</script>
```



#### ④日历生成器。

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>函数</title>
    <style>
        table {
            width: 700px;
            border-collapse: collapse;
        }
        th,td {
            padding: 10px;
            border: 1px solid #999;
        }
        tr:first-child {
            background-color:#f5f5f5;
        }
    </style>
</head>
<body>
    <h1>日历生成器</h1>
    <hr>

    本月多少天：
    <input type="number" id="daysInput" max="31" min="28"><br>
    一号星期几：
    <select id="weekSelect">
        <option value="0">星期天</option>
        <option value="1">星期一</option>
        <option value="2">星期二</option>
        <option value="3">星期三</option>
        <option value="4">星期四</option>
        <option value="5">星期五</option>
        <option value="6">星期六</option>
   </select>
    <br>

    <button onclick="createTable()">生成</button>

    <br>
    <br>
    <br>
    <br>

    <div id="box"></div>

    <script>
        // 实现生成日历表格
        function createTable() {
            // 获取用户输入
            var days = Number(document.getElementById('daysInput').value);
            var weekday = Number(document.getElementById('weekSelect').value);

            //验证用户输入
            if (isNaN(days) || days < 28 || days > 31) {
                alert('请输入正确的天数');
                return;
            }

            //定义变量
            var html = '<table>';
            //表头
            html += '<tr><th>星期日</th><th>星期一</th><th>星期二</th><th>星期三</th><th>星期四</th><th>星期五</th><th>星期六</th></tr>';
            //计算所少行
            var rows = (days + weekday) / 7;
            // 声明变量 表示几号
            var date = 1;
            //循环
            for (var i = 0; i < rows; i ++) {
                html += '<tr>';
                for (var j = 0; j < 7; j ++) {
                    //定义单元格里的内容
                    var content = '';
                    //如果满足条件，才填入内容
                    if ((i !== 0 || j >= weekday) && date <= days) {
                        content = date;
                        date ++; //日期+1
                    }

                    //不需要输出内容的单元格条件
                    //i === 0 && j < weekday

                    html += '<td>'+content+'</td>';
                }
                html += '</tr>';
            }

            html += '</table>';


            // 获取div元素
            var box = document.getElementById('box');
            // 设置div元素的内容
            box.innerHTML = html;
        }


        // document.write('<table>');
        // document.write('</table>');
    </script>
</body>
</html>
```





# 第七天，JavaScript 课堂笔记

## 1 函数回顾

```
1. 函数的定义方式
① 字面量/function关键字 
	function 函数名(形参1,形参2) {
		函数体
	}
② 表达式方式 
	var 函数名 = function(参数1,参数2) {
		函数体
	}
③ 构造函数方式
	var 函数名 = new Function('参数', '函数体')



2. 函数的参数
2.1 形参和实参
	形参： 定义（声明）函数的时候 
	实参： 调用函数的时候
2.2 形参和实参的数量
	实参数量>形参数量： 多出来的实参无意义
	实参数量<形参数量： 导致后面的形参没有值， 取默认值undefined
2.3 设置参数的默认值
	有默认值的参数，在调用的时候，可以没有与之对应的实参。
	有默认值的形参，放在后面
2.4 arguments
	arguments是一个类数组对象
	在函数体内直接使用，获取所有的实参
	可以实现可变数量参数的函数
	



3. 作用域
	3.1 什么是作用域？
		变量的作用范围
	3.2 局部变量和全局变量
		局部变量： 局部变量作用域就是所在函数； 在函数内声明的就是局部变量。
		全局变量： 全局变量的作用域是任何地方； 在函数外部声明的变量是全局变量。
	3.3 作用域链
    	函数声明的时候，函数嵌套函数，形成了作用域链； 
    	一个变量的作用范围，本函数作用域内和下层作用域内。
    	当使用某个变量的时候，解释器先从本作用域内查找该变量，找到就停止，找不到继续在上层作用域查找，找到停止，没有一直向上层作用域查找，知道全局作用域。都没有，报错！ 
    	


4. 变量提升和函数提升
	变量提升： 程序正式执行之前，对变量的声明进行预编译；
	函数提升： 程序正式执行之前，对函数进行预编译，函数名和函数体都会提升；（字面量定义的函数才可以）
	
	console.log(a); // undefined
	var a = 100;
	
	console.log(demo);  //输出函数体
	demo(); //可以调用
	function demo(){
	
	}
```



## 2 函数

### 2.1 自调用函数

**匿名函数：** 没有名字的函数

```
function() {
	//匿名函数
}
```

**自调用函数：** 函数声明完立即调用，也叫**立即调用函数**。IIFE: Immediately Invoked Function Expression

**自调用函数作用：** 较少全局变量的使用，把自己代码或者每个特效写到自调用函数中,全局变量影响太大了,包括外链式的,也会被影响。

```
(function(){
	函数体
})()
```

> **注意：**
>
> 两个连续的自调用函数，之间加分号，告诉浏览器是不同的函数。
>
> 或者，在后面的自调用函数前加 `!` 等没有副作用的一元云算法



```html
<script>
        // 函数直接量，不给函数取名字； 匿名函数；
        /*(function() {
            console.log('ok');
        });*/

        // 函数允许匿名，但是匿名的函数要立即使用
        // 自调用函数，立即调用函数
        (function(){
            console.log('哈哈哈，我被调用了');
        })();

        // 自调用函数 传参
        (function(a, b){
            console.log(a+'和'+b+'跳舞');
        })('曹操', '刘姥姥');


        // 每个效果都封装到自调用函数内

        //定义字面量函数
        (function(){

        })();

        //注意事项
        (function(){
            console.log('嘿嘿嘿，我被调用了');
        })()

        !(function(){
            console.log('呵呵呵，我也紫貂');
        })();

</script>
```



### 2.2 回调函数

一个函数如果作为参数，称之为回调函数

回调函数也能接受参数

```js
function fun(callback) {
    callback(100, 200); //给回调函数传递实参
}

// 回调函数是匿名的
fun(function(a, b){
})
//回调函数有名字的
fun(fn);
function fn(a, b){
    
}
```

```html
<script>

        /**
         * 定义函数，接收一个参数，要求参数的类型是函数
         * @param callback 回调函数
         */
        function fun(callback) {
            //使用一下参数 调用参数 调用回调韩
            callback();
        }

        // 调用fun
       fun(function(){
           console.log('啊，作为一个回调函数，我被调用了');
       });


        // 调用fun
        fun(fn);  // 实参是fn本身
       // fun(fn());  //实参是 fn()的返回值

        function fn(){
            console.log('啊，我是fn');
        }
        console.log('');


        function demo(callback) {
            callback(100, 200);
        }
        demo(function(a,b){
            console.log(a, b);
        });
        demo(fn1);
        function fn1(a, b) {
            console.log(a+b);
        }

        console.log('');


        /**
         * @param num1
         * @param num2
         * @param call
         */
        function progress(num1, num2, call) {
            call(num1, num2);
        }

        progress(100, 200, function(a,b){console.log(a+b)});
        progress(100, 200, function(a,b){console.log(a*b)});

    </script>
```



### 2.3 递归

**递归函数：** 函数不断调用自身。

**注意：** 递归函数内要有递归条件。

```js
function fn(){
    //当满足某个条件
    if（条件） {
        return;
    }
	fn();    
}

```

```html
 <script>

       /* function fn(){
            prompt('请输入我是狗：');
            //console.log('fn');
            fn(); //递归调用
        }

        fn();*/

       /*
       * 实现某个数字的阶乘
       * */
       function fn(n) {
           if (n <= 1) {
               return 1;
           }
           return n * fn(n-1);
       }

       console.log(fn(5));
       console.log(fn(3));
       console.log(fn(1));
       console.log(fn(10));


       /**
        *  调用 fn(3)
        *       3 * fn(2)
        *       调用fn(2)
        *           2 * fn(1)  结果2
        *           调用fn(1)
        *               return 1
        *           调用完fn(1)
        *        调用完fn(2)
        *   调用完 fn(3)  结果6
        * */

       /**
        * 递归应用场景
        *    删除文件夹，需要递归删除（操作系统的原始接口只能删除文件和空文件夹）
        *    复制文件夹，剪切文件夹
        * */

        console.log('');

       // 定义递归函数
        function fun(n) {
            if (n <= 0) {
                console.log(0);
                return;
            }
            console.log(n);
            fun(n-1);
            console.log(n);
       }

       fun(5);


        /**
         *
         *  fun(1)
         *      输出1
         *      fun(0)
         *          输出0
         *      输出 1
         *
         *
         * */


        /**
         * 调用 fun(5)
         *      输出 5
         *      调用 fun(4)
         *          输出 4
         *          调用 fun(3)
         *              输出 3
         *                  调用 fun(2)
         *                      输出 2
         *                      调用fun(1)
         *                          输出 1
         *                          调用fun(0)
         *                              输出 0
         *                           调用结束 func(0)
         *                           输出 1
         *                       调用完成fun(1)
         *                       输出2
         *                    .....
         * */

    </script>
```



## 3 对象

### 3.1 对象的定义

**广义的理解：** 一切皆对象，数组、函数都是对象的一种。

**狭义的理解：** Object数据类型，与Array、Function是等价的。（大部分）

#### ①对象的属性名命名

```html
<script>
        /*
        * 定义对象属性的时候，直接量形式
        *   属性名以字符串的形式给出，可以是任意的字符，如果属性名的规范刚好满足变量名的规范，引号可以省略
        * */

        var obj = {
            name: '小艳艳',
            'user-age': 119,
            'age': 19
        };

        console.log(obj);

        // .运算符获取属性，属性名不需指定引号。 只有满足变量名命名规范的属性才可以。
        console.log(obj.name);
        console.log(obj.age);
        console.log(obj['user-age']);
    </script>
```



### 3.2 Object类型

#### ① 什么是Object

- 对象（Object）是值的无序集合
- 别称：字典、散列、关联数组、散列表。
- 对象由属性组成， 如果属性的类型是function，该属性称为方法



#### ② 声明一个Object类型的数据

- 直接量 `{}`
- 构造函数方式  `new Object()`

```html
<script>

        // 定义对象 // 直接量方式
        // 指定属性名，属性名对应的值， 属性名
        var data = {name:'小艳艳', age:18, numbers:[100, 200, 300, 400], say: function(){
                console.log('我会说话');
            }, eat: function(){
                console.log('我会吃');
            }};

        // 在对象外面给对象添加属性
        data.sex = 'male';
        data.sleep = function(){
            console.log('我会睡');
        };

        console.log(data);
        console.log(typeof(data));
        console.log('');

        // 构造函数
        var obj = new Object();
        obj.name = '小芳芳';
        obj.age = 19;
        obj.eat = function(){

        };

        console.log(obj);
        console.log(typeof obj);

    </script>
```



#### ③ 属性操作

```
属性的读取和设置（属性读写）：
	. 运算符 obj.name
	[] 	    obj['name']  属性名要以字符串形式给出， 也可以给变量
	
设置属性值的时候，属性已经存在，就修改属性值；如果属性不存在，就添加属性；
获取对象中不存在的属性的时候，返回undefined

遍历读取所有的属性
	使用 for ... in  循环
	for (var i in obj) {
		i // 是属性名
		obj[i];  //只能使用[]形式获取属性值
	}
	
	
删除对象中某个属性：
	delete obj.name;
	ddlete obj['name']
	
	
判断对象中是否存在某个属性，运算符 in，表达式结果布尔值
	'name' in obj;  //属性名以字符串的形式给出
```

```html
<script>

        // 指定属性名，属性名对应的值， 属性名
        var data = {name:'小艳艳', age:18, numbers:[100, 200, 300, 400], say: function(){
                console.log('我会说话');
            }, eat: function(){
                console.log('我会吃');
            }};

        // 修改和添加属性
        data.name = '大艳艳';
        data.sex = 'female';
        data['numbers'] = [1,2,3,4];

        console.log(data);

        // 读取属性 .
        console.log(data.name, data.age);
        data.eat();
        // 读取属性 可以使用 [], 属性名必须以字符串的形式给出
        console.log(data['age']);
        data['say']();

        console.log(data.length);  //获取对象中不存在的属性，得到undefined

        console.log('');

        // 遍历对象， 把对象的属性遍历读取出来 for ... in
        for (var i in data) {
            console.log(i, data[i]);
        }
        console.log('');


        // 删除属性 delete
        delete data.numbers;
        delete data['say'];
        console.log(data);
        console.log('');


        // in运算符 二元运算符； 表达式的结果是布尔值； 判断对象中是否存在某个属性
        console.log('age' in data);
        console.log('eat' in data);
        console.log('say' in data);

</script>
```



### 3.3 构造函数

#### ① 什么是构造函数

- 对象是一个实际的存在， 构造函数是对对象的描述
- 对象是构造函数的实例，构造函数是对象的抽象
- JS中的构造函数相当于其他编程语言的**类**
- 每一对象都有与之对应的构造函数。
- 一个构造函数可以对应很多对象， 一个对象只有一个构造函数。



#### ② 判断构造函数

```
instanceof   对象 instanceof 构造函数   返回布尔值
.constructor   所有的对象都有该属性，返回对象的构造函数
```

```html
<div id="box"></div>
    <script>
        var obj1 = {name:'小艳艳'};
        var obj2 = new Object();
        var list = [];
        var msg = 'hello';
        var num = 1001;
        var box = document.getElementById('box');

        console.log(obj1.constructor);  //Object
        console.log(obj2.constructor); // Object
        console.log(list.constructor);  //Array
        console.log(msg.constructor); //String
        console.log(num.constructor); //Number
        console.log(true.constructor); //Boolean
        console.log(box.constructor); //HTMLDivElement


        console.log(100 instanceof Number); // 数字是原始类型
        console.log(new Number(1000) instanceof Number); // 数字是原始类型
        console.log([] instanceof Array); //true
        console.log(alert.constructor);
        console.log(alert instanceof Function);  //true
</script>
```



#### ③ 自定义构造函数

```js
function Person(){
    
}

var p1 = new Person();
var p2 = new Person();
```

```html
<script>
        // 自定义构造函数 与定义普通函数一个样
        //定义描述人的 构造函数
        function Person() {
            //描述一下实例所需要的属性
            this.name = '小莉莉';
            this.age = 18;
        }


        // 根据构造函数 实例化对象
        var p1 = new Person();
        var p2 = new Person();

        console.log(p1);
        console.log(typeof p1);
        console.log(p1.constructor);

        console.log(p2);
    </script>
```





# 第八天，JavaScript 课堂笔记

## 1 回顾

```
函数：
	匿名函数
	自调用函数:  作用域
		(function() {
		
		})();
	回调函数：
    	作为参数的回调函数
            map(function(){})
            map(函数名)
            list.sort(function(a,b){});
     递归函数
     	 函数调用自身，就是递归
     	 通常，递归函数需要递归条件
     	 
     	 
 
对象：
	1. 创建对象（Object）
		① 直接量
		② 构造函数
	2. 什么是一个对象(Object)
		值的无序集合
		对象有属性组成，属性的值可以是任意类型； 如果属性的值是function，该属性也叫方法。
	3. 属性名命名规范
    	属性名时任意字符组成的字符串
    	如果属性名满足变量的命名规范，省略引号
    4. 属性操作
    	4.1 读取和设置属性
    		.  obj.name  obj.age 
    		[] obj['name'] obj[age] obj['user-name']
    	4.2 遍历读取属性
    		for ... in
    	4.3 删除属性
    		delete obj.name/delete obj['name']
    	4.4 判断对象中是否存在某个属性
        	'name' in obj
        	
 构造函数：
 	构造函数就是对对象特性的描述；其他编程语言叫 "类"
 	对象是构造函数的实例，构造函数是对象的抽象。
 	一个构造函数对应多个对象，一个对象对应一个构造函数
 	
 	定义构造函数：
 		function Person(){
 		}
 	
 	实例化对象：
 		new Person();
 		
 	验证对象和构造函数
 		instanceof  obj instance Fun  返回布尔值
 		.constructor  属性，所有的对象都有。
   	
```



## 2 对象

### 2.1 this

```
this指向：
	在构造函数使用this， this指向实例化之后对象
	在方法中使用this，this指向方法所属的对象（指定调用该方法的对象）
```

```html
<script>
        // 在方法中使用this
        var obj = {};
        obj.name = '曹操';
        obj.age = 29;
        obj.say = function(){
            //console.log(this); //this知道是方法所属的对象
            //console.log('我叫'+obj.name+',我今年'+obj.age+'岁了');
            console.log('我叫'+this.name+',我今年'+this.age+'岁了');
        };
        //调用对象的方法
        obj.say();
        console.log('');


        // 在构造函数中使用this
        // this表示构造函数将来实例化成的对象
        function Person(name, age) {
            // 描述对象 定义对象所拥有的的属性
            this.name = name;
            this.age = age;
            // 描述对象， 定义对象的方法
            this.eat = function(){
                console.log('我叫'+this.name+'，我能吃');
            };
            this.drink = function(){
                console.log('我叫'+this.name+',我能喝');
            }
        }
        // 实例化对象
        var p1 = new Person('小莉莉', 18);
        var p2 = new Person('诸葛亮', 19);

        console.log(p1, p2);
        p1.eat();
        p2.eat();
        console.log();

    </script>
```



```
window对象：
	window是JS的全局对象；
	所有的全局属性都是window的属性
	使用window的属性和方法的时候，可以省略window.; 
	系统的函数 alert\prompt\Number\Boolean\Array\Object等 也是window的属性
```

```html
<script>
        function Dog(name){
            this.name = name;
            console.log(this);
        }

        //实例化
        var d = new Dog('旺财');


        // 调用函数, 当方法用，里面的this根据方法中使用this的规则
        // 方法中 this指向该方法所属的对象
        // 所有的全局变量都是window对象的属性
        Dog('小黄');
        console.log(name); //小黄
        console.log(window.name);

        //window.alert('警告框');

        /**
         * window 是Js的全局对象
         * 所有的全局变量都是window对象的属性
         * 可以直接使用的函数（系统函数）起始本质上是window的属性
         * window的属性（方法），使用的时候，可以省略window.
         *
         * */

        console.log('');

        function map(callback) {
            callback();
        }

        // 调用函数
        map(function(){
            console.log(this); //
        });

    </script>
```



### 2.2 原型

#### ① 原型

```
原型是个对象
所有的对象都有原型
对象可以继承原型的属性（方法）
```

#### ② 获取原型对象

```
对象.__proto__ (隐式原型)		
构造函数.prototype	
```

```html
<script>

        // 定义数组
        var arr = [10,20,30];

        console.log(arr);
        console.log(arr.constructor);
        // 获取对象的原型，两种获取方式
        // 使用对象直接获取
        console.log(arr.__proto__);
        // 通过构造函数来获取原型
        console.log(Array.prototype); //构造函数实例的原型
        console.log('');


        // 自定义构造函数
        function Person(){
            this.username = '小艳艳';
        }
        var p = new Person();
        console.log(p);
        console.log(p.__proto__);
        console.log(Person.prototype);

    </script>
```



#### ③ 把方法定义在原型上

```js
function Person(name, age) {
	this.name = name;
	this.age = age;
}
Person.prototype.say = function(){}

/*
 把属性（方法）定义在原型上，好处：
 	节省内存
 	每个实例无需把方法在存储一遍
*/
```

```html
<script>

        // 自定义构造函数
        function Person(name, age) {
            //设置对象的属性
            this.name = name;
            this.age = age;
           /* this.say = function(){
                console.log('我是'+this.name+'，我今年'+this.age+'岁了');
            }*/
        }
        // 给原型添加方法
        // 把方法定义到原型上，可以节省内存
        Person.prototype.say = function(){
            console.log(this); //谁调用了this，this就指向谁。
            console.log('我是'+this.name+'，我今年'+this.age+'岁了');
        };


        //实例化对象
        var p1 = new Person('曹操', 18);
        var p2 = new Person('小乔', 18);

        console.log(p1);
        console.log(p2);
        console.log(Person.prototype);
        console.log('');

        p1.say();
        p2.say();

    </script>
```



#### ④ 对象、构造函数、原型之间关系

```
对象和构造函数： 对象是构造函数的实例， 对象由构造函数产生。
对象和原型： 每个对象都有原型，可以继承原型上的属性。
构造函数和原型：  如果对象的构造函数相同，对象的原型也相同。
```

![](D:\尚硅谷资料\02尚硅谷0908面授javascript\JS-课堂笔记\图例\01对象原型和构造函数.png)

#### ⑤ 原型链



```
原型是个对象
对象有原型，原型还有原型，原型还有原型， 直到null
```

```html
<script>

        // 自定义构造函数
        function Person(name, age) {
            //设置对象的属性
            this.name = name;
            this.age = age;
            this.toString = '啦啦啦';
           /* this.say = function(){
                console.log('我是'+this.name+'，我今年'+this.age+'岁了');
            }*/
        }
        // 给原型添加方法
        // 把方法定义到原型上，可以节省内存
        Person.prototype.say = function(){
            console.log(this); //谁调用了this，this就指向谁。
            console.log('我是'+this.name+'，我今年'+this.age+'岁了');
        };


        //实例化对象
        var p1 = new Person('曹操', 18);


        console.log(p1);
        console.log(p1.__proto__);
        console.log(p1.__proto__.__proto__); //到头了
        console.log(p1.__proto__.__proto__.__proto__); //null

        console.log('');

        var list = [100,200,300];
        console.log(list);
        console.log(list.__proto__);
        console.log(list.__proto__.__proto__); //到头了
        console.log(list.__proto__.__proto__.__proto__); //null

    </script>
```



#### ⑥ 判断属性是否属于对象自身

```
hasOwnProperty(属性名) 返回布尔值，判断属性是否是对象自身的属性（原型上的不上）
```

```html
<script>

        // 自定义构造函数
        function Person(name, age) {
            //设置对象的属性
            this.name = name;
            this.age = age;
        }
        // 给原型添加方法
        // 把方法定义到原型上，可以节省内存
        Person.prototype.say = function(){
            console.log(this); //谁调用了this，this就指向谁。
            console.log('我是'+this.name+'，我今年'+this.age+'岁了');
        };


        //实例化对象
        var p1 = new Person('曹操', 18);
        console.log(p1);

        console.log(p1.hasOwnProperty('name'));
        console.log(p1.hasOwnProperty('age'));
        console.log(p1.hasOwnProperty('say')); //说明不是对象自身的
        console.log(p1.hasOwnProperty('constructor'));

        var list = [];
        console.log(list.hasOwnProperty('length'));
        console.log(list.hasOwnProperty('push'));

        console.log('');


        // 创建一个对象，并制定对象的原型
        // 如果指定一个没有原型的对象，参数就是null
        var obj = Object.create(null);
        console.log(obj);
        console.log(obj.constructor); //应为obj对象上没有constroctor这个属性

    </script>
```



#### ⑦  创建对象并且指定原型

```js
//ES5新语法
Object.create(对象)
参数是个对象，对象作为将来创建的对象的原型
如果指定null，认为创建的对象没有原型
```

```html
	<script>
		// 创建一个对象，并制定对象的原型
        // 如果指定一个没有原型的对象，参数就是null
        var obj = Object.create(null);
        console.log(obj);
        console.log(obj.constructor); //应为obj对象上没有constroctor这个属性
        
   </script>
```



### 2.3 值类型和引用类型

**原始类型：** 也叫值类型。

**对象类型：** 也叫引用类型。

![](D:\尚硅谷资料\02尚硅谷0908面授javascript\JS-课堂笔记\图例\02值类型和引用类型.png)

```html
 <script>

        // 值类型
        var a = 100;
        var b = a;
        a = 200;
        console.log(b); //100
        console.log('');


        // 引用类型
        var obj1 = {age: 100};
        var obj2 = obj1;  //由于是引用类型，obj1给obj2是地址，导致obj1和obj2指向一个对象
        obj1.age = 200;
        console.log(obj2.age); //200
        console.log('');


        // 对变量重新赋值
        // 起始是把obj2指向了新的对象， obj2和obj1再无关系了。
        obj2 = {}; // 给obj2重新赋值了一个对象 （和修改obj2的属性不一样）

        console.log(obj1);

    </script>
```



## 3 内置对象

### 3.1 Boolean对象

```html
<script>

       // 直接赋值
        var b1 = true;
        var b2 = Boolean(false);
        var b3 = new Boolean(false); //依然可以类型转换 原始值的包装对象形式

        console.log(b1,b2,b3);
        console.log(b3.constructor);
        console.log(b1.constructor);  //把一个原始值当做对象去使用的时候，自动包装成对象
        console.log(b3 instanceof Boolean); //true
        console.log(b1 instanceof Boolean); //false


        console.log('');

        var n1 = 100;
        var n2 = Number(200);
        var n3 = new Number(300);
        console.log(n1,n2,n3);
        console.log(n2+n3);

    </script>
```



### 3.2 Number 对象

#### 属性

```
Number.MAX_VALUE  是Number构造函数本身的属性，不是数字对象的属性！！
Number.MIN_VALUE
```

#### 方法

```
toFixed()  保留指定位数的小数
toString() 转为字符串，指定进制，把数字转换为指定的进制形式
```

```html
<script>

        // 创建Number对象
        var n1 = new Number(200); //构造函数方式
        var n2 = 100.2323; //直接量
        var n3 = Number(10023); //转换函数方式


        //JS可以表示的最大值和最小值（数字）
        console.log(Number.MAX_VALUE);
        console.log(Number.MIN_VALUE);

        //toFixed 用于保留指定位数的小数 四舍五入
        console.log(n1.toFixed(2));
        console.log(n2.toFixed(3));
        console.log(n3.toFixed(30));

        //toString 转换为字符串； 指定参数，指定进制
        console.log('');
        console.log(n1.toString());
        console.log(n1.toString(2));
        console.log(n1.toString(8));
        console.log(n1.toString(16));
        console.log(n1.toString(9));
        console.log('');



        //console.log(23.toString(2)); 语法错误
        //使用数字直接量的是，不区分Int和Float，内部存储都是按照Float来存储的； 每个数字后面默认有个.
        // 浏览器会认为数字后面的.是小数点
        console.log(23..toString(2));
        console.log(100.);
        console.log((23).toString(2));

    </script>
```



### 3.3 String对象

#### 属性

```
length  字符串长度
```

#### 方法

```
indexOf()  返回字符串/字符在某个字符串第一次出现的位置 没有-1
lastIndexOf()   返回字符串/字符在某个字符串最后一次出现的位置 没有-1
slice(start, end)   截取字符串，指定开始索引和结束索引，结束索引不会被截取到，第二个可以省略（截取到最后）
substring(start, end) 同上(slice的别名)
substr(start, lenth)  截取字符串，指定开始索引和截取长度； 第二个参数可以省略（截取到最后）
split()  把字符串分割为数组，可以指定分隔符
toUpperCase()  字符串转为大写
toLowerCase()  字符串转为小写
chatCodeAt()   返回指定位置字符的unicode字符码
String.fromCharCode()  根据unicode编码生成指定字符 （不是字符串对象的方法，是String构造函数的方法）

正则三剑客：
search()
match()
replace()
```

```html
 <script>
        //创建字符串对象
        var msg1 = 'hello world';
        var msg2 = String(100);
        var msg3  = new String('hello 小艳艳');


        console.log(msg1);
        console.log(msg1.big());
        console.log(msg1.charAt(3)); //获取指定位置字符（不用）
        console.log(msg1[3]);
        console.log(msg1.concat(msg2)); //连接字符串(不用)
        console.log(msg1+msg2+msg3);
        console.log('');


        console.log(msg1.indexOf('l'));  //某个字符在字符串中第一次出现的位置
        console.log(msg1.indexOf('world')); //某个字符串在大字符串出现的位置
        console.log(msg1.indexOf('我')); //-1 没有出现 -1
        console.log(msg1.lastIndexOf('l')); //9 最后一次出现的位置
        console.log('');

        console.log(msg1.slice(3));
        console.log(msg1.slice(3, 7));
        console.log(msg1.substring(3));
        console.log(msg1.substring(3, 7)); //slice的别名
        console.log(msg1.substr(3)); //从索引3的位置，截取到最后
        console.log(msg1.substr(3, 7)); //从索引3开始截取，截取7个
        console.log('');


        console.log(msg1.split());
        console.log(msg1.split(' '));
        console.log(msg1.split('l'));
        console.log(msg1.split('')); //空字符当分隔符
        var list = [100,200,300,400];
        console.log(list.join());
        console.log(list.join('-'));
        console.log(list.join('娃哈哈'));
        console.log(list.join(''));
        console.log('');

        console.log(msg1.toUpperCase());
        console.log(msg1.toLowerCase());
        console.log('');


        console.log(msg1.replace('l', '艾奥')); //只能替换一个， 用正则

        console.log('');
        //输出字符的unicode编码
        console.log(msg1.charCodeAt(1));  //101 uncode向下兼容 ascii
        console.log(msg3.charCodeAt(7))
        console.log(msg3.charCodeAt(7).toString(16))
        //根据unicode编码得到字符
        console.log(String.fromCharCode(0x8273));



        /*
        *  一个英文字符 占一个字节
        *  一个汉字字符 占2个字节（GBK）
        *
        *  一个字节表示8个二进制位
        *  1Byte = 8bit
        *
        *  GB2312   用两个字节表示一个汉字
        *  GBK      用两个字节表示一个汉字（简体、繁体）
        *  UTF-8    （基础unicode编码）万国码 可变长编码； 汉字用3~6个字节 大部分是3个
        * */
    </script>
```



## 练习

```
做一个汉字和unicode编码转换的计算器

默写：
冒泡排序
自定义构造函数

```

### 做一个汉字和unicode编码转换的计算器

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>unicode编码计算器</title>
    <style>
        .box {
            margin: 100px auto 20px;
            width: 1000px;
            display: flex;
            justify-content: space-between;
        }
        .btns {
            width: 1000px;
            margin:0 auto;
        }
        .box textarea {
            box-sizing: border-box;
            padding: 10px;
            font-size: 14px;
            width: 480px;
            height: 150px;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
    <div class="box">
        <textarea id="leftText"></textarea>
        <textarea id="rightText"></textarea>
    </div>
    <div class="btns">
        <button onclick="progress(1)">中文转unicode</button>
        <button onclick="progress(2)">unicode转中文</button>
    </div>

    <script>
        /**
         * 实现unicode编码和中文之间的转换
         * @param tag 标记 1表示中文转unicode，如果是2表示unicode转中文
         */
        function progress(tag) {
            // 分别获取两个文本框内元素
            var leftText = document.getElementById('leftText');
            var rightText = document.getElementById('rightText');

            if (tag === 1) {
                //中文转unicode
                //定义变量 记录转换的结果
                var res = '';
                // 遍历第一个输入框中的内容
                for (var i = 0; i < leftText.value.length; i ++) {
                    res += '\\u' + leftText.value.charCodeAt(i).toString(16);
                }
                //把结果输出到第二个文本框中
                rightText.value = res;

            } else if (tag === 2) {
                // unicode转中文
                // 把字符串分割为数组
                var conList = leftText.value.split('\\u').slice(1);
                //定义变量 记录转换的结果
                var res = '';
                //遍历数组
                for (var i = 0; i < conList.length; i ++) {
                   res += String.fromCharCode(Number('0x'+conList[i]));
                }
                //把结果输出到第二个文本框中
                rightText.value = res;
            }

        }
    </script>

</body>
</html>
```



# 第九天，JavaScript 课堂笔记

## 回顾 对象

### 1.  Object

```
值的无序集合
别名： 散列、字典、关联数组...
对象由属性组成， 如果属性值的类型是function，该属性称之为方法。
```



### 2 声明对象 Object

```
直接量
	{name:value, name2:value}
	属性名： 任意字符， 如果满足了变量名命名规范，省略引号
    
构造函数方式：
	 new Object()

```



### 3 对象的属性操作

```
读写属性：
	. 运算符  
	[] 运算符
	
遍历：
	for ... in
	
删除属性
	delete  运算符
	
判断对象是否包含某个属性
	in 运算符    'name' in obj
```



### 4 构造函数

```
构造函数：
	构造函数就是用来构造对象， 构造函数内对对象描述（属性）
	
构造函数和对象关系：
	构造函数是对象的抽象，对象是构造函数的实例。
	
获取对象的构造函数
	.constructor   属性（所有的对象都有）
	
判断一个对象是否是某个构造函数的函数
	instanceof 
	
自定义构造函数
	function Person(){
		
	}
```



### 5 this的指向

```
在方法中使用：
	this指向方法所属的对象（谁调用该方法，this指向谁）

在构造函数中使用：
	this指向构造函数将来的实例
```

```
function Person(){
	this;
}
new Person(); //当做构造函数  this指向实例
Person();   // 当做函数，this指向window (方法，window全局对象调用了Person)
```



### 6 原型和原型链

```
原型：
	所有对象都有原型，对象可以继承原型上的属性。
	
原型链：
	对象有原型，原型仍然有原型，一直到null，组成了原型链
	当使用对象中某个属性的时候，先从对象本身寻找，找不到去原型上寻找，再找不到就是原型的原型，一直到没有原型了，都找不到才报错
	
对象、原型和构造函数 关系
	对象是构造函数的实例
	对象从原型上继承属性
	对象的原型通过构造函数来获取，同一个构造函数的实例，原型相同。
	
获取原型
	对象.__proto__
	构造函数.prototype
```



### 7 值类型和引用类型

```
值类型，又称原始类型： Number、String、Boolean、Null、Undefined
引用类型，又称对象类型： Object、Array、Function .....
```



## 内置对象

### 1. Number

#### ① 属性

```
Number.MAX_VALUE  构造函数本身的属性
Number.MIN_VALUE  构造函数本身的属性
```

#### ① 方法

```
toFixed()  保留指定位数小数
toString()  转为指定的进制  

特别用法:（查看跟类型）
consol.log(Object.prototype.toString.call(obj));
consol.log(Object.prototype.toString.call(arr));
consol.log(Object.prototype.toString.call(fn));
consol.log(Object.prototype.toString.call('字符串'));
```



### 2. String

#### ① 属性

```
length   字符串长度
```

#### ③ 方法

```
indexOf()  字符（串）在字符串中第一次出现的位置，没有-1
lastIndexOf() 最后一次出现的位置，没有 -1
split()   把字符串分割为数组
slice(start, end)  截取字符串
substring（start, end） 同上
substr(start, length) 截取字符串
toUpperCase()
toLowerCase()
charCodeAt() 返回字符对应的unicode编码
String.fromCharCode();  把unicode编码转为对应的字符（是String构造函数本身的方法）
```



## 以下第九天课程

## 定时器函数

```
setInterval()   多次定时	返回定时标记（用于清除定时）
clearInterval() 清除多次定时
setTimeout()    单次定时	返回定时标记
clearTimeout()  清除单次定时
```

#### ①多次定时

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>定时器</title>
    <style>
        #box {
            font-size: 100px;
            text-align: center;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div id="box">0</div>
    <button onclick="stop()">停止</button>
    <script>
        /*
            setInterval()  多次定时
            setTimeout()  单次定时
            clearInterval()  清除多次定时
            clearTimeout()   清除单次定时
        */

        /**
         * setInterval(字符串/函数 ,时间间隔)
         *
         * 时间间隔的单位是 毫秒，  1s=1000ms
         * */

        // 每隔1s钟。输出一句 hello world
        //第一个参数是字符串，在字符串中写代码
        //setInterval('console.log("hello world")', 1000);

        //  第一个参数 写个函数（回调函数）
        setInterval(function(){
            console.log('hello，小艳艳');
        }, 1000);



        var number = 0; //定义数字
        //定时器，每隔一秒钟数字+1
        var timeId = setInterval(function(){
            document.getElementById('box').innerHTML = ++number;
        }, 300);



        //定义函数 停止定时
        function stop(){
            clearInterval(timeId);
        }

    </script>
</body>
</html>
```

#### ②定时器暂停和继续

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>定时器</title>
    <style>
        #box {
            font-size: 100px;
            text-align: center;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div id="box">0</div>

    <!--此时 this指向button元素-->
    <button onclick="stop(this)">停止</button>
    <script>


        var number = 0; //定义数字
        //定时器，每隔一秒钟数字+1
        var timeId = setInterval(run, 300);

        //定时函数
        function run(){
            document.getElementById('box').innerHTML = ++number;
        }

        //定义函数 停止定时
        function stop(btn){
            //判断一下按钮上的文字
            if (btn.innerHTML === '停止') {
                // 把里面的文字设置为 继续
                btn.innerHTML = '继续';
                //执行停止
                clearInterval(timeId);
            } else {
                // 把里面的文字设置为 停止
                btn.innerHTML = '停止';
                //继续定时
                timeId = setInterval(run, 300);
            }
        }

    </script>
</body>
</html>
```

#### ③定时器倒计时

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>定时器</title>
    <style>
        #box {
            font-size: 100px;
            text-align: center;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div id="box">10</div>

    <script>
        //获取元素
        var box = document.getElementById('box');

        //定义变量
        var number = 10;

        //定时器
        var intervalId = setInterval(function(){
            box.innerHTML = --number ;
            //如果number的值 <= 0 定时器可以停止了
            if (number <= 0) {
                clearInterval(intervalId);
                box.innerHTML = '开始';
            }
        }, 1000)

    </script>
</body>
</html>
```



#### 单次定时

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>定时器</title>
    <style>
        #box {
            font-size: 100px;
            text-align: center;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div id="box"></div>

    <script>
        // 只定时一次
        // 用于延迟执行
        setTimeout(function(){
            console.log('啊，单次定时');
        }, 1000);


    // 单次循环使用回调函数倒计时
        // 定义变量标记数字
        var number = 10;

        //函数
        function run() {
            //输出文字
            document.getElementById('box').innerHTML = number --;
            // 判断满足一定条件，停止停止
            if (number < 0) {
                return;
            }
            //单次定时
            setTimeout(run, 100);
        }

        run();


       /*for (var i = 0; i < 10; i ++) {
            setTimeout(function(){
                document.getElementById('box').innerHTML = --number;
            }, 1000);
        }*/

    </script>
</body>
</html>
```



## 1. Math(数学计算)

### 属性

```
PI   圆周率
```

### 方法

```
abs() 取绝对值
sqrt() 求平方根
pow()  求某个数的几次方
round()  四舍五入取整
floor() 舍一取整
ceil() 进一取整
max()  取参数里面最大的（任意次数参数）
min()  取参数里面最小的（任意次数参数）
random() 随机取0~1之间的小数，0有可能取到的，1不可能取到 

三角函数类：
sin()
cos()
tan()
.......
```

```html
<script>
        console.log(Math.PI);

        console.log(Math.abs(101));
        console.log(Math.abs(-101.23));

        //取平方根
        console.log(Math.sqrt(100));
        console.log(Math.sqrt(6));

        //计算某个数的几次方
        console.log(Math.pow(2, 5));
        console.log(Math.pow(34, 50));

        console.log('');

        //取整数 四舍五入 进一取整 舍已取证
        var number1 = 121.09;
        var number2 = 121.99;

        console.log(Math.round(number1), Math.round(number2));  //四舍五入
        console.log(Math.ceil(number1), Math.ceil(number2));  //ceil进一取整 天花板
        console.log(Math.floor(number1), Math.floor(number2));  //floor舍一取整 地板
        console.log('');


        console.log(Math.max(100, 23, 101, 6, 1000, 299));
        console.log(Math.min(100, 23, 101, 6, 1000, 299));
        console.log('');


        console.log(Math.random());  //返回是小数 0~1之间； 可能等于0，但绝对不会等于=1
    </script>
```

#### ①随机数

```html
<script>
        // 取 0~9之间的随机数（整数）
        console.log(Math.floor(Math.random() * 10));

        // 取0~10之间的随机数（整数）
        console.log(Math.round(Math.random() * 10));

        // 不太好 1~10 但是0也是有可能， 概率极低
        //console.log(Math.ceil(Math.random() * 10));

        // 取0~16 之间的随机数
        console.log(Math.floor(Math.random() * 17));

        // 随机取 3~17之间的随机数
        console.log(Math.floor(Math.random() * 15) + 3);

    </script>
```

#### ②随机点名器

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>内置对象</title>
    <style>
        body {
            text-align: center;
        }
        #box {
            margin: 50px;
            font-size: 120px;
        }
        button {
            border: 1px solid #ccc;
            border-radius: 5px;
            width: 100px;
            padding:20px;
            background: #f5f5f5;
            font-size: 16px;
            outline: none;
        }
    </style>
</head>
<body>

    <div id="box">随机点名器</div>
    <button id="btn">开 始</button>

    <script>
        // 定义数组，存储姓名
        var nameList = ['曹操', '张飞', '赵云', '于禁', '关羽', '许褚', '孙悟空', '白骨精', '贾宝玉', '潘金莲'];

        //获取相关元素
        var box = document.getElementById('box');
        var btn = document.getElementById('btn');

        // 定义全局变量 标记定时器标记
        var intervalId = null;

        // 给按钮绑定事件
        btn.onclick = function(){
            //判断是开始还是停止
            if (this.innerHTML === '开 始') {
                //设置按钮文字 为停止
                this.innerHTML = '停 止';
                // 开始定时
                intervalId = setInterval(function () {
                    // 计算随机的索引 0~nameList.length - 1
                    var index = Math.floor(Math.random() * nameList.length);
                    //随机从数组中去数据
                    var name = nameList[index];
                    // 设置div的内容
                    box.innerHTML = name;
                }, 100);

            } else if (this.innerHTML === '停 止') {
                console.log(intervalId);
                // 设置按钮文字 为开始
                this.innerHTML = '开 始';
                // 结束定时
                clearInterval(intervalId);

            }
        }

    </script>
</body>
</html>
```



## 2. Date(年月日时间)

Date是构造函数,需要先实例化对象

var date = new Date();不写参数可以获取当前的时间,如果写参数会修改里面的时间;

#### 方法

```
getFullYear()   年 公元纪年
getMonth()      范围是0~11 需要+1
getDate()       日 几号
getDay()        星期几
getHours()      几点（24）
getMinutes()    几分
getSeconds()    几秒
getMilliseconds()  几毫秒
getTime()       时间戳（毫秒） 1970年月1日0时0分0秒至今的毫秒数

getUTC...       得到标准时区的 年月日时分秒

set...           设置年月日时分秒
setUTC...        设置标准时区的年月日时分秒

toLocaleString()
toLocaleTimeString()
toLocaleDateString()
```

```html
<script>
        // 创建日期对象
        var date = new Date();

        console.log(date);

        // 设置date的日期事件
        date.setFullYear(1978);
        date.setMonth(11);
        date.setHours(7);
        date.setTime(10000);
        date.setUTCHours(12);

        // 当前年
        console.log(date.getYear()); //119
        console.log(date.getFullYear()); //2019 公元纪年

        // 当前月
        console.log(date.getMonth() + 1);  // 范围是0~11

        // 当前日 每月几号
        console.log(date.getDate());

        // 当前星期几
        console.log(date.getDay());
        console.log('');


        console.log('小时：'+date.getHours());
        console.log('分：'+date.getMinutes());
        console.log('秒：'+date.getSeconds());
        console.log('毫秒：'+date.getMilliseconds());
        console.log('');
        console.log('');


        // UTC系列  获取的是标准时区事件，0时区时间；
        console.log(date.getUTCFullYear());
        console.log(date.getUTCMonth() + 1);
        console.log(date.getUTCDate());
        console.log(date.getUTCDay());
        console.log('伦敦时间：'+date.getUTCHours());
        console.log(date.getUTCMinutes());
        console.log(date.getUTCSeconds());

        console.log('');
        console.log('');

        // 1970年1月1日0点0分0秒 至今的 毫秒数
        // unix元年
        // 时间戳（1970年1月1日0点0分0秒 至今的 秒数）
        console.log(date.getTime());
        console.log('');
        console.log('');


        console.log(date.getTimezoneOffset());

        console.log('');
        console.log('');

        console.log(date.toLocaleString());
        console.log(date.toLocaleTimeString());
        console.log(date.toLocaleDateString());

    </script>
```

#### ①电子时钟

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>内置对象</title>
    <style>
        #watch {
            margin-top: 100px;
            font-size: 40px;
            text-align: center;
        }
    </style>
</head>
<body>

    <div id="watch"></div>

    <script>
        runTime(); //先计算一下 当前时间

        //开启定时
        setInterval(runTime, 1000);

        // 定义函数
        function runTime(){
            //实例化 date对象
            var date = new Date();
            // 分别获取年月日时分秒
            var y = date.getFullYear();
            var m = date.getMonth()+1;
            var d = date.getDate();
            var h = date.getHours();
            var i = date.getMinutes();
            var s = date.getSeconds();
            // 判断如果是个位数 补0
            m = m < 10 ? '0' + m : m;
            d = d < 10 ? '0' + d : d;
            h = h < 10 ? '0' + h : h;
            i = i < 10 ? '0' + i : i;
            s = s < 10 ? '0' + s : s;
            //组合一个时间日期字符串
            var datetimeStr = y+'年'+m+'月'+d+'日 '+h+':'+i+':'+s;
            //显示时间
            document.getElementById('watch').innerHTML = datetimeStr;
        }
    </script>
</body>
</html>
```



## 3. Array(数组)

#### ① 属性

```
length
```

#### ② 方法

```
push()
pop()
unshift()
shift()
reverse()
sort()
splice()
---------------------------
concat()
join()
slice()
```

#### ④ ES5新增的方法

```
forEach()  用于数组遍历
filter()   用于数组过滤，参数是回调函数，返回过滤好的数组
map()      用于统一处理数组元素，参数是回调函数，返回处理好的数组
```

```html
 <script>
        //ES5 数组对象新增的方法

        //定义数组
        var stuInfos = [
            {
                name:'曹操',
                age: 18,
                sorce: 45
            },
            {
                name:'曹丕',
                age: 26,
                sorce: 65
            },
            {
                name:'曹植',
                age: 41,
                sorce: 57
            },
            {
                name:'曹冲',
                age: 27,
                sorce: 88
            },
            {
                name:'曹昂',
                age: 19,
                sorce: 75
            }
        ];


        //forEach 遍历数组
        // forEach 没有返回值
        stuInfos.forEach(function(item,index){
            console.log(item, index);
        });
        [100,200,300,400].forEach(function (item) {
            console.log(item);
        });

        console.log('');


        // filter 过滤
        // 要求回调函数 返回布尔值
        // 把不及格的过滤的
        var stuFilterInfos = stuInfos.filter(function(item,index){
            //console.log(item, index);
            if (item.sorce >= 60) {
                return true;
            } else {
                return false;
            }
        });
        console.log(stuFilterInfos);
        console.log('');


        // map
        // 用于对数组的每个元素进行处理， 过了一年了，把每个人的年龄+1
        var stuMapInfos = stuInfos.map(function(item, index){
            item['age'] ++;
            return item;
        });
        console.log(stuMapInfos);

    </script>
```



## 练习

```
① 倒计时， 距离春节还有 123天8小时23分钟15秒
② 钟表（转） （选做）
```

#### ①倒计时

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>倒计时</title>
    <style>
        #box {
            margin-top: 100px;
            font-size: 40px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div id="box"></div>
    <script>
        // 定义一个结束日期对象
        var endDate = new Date('2019-10-22 09:20:00');

        //开启定时之前，先计算一下时间
        runTime();

        // 开启定时器
        var intervalId = setInterval(runTime, 1000);

        // 定义定时函数
        function runTime(){
            //创建当前的日期
            var currDate = new Date();
            // 计算结束的日期与当前日期的差 （秒）
            var seconds = parseInt((endDate.getTime() - currDate.getTime()) / 1000);
            //如果seconds 小于等于 0， 定时器要停止
            if (seconds <= 0) {
                document.getElementById('box').innerText = '新年快乐!';
                clearInterval(intervalId);
                return;
            }

            // 计算包含的整天数
            var d = parseInt(seconds / (3600 * 24));
            // 计算剩下的秒数
            var s = seconds % (3600 * 24);
            // 计算剩下的秒数里包含的小时
            var h = parseInt(s / 3600);
            // 再次计算剩下的秒数
            s %= 3600;   //s = s % 3600
            // 计算剩下的秒数里包含的分钟数
            var m = parseInt(s / 60)
            // 最后计算剩下的秒数
            s %= 60;

            // 处理 日时分秒 如果是个位数前面补0
            d = d < 10 ? '0' + d : d;
            h = h < 10 ? '0' + h : h;
            m = m < 10 ? '0' + m : m;
            s = s < 10 ? '0' + s : s;

            // 拼装字符串
            var html = '距离全面小康还有'+d+'天'+h+'小时'+m+'分钟'+s+'秒';

            // 显示到页面
            document.getElementById('box').innerText = html;
        }
    </script>
</body>
</html>
```



# 第十天，JavaScript 课堂笔记

## 回顾

### 1 定时器函数

```
setInterval()
setTimeout()
clearInterval()
clearTimeout()
```



### 2. Math

```
Math.PI

Math.abs()
Math.sqrt()
Math.pow()
Math.max()
Math.min()
Math.round()
Math.floor()  parseInt()
Math.ceil()
Math.random()

```



### 3. Date

```
getFullYear()
getMonth()+1
getDate()   
getHours()
getMinutes()
getSeconds()
getMilliseconds()
getDay()
getTime()

getUTC....

set...
setUTC...

```



## 以下第十天课程

## 内置对象

### 1 Array

#### ① 属性

```
length
```

#### ② 方法

```
push()
pop()
unshift()
shift()
splice()
reverse()
sort()
------------------
join()
slice()
concat()
```

#### ③ ES5新增方法

```
forEach()	遍历数组
filter()	过滤。 回调函数返回布尔值（true-->当前的元素留下， false-->当前的元素去掉）
map()		map用于对数组的每个元素都进行处理， 回调函数返回什么，最终得到的数组的元素就是什么。
----------------------------------------以上昨天已讲
every()     数组的每个元素都满足某个条件，返回true
some()      数组中只要有元素满足条件，返回true
reduce()	对数组的元素进行组合  从左到右
reduceRight()  对数组元素进行组合  从右到左
indexOf()		某个元素在数组中第一次出现的位置(如同字符串一样)
lastIndexOf()	某个元素在数组中最后一次出现的位置(如同字符串一样)
```

```html
<script>
    //定义数组
    var stuInfos = [
        {
            name:'曹操',
            age: 18,
            sorce: 45
        },
        {
            name:'曹丕',
            age: 26,
            sorce: 65
        },
        {
            name:'曹植',
            age: 41,
            sorce: 57
        },
        {
            name:'曹冲',
            age: 27,
            sorce: 88
        },
        {
            name:'曹昂',
            age: 19,
            sorce: 75
        }
    ];

    // 判断是不是每个人都成年了
    var res = stuInfos.every(function(item, index){
        if (item.age >= 18) {
            return true;
        }
    });
    console.log(res);
    // 判断是否每个人都及格了
    var res1 = stuInfos.every(function (item) {
        if (item.sorce >= 60) {
            return true;
        }
    });
    console.log(res1);
    console.log('');


    // some()  只有有个元素满足条件就算满足条件了
    //只要有人及格，就胜利了
    var res2 = stuInfos.some(function (item, index) {
        if (item.sorce >= 60) {
            return true;
        }
    });
    console.log(res2);
    // 要求团队中必须有未成年人
    var res3 = stuInfos.some(function (item) {
       if (item.age < 18) {
           return true;
       }
    });
    console.log(res3);
    console.log('');


    // reduct  把数组的元素进行组合
    // 回调函数接受两个参数，第一个是上一个回调函数的返回值， 第二个当前的数组元素
    // 对数组中的元素进行统一的计算
    // 最后一次回调韩调用的返回值 就是reduce的返回值
   /* stuInfos.reduce(function(res, item){
       console.log(res, item);
       return 100;
    }, 'hello');*/
    // 计算所有人年龄之和
    var sumAges = stuInfos.reduce(function(res, item) {
        //console.log(res, item.age);
        return res + item.age;
    }, 0);
    console.log(sumAges);
    // 实现所有元素之和
    var sum = [10,20,30,40,50].reduce(function(res, item) {
        return res + item;
    });
    console.log(sum);
    // 把二维数组 变为一维数组
    var arr = [[10,20,30,40], ['a','b','c'], [100, 'hello', 'dds', '123123', '小莉莉']];
    console.log(arr);
    // 把二维数组，转为一维数组
    var newArr = arr.reduce(function(res, item){
        return res.concat(item);
    });
    console.log(newArr);
    console.log('');


    [10,20,30,40].reduceRight(function (res, item) {
        console.log(res, item);
        return res + item;
    }, 0);

    console.log('');


    var nubmers = [10,23,30,40,540, 23, 60];
    console.log(nubmers.indexOf(23))
    console.log(nubmers.lastIndexOf(23))
    console.log(nubmers.lastIndexOf('hello'))

</script>
```



### 2 Function

#### ① 属性

```
length
prototyoe
```

#### ② 方法

```
call()		在调用函数的同时设置this的指向； call() 任意参数，第一个参数就是this的指向
applay()	在调用函数的同时设置this的指向； applay两个参数，第一个参数是this的指向，第二个是数组
bind()		返回新的函数，新函数内的this已经被重新设置了 （ES5新增的）
```

```html
<script>
    var name = '曹雪芹';
   //定义函数
    function demo(a,b,c){
        console.log(this);
        console.log('啊，调用了', a,b,c);
    }

    var obj = {
        name: '曹操',
        say: function(){
            console.log(this.name);
        }
    };


    console.log(demo.length);
    console.log(obj.say.length);
    console.log('');


    // applay 可以把函数给调用了
    // 在调用函数的同时，可以修改this的指向。
    demo.apply({name:'贾宝玉'}, [10,20,30]); //this指向applay第一个参数


    // 一般方法 调用韩
    demo(100, 300, 600); //this->window

    obj.say.apply(window);
    console.log('');


    //call 与applay是相同的意思
    demo.call([10,20], '张姥姥', '刘姥姥', '欧阳姥姥');
    obj.say.call({name:'孙悟空'});
    console.log('');


    // bind 不会让方法执行
    // 返回值的function，返回的fnuction里面的this已经修改了
    var fn = obj.say.bind({name:'唐长老'});
    fn();

    var fun = demo.bind([10,20]);
    fun(100, 200, 300);

</script>
```

#### call和applay的实际应用

```html
<script>
    function sum() {
        //console.log(arguments);
        //遍历arguments
        /*arguments.forEach(function (item, index) {
            console.log(item, index);
        })*/
/*
        [].forEach.call(arguments, function(item, index){
            console.log(item, index);
        });*/

        [].forEach.apply(arguments, [function(item, index){
            console.log(item, index);
        }]);
    }

    sum(10,23,234,234,212,121,23,34,34);

</script>
```



### 3 Object对象(后期再学)

### 4 Global对象

```
全局对象

方法：
	escape() 把中文和特殊符号转为unicode编码
	unescape() unicode解码
	eval()  把字符串当做代码执行（不建议）
```

```html
<script>
    //escape    只能对汉字编码
    console.log(escape('你好'));

    //解码
    console.log(unescape('%u4F60%u597D'));

    //参数是字符串
    //把字符串当做代码去执行
    eval('alert("OK")');
</script>
```



### 5 JSON对象

```
parse()   把json格式的字符串转为数组或对象
stringify  把对象或数组转为json格式的字符串
```

```html
<script>
    // JSON是一个字符串，有格式

    // 获取后端的数据
    var dataStr = '[\n' +
        '  {\n' +
        '    "name":"曹操",\n' +
        '    "age": 18,\n' +
        '    "sorce": 56\n' +
        '  },\n' +
        '  {\n' +
        '    "name":"曹植",\n' +
        '    "age": 28,\n' +
        '    "sorce": 56\n' +
        '  }\n' +
        ']';

    console.log(dataStr);

    //把json格式的字符串 转为 JS的数组或对象
    var data = JSON.parse(dataStr);
    console.log(data);

    // 把JS的数组或对象转为JSON格式的字符串
    var arr = [100,200,300,400];
    var obj = {name:'小艳艳', age: 18};

    console.log(JSON.stringify(arr))
    console.log(JSON.stringify(obj))

</script>
```



## 严格模式

```js
'use strict';  //开启严格模式
```

```
严格模式，有些JS的老旧不可用
	声明必须使用var
	eval() 无法执行字符串代码
```

## 检查错误

```html
<script>

    try {
        //demo();
        var a = 100;
        var obj = {};


        console.log(obj.userinfo.name);
    } catch {
        console.log('发生错误了');
    } finally {

    }

    // 不影响后面代码执行
    console.log('OK');

</script>
```



## BOM 浏览器对象模型

### 1. window

#### ① 属性

```
document
history
location
screen
navigator

innerWidth / innerHeight   是视口的宽度（页面中的文档区域）
outerWidth / outerHeight   是浏览器窗口的宽高
name   标记窗口的名字/系统要求name的值必须是字符串，如果设置了其他类型也会自动转为字符串！！
```

#### ② 方法

```
alert（） 警告框
confirm()  确认框
prompt()  输出框
setInterval()
setTimeout()
clearInterval()
clearTimeout()
open()  打开一个窗口 参数一：地址  参数二：窗口名字  参数三：指定窗口大小 width=400,height=300
close()  关闭窗口（只有open打开才能关闭）
print() 调用打印
scrollTo(x, y) 页面滚动到指定的坐标位置
scrollBy(x, y) 页面滚动多少距离
```

```html
<body>
    <button onclick="alert('警告框')">alert</button>
    <button onclick="confirm('确认框')">confirm</button>
    <br>
    <br>

    <button onclick="window.open('11.html')">open</button>
    <button onclick="window.open('http://www.atguigu.com', '小艳艳')">open本窗口</button>
    <button onclick="window.open('http://www.atguigu.com', '', 'width=400,height=300')">open指定打开窗口的大小</button>
    <br>
    <br>
    <button onclick="window.print()">打印订单</button>


    <script>

        // 以下是属性
        console.log(window.innerWidth, window.innerHeight);
        console.log(window.outerWidth, window.outerHeight);

        var name = 'hello wrold';
        name = [100, 200, 300, 4000];
        console.log(window.name); //window.name的值必须是个字符串（系统要求的）
        console.log(name);
        console.log(typeof name);

        window.name = '小艳艳';
    </script>
</body>
```

```html
<head>
    <meta charset="UTF-8">
    <title>window</title>
    <style>
        #gotoTop {
            width: 50px;
            height: 50px;
            color: #fff;
            background: rgba(0, 0, 0, .8);
            line-height: 50px;
            text-align: center;
            cursor: pointer;
            position: fixed;
            right: 10px;
            bottom: 20px;
            user-select: none;
        }
    </style>
</head>
<body>

    <div style="height: 500px;background-color:pink">
        <a href="14history.html">14history</a>
    </div>
    <div style="height: 500px;background-color:#f90"></div>
    <div style="height: 500px;background-color:yellowgreen"></div>

    <div id="gotoTop">TOP</div>

    <script>
        //获取返回顶部的按钮
        var gotoTop = document.getElementById('gotoTop');
        //定义定时标记
        var intervalId = null;
        // 绑定单击事件
        gotoTop.onclick = function(){

            intervalId = setInterval(function () {
                //先获取一下页面滚动的距离
                var top = document.documentElement.scrollTop || document.body.scrollTop;
                //如果页面滚到顶了
                if (top <= 0) {
                    clearInterval(intervalId);
                    return;
                }
                window.scrollBy(0, -20);
            }, 10);
        }

    </script>
</body>
</html>
```



### 2. history

history 对象表示窗口的历史记录

#### ① 属性

```
length
```

#### ② 方法

```
back()
forward()
go()
```

```html
<body>

        <button onclick="history.back()">返回上一步</button>
        <button onclick="history.go(-1)">go返回上一步</button>
        <button onclick="history.go(-2)">go返回上两步</button>
        <br>
        <br>
        <button onclick="history.forward()">下一步</button>
        <button onclick="history.go(1)">go下一步</button>
        <button onclick="history.go(2)">go下两步</button>

        <br>
        <br>
        <br>
        <br>
        <hr>
        <a href="http://www.atguigu.com">超链接</a>

    <script>
        console.log('本窗口的历史记录的个数：'+history.length);
    </script>
</body>
```



### 3. location

location描述地址信息，location和他的属性可读可写

#### ① 属性

```
href 完整的URL
protocol 协议部分
hostname  主机名部分
port 端口
host  主机名+端口
pathname  路径部分
search   ?搜索部分
hash    锚点部分
```

#### ② 方法

```
reload() 页面重新加载
assign()	打开一个新的页面
replace()   打开新的页面（会把当前页面的历史记录抹掉）
```

```html
<body>
    <button onclick="location.reload()">刷新</button>
    <br>
    <br>
    <button onclick="location.assign('http://www.baidu.com')">assign</button>
    <button onclick="location.replace('http://www.baidu.com')">replace</button>

    <script>
        console.log(location);

        console.log('完整的URL：'+location.href);
        // http://www.baidu.com:8080/images/index.html?kw=hello#mao

        console.log('协议：'+location.protocol);
        console.log('主机名：'+location.hostname);
        console.log('端口号：'+location.port);
        console.log('主机名+端口号：'+location.host);
        console.log('路径：'+location.pathname);
        console.log('请求部分：'+location.search);
        console.log('锚点部分：'+location.hash);

        // location和他的属性 可读可写
        //location.href = 'http://www.baidu.com';
        //location.search = '';
        //location.hostname = '127.0.0.1';

        //location.protocol = 'https:'
    </script>
</body>
```



### 4. screen( 屏幕)

#### 属性

```
width 屏幕宽高
height
```



### 5. navigator

#### 属性

```
userAgent   获取用户浏览器的信息
```

```html
<body>
    <div id="box"></div>

    <script>
        document.getElementById('box').innerHTML = navigator.userAgent;
    </script>
</body>
```





# 第十一天，JavaScript 课堂笔记

## 回顾

## BOM 浏览器对象模型

### 1 window

```
属性：
innerWidth/innerHeight
outerWidth/outerHeight

方法：
open()
close() 
print()
scrollTo()
scrollBy()
```



### 2. history

```
属性：
length
方法：
back()
go()
forward()
```



### 3. location

```
属性：
	href
	protocol
	hostname
	port
	host
	pathname
	search
	hash

方法：
	reload()
	assign()
	replace()
```



### 4 screen

```
width/height
```



### 5 navigator

```
userAgent
```



## 以下是第十一天的课程



## DOM  文档对象模型

### 1 DOM概述

#### 1.1 XML DOM 和 HTML DOM

```
XML: 可扩展标记语言
HTML: 超文本标记语言

XML DOM： 规定了所有的元素都具有的属性和方法
HTML DOM： 规定了不同的标签元素各自特有的属性和方法
```

#### 1.2 DOM树

```
父元素
子元素
兄弟元素 （具有相同父元素）
祖先元素
后代元素
```

#### 1.3 DOM版本

```
0级DOM DOM0
1级DOM DOM1
2级DOM DOM2
3级DOM DOM3
```



### 2 节点 node

#### 2.1 节点的定义

文档中每一部分都是节点

#### 2.2 节点的分类

- document
- elementNode  元素节点  
- attributeNode  属性节点
- textNode  文本节点
- commentNode 注释节点

#### 2.3 节点属性

- nodeName  节点名     元素节点通过nodeName可以获取标签名
- nodeValue  节点值
- nodeType  节点类型 数字； document（9） element(1)  attribute(2)  text(3)   comment(8)

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
</head>
<body>
    <div id="box" class="item">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Repellat, sunt.
        <!--哈哈我是注释-->
        <p>Lorem ipsum dolor sit amet.</p>
    </div>

    <script>
        // document 节点
        console.log(document);
        console.log(document.constructor);  //HTMLDocument
        console.log(document.nodeName);     //#document
        console.log(document.nodeValue);    //null
        console.log(document.nodeType);     //9
        console.log('');


        //element节点 元素
        var element = document.getElementById('box');
        console.log(element);  //HTMLDivElement()
        console.log(element.constructor);
        console.log('nodeName : '+element.nodeName);   //DIV 标签名
        console.log('nodeValue : '+element.nodeValue); // null
        console.log('nodeType : '+element.nodeType); //1
        console.log('');


        // 属性节点
        //获取属性节点 通过元素
        var propNode = element.getAttributeNode('id');
        console.log(propNode);
        console.log(propNode.constructor);  // Attr（）
        console.log('nodeName : '+propNode.nodeName);  //id 属性节点的名字
        console.log('nodeValue : '+propNode.nodeValue); //box  属性对应的值
        console.log('nodeType : '+propNode.nodeType);  // 2
        console.log('');


        // 文本节点
        // 获取文本节点
        var text = element.firstChild; //第一个子节点
        console.log(text);
        console.log(text.constructor); //Text()
        console.log('nodeName : '+text.nodeName);  // #text
        console.log('nodeValue : '+text.nodeValue); // 文本的内容
        console.log('nodeType : '+text.nodeType); // 3
        console.log('');


        // 注释节点
        // 获取注释节点
        var comment = element.childNodes[1];
        console.log(comment);
        console.log(comment.constructor);  //Comment
        console.log('nodeName : '+comment.nodeName);  //#comment
        console.log('nodeValue : '+comment.nodeValue);  //#注释的内容
        console.log('nodeType : '+comment.nodeType);  // 8

    </script>

</body>
</html>
```



### 3 获取元素

#### 1.1 根据id名获取

```js
document.getElementById(idName)
element.getElementById(idName)
```

#### 1.2 根据标签名获取

```js
document.getElementsByTagName(tagName)   // 返回一个集合 （类数组对象）  从整个文档获取
element.getElementsByTagName(tagName)    // 从element的后代元素中获取
```

#### 1.3 根据类名获取 (IE9+)

```js
document.getElementsByClassName(className)   // 返回一个集合（类数组对象）  从整个文档获取
element.getElementsByClassName(className)   // 从element的后代中获取
```

#### 1.4 根据name属性值获取

```js
document.getElementsByName()  //返回集合  只有document才有该方法
```

#### 1.5 根据选择器获取 （推荐） （IE8+）

```js
document.querySelector(选择器)   //选择器第一个满足选择器条件的
document.querySelectorAll(选择器) //选择所有满足选择器条件的，返回nodeList（类数组对象）
element.querySelector(选择器)
element.querySelectorAll(选择器)
```

#### 1.6 获取所有的元素

```js
document.all  //所有的元素组成的集合（类数组对象）
```

```js
//document.all的妙用
if (document.all) {
    //说明是IE浏览器   IE10以及以下版本
} else {
    // 说明非IE浏览器 IE11以及EDGE 
}
```

```html
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
</head>
<body>
    <h1 id="title">DOM</h1>
    <ul class="list" id="myList">
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li name="yanyan">Lorem ipsum dolor sit amet.</li>
    </ul>
    <ol>
        <li>Lorem ipsum dolor.</li>
        <li>Lorem ipsum dolor.</li>
        <li name="yanyan">Lorem ipsum dolor.</li>
        <li>Lorem ipsum dolor.</li>
        <li>Lorem ipsum dolor.</li>
    </ol>


    <script>
        // 根据ID来获取元素
        var ul = document.getElementById('myList');
        console.log(ul);
        console.log('');


        // 根据标签名 来获取元素
        var lis = document.getElementsByTagName('li'); //获取一个所有的li元素组成的伪数组
        console.log(lis);
        console.log(lis.constructor);
        console.log(lis.length);
        var h1 = document.getElementsByTagName('h1');  //获取集合
        console.log(h1);
        var lis2 = ul.getElementsByTagName('li');
        console.log(lis2);
        console.log('');


        // 通过类名
        var ul2 = document.getElementsByClassName('list');
        var ul3 = ul.getElementsByClassName('list');
        console.log(ul2);
        console.log(ul3);
        console.log('');


        // 通过name属性的值
        var liss = document.getElementsByName('yanyan');
        //console.log(ul);
        //var liss2 = ul.getElementsByName('yanyan');
        console.log(liss);
        console.log('');



        // 根据选择器 css选择器
        var h1 = document.querySelector('#title');
        var ul = document.querySelector('.list');
        var li = document.querySelector('.list li:first-child');  //返回满足条件的第一个
        var lis = document.querySelectorAll('.list li');
        var title = document.querySelectorAll('#title');
        var lis2 = ul.querySelectorAll('li');
        console.log(h1);
        console.log(ul);
        console.log(li);
        console.log(lis);
        console.log(title);
        console.log(lis2);
        console.log('');


        console.log(document.all);


       /* if (document.all) {
            console.log('成立');
        } else {
            console.log('不成立');
        }*/


// 快速判断IE浏览器
        if (document.all) {
        document.write('我是IE浏览器');
    } else {
        document.write('我不是IE浏览器');
    }
    </script>
</body>
</html>
```

#### ①处理元素的集合

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
</head>
<body>
    <ul class="list">
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
    </ul>

    <button id="btn">更改li内的文字</button>

    <script>
        //获取按钮
        var btn = document.querySelector('#btn');

        // 给按钮绑定事件
        btn.onclick = function(){
            //获取所有的li
            var lis = document.querySelectorAll('.list li');
            //遍历 nodeList
            // 不要使用for ... in
            /*for (var i in lis) {
                console.log(lis[i], i);
            }*/

            // 可以使用for循环
            /*for (var i = 0; i < lis.length; i ++) {
                //console.log(lis[i]);
                lis[i].innerHTML = '第'+i+'个小艳艳';
            }*/

            // forEach ES5 IE9+
            lis.forEach(function (item, index) {
               item.innerHTML = '第'+index+'个小艳艳';
            });
        }
    </script>
</body>
</html>
```



### 4 文档结构

#### 4.1 作为节点树

```
parentNode    父节点
childNode     所有子节点的集合
firstChild    第一个子节点
lastChild     最后一个子节点
previousSibling   上一个兄弟节点
nextSibling       下一个兄弟节点
```

#### 4.2 作为元素树

```
parentElement  父元素
children     所有子元素的集合
firstElementChild   第一个子元素  IE9+
lastElementChild    最后一个子元素 IE9+
previousElementSibling  上一个兄弟元素
nextElementSibling    下一个兄弟元素
childElementCount    子元素的数量
ownerDocument     元素所属的文档对象（document）
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
</head>
<body>
    <ul class="list">
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li id="myLi">Lorem ipsum dolor sit amet.</li><li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
    </ul>


    <script>
        var ul = document.querySelector('.list');

        console.log(ul);
        console.log('');

        // 获取某个元素的父元素
        console.log(ul.parentNode, ul.parentElement); //父节点 父元素
        console.log(ul.parentNode.parentNode, ul.parentElement.parentElement);
        console.log(ul.parentNode.parentNode.parentNode, ul.parentElement.parentElement.parentElement);
        //console.log(ul.parentNode.parentNode.parentNode.parentNode);
        console.log('');


        // 子元素
        console.log(ul.childNodes); //所有的子节点
        console.log(ul.children); //所有的子元素
        console.log(ul.firstChild);   // 第一个子节点
        console.log(ul.firstElementChild); //第一个子元素
        console.log(ul.lastChild); //最后一个子节点
        console.log(ul.lastElementChild); //最后一个子元素
        console.log(ul.children[1]);//第二个子元素
        console.log('');

        // 兄弟元素
        var myLi = document.querySelector('#myLi');
        console.log(myLi.previousSibling, myLi.previousElementSibling);
        console.log(myLi.nextSibling, myLi.nextElementSibling);
        console.log('');


        console.log(ul.childElementCount);
        console.log(ul.ownerDocument);
        console.log(myLi.ownerDocument);

    </script>
</body>
</html>
```



### 5 属性操作

#### 5.1 内置属性

```
element.属性名;  可读可写
```

#### 5.2 自定义属性

```
element.getAttribute(attrName)  获取属性的值（只有写到html上的属性，都可获取；一般用于自定义属性）
element.setAttribute(attrName, value)   设置属性的值（一般用于自定义属性）
element.removeAttribute('');移除属性
```

#### 5.3 `data-`开头的自定义属性

```
element.dataset.名字  可读可写
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
</head>
<body>
    <button id="btn1">修改图片路径</button>
    <button id="btn2">大</button>
    <hr>
    <hr>
    <img src="1.jpg" alt="小艳艳" width="300" loadpic="100.jpg" data-name="艳艳" data-age="19">


    <script>

        //获取img元素对象
        var imgNode = document.querySelector('img');

        // 获取某个属性的值
        // 一个html标签变为以js元素对象之后，标签的属性会映射到元素对象
        console.dir(imgNode);
        console.log(imgNode.src);
        console.log(imgNode.width);
        console.log(imgNode.alt);
        console.log(imgNode.height);
        console.log('');

        // 自定义属性
        console.log(imgNode.getAttribute('loadpic'));
        console.log(imgNode.getAttribute('src'));
        console.log(imgNode.getAttribute('width'));
        console.log(imgNode.getAttribute('height')); //null
        console.log('');

        //如果属性是data-开头的
        console.log(imgNode.getAttribute('data-name'));
        console.log(imgNode.dataset.name);
        console.log(imgNode.dataset.age);

        //设置自定义属性
        //imgNode.mmdds = 'hello艳艳';
        imgNode.setAttribute('mmdds', 'hello艳艳');
        imgNode.dataset.age = 100;

        // 获取按钮
        var btn1 = document.querySelector('#btn1');
        var btn2 = document.querySelector('#btn2');
        btn1.onclick = function(){
            imgNode.src = 'http://e.hiphotos.baidu.com/image/pic/item/dc54564e9258d1092f7663c9db58ccbf6c814d30.jpg';
        };
        btn2.onclick  = function(){
            imgNode.width += 10; // imgNode.width = imgNode.width + 10
            //console.log(imgNode.width); //是一个数字
        };

    </script>
</body>
</html>
```



### 6 CSS操作

#### 6.1 style属性

```js
element,style.属性名  读写css属性

只能读写标签内写在style里面的css属性，设置的css属性添加到标签内的style里
```

#### 6.2 读取计算样式（只读，window的方法）

```
getComputed(元素).属性； //非IE(IE11和Edge)
元素.currentStyle.属性   //IE   获取不到复合属性(background、border)
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
    <style>
        #box {
            width: 400px;
            height: 200px;
            border: 1px solid #333;
        }
    </style>
</head>
<body>
    <button id="btn1">变色</button>
    <button id="btn2">变大</button>
    <hr>
    <hr>
    <div id="box" style="width:200px;height:200px"></div>


    <script>

        // 获取元素
        var box = document.querySelector('#box');
        // 获取按钮
        var btn1 = document.querySelector('#btn1');
        var btn2 = document.querySelector('#btn2');

        // 事件
        btn1.onclick = function(){
            //box.style.background = '#f90';
            //box.style['background-color'] = '#f90';
            box.style.backgroundColor = 'red';
        };

        btn2.onclick = function(){
            //box.style.width = 300+'px'; //注意拼接单位
            // 通过style获取属性的值。css属性必须写到标签内的style上
            //console.log(box.style.width);

            box.style.width = parseInt(box.style.width) + 50 + 'px';
            box.style.height = parseInt(box.style.height) + 50 + 'px';
        };



        // 获取写到style标签或者外部css 的属性性
        // 最终生效的css属性
        // 非IE可以使用
        if (window.getComputedStyle) {
            console.log(getComputedStyle(box).width);
            console.log(getComputedStyle(box).height);
            console.log(getComputedStyle(box).border);
            console.log(getComputedStyle(box).backgroundColor);//没写，取默认值
            console.log(getComputedStyle(box).fontSize);//没写，取默认值
        } else if (box.currentStyle) {
            //IE
            console.log(box.currentStyle.width);
            console.log(box.currentStyle.height);
            console.log(box.currentStyle.borderColor);
            console.log(box.currentStyle.borderWidth);
            console.log(box.currentStyle.borderStyle);
            console.log(box.currentStyle.fontSize);
        }

    </script>
</body>
</html>
```

#### ①全选全不选反选案列

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
    <style>
      
    </style>
</head>
<body>
    <ul class="list">
        <li><input type="checkbox"> Lorem ipsum dolor sit amet.</li>
        <li><input type="checkbox"> Lorem ipsum dolor sit amet.</li>
        <li><input type="checkbox"> Lorem ipsum dolor sit amet.</li>
        <li><input type="checkbox" checked> Lorem ipsum dolor sit amet.</li>
        <li><input type="checkbox"> Lorem ipsum dolor sit amet.</li>
        <li><input type="checkbox"> Lorem ipsum dolor sit amet.</li>
        <li><input type="checkbox"> Lorem ipsum dolor sit amet.</li>
        <li><input type="checkbox"> Lorem ipsum dolor sit amet.</li>
    </ul>
    <button id="btn1">全选</button>
    <button id="btn2">全不选</button>
    <button id="btn3">反选</button>


    <script>

        // 获取元素
        var btn1 = document.querySelector('#btn1');
        var btn2 = document.querySelector('#btn2');
        var btn3 = document.querySelector('#btn3');

        //获取所有input:checkbox 元素
        var inputs = document.querySelectorAll('.list input[type=checkbox]');

        // 绑定单击事件
        btn1.onclick = function(){
            //遍历
            inputs.forEach(function (input) {
               input.checked = true;
            });
        };

        // 全不选
        btn2.onclick = function(){
            //遍历
            inputs.forEach(function(input){
                input.checked = false;
            })
        };

        // 反选
        btn3.onclick = function(){
            //遍历
            inputs.forEach(function (input) {
              /* if (input.checked) {
                   input.checked = false;
               } else {
                   input.checked = true;
               }*/
               input.checked = !input.checked;
            });
        }
    </script>
</body>
</html>
```



#### ②点击背景设置颜色案列

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
    <style>
        .list {
            list-style: none;
            width: 800px;
            margin: 100px auto;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
        }
        .list li {
            width: 160px;
            margin-top: 20px;
            height: 50px;
            text-align: center;
            line-height: 50px;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
    <ul class="list">
       <li>Lorem ipsum.</li>
       <li>Lorem ipsum.</li>
       <li>Lorem ipsum.</li>
       <li>Lorem ipsum.</li>
       <li>Lorem ipsum.</li>
       <li>Lorem ipsum.</li>
       <li>Lorem ipsum.</li>
       <li>Lorem ipsum.</li>
       <li>Lorem ipsum.</li>
    </ul>

    <script>
        //获取所有的li
        var lis = document.querySelectorAll('.list li');

        // 遍历
        lis.forEach(function (liItem) {
           //给每个li绑定单击事件
            liItem.onclick = function(){
                //判断当前的li是选中还是不选中
                if (liItem.style.backgroundColor === 'rgb(255, 153, 0)') {
                    //取消选中
                    liItem.style.backgroundColor = ''; //设置为空，会取默认值
                } else {
                    //设置背景颜色为选中
                    liItem.style.backgroundColor = '#f90';
                }
            }
        });

    </script>
</body>
</html>
```



#### ③点击背景设置颜色,排他案列

```html
<script>
        //获取所有的li
        var lis = document.querySelectorAll('.list li');

        // 遍历
        lis.forEach(function (liItem) {
            //给每个li绑定单击事件
            liItem.onclick = function(){
                //所有的不选中
                lis.forEach(function (item) {
                    item.style.backgroundColor = '';
                });
                // 让自己选中
                liItem.style.backgroundColor = '#f90';
            }
        });

    </script>
```







# 第十二天，JavaScript 课堂笔记

## 回顾

### 1. 节点 node

```
节点分类：
	document
	元素
	属性
	文本
	注释
	
节点属性：
	nodeName: 元素节点:标签名
	nodeValue
	nodeType: 1(元素节点)、2（属性节点）、3（文本节点）、8（注释节点）、9（document）
```



### 2. 获取元素

```
1. getElementById()
2. getElementsByTagName()
3. getElementsByClassName()
4. document.getElementsByName()
5. querySelector(）  IE8+
   querySelectorAll()
6. document.all
   妙用，判断IE和非IE
```



### 3 文档操作

```
父元素：
parentNode (父节点)
parentElement （父元素）

子元素：
children (子元素集合)
childNodes (子节点集合)
firstChild
lastChild
firstElementChild  IE9+
lastElementChild	IE9+

兄弟元素：
previousSibling  
previousElementSibling
nextSibling
nextElementSibling

childElementCount 子元素的数量

```



### 4 属性操作

```
内置属性：
	element.属性名
	
自定义属性：
	element.getAttribute(属性名)
	element.setAttribute(属性名,值)
	
data-开头的自定义属性：
	element.dataset.名字

```



### 5. CSS样式操作

```
style内联式：
	element.style.css属性名   //可读可写
	
计算样式：
	window.getComputedStyle(element)  返回样式对象   // 非IE、IE11+
	element.currentStyle.css属性名  //IE
```



## 以下是第十二天的课程

## DOM 文档对象模型

### 1. 元素的class属性

#### 1.1 className

```
element.className 可读可写
返回字符串
元素的class属性的值
```

#### 1.2 classList (IE9+)

```
对象，类数组对象。元素所有class值的列表。
方法：
add() 添加一个class值
remove()  删除一个class值
toggle()  切换一个class值（没有就添加，有就删除）
```

#### ①案列

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        .box {
            margin: 100px auto;
            width: 800px;
        }
        .item {
            float:left;
            margin: 20px;
            width: 200px;
            height: 60px;
            border: 1px solid #ccc;
        }
        .item.active {
            border: 2px solid red;
            background-color: #f90;
            width: 198px;
            height: 58px;
        }
    </style>
</head>
<body>

    <div class="box container" id="wrapper">
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
    </div>
    
    
方法一
    <script>
        // 获取元素
        var box = document.querySelector('.box');

        // 输出 box元素的class属性值
        console.log(box.class);  //undefined
        console.log(box.id);

        console.log(box.className);  //box


        //获取所有的.item的div组成集合
        var items = document.querySelectorAll('.box .item');
        // 给每个item绑定单击事件
        for (var i = 0; i < items.length; i ++) {
            items[i].onclick = function(){

                //判断是否是选中的状态
                if (this.className === 'item') {
                    //说明还没有被选中
                    //设置 class
                    this.className = 'item active';
                } else {
                    //设置为不选中
                    this.className = 'item';
                }




                // 直接设置样式
                /*this.style.border = '2px solid red';
                this.style.backgroundColor = '#f90';
                this.style.width = '198px';
                this.style.height = '58px';*/

                //items[i].style.border = '1px solid red';
                //console.log(items[i]);
                //console.log(i);
            }
        }

        console.log(i); //for循环 执行结束后 i的值是 9

    </script>
    
    
方法二
    <script>
        // 获取元素
        var box = document.querySelector('.box');
        //获取所有的.item的div组成集合
        var items = document.querySelectorAll('.box .item');
        // 给每个item绑定单击事件
        for (var i = 0; i < items.length; i ++) {
            // 给每个div绑定单击事件
            items[i].onclick = function(){
                // 判断是否选中
                if (this.className.indexOf('active') === -1) { //表示还没选中
                    //添加一个active类 选中
                    this.classList.add('active');
                } else { //表示当前是选中的状态
                    // 删除元素的 active 类
                    this.classList.remove('active');
                }
            }
        }

        console.log(box.classList);

    </script>
     
方法三
    <script>
        // 获取元素
        var box = document.querySelector('.box');
        //获取所有的.item的div组成集合
        var items = document.querySelectorAll('.box .item');
        // 给每个item绑定单击事件
        for (var i = 0; i < items.length; i ++) {
            // 给每个div绑定单击事件
            items[i].onclick = function(){
               this.classList.toggle('active');
            }
        }

    </script>
```



### 2.  元素的文本内容

```
用于双标签元素
可读可写

把内容当做HTML：
innerHTML
outerHTML

把内容当做文本
innerText
textContent
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        .box {
            margin: 100px auto;
            width: 600px;
            border: 1px solid #ccc;
            padding:20px;
        }

    </style>
</head>
<body>

    <div class="box container" id="wrapper">
        <h1>悯农</h1>
        <p>锄禾日当午</p>
        <p>汗滴禾下土</p>
        <p>谁知盘中餐</p>
        <p>粒粒皆辛苦</p>
    </div>

    <button onclick="setHTML()">设置</button>

    <script>
        // 获取元素
        var box = document.querySelector('.box');

        console.log(box.innerHTML);
        console.log('');
        console.log(box.outerHTML);
        console.log('');
        console.log(box.innerText);
        console.log('');
        console.log(box.textContent); //去掉了不必要换行    IE9+


        function setHTML(){
            var content = '<h1>啊，一首好诗！</h1>';

            //box.innerHTML = content;
            //box.outerHTML = content;

           // box.innerText = content;
            box.textContent = content;
        }
    </script>
</body>
</html>
```



### 3. 元素尺寸位置

#### 3.1 元素的尺寸(只读)

```
offsetWidth / offsetHeight   元素尺寸(内容宽高+内边距宽高+边框)
clientWidth / clientHeihgt   元素尺寸（内容宽高+内边距宽高）
scrollWidth / scrollHeight   元素尺寸（如果子元素没有溢出，同client系列；如果子元素溢出：子元素宽度+一个方向的内边距）

getBoundingClientRect()  返回对象（对象中包含width和height属性）   IE8中没有width和heihgt属性
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        .box {
            margin: 100px auto;
            width: 400px;
            height: 300px;
            border: 3px solid #ccc;
            padding:20px;
            overflow: auto;
            overflow: hidden;
        }
        .item {
            width: 800px;
            height: 100px;
            background: #f90;
        }

    </style>
</head>
<body>

    <div class="box">
        <div class="item"></div>
    </div>

    <script>
        // 获取元素
        var box = document.querySelector('.box');

        //获取元素的大小

        // offsetWidth   offsetHeight
        // content+padding+border
        console.log(box.offsetWidth, box.offsetHeight);

        // clientWidth   clientHeight
        // content+padding
        console.log(box.clientWidth, box.clientHeight);

        // scrollWidth   scrollHeight
        console.log(box.scrollWidth, box.scrollHeight);


        // getBoundingClientRect()
        console.log('');
        console.log(box.getBoundingClientRect());
        console.log(box.getBoundingClientRect().width, box.getBoundingClientRect().height);

    </script>
</body>
</html>
```



#### 3.2 元素的位置（只读）

```
offsetLeft / offsetTop  元素位置，在第一个定位的祖先元素上的位置，如果都没定位在根元素上的位置
clientLeft / clientTop  元素边框的宽度

getBoundingClientRect()  返回对象  元素在视口上的位置 
	left        元素的坐左边距离视口左边的距离
	top         
	right		元素的最右边距离视口左边的距离
	bottom
	x	同left
	y   同top
```

```html
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        html {
            margin-top: 10px;
        }
        html,body {
            /*margin: 0;*/
            overflow: hidden;
        }
        .box {
            margin: 100px auto;
            width: 400px;
            height: 300px;
            border: 3px solid #ccc;
            padding:20px;
            position: relative;
        }
        .item {
            width: 200px;
            height: 100px;
            background: #f90;
            margin: 10px;
            border: 4px solid red;
        }

    </style>
</head>
<body>

    <div class="box">
        <div class="item"></div>
    </div>

    <script>
        //获取元素
        var item = document.querySelector('.item');
        var box = document.querySelector('.box');


        // 计算元素的位置
        // 在第一个定位的祖先元素上的位置，如果都没有定位，在根元素上的位置。
        console.log(item.offsetLeft, item.offsetTop);

        // 自己的边框的宽度
        console.log(item.clientLeft, item.clientTop);


        console.log('');
        console.log(item.getBoundingClientRect());
        
 //兼容IE浏览器
         //IE8浏览器 没有widht和height属性
        console.log(item.getBoundingClientRect());

        console.log('width ： '+(item.getBoundingClientRect().right - 			item.getBoundingClientRect().left));
        console.log('height ： '+(item.getBoundingClientRect().bottom - 	item.getBoundingClientRect().top));
    </script>
</body>
</html>
```



#### 3.3 内容位置 （可读可写）

```
scrollLeft   元素内容的滚动位置； 值增大，内容向左滚；
scrollTop

生效前提： 子元素溢出父元素，设置父元素overflow：hidden/auto/scroll
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        html {
            margin-top: 10px;
        }
        html,body {
            /*margin: 0;*/
            overflow: hidden;
        }
        .box {
            margin: 100px auto;
            width: 400px;
            height: 300px;
            border: 3px solid #ccc;
            padding:20px;
            position: relative;
            overflow: hidden;
        }
        .item {
            width: 800px;
            height: 100px;
            background: #f90;
            margin: 10px;
            border: 4px solid red;
        }

    </style>
</head>
<body>
    <button onclick='leftMove()'>左移</button>
    <button onclick='rightMove()'>右移</button>
    <div class="box">
        <div class="item">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab aliquam aspernatur dignissimos eius eum exercitationem explicabo fuga, illo magni, natus neque nesciunt numquam officiis quia ratione reprehenderit sapiente sint sunt.</div>
    </div>

    <script>
        //获取元素
        var item = document.querySelector('.item');
        var box = document.querySelector('.box');

        //设置
        box.scrollLeft = 100;
        item.scrollTop = 200;

        //IE8浏览器 没有widht和height属性
        console.log(item.scrollLeft, item.scrollTop);
        console.log(box.scrollLeft, box.scrollTop);

        function leftMove() {
            box.scrollLeft += 10;
        }
        function rightMove(){
            box.scrollLeft -= 10;
        }

    </script>
</body>
</html>
```

#### 无缝滚动案列

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        ul {
            margin: 0;
            padding: 0;
            list-style: none;
        }
        #imgList {
            margin: 100px auto;
            width: 800px;
            height: 200px;
            border: 1px solid #ccc;
            overflow: hidden;
        }
        .container {
            width: 2000px;
        }
        .image-wrapper {
            float: left;
        }
        .image-wrapper li {
            float: left;
            width: 200px;
            height: 200px;
        }
        .image-wrapper li img {
            width: 200px;
            height: 200px;
            display: block;
        }
    </style>
</head>
<body>
    <div id="imgList">
        <div class="container">
            <ul class="image-wrapper">
                <li><img src="../images/1.jpg"></li>
                <li><img src="../images/2.jpg"></li>
                <li><img src="../images/3.jpg"></li>
                <li><img src="../images/4.jpg"></li>
                <li><img src="../images/5.jpg"></li>
                <li><img src="../images/6.jpg"></li>
                <li><img src="../images/7.jpg"></li>
                <li><img src="../images/8.jpg"></li>
                <li><img src="../images/9.jpg"></li>
            </ul>
        </div>
    </div>

    <script>
        // 获取元素
        var imgList = document.querySelector('#imgList');
        var imgContainer = document.querySelector('#imgList .container');
        var imgWrapper = document.querySelector('#imgList .image-wrapper');

        // 1，把所有的图片复制一份
        //imgContainer.innerHTML += imgContainer.innerHTML;

        //,2，把所有的图片克隆一份
        imgContainer.appendChild(imgWrapper.cloneNode(true));

        //获取所有图片组成的集合
        var imgItems = document.querySelectorAll('#imgList li');

        // 计算container元素的宽度
        var width = imgItems[0].offsetWidth * imgItems.length
        imgContainer.style.width = width + 'px';

        // 定时器
        setInterval(function () {
            imgList.scrollLeft += 5;


            //判断临界点
            if (imgList.scrollLeft >= width/2) {
                imgList.scrollLeft = 0;  //从头开始
            }
        }, 20);
    </script>
    
无缝滚鼠标悬停 停止定时
    
    <script>
        // 获取元素
        var imgList = document.querySelector('#imgList');
        var imgContainer = document.querySelector('#imgList .container');
        var imgWrapper = document.querySelector('#imgList .image-wrapper');

        // 把所有的图片复制一份
        //imgContainer.innerHTML += imgContainer.innerHTML;
        imgContainer.appendChild(imgWrapper.cloneNode(true));

        //获取所有图片组成的集合
        var imgItems = document.querySelectorAll('#imgList li');

        // 计算container元素的宽度
        var width = imgItems[0].offsetWidth * imgItems.length
        imgContainer.style.width = width + 'px';

        // 定时器
        var intervalId = setInterval(run, 20);

        //绑定 mouseover
        imgList.onmouseover = function(){
            //停止定时
            clearInterval(intervalId);
        };
        //绑定mouseout
        imgList.onmouseout = function(){
            //重新开始定时
            intervalId = setInterval(run, 20);
        };


        //定时函数
        function run () {
            imgList.scrollLeft += 5;
            //判断临界点
            if (imgList.scrollLeft >= width/2) {
                imgList.scrollLeft = 0;  //从头开始
            }
        }

    </script>
</body>
</html>
```



### 4 节点的添加/删除/替换/克隆

#### 4.1 创建元素节点

```
document.createElement(tagName)
```

#### 4.2 添加子节点

```
parentElement.appendChild(node)  追加子节点
parentElement.insertBefore(newNode, oldNode)   指定位置插入节点
```

#### 4.4 删除子节点

```
parentElement.removeChild(node)  
```

#### 4.5 替换子节点

```
parentElement.replaceChild(newNode, oldNode)   会把旧的节点删掉换成新的节点
```

#### 4.6 克隆节点

```
element.cloneNode(true)  克隆节点
参数 true  深度克隆，元素自己和后代元素都会克隆
	false (默认)  只克隆元素自己，不克隆后代元素

```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        ul {
            list-style: none;
        }
        .box {
            margin: 60px auto;
            width: 600px;
        }
        .todo-list li {
            margin-top: 5px;
            border:1px solid #ccc;
            padding: 10px;
            position: relative;
        }
        .todo-list li .close {
            position: absolute;
            right: 10px;
            cursor: pointer;
        }
        .todo-list li.active {
            border: 1px solid red;
        }
        .todo-header input {
            padding: 10px;
            border: 1px solid #ccc;
        }
        .todo-header button {
            border: 1px solid #ccc;
            padding: 10px;
            background: #f5f5f5;
        }
    </style>
</head>
<body>
    <div class="box">

        <div class="todo-header">
            <input type="text">
            <button onclick="addTodo()">追加</button>
            <button onclick="insertTodo()">插入</button>
            <button onclick="replaceTodo()">替换</button>
        </div>
        <ul class="todo-list">
            <li class="todo-item">吃饭 <span onclick="deleteTodo(this)" class="close">&times;</span></li>
            <li class="todo-item">睡觉 <span onclick="deleteTodo(this)" class="close">&times;</span></li>
            <li class="todo-item">打豆豆 <span onclick="deleteTodo(this)" class="close">&times;</span></li>
            <li class="todo-item">喝水 <span onclick="deleteTodo(this)" class="close">&times;</span></li>
            <li class="todo-item">洗澡 <span onclick="deleteTodo(this)" class="close">&times;</span></li>
        </ul>
    </div>


    <li id="myLi">啦啦啦</li>
    <button onclick="addTodo2()">添加</button>

    <script>
        // 获取元素
        var todoList = document.querySelector('.todo-list');
        var input = document.querySelector('.todo-header input');
        var todoItems = document.querySelectorAll('.todo-list li');


        // 给所有的li绑定单击事件
        todoItems.forEach(function (item) {
           item.onclick = function(){
               item.classList.toggle('active');
           }
        });

        // 定义函数
        function addTodo(){
            //创建一个li元素
            var newLi = document.createElement('li');
            newLi.innerHTML = input.value + ' <span onclick="deleteTodo(this)" class="close">&times;</span>';

 //把新创建的li元素，追加到ul中
            todoList.appendChild(newLi);

            // 清空输入框里的内容
            input.value = '';

        }

        // 定义函数
        function insertTodo(){
            //创建一个li元素
            var newLi = document.createElement('li');
            newLi.innerHTML = input.value + ' <span onclick="deleteTodo(this)" class="close">&times;</span>';

//把新创建的li元素，插入到ul中的第一个位置
            todoList.insertBefore(newLi, todoList.firstChild);
            //todoList.insertBefore(newLi, todoList.children[2]);

            // 清空输入框里的内容
            input.value = '';
        }

//定义删除 删除li
        function deleteTodo(node) {
            //删除所在li
            todoList.removeChild(node.parentNode);
        }


// 定义函数。 替换li
        function replaceTodo() {
            //创建一个li元素
            var newLi = document.createElement('li');
            newLi.innerHTML = input.value + ' <span onclick="deleteTodo(this)" class="close">&times;</span>';

           /*
            //替换 替换被选中的li
           值能替换第一个被选中的li
            //获取被选中的li元素
            var activedTodo = document.querySelector('.todo-list li.active');
            //执行替换
            todoList.replaceChild(newLi, activedTodo);
            */

// 克隆元素 
            // 获取所有被选中的li
            var activedTodos = document.querySelectorAll('.todo-list li.active')
            // 遍历，一个一个的进行替换
            activedTodos.forEach(function (item) {
               todoList.replaceChild(newLi.cloneNode(true), item);
            });


            // 清空输入框里的内容
            input.value = '';

        }


        var myLi = document.querySelector('#myLi');

        function addTodo2() {
            todoList.appendChild(myLi.cloneNode(true));
        }


        console.log(todoList.cloneNode());
        console.log(todoList.cloneNode(true));
    </script>
</body>
</html>
```

#### 4.7 documentFragment（不会出现在dom树中）

```
也是一类节点， nodeType是11， 不是元素。
可以给df对象添加子节点，df节点也可以作为其他元素的子节点
df对象不会出先在dom树中

用法：
	如果连续给一个元素添加多个子元素，可以先把子元素添加到df对象中，最后把df对象添加到父元素中！ 减少浏览器渲染次数。
```

#### documentFragment实现元素翻转案列

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        ul {
            list-style: none;
        }
        .box {
            margin: 60px auto;
            width: 600px;
        }
        .todo-list li {
            margin-top: 5px;
            border:1px solid #ccc;
            padding: 10px;
            position: relative;
        }
        .todo-list li .close {
            position: absolute;
            right: 10px;
            cursor: pointer;
        }
        .todo-list li.active {
            border: 1px solid red;
        }
        .todo-header input {
            padding: 10px;
            border: 1px solid #ccc;
        }
        .todo-header button {
            border: 1px solid #ccc;
            padding: 10px;
            background: #f5f5f5;
        }
    </style>
</head>
<body>
<div class="box">

    <div class="todo-header">
        <button onclick="reverseTodo()">翻转</button>
    </div>
    <ul class="todo-list">
        <li class="todo-item">吃饭 <span onclick="deleteTodo(this)" class="close">&times;</span></li>
        <li class="todo-item">睡觉 <span onclick="deleteTodo(this)" class="close">&times;</span></li>
        <li class="todo-item">打豆豆 <span onclick="deleteTodo(this)" class="close">&times;</span></li>
        <li class="todo-item">喝水 <span onclick="deleteTodo(this)" class="close">&times;</span></li>
        <li class="todo-item">洗澡 <span onclick="deleteTodo(this)" class="close">&times;</span></li>
    </ul>
</div>



<script>
    // 获取元素
    var todoList = document.querySelector('.todo-list');
    var todoItems = document.querySelectorAll('.todo-list li');


    // 新方法
    function reverseTodo() {
        // 创建 documentFragment对象
        var df = document.createDocumentFragment();
        // 反着遍历 todoItems
        for (var i = todoItems.length-1; i >=0; i --) {
            df.appendChild(todoItems[i]);
        }
        // 给ul添加
        todoList.appendChild(df);
    }

    // 旧的方法
   /* function reverseTodo() {
        //定义新数组
        var newTodoItems = [];
        //反着遍历 todoItems
        for (var i = todoItems.length-1; i >= 0; i --) {
            newTodoItems.push(todoItems[i]);
        }

        //清空ul
        todoList.innerHTML = '';

        //遍历新数组
        newTodoItems.forEach(function (item) {
            todoList.appendChild(item);
        });

    }*/

</script>
</body>
</html>
```



## 作业

```
1. 实现一个选项卡效果
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        ul {
            list-style: none;
        }
        .container {
            margin: 100px auto;
            width: 800px;
        }

        .options {
            height: 40px;
            border-left: 1px solid #ccc;
            border-bottom: 1px solid #ccc;
        }
        .options li {
            float: left;
            width: 100px;
            height: 39px;
            text-align:center;
            line-height: 40px;
            border-top: 1px solid #ccc;
            border-right: 1px solid #ccc;
            background: #f5f5f5;
            cursor: pointer;
        }
        .options li.active {
            background-color:#fff;
            height: 40px;
        }

        .card li {
            display: none;
            padding: 20px;
            border: 1px solid #ccc;
            border-top: none;
            min-height: 200px;
        }
        .card li.active {
            display: block;
        }
    </style>
</head>
<body>

    <div class="container">
        <ul class="options">
            <li class="active">未付款订单</li>
            <li>未发货订单</li>
            <li>未收货订单</li>
            <li>未评价订单</li>
            <li>已完成订单</li>
        </ul>
        <ul class="card">
            <li class="active">这是未付款的订单....</li>
            <li>这是未发货的订单....</li>
            <li>这是未收货的订单....</li>
            <li>这是未评价的订单....</li>
            <li>这是已完成的订单....</li>
        </ul>

    </div>


forEach版本

    <script>
        //获取元素
        var optionItems = document.querySelectorAll('.options li');
        var cardItems = document.querySelectorAll('.card li');

        // 给每个选项 绑定单击事件
        optionItems.forEach(function (optionItem, index) {
            optionItem.onclick = function(){
                //所有的选项 取消选中
                optionItems.forEach(function(item){
                    item.classList.remove('active');
                });
                //先把所有的卡 隐藏
                cardItems.forEach(function (item) {
                    item.classList.remove('active');
                });

                //添加 active类
                optionItem.classList.add('active');
                //对应的卡 添加 active类
                cardItems[index].classList.add('active');
            }
        });
    </script>
    
    
for循环版
    
     <script>
        //获取元素
        var optionItems = document.querySelectorAll('.options li');
        var cardItems = document.querySelectorAll('.card li');

        // 给每个选项 绑定单击事件
        for (var i = 0; i < optionItems.length; i ++) {
            optionItems[i].index = i; //每个options下的li添加一个index属性
            optionItems[i].onclick = function(){
                //排他 所有的去掉active类
                for (var j = 0; j < optionItems.length; j ++) {
                    optionItems[j].classList.remove('active');
                    cardItems[j].classList.remove('active');
                }
                //当前的添加active类
                this.classList.add('active');
                cardItems[this.index].classList.add('active');
            }
        }
    </script>
    
</body>
</html>
```





# 第十三天，JavaScript 课堂笔记

## 回顾

### 1. class属性

```
className
classList
	add()
	remove()
	toggle()
```



### 2. 文本内容

```
把内容当html
	innerHTML
	outerHTML

把内容当文本
	innerText
	textContent
```



### 3. 元素的尺寸和位置

```
尺寸大小：(只读)
	offsetWidth / offsetHeight
	clientWidth / clientHeight
	scrollWidth / scrollHeight
	getBoundingClientRect()
	

位置：(只读)
	offsetLeft / offsetTop
	clientLeft / clientTop
	getBoundingClientRect()
	
	
内容的位置：(可读可写)
	scrollLeft / scrollTop
```



### 4. 节点操作

```
1. 创建元素节点
	document.createElement()
	
2. 添加节点
	parentElement.appendChild(newNode) 
	parentElement.insertBefore(newNode, oldNode)
	
3. 删除子节点
	parentElement.removeChild(node)
	
4. 替换子节点
	parentElement.repaceChild(newNode, oldNode)
	
5. 克隆节点
	node.cloneNode(true)
	
6. DocumentFragment
	
```



## 以下是第十三天的课程

## DOM

### 1 Document 

#### 属性

```
referrer   历史记录中上一个地址（只读）
URL			页面地址（只读）
domain		域名（只读）
lastModified   文件的最后一次修改时间（只读）
title       网页标题（可读可写）
cookie	    会话内容（可读可写）

documentElement  获取html元素
body  			获取body元素
head			获取的head元素
all				获取所有的元素
```

#### 方法

```
write()
```

```html
<script>
        console.log(document);

        // 只读
        console.log(document.URL);
        document.URL = 'http://www.atguigu.com';
        //只读
        console.log(document.domain);

        // 历史记录中的上一个地址
        console.log(document.referrer);

        // 可读可写
        console.log(document.title);
        document.title = '在线交友';


        console.log(document.lastModified);  //页面最后一次修改时间

        console.log(document.cookie);

        console.log('');

        console.log(document.documentElement);
        console.log(document.body);
        console.log(document.head);
    </script>
```



### 2 表单相关的元素

#### 2.1 获取表单元素以及表单控件元素（了解）

```
document.forms   获取页面中所有form元素组成的集合
document.formName   通过form元素的name属性值
formElement.inputName   通过表单控件的name属性值
formElement.elements    所有的表单控件组成的集合 (类数组)
formElement[index]      form元素本身也可以取索引   
```

#### 2.2 form 元素

```
属性：
length   返回所有表单控件的数量
elements  所有表单控件组成的集合

方法：
submit()
reset()
```

#### 2.3 input元素

```
方法：
blur()  失去焦点
focus()  获取焦点
select()  选中里面的文字
```

#### 2.4 textarea

```
方法：
select()  选中文本
```

#### 2.5 select元素

```
属性：
	options  所有option元素的集合
	selectedIndex  被选中的option的索引（如果选中了多个，取第一个）
	length   option元素的个数
	
方法：
	add(option元素)  追加一个option
	remove(index)  删除指定的索引
	focus()
	blur()

创建option元素：
	new Option(innerText值， value值)
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
    <style>
        select {
            width: 120px;
            height: 200px;
        }
    </style>
</head>
<body>
    <form action="1.php" name="userform">
        <div>
            姓名；<br>
            <input type="text" name="username">
        </div>

        <div>
            介绍：<br>
            <textarea name="des" cols="30" rows="10"></textarea>
        </div>
    </form>
    <hr>
    <button onclick="document.userform.submit()">提交</button>
    <button onclick="document.userform.reset()">重置</button>
    <br>
    <button onclick="document.userform.des.select()">选中input内的文字</button>

    <hr>

    <select id="leftSelect" multiple>
        <option value="1">广州</option>
        <option value="2">深圳</option>
        <option value="3">北京</option>
        <option value="4">上海</option>
        <option value="5">南京</option>
        <option value="6">杭州</option>
    </select>
    <button onclick="toRight()"> >> </button>
    <select id="rightSelect" multiple></select>
    <br>
    <input type="text" id="content"> <button onclick="addOption()">添加选项</button>
    <br>
    <button onclick="deleteOption()">删除选中</button>

    <script>
        //快速的获取 表单元素以及表单控件元素
        console.log(document.forms); //获取所有的form组成的集合
        console.log(document.userform);  //获取form元素
        // 获取input元素
        console.log(document.userform.username);
        console.log(document.userform.elements[0]);
        console.log(document.userform[1]);


        console.log(document.userform.length);

        //获取input元素
        var inputEle = document.userform.username;

        //自动获取焦点
        inputEle.focus();


        var leftSelect = document.querySelector('#leftSelect');
        var rightSelect = document.querySelector('#rightSelect');

        //移动到右边
        function toRight() {


            // 把左边选中的添加到右边
            //console.log(leftSelect.selectedIndex);

            //遍历所有的option元素
            //console.log(leftSelect.length);
            //console.log(leftSelect.options);

            for (var i = 0; i < leftSelect.length; i ++) {
                //console.log(leftSelect.options[i].selected)
                if (leftSelect.options[i].selected) {
                    rightSelect.add(leftSelect.options[i]);
                    i --; //把i的值倒回去
                }
            }

        }

        //添加选项
        function addOption(){
            //创建options元素
            var optionNode = new Option(document.querySelector('#content').value, 100);
            //添加
            leftSelect.add(optionNode);
        }

        //删除选中
        function deleteOption(){
            for (var i = 0; i < leftSelect.length; i ++) {
                if (leftSelect.options[i].selected) {
                    leftSelect.remove(i);
                    i --;
                }
            }

        }
    </script>
</body>
</html>
```



### 3 表格相关的元素

#### 3.1 table元素

```
属性：
	rows  所有tr的集合
	cells  所有td和th的集合
	
方法：
	insertRow(index) 创建并插入一个tr
	deleteRow(index) 删除一行
```

#### 3.2 tr元素 tableRow

```
属性：
	cells  行内所有的单元格的集合
	rowIndex   行的索引
	
方法：
	insertCell(index)  创建并添加一个td
	deleteCell(index)  删除一个单元格
```



#### 3.3 td\th 单元格元素

```
属性：
	cellIndex  单元格的索引（在行内）
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
    <style>
        table {
            border-collapse: collapse;
            width: 800px;
        }
        td,th {
            border: 1px solid #ccc;
            padding: 10px;
        }
        th {
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="form">
        <div>
            姓名： <input type="text" id="name">
        </div>
        <div>
            年龄： <input type="text" id="age">
        </div>
        <div>
            职业： <input type="text" id="job">
        </div>
        <div>
            <button onclick="add()">添加</button>
        </div>
    </div>
    <br>
    <br>

    <table>
        <tr>
            <th>序号</th>
            <th>姓名</th>
            <th>年龄</th>
            <th>职业</th>
            <th>操作</th>
        </tr>
        <tr>
            <td>1</td>
            <td>曹操</td>
            <td>18</td>
            <td>丞相</td>
            <td>
                <button onclick="deleteRow(this)">删除</button>
            </td>
        </tr>
        <tr>
            <td>2</td>
            <td>曹植</td>
            <td>18</td>
            <td>儿子</td>
            <td>
                <button onclick="deleteRow(this)">删除</button>
            </td>
        </tr>
        <tr>
            <td>3</td>
            <td>曹丕</td>
            <td>18</td>
            <td>皇帝</td>
            <td>
                <button onclick="deleteRow(this)">删除</button>
            </td>
        </tr>
    </table>

    <script>
        //获取元素
        var table = document.querySelector('table');

        //添加一行
        function add(){
            //添加一行 添加tr元素
            var tr = table.insertRow();
            // 给tr元素添加单元格
            tr.insertCell(0).innerHTML = table.rows.length - 1;
            tr.insertCell(1).innerHTML = document.querySelector('#name').value;
            tr.insertCell(2).innerHTML = document.querySelector('#age').value;
            tr.insertCell(3).innerHTML = document.querySelector('#job').value;
            tr.insertCell(4).innerHTML = '<button onclick="deleteRow(this)">删除</button>';

        }

        //删除一行
        function deleteRow(btn) {
            table.deleteRow(btn.parentNode.parentNode.rowIndex);
        }
    </script>
</body>
</html>
```

### 4 dom对象的原型

```html
<body>
    <div id="box"></div>

    <ul>
        <li>Lorem ipsum dolor sit amet.</li>
    </ul>

    <script>
        // 获取box元素
        var box = document.querySelector('#box');

        /*
        * box ---> HTMLElement对象 ---> ELment对象  ----> Node对象  --> EventTarget对象 ----> Object对象（顶）
        *
        * */

        console.dir(box);
        console.dir(box.constructor);

        // 不同的标签是不同的元素，但是它们的原型可能是一样的
        console.log(document.querySelector('ul').constructor)
    </script>
</body>
```



### 5 NodeList 和 HTMLCollection 区别

```
NodeList: querySelectorAll() 返回的就是NodeList
	静态的；
	
HTMLCollection: getElementsBy... 返回的
	动态的；
	获取之后，又添加了新的元素，HTMLCollection会动态的变化
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
    <style>

    </style>
</head>
<body>
    <ul>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
    </ul>

    <script>
        var liItems1 = document.querySelectorAll('ul li');  //静态
        var liItems2 = document.getElementsByTagName('li'); // 动态

        console.log(liItems1);
        console.log(liItems2);


        //创建一个li元素
        var liNode = document.createElement('li');
        liNode.innerHTML = '哈哈哈';
        document.querySelector('ul').appendChild(liNode);

        console.log('');

        console.log(liItems1);
        console.log(liItems2);
    </script>
</body>
</html>
```



## 事件

### 1. 给元素监听/绑定事件

#### 1.1 事件的监听/绑定 三种方式

```js
// 第一种方法  把事件当做标签的属性
<button onclick="fn()"></button>

// 第二种方法， 把事件当做元素对象的方法
btnElement.onclick = fn;

// 第三种方法 事件监听方式
element.addEvenetListener('click', fn);

```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
</head>
<body>
    <button onclick="clickFn()">按钮1</button>
    <button id="btn2">按钮2</button>
    <button id="btn3">按钮3</button>


    <script>
        //第一种方式， 把事件作为html标签的一个属性
        function clickFn(){
            alert('啊，我被点击了');
        }

        //第二种方式，把事件作为元素对象一个方法
        //获取元素
        var btn2 = document.querySelector('#btn2');
        btn2.onclick = function(){
            alert('啊，我也被点击了');
        };
        //会覆盖前面的
        btn2.onclick = function(){
            alert('啊，我也被点击了2');
        };
        //btn2.onclick(); 可以被调用


        // 第三种 事件监听方式
        var btn3 = document.querySelector('#btn3');
        btn3.addEventListener('click', function(){
            alert('啊，我还是被点击了');
        });
        btn3.addEventListener('click', function(){
            alert('啊，我还是被点击了2');
        });


    </script>
</body>
</html>
```



#### 1.2 解除事件绑定

```js
// 如果是第一种方式绑定 把事件当做标签属性
element.onclick = null;  //覆盖

// 如果是第二种方式绑定 把事件当做元素对象方法
element.onclick = null;   //覆盖

// 如果是第三种方式绑定 事件监听， 移除监听者
element.removeEventListener('click', fn);

```

```html
<head>
    <meta charset="UTF-8">
    <title>DOM</title>

</head>
<body>
    <button id="btn1" onclick="clickFn()">按钮1</button>
    <button id="btn2">按钮2</button>
    <button id="btn3">按钮3</button>

    <hr>

    <button id="btn4">解除绑定</button>


    <script>
        //第一种方式， 把事件作为html标签的一个属性\
        var btn1 = document.getElementById('btn1');
        function clickFn(){
            alert('啊，我被点击了');
        }

        //第二种方式，把事件作为元素对象一个方法
        //获取元素
        var btn2 = document.querySelector('#btn2');
        btn2.onclick = function(){
            alert('啊，我也被点击了');
        };


        // 第三种 事件监听方式
        var btn3 = document.querySelector('#btn3');
        btn3.addEventListener('click', clickFn1);
        function clickFn1(){
            alert('啊，我还是被点击了');
        }


        //解除绑定
        var btn4 = document.querySelector('#btn4');
        btn4.onclick = function(){

            //解除 使用addEventListener方式监听的事件
            btn3.removeEventListener('click', clickFn1)

            // 解除第二种方式绑定 把事件当做元素对象的方法
            btn2.onclick = null; //覆盖

            //解除第一种方式绑定 把事件做当标签的属性
            btn1.onclick = null;

        }

    </script>
</body>
</html>
```



#### 1.3 事件监听兼容性问题

```js
//IE9+ 以及其他浏览器
addEventListener()
removeEventListener()

// IE8以及以下
attachEvent()  //添加监听 事件名加on
detachEvent()  //移除监听
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>

</head>
<body>
    <button id="btn">按钮</button>

    <hr>

    <button id="btn4">解除绑定</button>


    <script>
        var btn = document.querySelector('#btn');
        var btn4 = document.querySelector('#btn4');


        addEventListener(btn, 'click', fn);
        function fn(){
            alert('ok');
        }

        btn4.onclick = function(){
            removeEventListener(btn, 'click', fn);
        };

        /**
         * 用于监听事件（兼容）
         * @param node 要绑定事件的元素
         * @param eventName
         * @param callback
         * */
        function addEventListener(node, eventName, callback) {
            if (node.addEventListener) {
                node.addEventListener(eventName, callback);
            } else if (node.attachEvent) {
                node.attachEvent('on'+eventName, callback);
            }
        }

        /**
         * 用于解除监听事件（兼容）
         * @param node 要绑定事件的元素
         * @param eventName
         * @param callback
         * */
        function removeEventListener(node, eventName, callback) {
            if (node.removeEventListener) {
                node.removeEventListener(eventName, callback)
            } else if (node.detachEvent) {
                node.detachEvent('on'+eventName, callback);
            }
        }

    </script>
</body>
</html>
```



### 2. 事件的捕获和冒泡

```
默认，事件是在冒泡阶段触发
addEventListener（） 第三个参数是布尔值，默认是(false)表示冒泡阶段触发，如果设置为true，会在捕获阶段触发
其他绑定事件的方式，无法设置在冒泡阶段触发还是捕获阶段触发，统一在冒泡阶段触发

当事件动作发生之后，先进行捕获： 从document开始一直到最底层的元素（没有子元素）； 目的是确定事件具体发生在了哪个元素。
捕获完成之后，进行冒泡，冒泡从最底层的元素一直向上，向他的祖先元素冒泡

```

![](D:\尚硅谷资料\02尚硅谷0908面授javascript\JS-课堂笔记\图例\事件捕获和冒泡.png)

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>
    <style>
        .wrapper {
            margin: 100px auto;
            width: 600px;
            height: 400px;
            background: red;
        }

        .inner {
            width: 200px;
            height: 200px;
            background: yellow;
        }
    </style>
</head>
<body>

    <div class="wrapper">
        <div class="inner"></div>
    </div>

    <script>
        //获取元素
        var wrapper = document.querySelector('.wrapper');
        var inner = document.querySelector('.inner');

        //监听单击事件
        wrapper.addEventListener('click', function(){
           alert('啊，我是wrapper');
        }, true);

        inner.addEventListener('click', function(){
            alert('啊，我是inner');
        }, true)

    </script>
</body>
</html>
```



### 3 this在事件中的指向

```
① 第一种方式 事件当做标签属性
this在事件属性的值用表示触发事件的元素
通常把this当实参，把元素对象传入函数中

② 第二种方式 把事件当做元素对象的方法
this指向触发事件的元素对象

③ 第三种方式 事件监听方式
this指向调用addEventListener的元素
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM</title>

</head>
<body>
<button id="btn1" onclick="clickFn(this)">按钮1</button>
<button id="btn2">按钮2</button>
<button id="btn3">按钮3</button>



<script>
    //第一种方式， 把事件作为html标签的一个属性
    var btn1 = document.getElementById('btn1');
    function clickFn(node){
        alert('啊，我被点击了');
        console.log(node); //btn1元素
        console.log(this); //window
    }

    //第二种方式，把事件作为元素对象一个方法
    //获取元素
    var btn2 = document.querySelector('#btn2');
    btn2.onclick = function(){
        alert('啊，我也被点击了');
        console.log(this); //btn2元素
    };


    // 第三种 事件监听方式
    var btn3 = document.querySelector('#btn3');
    btn3.addEventListener('click', clickFn1);
    function clickFn1(){
        alert('啊，我还是被点击了');
        console.log(this); //btn3元素
    }

   // clickFn1();

</script>
</body>
</html>
```



## 练习

### 1.轮播图

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>轮播图</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        ul,ol {
            list-style: none;
        }
        #play {
            margin: 100px auto;
            width: 900px;
            height: 350px;
            /*overflow: hidden;*/
            position:relative;
        }
        #play img {
            display: block;
        }
        .image-list li {
            position: absolute;
            left: 0;
            top: 0;
            opacity: 0;
            transition: opacity 1s;
        }
        .image-list li.current {
            opacity: 1;
        }
        .icon-list {
            position: absolute;
            bottom: 10px;
            right: 10px;
        }
        .icon-list li {
            float: left;
            margin-right: 8px;
            width: 20px;
            height: 20px;
            color: #fff;
            font-size: 14px;
            text-align: center;
            line-height: 20px;
            border: 1px solid #fff;
            border-radius: 50%;
            cursor: pointer;
        }
        .icon-list li.current {
            color: #f60;
            border-color: #f60;
            background: #000;
        }
        .prev-btn,.next-btn {
            position: absolute;
            top: 0;
            bottom: 0;
            margin-top: auto;
            margin-bottom: auto;
            width: 40px;
            height: 100px;
            /*background: #000;*/
            background: url('../images/play/index.png') no-repeat;
        }
        .prev-btn {
            left: 0;
        }
        .next-btn {
            right: 0;
            background-position:-50px 0;
        }
    </style>
</head>
<body>
    <div id="play">
        <ul class="image-list">
            <li class="current"><img src="../images/play/01.jpg" alt="轮播图"></li>
            <li><img src="../images/play/02.jpg" alt="轮播图"></li>
            <li><img src="../images/play/03.jpg" alt="轮播图"></li>
            <li><img src="../images/play/04.jpg" alt="轮播图"></li>
            <li><img src="../images/play/05.jpg" alt="轮播图"></li>
        </ul>
        <ol class="icon-list">
            <li class="current">1</li>
            <li>2</li>
            <li>3</li>
            <li>4</li>
            <li>5</li>
        </ol>
        <div class="control-btns">
            <div class="prev-btn"></div>
            <div class="next-btn"></div>
        </div>
    </div>

    <script>
        //获取元素
        var play = document.querySelector('#play');  //包裹元素
        var imageItems = play.querySelectorAll('.image-list li'); //所有图片的集合
        var iconItems = play.querySelectorAll('.icon-list li');  //所有的控制按钮元素
        var prevBtn = play.querySelector('.prev-btn'); //上一张的按钮
        var nextBtn = play.querySelector('.next-btn'); //下一张的按钮
        var currentIndex = 0; //标记当前显示的图片的索引
        var itemLength = iconItems.length; //图片的数量
        var duration = 3000;  //自动播放时间间隔

        // 给每一个控制按钮 绑定单击事件
        iconItems.forEach(function (iconItem, index) {
            iconItem.onclick = function(){
                //重新设置索引标记
                currentIndex = index;
                //设置高亮
                setPlay();
            }
        });

        //点击上一张
        prevBtn.onclick = function() {
            setIndex('prev');
        };

        //点击下一张
        nextBtn.onclick = function(){
            setIndex('next');
        };

        // 自动播放
        var intervalId = setInterval(function () {
            setIndex('next');
        }, duration);

        // 鼠标悬停在轮播图上，停止定时
        play.onmouseenter = function () {
            clearInterval(intervalId);
        };

        //鼠标离开轮播图，轮播继续
        play.onmouseleave = function(){
          intervalId = setInterval(function(){
              setIndex('next');
          }, duration);
        };

        /**
         * @param tag 值是prev表示上一张， 值是next表示下一张
         */
        function setIndex(tag) {
            if (tag === 'prev') {
                //当前的索引 -1
                currentIndex --;
                //判断范围
                if (currentIndex < 0) {
                    currentIndex = itemLength - 1;
                }
                //设置高亮
                setPlay();
            } else if (tag === 'next') {
                //当前的索引标记 +1
                currentIndex ++;
                //如果 currentIndex 超出范围
                if (currentIndex > itemLength - 1) {
                    currentIndex = 0;
                }
                //设置高亮
                setPlay();
            }
        }

        // 实现根据 currentIndex 显示当前的图片和控制按钮
        function setPlay() {
            //排他 所有控制按钮的取消高亮，所有图片的隐藏
            iconItems.forEach(function (item, index) {
                item.classList.remove('current');
                imageItems[index].classList.remove('current');
            });
            //当前控制按钮设置高亮 当前的图片显示
            iconItems[currentIndex].classList.add('current');
            imageItems[currentIndex].classList.add('current');
        }

    </script>
</body>
</html>
```





# 第十四天，JavaScript 课堂笔记

## 回顾

### 1. HTMLCollection 和 NodeList 什么区别

```
getElementsBy... 获取 HTMLCollection
	动态
	没有forEach方法
	

querySelectorAll() 获取 NodeList
	静态
	有forEach方法
```



### 2. Document

```
document.title
document.body
document.documentElement
document.head

document.URL
document.domain
document.lastModified
document.referrer
document.cookie

document.write()

```



### 3. 表单元素

```
获取:
document.forms
document.form元素的name属性值

formEle.name值  获取表单控件
formEle.elements


formELe
	submit()
	reset()
	
inputEle
	focus()
	blur()
	select()
	
textareaEle
	select()
	
selectEle
	add(option)
	remove(index)
	options
	selectedIndex
	new Option()

```

### 4 表格元素

```
table
	insertRow(index)
	deleteRow(index)
	rows
	cells

tr
	insertCell(index)
	deleteCell(index)
	rowIndex
	cells

td/th
	cellIndex
```



### 5. 给元素绑定事件 三种方式

```
① 把事件作为标签的属性

② 把事件作为元素对象的方法

③ 事件监听
	addEventListener()
	attachEvent()
	
	
解除绑定
	前两种方式绑定：  覆盖
	第三种方式：
		removeEventListener
		detachEvent
```



### 6. this在事件中

```
<button onclick="this">   this指向触发事件的元素（button）
<button onclick="demo()">
	function demo(){
		this //指向window
	}

btn.onclick = function(){
	this;  //指向触发事件的元素（button）
}

btn.addEventlistener('click', function(){
	this; //指向触发事件的元素（button）
})
```



### 7. 事件的捕获和冒泡

```
先捕获 再冒泡
捕获： 从根元素（根节点）到具体绑定事件那个元素
冒泡： 从绑定事件的元素到根元素（根节点）

事件默认在冒泡阶段触发
```



## 以下是第十四天的课程

## 1.事件列表

### 1.1 鼠标事件

```
click  			单击
dblclick 		双击
contextmenu	    右击

mousedown		鼠标按键按下
mouseup			鼠标按键抬起
mousemove		鼠标移动

多次触发
mouseover		鼠标悬停在元素上
mouseout		鼠标离开元素

触发一次
mouseenter		mouseover的代替方案 鼠标悬停在元素上		（IE9+）
mouseleave		mouseout的代替方法  鼠标离开元素		  (IE9+)
```

#### ①click 单击 / dblclick 双击  / contextmenu 右击

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>
        #box {
            width: 600px;
            height: 200px;
            background: #f90;
        }
    </style>
</head>
<body>
    <div id="box"></div>
    <script>
        //获取元素
        var box = document.querySelector('#box');

        //绑定事件
        box.onclick = function(){
            console.log('啊，我被点击了');
        };

        // 双击事件
        box.ondblclick = function(){
            console.log('啊，我被双击了');
        };

        //右单击
        box.oncontextmenu = function(){
            console.log('啊，我被右击了');
            return false;  //阻止系统菜单
        }

    </script>
</body>
</html>
```

#### 自定义菜单案列

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        body {
            background: #fff;
            position: relative;
        }
        ul {
            list-style: none;
        }
        #menu {
            position: fixed;
            left: 0;
            top: 0;
            width: 120px;
            border: 1px solid #ccc;
            box-shadow: 3px 3px 3px #f5f5f5;
            background: #fff;
            /*display: none;*/
            /*z-index: -1;*/
        }
        #menu li {
            padding: 0 10px;
            line-height: 38px;
            border-bottom: 1px solid #ccc;
        }
        #menu li:hover {
            background: #f5f5f5;
        }

        #box {
            width: 600px;
            height: 200px;
            background: #f90;
        }
    </style>
</head>
<body>
    <div id="box"></div>

    <div id="menu">
        <ul class="menu-list">
            <li>复制</li>
            <li>剪切</li>
            <li>粘贴</li>
            <li>全选</li>
            <li>新建</li>
        </ul>
    </div>

    <div style="height: 2000px">

    </div>

    <script>
        //获取menu元素
        var menu = document.querySelector('#menu');

        // 获取菜单的高度
        var menuHeight = menu.offsetHeight;

        // 设置菜单隐藏
        menu.style.display = 'none';


        // 绑定右单击事件
        document.oncontextmenu = function(event){
            //console.log(event.clientX, event.clientY);
            // 获取鼠标的位置
            var left = event.clientX; //返回的是数字
            var top = event.clientY;

            //水平位置范围限定
            if ( left > document.documentElement.clientWidth - menu.offsetWidth) {
                left = document.documentElement.clientWidth - menu.offsetWidth;
            }

            // 垂直位置范围限定
            if (top > document.documentElement.clientHeight - menuHeight) {
                top = document.documentElement.clientHeight - menuHeight;
            }

            //console.log(document.documentElement.clientHeight,  menuHeight);

            // 设置menu元素的位置， 与鼠标位置相同
            menu.style.left = left + 'px';
            menu.style.top = top + 'px';

            // 设置菜单显示
            menu.style.display = 'block';

            //阻止系统菜单
            return false;
        };

       /* document.addEventListener('contextmenu', function(event){

        })
        */
        //绑定 单击事件，取消菜单
        document.onclick = function(){
            //取消菜单显示
            menu.style.display = 'none';
        };

    </script>
</body>
</html>
```



#### ②mousedown 鼠标按下  /  mouseup 鼠标抬起  /  mousemove  鼠标移动

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>
        #box {
            width: 600px;
            height: 400px;
            /*background: #f90;*/
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
    <div id="box"></div>
    <script>
        //获取元素
        var box = document.querySelector('#box');

        //鼠标按下
        box.onmousedown = function(){
            this.style.backgroundColor = '#f90';
        };

        // 鼠标抬起
        box.onmouseup = function(){
            this.style.backgroundColor = '#fff';
        };

        //鼠标移动
        box.onmousemove = function(event){
            this.innerHTML = 'x:'+event.clientX + ', y:'+event.clientY;
        }

    </script>
</body>
</html>
```

#### 鼠标拖拽案列

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        html,body {
            width: 100%;
            height: 100%;
            overflow: hidden;
        }
        #box {
            position: absolute;
            width: 150px;
            height: 150px;
            background: #f90;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div id="box"></div>
    <script>
        //获取元素
        var box = document.querySelector('#box');

        //绑定鼠标按下事件
        box.onmousedown = function(event){
            //获取鼠标在元素上的位置
            var eleLeft = event.offsetX;
            var eleTop = event.offsetY;
            //重新设置颜色
            this.style.backgroundColor = 'pink';
            //绑定鼠标移动事件
            document.onmousemove = function(event){
                //根据鼠标的位置，计算元素的位置
                var left = event.clientX - eleLeft;
                var top = event.clientY - eleTop;
                // 进行位置大小限定
                if (left < 0) {
                    left = 0;
                } else if (left > window.innerWidth - box.offsetWidth) {
                    left = window.innerWidth - box.offsetWidth;
                }
                if (top < 0) {
                    top = 0;
                } else if (top > window.innerHeight - box.offsetHeight) {
                    top = window.innerHeight - box.offsetHeight;
                }
                //设置元素的位置
                box.style.left = left + 'px';
                box.style.top = top + 'px';
            }
        };

        // 鼠标抬起
        document.onmouseup = function(){
            //恢复颜色
            box.style.backgroundColor = '#f90';
            //解除鼠标移动事件的绑定
            this.onmousemove = null;
        }

    </script>
</body>
</html>
```

#### ③mouseover 鼠标悬停  /   mouseout 鼠标离开

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        ul {
            list-style: none;
        }
        .news-list {
            margin: 100px auto;
            width: 800px;
        }
        .news-list li {
            padding: 20px;
            border-bottom: 1px dotted #ccc;
        }

    </style>
</head>
<body>
    <ul class="news-list">
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
    </ul>
    <script>
        //获取所有的li
        var lis = document.querySelectorAll('.news-list li');

        // 给每个li绑定 mouseover事件
        lis.forEach(function (li) {
           li.onmouseover = function(){
               this.style.backgroundColor = '#f90';
           };
           li.onmouseout = function(){
                this.style.backgroundColor = '';
           }
        });

    </script>
</body>
</html>
```

#### ④mouseover 和 mouseenter的区别

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        #outer {
            width: 200px;
            height: 200px;
            background: red;
            overflow: hidden;
        }
        #inner {
            margin:50px;
            width: 100px;
            height: 100px;
            background: green;
        }
    </style>
</head>
<body>
    <div id="outer">
        <div id="inner"></div>
    </div>

    <script>
        // 获取元素
        var outer = document.querySelector('#outer');

        //绑定元素
       /* outer.onmouseover = function(){
            console.log('mouseover');
        };
        outer.onmouseout = function(){
            console.log('mouseout')
        };*/

        //代替方法
        outer.onmouseenter = function(){
            console.log('mouseenter');
        };
        outer.onmouseleave = function(){
            console.log('mouseleave')
        };

    </script>
</body>
</html>
```



### 1.2 键盘事件

```
keydown   键盘的按键按下
keyup	  键盘的按键抬起
keypress  键盘的按键按下（字符按键）
```

```html
<script>
        //键盘按键按下
        document.onkeydown = function(event){
           var r = Math.floor(Math.random() * 256);
           var g = Math.floor(Math.random() * 256);
           var b = Math.floor(Math.random() * 256);
           document.body.style.backgroundColor = 'rgb('+r+','+g+','+b+')';

            console.log('keydown', event.keyCode);
        };

        //键盘抬起
        document.onkeyup = function(){
            document.body.style.backgroundColor = '#fff';
        };

        //keypress 按键按下
        document.onkeypress = function(){
            console.log('keypress');
        }

    </script>
```

#### 按键盘输入内容

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        body {
            font-size: 40px;
        }
    </style>

</head>
<body>

    <div id="content"></div>


    <script>
        document.onkeypress = function(event){
            var content = document.querySelector('#content');
            content.innerHTML += String.fromCharCode(event.keyCode);
        }

    </script>
</body>
</html>
```

#### 按键盘输入内容放大

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        input {
            font-size: 16px;
            padding: 10px;
            width: 300px;
            border: 1px solid #ccc;
        }
        #box {
            padding: 20px 40px;
            font-size: 30px;
        }
    </style>

</head>
<body>

    <input type="text" id="input">
    <div id="box"></div>


    <script>
        //获取元素
        var input = document.querySelector('#input');
        var box = document.querySelector('#box');

        //按键抬起事件
        input.onkeyup = function(){
            box.innerHTML = input.value;
        }

    </script>
</body>
</html>
```

#### 键盘控制元素移动

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        html,body {
            width: 100%;
            height: 100%;
            overflow: hidden;
        }
        #plane {
            position: absolute;
            left: 200px;
            top: 500px;
            width: 50px;
            height: 50px;
            background: #f90;
        }
    </style>

</head>
<body>

    <div id="plane"></div>
    <script>
        //获取元素
        var plane = document.querySelector('#plane');

        //键盘按下事件
        document.onkeydown = function(event){
            //判断按键
            switch (event.keyCode) {
                case 37: //向左移动
                    plane.style.left =  plane.offsetLeft - 5 + 'px';
                    break;
                case 38: //向上移动
                    plane.style.top = plane.offsetTop - 5 + 'px';
                    break;
                case 39:
                    plane.style.left = plane.offsetLeft + 5 + 'px';
                    break;
                case 40:
                    plane.style.top = plane.offsetTop + 5 + 'px';
            }
        }
    </script>
</body>
</html>
```



### 1.3 文档事件

```
load  	 		加载完成
unload   		文档关闭  浏览器绑定该事件的时候，不允许弹框。
beforeunload    文档关闭之前
```

#### load加载完成

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        html,body {
            width: 100%;
            height: 100%;
            overflow: hidden;
        }

    </style>

    <script>
       /* var box = document.querySelector('#box');
        console.log(box); //null
*/

    </script>

</head>
<body>

    <div id="box"></div>

    <img src="../images/1.jpg" alt="图片" id="myImg">

    <script>
        /*var box = document.querySelector('#box');
        console.log(box); //*/

        // 加载完成 通常绑定给window,body
        // 页面中所有的一切加载完毕（html,css渲染号，外部的文件加载完成）
        window.onload = function(){
            console.log('啊，加载完成了');

            var box = document.querySelector('#box');
            console.log(box); //null

            var imgNode = document.querySelector('#myImg');
            console.log(imgNode);
            console.log(imgNode.offsetHeight); //获取图片的高度
        }

    </script>
</body>
</html>
```

#### unload 文档关闭  /  beforeunload 文档关闭之前

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        html,body {
            width: 100%;
            height: 100%;
            overflow: hidden;
        }

    </style>

    <script>

    </script>

</head>
<body>

    <div id="box"></div>

    <img src="../images/1.jpg" alt="图片" id="myImg">

    <script>

        //浏览器不允许在关闭页面的时候弹框！！！
       /* window.onunload = function(){
            confirm('确认要关闭吗？');
        };*/


        window.onbeforeunload = function(){
            //confirm('确认要关闭吗？');
            return '确认要关闭吗？';
        }

    </script>
</body>
</html>
```



### 1.4 表单事件

```
submit		表单提交的时候
reset		表单重置的时候
blur		当表单控件失去焦点的时候
focus		当表单控件获取焦点的时候
select      当输入框内的文本被选中的时候
change		表单控件内容改变的时候 用于select或者input:radio以及input:checkbox
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        html,body {
            width: 100%;
            height: 100%;
            overflow: hidden;
        }
        form {
            margin: 100px;
        }
        input {
            color: #ccc;
        }

    </style>


</head>
<body>

    <form action="1.php" id="myForm">
        用户名： <br>
        <input type="text" name="username" id="usernameInput" value="请输入用户名"> <br>
        <br>
        介绍: <br>
        <textarea name="des" id="desTextarea" cols="30" rows="10"></textarea>
        <br>
        <br>
        <button>提交</button>
    </form>

    <script>
        //获取元素
        var form = document.querySelector('#myForm');
        // 提交表单
        form.onsubmit = function(){
            alert('啊，我被提交了');
            return false;  //阻止表单的提交
        };

        var usernameInput = document.querySelector('#usernameInput');
        //失去焦点
        usernameInput.onblur = function(){
            //表单的验证
            console.log('我input失去焦点了');
        };

        //获取焦点
        usernameInput.onfocus = function(){
            console.log('我input获取焦点了');
            this.value = '';
            this.style.color = '#000';
        };


        //获取textarea
        var textarea = document.querySelector('#desTextarea');
        textarea.onselect = function(){
            alert('啊，我被选中了');
        };


        //给文本输入框绑定 change事件
        usernameInput.onchange = function(){
            alert('我被改变了');
        }

    </script>
</body>
</html>
```

#### 地址联动，下拉列表

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>dom</title>
    <style>
        select {
            width: 120px;
        }

    </style>


</head>
<body>

    <select id="prov"></select>
    <select id="city"></select>

    <script>
        //定义数组 定义省的信息
        var provList = ['广东', '广西', '福建', '湖南', '江西'];
        //定义数组 定义城市信息
        var cityList = [
            ['广州', '深圳', '东莞', '惠州', '佛山'],
            ['南宁', '桂林', '柳州', '百色', '北海'],
            ['福州', '厦门', '漳州', '泉州', '三明'],
            ['长沙', '常德', '岳阳', '湘潭', '衡阳'],
            ['南昌', '赣州', '景德镇', '九江', '上饶']
        ];

        //获取select元素
        var provSelect = document.querySelector('#prov');
        var citySelect = document.querySelector('#city');

        // 把省的select 添加选项
        provList.forEach(function(item,index){
           provSelect.add(new Option(item, index));
        });

        //给省的select 绑定change事件
        provSelect.onchange = function(){
            // 清空原来的城市信息
            citySelect.options.length = 0;
            //获取该省对应的城市
            var citys = cityList[this.value];
            //把城市信息添加到城市的select内
            citys.forEach(function(item, index) {
                citySelect.add(new Option(item, index));
            });
        };

        // 手动触发事件
        provSelect.onchange();

    </script>
</body>
</html>
```



## 其他

### 1. 视口大小（获取视口的大小）

```
window.innerWidth	window.innerHeight

document.documentElement.clientWidth	document.documentElement.clientHeight
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>

    </style>
</head>
<body>
    <div style="height: 400px;"></div>

    <script>
        console.log(document.documentElement.clientHeight);
        console.log(window.innerHeight);

        console.log('');
        console.log(document.body.clientHeight);

    </script>
</body>
</html>
```



## 练习

### 1. 放大镜

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>
        #smallImage {
            position: relative;
            width: 400px;
            height: 400px;
            cursor: move;
        }
        #smallImage img {
            width: 400px;
            height: 400px;
            display: block;
        }
        #zoom {
            position: absolute;
            left: 0;
            top: 0;
            width: 200px;
            height: 200px;
            background-image: url('../images/zoom/zoom-bg.png');
            display: none;
        }
        #bigImage {
            display: none;
            position: absolute;
            width: 400px;
            height: 400px;
            overflow: hidden;
        }
        #bigImage img {
            width: 800px;
            height: 800px;
            display: block;
        }
    </style>
</head>
<body>

    <div id="smallImage">
        <img src="../images/zoom/small.jpg" alt="小图">
        <div id="zoom"></div>
    </div>
    <div id="bigImage">
        <img src="../images/zoom/big.jpg" alt="大图">
    </div>


    <script>
        //获取元素
        var smallImage = document.querySelector('#smallImage');
        var bigImage = document.querySelector('#bigImage');
        var zoom = document.querySelector('#zoom');

        // 小图 鼠标悬停在上面， 大图显示
        smallImage.onmouseenter = function(){
            //计算大图的位置
            bigImage.style.left = smallImage.offsetLeft + smallImage.offsetWidth + 10 + 'px';
            bigImage.style.top = smallImage.offsetTop + 'px';
            //大图显示
            bigImage.style.display = 'block';
            //zoom显示
            zoom.style.display = 'block';
        };
        // 鼠标离开小图，大图隐藏
        smallImage.onmouseleave = function(){
            bigImage.style.display = 'none';
            zoom.style.display = 'none';
        };
        //鼠标在小图上移动
        smallImage.onmousemove = function(event){
            //获取鼠标在小图上的位置
            var left = event.clientX - smallImage.getBoundingClientRect().left;
            var top = event.clientY - smallImage.getBoundingClientRect().top;

            //计算zoom的位置
            var zoomLeft = left - zoom.offsetWidth/2;
            var zoomTop = top - zoom.offsetHeight/2;

            //zoom大小限制
            if (zoomLeft < 0) {
                zoomLeft = 0;
            } else if (zoomLeft > smallImage.offsetWidth - zoom.offsetWidth) {
                zoomLeft = smallImage.offsetWidth - zoom.offsetWidth;
            }
            if (zoomTop < 0) {
                zoomTop = 0;
            } else if (zoomTop > smallImage.offsetHeight - zoom.offsetHeight) {
                zoomTop = smallImage.offsetHeight - zoom.offsetHeight;
            }


            //设置zoom位置
            zoom.style.left = zoomLeft + 'px';
            zoom.style.top = zoomTop + 'px';

            // 根据鼠标在小图上的位置，设置比例，设置大图的位置
            bigImage.scrollLeft = zoomLeft * 2;
            bigImage.scrollTop = zoomTop * 2;
        }

    </script>

</body>
</html>
```





# 第十五天，JavaScript 课堂笔记

## 事件回顾

### 1  事件的绑定

#### 1.1 三种绑定方式

```
① 在标签内，作为标签的属性
② 作为标签元素的方法  btn.onclick = function(){}
③ 事件监听方式
	addEventListener(事件名, 回调函数)
	attachEvent(on事件名, 回调函数)
```

#### 1.2 解除事件的绑定

```
① 前两种方式绑定的事件
  覆盖
  btn.onclick = null;
  
② 事件监听方式绑定
   removeEventListene()
   detachEvent()
```

#### 1.3 捕获和冒泡

```
事件是一个动作
发生了事件，就会有捕获和冒泡两个阶段
捕获阶段，从根节点一直到触发事件的元素
冒泡阶段，从触发事件的元素到根节点

事件默认在冒泡阶段触发

设置事件在捕获阶段触发
	addEventListener 第三个参数 设置为true
```

### 2. 事件中的this

```html
<button onclick="demo(this) (这个地方this指向button元素)">
<script>
	function demo(){
		this; //指向window
	}
	
	
	btn,onclick = function(){
		this; //btn元素
	}
	
	btn.addEventListener('click', function(){
		this; //btn元素
	})
</script>
```

### 3 事件列表

#### 3.1 鼠标事件

```
click   	鼠标单击
dblclick   	鼠标双击
contextmenu  右击
mousedown    鼠标按键按下
mouseup      鼠标按键抬起
mousemove    鼠标移动
mouseover	  鼠标悬停在元素上
mouseout	  鼠标离开元素
mouseenter	  代替 mouseover;  IE9+
mouseleave    代替 mouseout;   IE9+
```

#### 3.2 键盘事件

```
keydown  键盘按键按下    控制元素移动（游戏）
keyup    键盘按键抬起     实时获取输入框内容
keypress  键盘按键按下（只有可输入字符能触发） 获取用户输入字符
```

#### 3.3 文档事件

```
load     文档加载完毕 绑定给window
unload    文档关闭 绑定给window
beforeunload   文档关闭之前 绑定给window
```

#### 3.4 表单事件

```
submit		表单提交的时候，submit事件绑定form元素
reset		表单重置的时候，reset事件绑定给form元素
blur		失去焦点 ，绑定表单控件元素。 用于输入格式的验证
focus		获取焦点的时候， 绑定给表单控件元素
select      文本被选中的时候，绑定给文本输入框元素
change      内容改变的时候。 通常绑定给 select、input:checkbox、input:radio
```



## 以下是第十五天的课程

#### 3.5 图片事件

```
load	   图片加载完毕
error      图片加载错误
abort 	   图片加载中断
```

```html
<body>
    <img src="../images/11.jpg" alt="一张美丽的图片" id="bImage">
    <script>
        //获取图片元素
        var imgNode = document.querySelector('#bImage');

        //图片加载成功
        imgNode.onload = function(){
            console.log('图片加载成功！');
            console.log(this.offsetWidth, this.offsetHeight);
        };

        imgNode.onerror = function(){
            console.log('图片加载失败！');
            this.src = '../images/noimage.png';
        }
    </script>

</body>
```



#### 3.6 其他事件

```
scroll     内容发生滚动  绑定给有滚动条的元素或者window
resize     视口大小发生变化  绑定给window (主要是做视配用的)
```

```html
<script>
        window.onresize = function(){
            console.log('视口大小发生变化了');
        }
 </script>
```



#### ①scroll导航栏顶部案列

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        h1 {
            padding: 20px;
            margin: 20px;
        }
        #nav {
            background: #333;
            line-height: 40px;
        }
        #nav.fixed {
            position: fixed;
            left: 0;
            top: 0;
            width: 100%;

        }
        #nav a {
            display: inline-block;
            color: #fff;
            width: 120px;
            text-align: center;
            text-decoration: none;
        }
        #box {
            margin: 100px auto;
            width: 600px;
            padding: 20px;
            border: 1px solid #ccc;

        }
    </style>
</head>
<body>
    <h1>啊，一个页面</h1>
    <nav id="nav">
        <a href="javascript:">首页</a>
        <a href="javascript:">博客</a>
        <a href="javascript:">论坛</a>
        <a href="javascript:">关于我们</a>
        <a href="javascript:">举报我们</a>
    </nav>


    <div id="box">
        <p>Lorem ipsum dolor sit amet, consectetur.</p> //*10（内容超出才显示）
        
    </div>
    <script>
        //获取导航元素
        var nav = document.querySelector('#nav');
        //获取nav距离根元素顶部的距离 固定不变的
        var navTop = nav.offsetTop;

        //页面发生滚动
        window.onscroll = function(){

            //获取页面滚动距离
            var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;

            //console.log(scrollTop, navTop);

            //如果页面滚动的距离 >= nav距离页面顶部距离
            if (scrollTop >= navTop) {
                nav.classList.add('fixed');
                document.body.style.paddingTop = nav.offsetHeight + 'px';
            } else {
                nav.classList.remove('fixed');
                document.body.style.paddingTop = '0';
            }
        };

    </script>

</body>
</html>
```



### 4 Event对象

#### 4.1 鼠标事件对象 MouseEvent

```
clientX / clientY		鼠标在视口上的位置
offsetX / offsetY		鼠标在元素上的位置
pageX / pageY			鼠标在页面上（根元素上）的位置
screenX / screenY		鼠标在屏幕上的位置	
button					鼠标按键键值 （0表示左键，1表示滑轮， 2表示右键）
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>
        #box {
            margin: 200px auto;
            width: 200px;
            height: 200px;
            background: #f90;
        }
    </style>
</head>
<body>
    <div style="height: 300px;"></div>
    <div id="box"></div>
    <div style="height: 500px;"></div>

    <script>
        //获取元素
        var box = document.querySelector('#box');

        // 绑定鼠标事件
        box.onclick = function(event) {
            console.log('鼠标在元素上的位置：'+event.offsetX+ ' , '+event.offsetY);
            console.log('鼠标在视口上的位置：'+event.clientX+ ' , '+event.clientY);
            console.log('鼠标在页面上的位置：'+event.pageX+ ' , '+event.pageY);
            console.log('鼠标在屏幕的位置：'+event.screenX+ ' , '+event.screenY);
        }
    </script>

    
用于button的
    <div id="box"></div>


    <script>
        //获取元素
        var box = document.querySelector('#box');

        //鼠标按下
        box.onmousedown = function(event) {
            console.log('啊，鼠标按下了', event.button);
        }
    </script>
    
</body>
</html>
```



#### 4.2 键盘事件对象 KeyboardEvent

```
keyCode  键盘按键对应的ascii值
which    同keyCode
key		 键盘按键的值 （返回是字符串）  dom3
```

```html
<body>

    <div id="box"></div>


    <script>
        document.onkeydown = function(event){
            //console.log(event.keyCode);
            //console.log(event.which);
            //console.log(event.key);

            console.log(event.ctrlKey)
        }
    </script>

</body>
```



#### 4.3 所有的事件对象共有的属性 Event

```
type		返回事件类型（事件名）
timestamp   触发事件时的时间戳（从页面打开的那一刻开始计算）
target		获取目标元素 事件委派
stopPropagation()   阻止冒泡
preventDefault()    阻止默认行为（一些元素发生某些事件之后有默认行为）比如a标签，提交按钮
```

> **注意：**
>
> 在事件绑定的函数内，return false 既能阻止事件冒泡，又可以阻止默认行为。

#### type / timestamp / target 

```html
<body>
    <div id="box"></div>

    <script>
        var box = document.querySelector('#box');
     /*   box.onclick = function(event){
            console.log(event.type, event.timeStamp);
        };*/
        document.onkeydown = function(event){
            console.log(event.type);
        };

        document.onclick = function(event) {
            console.log(event.target);
        }

    </script>
</body>
```

#### stopPropagation（阻止冒泡）

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>
        #outer {
            margin: 100px;
            width: 300px;
            height: 300px;
            padding: 100px;
            background: pink;
        }
        #inner {
            width: 100px;
            height: 100px;
            background: #f90;
        }
    </style>
</head>
<body>
    <div id="outer">
        <div id="inner"></div>
    </div>


    <script>
        var outer = document.querySelector('#outer');
        var inner = document.querySelector('#inner');

        outer.onclick = function(){
            console.log('outer click');
        };
        inner.onclick = function(event){
            console.log('inner click');

            event.stopPropagation();
        };
    </script>

</body>
</html>
```

#### preventDefault(阻止默认事件)

```html
<body>
    <a href="http://www.baidu.com" id="myLink">我是超链接</a>


    <script>

        var a = document.querySelector('#myLink');

        a.onclick = function(event){
            alert('啊，你点我');

            event.preventDefault(); //阻止默认行为
        };

        // 所有元素的右击事件，都有默认行为
        document.oncontextmenu = function(event){

            event.preventDefault();
            alert('啊，我被右击了');
        }

    </script>

</body>
```



#### 5 target事件委派案列

```
给新添加的元素也绑定事件

原理：
	给一个一直都存在的元素绑定事件（要绑定元素的祖先元素）
	在触发事件之后，判断target（目标元素）必须是我们要绑定事件的元素，才进行响应操作
```

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件</title>
    <style>
        #box {
            margin: 100px auto;
            width: 800px;
        }
        .item {
            padding: 20px;
            border: 1px solid #ccc;
            margin-bottom: 10px;
        }
        .item.active {
            background: #f90;
        }
    </style>
</head>
<body>

    <button id="btn">添加一个item</button>
    <div id="box">
        <div class="item">Lorem ipsum dolor sit amet.</div>
        <div class="item">Lorem ipsum dolor sit amet.</div>
        <div class="item">Lorem ipsum dolor sit amet.</div>
        <div class="item">Lorem ipsum dolor sit amet.</div>
        <div class="item">Lorem ipsum dolor sit amet.</div>
    </div>


    <script>
        //获取元素
        var box = document.querySelector('#box');
        var btn = document.querySelector('#btn');


        //获取所有的item元素
        //var items = document.querySelectorAll('#box .item');
        /*var items = box.getElementsByTagName('div');
        // 给每个item元素绑定单击事件
        [].forEach.call(items, function (item, index) {
            item.onclick = function() {
                this.classList.toggle('active');
            }
        });
*/

        //给一个一直都存在的元素绑定事件
        box.onclick = function(event){
            //判断 如果点击的 .item元素
            if (event.target.className.indexOf('item') >= 0) {
                event.target.classList.toggle('active');
            }
        };

        //单击添加item
        btn.onclick = function(){
            //创建div元素
            var div = document.createElement('div');
            div.className = 'item';
            div.innerHTML = '哈哈哈，嘿嘿额';
            //添加到box内
            box.appendChild(div);
        };

    </script>

</body>
</html>
```



## 作业练习

```
1. 所有的案例整到一起
2. JS（ECMAScript、BOM、DOM） 整理个思维导图
3. 练习
   addEeventListener 做个元素拖拽。
   轮播图（滑动效果）
  
```

#### ①addEeventListener 做个元素拖拽

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>拖拽</title>
    <style>
        #box {
            position: absolute;
            width: 150px;
            height: 150px;
            background: #f90;
        }
    </style>
</head>
<body>
    <div id="box"></div>
    <script>
        (function(){

            //获取元素
            var box = document.querySelector('#box');

            // 添加鼠标按键按下
            box.addEventListener('mousedown', function(event){
                //获取鼠标在元素上的位置
                box.eleX = event.offsetX;
                box.eleY = event.offsetY;

                //给元素添加鼠标移动事件
                document.addEventListener('mousemove', mousemoveFn)
            });

            // 添加鼠标按键抬起
            document.addEventListener('mouseup', function(){
                //解除鼠标移动事件的绑定
                document.removeEventListener('mousemove', mousemoveFn)

            });

            //鼠标移动时执行的函数
            function mousemoveFn(event) {
                //获取鼠标的在视口上的位置
                var clientX = event.clientX;
                var clientY = event.clientY;
                //计算元素的位置
                var left = clientX - box.eleX;
                var top = clientY - box.eleY;
                //设置元素的位置
                box.style.left = left + 'px';
                box.style.top = top + 'px';
            }
        })();
    </script>
</body>
</html>
```



#### ②轮播图（左右滑动效果）

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>轮播图</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        ul,ol {
            list-style: none;
        }
        #play {
            margin: 100px auto;
            width: 900px;
            height: 350px;
            overflow: hidden;
            position:relative;
        }
        #play img {
            display: block;
        }
        .image-list {
            position: absolute;
            left: 0;
            top: 0;
            /*transition: left .5s;*/
        }
        .image-list li {
            float: left;
            width: 900px;
            height: 350px;

        }
        .image-list li.current {

        }
        .icon-list {
            position: absolute;
            bottom: 10px;
            right: 10px;
        }
        .icon-list li {
            float: left;
            margin-right: 8px;
            width: 20px;
            height: 20px;
            color: #fff;
            font-size: 14px;
            text-align: center;
            line-height: 20px;
            border: 1px solid #fff;
            border-radius: 50%;
            cursor: pointer;
        }
        .icon-list li.current {
            color: #f60;
            border-color: #f60;
            background: #000;
        }
        .prev-btn,.next-btn {
            position: absolute;
            top: 0;
            bottom: 0;
            margin-top: auto;
            margin-bottom: auto;
            width: 40px;
            height: 100px;
            /*background: #000;*/
            background: url('images/play/index.png') no-repeat;
        }
        .prev-btn {
            left: 0;
        }
        .next-btn {
            right: 0;
            background-position:-50px 0;
        }
    </style>
</head>
<body>
    <div id="play">
        <ul class="image-list">
            <li><img src="images/play/01.jpg" alt="轮播图"></li>
            <li><img src="images/play/02.jpg" alt="轮播图"></li>
            <li><img src="images/play/03.jpg" alt="轮播图"></li>
            <li><img src="images/play/04.jpg" alt="轮播图"></li>
            <li><img src="images/play/05.jpg" alt="轮播图"></li>
        </ul>
        <ol class="icon-list">
            <li class="current">1</li>
            <li>2</li>
            <li>3</li>
            <li>4</li>
            <li>5</li>
        </ol>
        <div class="control-btns">
            <div class="prev-btn"></div>
            <div class="next-btn"></div>
        </div>
    </div>

    <script>
        //获取元素
        var play = document.querySelector('#play');  //包裹元素
        var imageList = play.querySelector('.image-list');
        var imageItems = imageList.getElementsByTagName('li'); //所有图片的集合
        var iconItems = play.querySelectorAll('.icon-list li');  //所有的控制按钮元素
        var prevBtn = play.querySelector('.prev-btn'); //上一张的按钮
        var nextBtn = play.querySelector('.next-btn'); //下一张的按钮
        var currentIndex = 0; //标记图标的索引
        var currentImageIndex = 1; //标记当前图片的索引
        var itemLength = iconItems.length; //图片的数量
        var duration = 5000;  //自动播放时间间隔

        //把原来的第一张图片克隆追加到最后，把原来的最后一张克隆追加到最前
        var firstImageItemClone = imageItems[0].cloneNode(true);
        var lastImageItemClone = imageItems[imageItems.length-1].cloneNode(true);
        imageList.appendChild(firstImageItemClone);
        imageList.insertBefore(lastImageItemClone, imageList.firstElementChild);

        //设置ul.image-list 元素的宽度， 宽度=所有图片宽度和
        imageList.style.width = imageItems[0].offsetWidth * imageItems.length + 'px';

        // 调整图片的位置
        setPlay();

        // 给每一个控制按钮 绑定单击事件
        iconItems.forEach(function (iconItem, index) {
            iconItem.onclick = function(){
                //重新设置索引标记
                currentIndex = index;
                //设置图片的索引
                currentImageIndex = index + 1;
                //设置高亮
                imageList.style.transition = 'left .5s';
                setPlay();
            }
        });

        //点击上一张
        prevBtn.onclick = function() {
            setIndex('prev');
        };

        //点击下一张
        nextBtn.onclick = function(){
            setIndex('next');
        };

        // 自动播放
        var intervalId = setInterval(function () {
            setIndex('next');
        }, duration);

        // 鼠标悬停在轮播图上，停止定时
        play.onmouseenter = function () {
            clearInterval(intervalId);
        };

        //鼠标离开轮播图，轮播继续
        play.onmouseleave = function(){
          intervalId = setInterval(function(){
              setIndex('next');
          }, duration);
        };

        /**
         * @param tag 值是prev表示上一张， 值是next表示下一张
         */
        function setIndex(tag) {
            if (tag === 'prev') {
                //当前的索引 -1
                currentIndex --;
                //判断范围
                if (currentIndex < 0) {
                    currentIndex = itemLength - 1;
                }
                // 图片索引变化
                currentImageIndex --;
                // 判断图片的索引范围
                if (currentImageIndex < 0) {
                    //瞬间切换imageList的位置
                    imageList.style.transition = 'none';
                    imageList.style.left = -imageItems[0].offsetWidth*(imageItems.length-2) + 'px';
                    //重新设置currentImageIndex
                    currentImageIndex = imageItems.length - 3;
                }
                setTimeout(function(){
                    // 设置过渡
                    imageList.style.transition = 'left .5s';
                    //设置高亮
                    setPlay();
                }, 1);
            } else if (tag === 'next') {
                //当前的索引标记 +1
                currentIndex ++;
                //如果 currentIndex 超出范围
                if (currentIndex > itemLength - 1) {
                    currentIndex = 0;
                }
                // 图片的索引变化
                currentImageIndex ++;
                // 如果图片的索引超出范围
                if (currentImageIndex > imageItems.length - 1) {
                    //瞬间 调整imageList的位置，调整到索引是1的位置
                    imageList.style.transition = 'none';
                    imageList.style.left = -imageItems[0].offsetWidth + 'px';
                    //设置索引应该显示第二张图片
                    currentImageIndex = 2;
                }
                setTimeout(function(){
                    // 设置过渡
                    imageList.style.transition = 'left .5s';
                    //设置高亮
                    setPlay();
                }, 1);
            }
        }

        // 实现根据 currentIndex 显示当前的图片和控制按钮
        function setPlay() {
            //排他 所有控制按钮的取消高亮，所有图片的隐藏
            iconItems.forEach(function (item, index) {
                item.classList.remove('current');
            });
            //当前控制按钮设置高亮 当前的图片显示
            iconItems[currentIndex].classList.add('current');
            //设置相应图片显示
            imageList.style.left = -currentImageIndex * imageItems[0].offsetWidth + 'px'

        }
    </script>
</body>
</html>

```



# 第十六天，JavaScript 课堂笔记 正则表达式

## 1. 正则的应用

- 匹配验证字符串（验证邮箱、电话、右边、QQ号）
- 爬虫程序、采集程序 （爬取图片、小视频）
- 富文本编辑器（百度Ueditor）



## 2. 学习正则

- 掌握如何定义正则
- 掌握在某个编程语言中如何使用正则



## 3. 正则的基本语法

### 3.1 原子

```
原子是正则表达式的最基本组成单位
正则表达式由 原子 和 对原子的修饰组成
一个原子匹配一个字符
```

#### ① 任意一个字符都是原子

```
任意的字母、数字、标点符号以及需要转义的特殊字符 都是原子
```

#### ② 具有特殊意义的原子

```
有些符号在正则表达式中具有特殊意义，如果要匹配符号本身，加转义 \
```

#### ③ 字符类

```
[...]  匹配指定的任意一个字符  例: [abcd] [a-z] [a-zA-Z0-9] 
[^...] 匹配除了指定字符之外的任意一个字符  例：[^abc_%]  [^a-z]  [^a-zA-Z0-9_$]
.	  匹配除了换行符之外任意一个字符 [^\n]
\w	  匹配任意一个数字、字母或者下划线  [a-zA-Z0-9_]
\W	  匹配除了数字、字母、下划线之外的任意字符     [^a-zA-Z0-9_]
\d	  匹配任意一个数字		[0-9]
\D    匹配任意一个非数字    [^0-9]
\s	  匹配任意一个空白字符   [\n\t\v\f\r ]
\S    匹配任意一个非空白字符  [^\n\t\v\f\r ]
```

```html
<script>
        var reg = /hello/;

        //特殊意义原子
        console.log('hello'.search(/./));
        console.log('he.llo'.search(/\./));
        console.log('');


        //字符类
        console.log(''.search(/./));
        console.log('\n'.search(/./));
        console.log('\nabc'.search(/./));

        console.log('abc'.search(/[bcd]/));
        console.log(/[abc]/.exec('apple'));
        console.log(/[^abc]/.exec('apple'));

        console.log(/[a-z]/.exec('apple')); //匹配任意一个小写字母
        console.log(/[a-zA-Z]/.exec('HellWorld')); //匹配任意一个大小写字母
        console.log(/[a-zA-Z0-9_$]/.exec('HellWorld')); //匹配任意一个大小写字母或数字或下划线或$

        console.log(/[^a-zA-Z]/.exec('Hell World')); //匹配任意除了大小写字母
        console.log('');


        console.log(/\w/.exec('我100hello'));
        console.log(/\W/.exec('我100hello'));
        console.log(/\W/.exec('100hello'));
        console.log('');


        console.log(/\d/.exec('hello100'));
        console.log(/\D/.exec('hello100'));
        console.log('');

        console.log(/\s/.exec('hello world'));
        console.log(/\s/.exec('hello\nworld'));
        console.log(/\s/.exec('hello\tworld'));
        console.log(/\S/.exec('hello\tworld'));

        console.log(/hello/.exec('hello world'));


    </script>
```



### 3.2 原子的数量修饰

#### 数量修饰符

```
{n}  前面的原子连续出现n次
{n,m}  前面的原子连续出现n次到m次
{n,}   前面的原子连续出现n次以及以上
?	   前面的原子0次或一次   {0,1}
+	   前面的原子出现1次以及以上  {1,}
*	   0次、1次或多次任意次  {0，}     万能匹配： /[.\n]*/
```

```html
<script>
        console.log(/h{5}llo/.exec('hello'));
        console.log(/h{5}llo/.exec('hellohhhh'));
        console.log(/h{5}llo/.exec('hhhhhel'));
        console.log(/h{5}llo/.exec('hhhhhllo'));
        console.log('');

        console.log(/\w{5}/.exec('hello'));
        console.log(/\w{5}/.exec('hello world'));
        console.log('');

        console.log(/\w{2,6}/.exec('helloworld'));
        console.log(/\w{2,6}/.exec('he我哈哈'));
        console.log(/\w{2,6}/.exec('h我哈哈'));
        console.log(/\w{2,6}/.exec('hello world'));
        console.log('');

        console.log(/\w{3,}/.exec('hello world'));
        console.log(/\w{3,}/.exec('helloworld'));
        console.log(/\w{3,}/.exec('我 go to 学校'));
        console.log(/\w{3,}/.exec('我 goto 学校'));

        console.log(/\w{3,}/.exec('\\w{3,}'));
        console.log(/\w{3,}/.exec('a{3,}'));
        console.log('');


        console.log(/\w?/.exec(''));
        console.log(/\w?/.exec('我们'));
        console.log(/\w?/.exec('hello'));
        console.log('');
        console.log(/\w+/.exec('hello'));
        console.log(/\w+/.exec('他们'));
        console.log('');
        console.log(/\w*/.exec('他们'));
        console.log(/\w*/.exec('hello'));
        console.log(/\w*/.exec(''));
    </script>
```



#### 贪婪匹配

```
尽可能多的匹配
阻止贪婪匹配  在数量修饰符的后面加个?
```

```html
  <script>
        console.log(/\w{2,6}/.exec('helloworld'));  //6
        console.log(/\w{2,6}?/.exec('helloworld')); //2
        console.log(/\w?/.exec('helloworld'));      //1
        console.log(/\w??/.exec('helloworld'));     //0
        console.log(/\w+?/.exec('helloworld'));     //1
    </script>
```

#### 贪婪匹配案列

```html
<body>
    <div id="box">
        <div class="container"><div class="item"><img src="http://www.google.com/100.jpg" alt="一张美丽的图片" /></div></div>
    </div>
    <script>
        //获取元素
        var box = document.querySelector('#box');
        //获取内容
        var content = box.innerHTML;


        console.log(content);

        //定义一个可以匹配 img标签的正则表达式
        var imgReg = /<img .+?>/;

        // 获取匹配结果
        console.log('匹配结果：');
        var res = imgReg.exec(content);
        console.log(res[0]);
    </script>
</body>
```



### 3.3 原子的位置修饰

#### ① 单词边界

```
\b	单词边界 （空格、标点符号、字符串的开始和结束、换行）
\B	非单词边界
```

```html
<script>
        console.log(/re/.exec('express result are'));
        console.log(/\bre/.exec('express result are'));
        console.log(/re\b/.exec('express result are'));
        console.log('');
        console.log(/\bre\b/.exec('express result are'));
        console.log(/\bre\b/.exec('express,re\nresult are'));

        console.log('');
        console.log(/hello\bworld/.exec('hello world'));
        console.log(/hello\b world/.exec('hello world'));
        console.log('');

        console.log(/re\B/.exec('express result are'));
        console.log(/\bre\B/.exec('express result are'));
        console.log(/\Bre\B/.exec('express result are'));
    </script>
```



#### ② 字符串边界

```
^	字符串开始边界  
$   字符串结束边界
```

```html
<script>
        console.log(/hello/.exec('我和你 hello world'));
        console.log(/^hello$/.exec('我和你 hello world')); //不能
        console.log(/^hello$/.exec('hello'));              //可以
        console.log(/^hello$/.exec('hello world'));//不能
        console.log(/^hello/.exec('hello world')); //可以

    </script>
```



### 3.4 选择修饰符

```
|   类似于逻辑或
/apple|orange/ 匹配 apple或者orange
```

```html
<script>
        var reg = /apple|orange/;

        console.log(reg.exec('apple'));
        console.log(reg.exec('orange'));
        console.log(reg.exec('applerange'));

    </script>
```



### 3.5 模式单元 （）

```
① 改变优先级
② 把多个原子当做一个整体
③ 会把模式单元匹配的内容暂存内存； 如果不想暂存内存 (?:)
④ 反向引用。 str.replace()方法中可以使用反向引用。
```

```html
<script>
        //优先级变高
        console.log(/appl(e|o)range/.exec('apple'));
        console.log(/appl(e|o)range/.exec('orange'));
        console.log(/appl(e|o)range/.exec('applerange'));
        console.log(/appl(e|o)range/.exec('applorange'));
        console.log('');


        //把多个原子当做一个整体
        console.log(/apple{3}/.exec('appleee'));
        console.log(/(apple){3}/.exec('appleappleapple'));
        console.log('');


        //模式单元的内容，会暂存内存;会把模式单元的内容单独匹配出来
        console.log(/apple/.exec('apple'));
        console.log(/a(pp)l(e)/.exec('apple'));
        console.log('');

        //告诉模式单元不暂存内存
        console.log(/a(pp)l(?:e)/.exec('apple'));
        console.log('');

    </script>
```



### 3.6 先行断言/后行断言 （位置修饰）

```
正向先行断言：  原子(?=)   正向预查
负向先行断言：  原子(?!)   反向预查  
正向后行断言：  (?<=)原子
负向后行断言:   (?<!)原子
```

```
断言本质上是位置修饰，不参与匹配。
```

```html
<script>
        // 正向先行断言
        // 匹配apple,要求apple后面是orange
        console.log(/apple(?=orange)/.exec('apple')); //null
        console.log(/apple(?=orange)/.exec('appleorange')); //apple
        console.log(/apple(?=orange)apple/.exec('appleorangeapple')); //null
        console.log(/apple(?=orange)orange/.exec('appleorangeapple')); //appleorange
        console.log('');

        // 负向先行断言
        // 匹配apple，要求apple的后面不能是orange
        console.log(/apple(?!orange)/.exec('apple'));
        console.log(/apple(?!orange)/.exec('appleorange'));  // null
        console.log('');


        // 正向后行断言
        // 匹配apple，要求apple的前面 是banana
        console.log(/(?<=banana)apple/.exec('apple'));//null
        console.log(/(?<=banana)apple/.exec('bananaapple')); //apple
        console.log('');


        // 负向后行断言
        //匹配apple要求前面不能是 banana
        console.log( /(?<!banana)apple/.exec('apple') );
        console.log( /(?<!banana)apple/.exec('bananaapple') );  //null


    </script>
```



### 3.7 修饰符（模式修正符） （修饰整个正则表达式）

```
i  不区分大小写
g  全局匹配
m  多行模式。 在多行模式下，换行可以被当做字符串边界
```

```html
 <script>
        //i 不区分大小写
       console.log(/a{3}/.exec('aaa'));
       console.log(/a{3}/.exec('aAa'));
       console.log(/a{3}/i.exec('aAa'));
       console.log('');

        //g全局匹配

        // m 多行模式
        var msg = `锄禾日当午
汗滴禾下土`;

        console.log(msg);

        console.log(/当午/.exec(msg));
        console.log(/当午$/.exec(msg));
        console.log(/当午$/m.exec(msg));

    </script>
```



## 4 正则在JavaScript的应用

### 4.1 在JS中如何定义正则

```js
//第一种 直接量
var reg = /hello/;

// 第二种 转换函数
var reg = RegExp('hello');

// 第三种 构造函数方式
var reg = new RegExp('hello');
```

### 4.2 字符串对象提供的方法

```
search()   	返回第一个匹配的字符串的位置，没有匹配返回-1
match()		返回数组，数组成员是第一个匹配的内容和模式单元匹配的内容；如果全局模式，数组中是每一个匹配到的内容。 匹配不成功null
replace()	替换。默认只替换一个，全局模式替换所有； 与模式单元配合后向引用。
split()     把字符串分割为数组。可以用正则指定多个分隔符。
```



### 4.3 RegExp对象提供的方法

```
test()  匹配成功true，匹配不成功false
exec()	返回数组，数组成员是第一个匹配的内容和模式单元匹配的内容；全局模式没用；匹配不成功null
```

```html
<script>
        //match
        var msg = 'apple banana orange pear xigua liulian putao shanzha';


        console.log(/\w+/.exec(msg));
        console.log(msg.match(/\w+/));
        console.log('');

        console.log(/(\w)+/.exec(msg));
        console.log(msg.match(/(\w)+/));
        console.log('');

        console.log(/(\w)+/g.exec(msg)); //就匹配一个
        console.log(msg.match(/(\w)+/g)); //匹配多个
        console.log('');

        msg = 'apple banana,orange-pear~xigua liulian putao shanzha';

        console.log(msg.split(' '));
        console.log(msg.split(','));
        console.log(msg.split(/[,\-~ ]/));
        console.log('');

        console.log(/\w{2}/.test('hello'));
        console.log(/\w{2}/.test('h'));

    </script>
```



#### 模式单元反向引用

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>正则</title>
    <style>
        #box {
            width: 400px;
            padding: 20px;
            border: 1px solid #ccc;
            font-size: 24px;
            font-family: '宋体';
        }
    </style>
</head>
<body>
    <div id="box">
        话说金莲陪着武松正在楼上说话未了，只见武大买了些肉菜果饼归家。放在厨
        ，走上楼来，叫道："大嫂，你且下来则个。"那妇人应道："你看那不晓事的，
        ！叔叔在此无人陪侍，却交我撇了下去。"武松道："嫂嫂请方便。"妇人道："
        何不去间壁请王乾娘来安排？只是这般不见便。"武大便自去央了间壁王婆来。安
        排端正，都拿上楼来，摆在桌子上，无非是些鱼肉果菜点心之类。随即烫酒上来。
        武大叫妇人坐了主位，武松对席，武大打横。三人坐下，把酒来斟，武大筛酒在各
        人面前。那妇人拿起酒来道："叔叔休怪，没甚管待，请杯儿水酒。"武松道："
        感谢嫂嫂，休这般说。"
    </div>
    <br>
    <br>
    <button id="btn">替换</button>
    <script>
        var btn = document.querySelector('#btn');
        btn.onclick = function(){
            var box = document.querySelector('#box');
            var content = box.innerHTML;
            //替换字符串
            box.innerHTML = content.replace(/"([^"]+)"/g, '“$1”');
        }
    </script>
</body>
</html>
```



#### 匹配URL案列

```html
<body>
    <div id="box">
        大家好，我是渣渣辉，我的艳照地址 https://www.zhazhahui.com/images/20192323/100.zip abasdfadsf，欢迎访问。
    </div>
    <script>
        var content = document.querySelector('#box').innerHTML;


        console.log(content);

        //定义正则 匹配url
        var url_reg = /(https?):\/\/(.+?)\/(.+?\.\w+)/;

        var res = url_reg.exec(content);
        console.log(res);

        console.log(res[0]);
        console.log('协议：'+res[1]);
        console.log('主机名：'+res[2]);
        console.log('pathname：'+res[3]);

    </script>
</body>
```

#### 常见的正则表达式（邮箱，电话号码）

```html
<script>
        // QQ号的正则
        var qqReg = /^\d{5,12}$/;
        console.log(qqReg.test(12345678));

        // 手机号的正则
        var phoneNumReg = /\d{11}/;
        phoneNumReg = /^1[3-9]\d{9}$/;

        //邮箱的正则
        /*
        lala@163.com
        lala@qq.com
        lala@sina.com.cn
        www.baidu.中国
         */
        var emailReg = /^[\w-]+@[\w-]+(\.[^\.]+){1,3}$/;

        console.log(emailReg.exec('lala@163.con'));
        console.log(emailReg.exec('lala163.com'));

    </script>
```



## 5 正则练习

```
1. 表单验证
2. 正则计算器
3. 输入银行卡号，每隔四位自动加空格（选做）
```

 http://example.fuming.site/#/js 

#### ①表单验证

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表单验证</title>
    <style>
        input,button {
            padding: 10px;
            border: 1px solid #ccc;
            font-size: 16px;
            width: 300px;
            box-sizing: content-box;
        }
        button {
            background: #f5f5f5;
        }
    </style>
</head>
<body>
    <form action="1.php" id="regForm">
        <table>
            <tr>
                <td>用户名:</td>
                <td><input type="text" name="username" id="usernameInput"></td>
                <td id="usernameInfo"></td>
            </tr>
            <tr>
                <td>邮箱：</td>
                <td><input type="text" name="eamil" id="emailInput"></td>
                <td id="emailInfo"></td>
            </tr>
            <tr>
                <td>密码：</td>
                <td><input type="password" name="pwd" id="pwdInput"></td>
                <td id="pwdInfo"></td>
            </tr>
            <tr>
                <td>确认密码：</td>
                <td><input type="password" name="repwd" id="repwdInput"></td>
                <td id="repwdInfo"></td>
            </tr>
            <tr>
                <td></td>
                <td><button>注 册</button></td>
                <td></td>
            </tr>
        </table>
    </form>

    <script>
        
        (function () {
            //获取各个输入框元素
            var form = document.querySelector('#regForm');
            var usernameInput = document.querySelector('#usernameInput');
            var emailInput = document.querySelector('#emailInput');
            var pwdInput = document.querySelector('#pwdInput');
            var repwdInput = document.querySelector('#repwdInput');

            //验证用户名
            usernameInput.onblur = checkUsername;
            //验证邮箱
            emailInput.onblur =checkEmail;
            // 验证密码
            pwdInput.onblur = checkPwd;
            // 验证确认密码
            repwdInput.onblur = checkRepwd;
            // 表单提交时间
            form.onsubmit = function(){
                return checkUsername() && checkEmail() && checkPwd() && checkRepwd();
            };

            // 验证用户名的函数
            function checkUsername(){
                //定义验证用户名的正则
                var reg = /^\w{4,12}$/;
                // 获取用户的输入
                var value = usernameInput.value;
                //获取显示信息的td元素
                var td = document.querySelector('#usernameInfo');
                //判断是否满足要求
                if (value.search(reg) === -1) {
                    //不满足条件
                    td.innerHTML = '用户名要求是4到12位的数字、字母、下划线';
                    td.style.color = 'red';
                    return false;
                } else {
                    //满足条件
                    td.innerHTML = '用户名可用';
                    td.style.color = 'green';
                    return true;
                }
            }

            // 验证邮箱
            function checkEmail() {
                //定义验证邮箱的正则
                var reg = /^[\w-]+@[\w-]+(\.[^\.]+){1,3}$/;
                // 获取用户的输入
                var value = emailInput.value;
                //获取显示信息的td元素
                var td = document.querySelector('#emailInfo');
                //判断是否满足要求
                if (value.match(reg) === null) {
                    //不满足条件
                    td.innerHTML = '邮箱不正确';
                    td.style.color = 'red';
                    return false;
                } else {
                    //满足条件
                    td.innerHTML = '邮箱可用';
                    td.style.color = 'green';
                    return true;
                }
            }

            // 验证密码
            function checkPwd() {
                // 获取用户的输入
                var value = pwdInput.value;
                //获取显示信息的td元素
                var td = document.querySelector('#pwdInfo');
                //判断是否满足要求
                if (value.length < 6 || value.length > 18) {
                    //不满足条件
                    td.innerHTML = '密码必须6~18位';
                    td.style.color = 'red';
                    return false;
                } else {
                    //满足条件
                    td.innerHTML = '密码可用';
                    td.style.color = 'green';
                    return true;
                }
            }

            // 验证确认密码
            function checkRepwd() {
                // 获取密码和确认密码
                var pwd = pwdInput.value;
                var repwd = repwdInput.value;
                //获取显示信息的td元素
                var td = document.querySelector('#repwdInfo');
                //判断是否满足要求
                if (pwd !== repwd) {
                    //不满足条件
                    td.innerHTML = '两次密码不一致';
                    td.style.color = 'red';
                    return false;
                } else {
                    //满足条件
                    td.innerHTML = '确认密码正确';
                    td.style.color = 'green';
                    return true;
                }
            }

        })();
        
    </script>
</body>
</html>
```

#### ②正则计算器

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>正则计算器</title>
    <style>
        input,button {
            box-sizing: content-box;
            padding: 10px;
            width: 300px;
            font-size: 16px;
            border: 1px solid #ccc;
        }
        button {
            background: #f5f5f5;
        }
        #res {
            margin-top: 20px;
            font-size: 20px;
            padding: 10px;
        }
    </style>
</head>
<body>
    <input type="text" placeholder="请输入字符串" id="strInput"> <br><br>
    <input type="text" placeholder="请输入正则表达式" id="regInput"> <br><br>
    <button id="btn">验 证</button>
    <div id="res"></div>

    <script>
        (function () {
            //获取元素
            var strInput = document.querySelector('#strInput');
            var regInput = document.querySelector('#regInput');
            var btn = document.querySelector('#btn');
            var res = document.querySelector('#res');

            // 单击事件
            btn.onclick = function(){
                //获取用户输入的字符串
                var str = strInput.value;
                //获取用户输入的正则表达式
                var reg = RegExp(regInput.value);
                //进行验证
                if (reg.test(str)) {
                    res.innerHTML = '验证通过';
                } else {
                    res.innerHTML = '验证失败';
                }
            }

        })();
    </script>
</body>
</html>
```



#### ③输入银行卡号，每隔四位自动加空格（选做）

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>正则计算器</title>
    <style>
        input{
            box-sizing: content-box;
            padding: 10px;
            width: 300px;
            font-size: 16px;
            border: 1px solid #ccc;
        }

    </style>
</head>
<body>
    <label for="cardInput">请输入银行卡号：</label>
    <input type="text" id="cardInput" maxlength="23">

    <script>
        //获取input元素
        var input = document.querySelector('#cardInput');
        //绑定 keyup事件 随着输入框输入，不停的触发
        input.onkeyup = function(){
            //对输入的内容执行替换，替换完毕后再次赋值给value
            this.value = this.value.replace(/\D/g, '').replace(/(\d{4})(?=\d)/g, '$1 ');
        };
    </script>



     <!--
        67543
        6754 3

        8765

        9898 8989 8988 9898
     -->

</body>
</html>
```





# 第十七天，JavaScript 课堂笔记 （空）



# 第十八天，JavaScript高级 课堂笔记



## 1 基础深入总结

### 1.1 数据类型

#### ① 分类

```
原始类型/基础类型/值类型：
	String
	Number
	Boolean
	Null
	Undefined
	
对象类型/引用类型
	Object  基本对象
	Array
	Function
	.....
```

#### ② 类型判断

```
typeof	
	两种形式：typeof函数，typeof运算符
	能判断： string、boolean、number、undefined、function
	不能判断： null和除了Function的对象类型

instanceof
	判断对象类型
	
==== 全等
	两个操作数，类型和值都要相等，不会自动类型转换，区分==
	判断 null和undefined
```

```html
<body>
<!--
1. 分类(2大类)
  * 基本(值)类型
    * Number: 任意数值
    * String: 任意文本
    * Boolean: true/false
    * undefined: undefined
    * null: null
  * 对象(引用)类型
    * Object: 任意对象
    * Array: 特别的对象类型(下标/内部数据有序)
    * Function: 特别的对象类型(可执行)
2. 判断
  * typeof:
    * 可以区别: 数值, 字符串, 布尔值, undefined, function
    * 不能区别: null与对象, 一般对象与数组
  * instanceof
    * 专门用来判断对象数据的类型: Object, Array与Function
  * ===
    * 可以判断: undefined和null
-->

<script type="text/javascript">

    console.log(typeof 'hello');
    console.log(typeof(100));
    console.log(typeof(true));
    console.log(typeof(undefined));
    console.log(typeof(null));  //object
    console.log(typeof Number); //function
    console.log('');


    console.log([] instanceof Array);
    console.log({} instanceof Object);
    console.log(function(){} instanceof Function);


    console.log('hello' instanceof String);
    var s = new String('hello');

    console.log(s instanceof String);

    console.log('');

    console.log(null == undefined); //true
    console.log(null === undefined); //false

</script>
</body>
```



#### ③ 相关问题

```
1. null和undefined的区别
	undefined 代表变量没有赋值
	null 代表变量赋值，只是值为null
	
2. 什么情况下数据类型是undefined
	① 变量未赋值
	② 函数的形参没有对应的实参
	③ 函数没有返回值
	④ 使用对象中不存在的属性
	
3. 什么情况下给变量赋值为null
	① 定义变量，暂时不需要设置其他值，先设置为null
	② 定义对象的某个属性，暂时不需要值
	③ 如果一个不使用的对象，设置为null，对象会变为垃圾对象，被回收。
```

```html
<body>
<!--
1. undefined与null的区别?
  * undefined代表没有赋值
  * null代表赋值了, 只是值为null
2. 什么时候给变量赋值为null呢?
  * var a = null //a将指向一个对象, 但对象此时还没有确定
  * a = null //让a指向的对象成为垃圾对象
3. 严格区别变量类型与数据类型?
  * js的变量本身是没有类型的, 变量的类型实际上是变量内存中数据的类型
  * 变量类型:
    * 基本类型: 保存基本类型数据的变量
    * 引用类型: 保存对象地址值的变量
  * 数据对象
    * 基本类型
    * 对象类型
-->

<script type="text/javascript">
  var obj = {};

  console.log(obj.username);
  console.log(username);
</script>
</body>
```



### 1.2 数据、变量和内存

#### ① 什么是数据？

```
存储于内存中代表特定信息的'东东', 本质就是0101二进制
  * 具有可读和可传递的基本特性
  * 万物(一切)皆数据, 函数也是数据
  * 程序中所有操作的目标: 数据
    * 算术运算
    * 逻辑运算
    * 赋值
    * 调用函数传参
    ...
```



#### ② 什么是变量?

```
变量就是可变的量
变量就是一小块内存的标识，里面存的数据
一个变量对应一块小内存, 变量名用来查找到内存, 变量值就是内存中保存的内容
```

#### ③ 什么是内存？

```
内存条通电后产生的存储空间(临时的)
  * 产生和死亡: 内存条(集成电路板)==>通电==>产生一定容量的存储空间==>存储各种数据==>断电==>内存全部消失
  * 内存的空间是临时的, 而硬盘的空间是持久的
  * 一块内存包含2个数据
    * 内部存储的数据(一般数据/地址数据)
    * 内存地址值数据
  * 内存分类
    * 栈: 全局变量, 局部变量 (空间较小)
    * 堆: 对象 (空间较大)
```



#### ④ 数据、变量、内存之间的关系

```
内存是一块存储空间，里面存数据
变量是对象这块内存标识，通过变量名可以找到这块内存，从而获取数据
```

#### ⑤ 相关问题

```
1. var a = xxx, a内存中到底保存的是什么?
	xxx是基本类型/原始类型( var a = 100;//在栈里面把100这个值存下来)
	xxx是对象类型(var a = new Date();// 堆中开辟控件，存储对象；  栈存地址)
	xxx是变量(var b = a;// a变量的栈存的是什么， b就复制一份)

2. 关于引用变量赋值问题?
	2个引用变量指向同一个对象, 通过一个引用变量修改对象内部数据, 另一个引用变量也看得见
  	2个引用变量指向同一个对象,让一个引用变量指向另一个对象, 另一个引用变量还是指向原来的对象
	
3. 问题: 在js调用函数时传递变量参数时, 是值传递还是引用传递
	值传递。
	值类型直接传值，引用类型传地址（相当于值）
	
4. JS引擎如何管理内存?
	1. 内存生命周期
		创建内存
		使用内存
		释放内存
	2. 释放内存
		对象一旦不被引用，变为垃圾对象，要被释放
		
5. 垃圾回收机制（GC)
	*   1. 什么是垃圾？
    *     一个对象没有被引用，就是垃圾对象
    *   2. 垃圾回收
    *     清空垃圾对象，释放内存。
    *     JavaScript/Java/Python等: 自动垃圾回收
    *     C/C++:  手动回收
    *   3. 内存泄漏
    *     垃圾对象没有被清除，导致内存空间被占用
    *     内存空间越占越多，导致程序卡顿甚至死机
    *
    *   4. 垃圾回收的算法（机制）
    *     ① 引用计数 （IE9以及以下）
    *     ② 标记清除  （除了IE和新的IE）
    *
    *   5. 引用计数
    *    ① 对象有个引用标记
    *    ② 如果对对象进行了引用 +1
    *    ③ 取消了对象对象的引用 -1
    *    ④ 当引用标记=0的时候，变为垃圾对象，并删除
    *    优点： 及时清除垃圾对象
    *    缺点： 互相引用的对象导致内存泄漏
    *
    *
    *   6. 标记清除
    *     标记阶段：从根集合出发，将所有引用的对象以及子对象都打上标记
    *     清除： 堆里面未打上标记都清掉
    *     优点： 不会内存泄漏
    *     缺点：  深度递归变量，定时的标记定时取清除
```

#### 2关于引用变量赋值问题?

```html
<body>
<!--
关于引用变量赋值问题
  * 2个引用变量指向同一个对象, 通过一个引用变量修改对象内部数据, 另一个引用变量也看得见
  * 2个引用变量指向同一个对象,让一个引用变量指向另一个对象, 另一个引用变量还是指向原来的对象
-->
<script type="text/javascript">
    var obj1 = {age: 100, username:'小艳艳'};
    var obj2 = obj1;
    obj1.age = 200;
    console.log(obj2.age);

    console.log('');

    var obj3 = {age: 100, username:'小艳艳'};
    var obj4 = obj3; //改变了obj4变量的引用地址
    obj3 = {age: 200};
    console.log(obj4.age);

</script>
</body>
```

#### 3问题: 在js调用函数时传递变量参数时, 是值传递还是引用传递

```html
<body>
<!--
问题: 在js调用函数时传递变量参数时, 是值传递还是引用传递
  * 只有值传递, 没有引用传递, 传递的都是变量的值, 只是这个值可能是基本数据, 也可能是地址(引用)数据
  * 如果后一种看成是引用传递, 那就值传递和引用传递都可以有
-->
<script type="text/javascript">
    //值传递还是引用传递？
    //ECMA标准答案： 只有值传递
    // 原始类型，传的是值
    // 对象类型： 传的是地址

    function fn(a) {
      a = 200;
      console.log(a);
    }

    var num = 100;
    fn(num);
    console.log(num);  // 100


    console.log('');

    function fn1(a) {
      a.username = 'hello';
      //a = {}
    }

    var obj = {username:'啦啦'};
    fn1(obj);
    console.log(obj.username); //hello

</script>
</body>
```



### 1.3 对象

#### ① 什么是对象?

```
万物皆对象
现实中的事物在编程中的抽象
多个数据的集合体，用于保存多个数据
```

#### ② 为什么使用对象？

```
便于对多个数据统一管理，集中管理多个数据
```

#### ③ 对象的组成

```
对象由属性组成： 其中属性名是字符串，值可以是任意类型
如果属性的值是function类型，该数据称之为方法

属性： 现实事物的状态数据
方法： 现实事物的行为数据
```

#### ④ 访问对象内部数据（属性）

```
.属性名  结构简单，不是所有情况都可以使用
[字符串] 适合于所有情况

什么情况下，只能使用[属性名]的形式访问属性？
	① 属性名不符合标识规范（变量名的命名规范）
	② 属性名不一定，给了变量
```

```html
<body>
<!--
问题: 什么时候必须使用['属性名']的方式?
  * 属性名不是合法的标识名
  * 属性名不确定
-->
<script type="text/javascript">

  var obj = {username: '小艳艳', age: 102, 'user-pwd': '123123'};

  console.log(obj['user-pwd']);

  var prop = 'username';


  console.log(obj.prop); //undefined
  console.log(obj[prop]);

</script>
</body>
```



### 1.4 函数

#### ① 什么是函数?

```h
函数是多条代码的集合
函数可以被调用
函数也是一种对象
```

#### ② 函数的作用？

```
提高代码可复用性
提高代码可读性
```

#### ③ 如何定义函数

```
1. 字面量  function 函数名() {}
2. 表达式  var fn = function(){}
3. 构造函数 new Function
```

#### ④ 调用函数

```
fn()
fn.call({a:'小艳艳'}, '啦啦');
fn.apply({a:'小芳芳'}, ['啦啦啦啦啦']);
new fn()
```

#### ⑤ 回调函数

```
一个函数给别的函数当参数，就是回调函数

回调的函数用途：
	1. 数组的方法 filter\forEach\map...
	2. 定时器
	3. 事件监听
	4. ajax
	5. 组件生命周期
```

#### ⑥ 自调用函数 IIEF

```
(function(){

})()
声明完立即调用
作用： 减少全局变量污染
```

#### ⑦ 函数中this的指向

```
this指向调用该函数的对象
构造函数中，this指向构造函数的实例
```



## 2 函数高级

### 2.1 原型和原型链

#### ① 原型

```
每个对象都有原型
函数的prototype指向一个对象，这个对象是原型对象（构造函数的实例的原型）
原型对象有constructor属性，执行构造函数(查看构造函数)
```

#### ② 原型应用

```js
funtion User() {
    this.name = ;
    this.age =;
}
User.prototype.getInfo = function(){
    console.log(this.name,this,age)
}
//把共有的方法添加到原型上
```

#### ③ 显示原型和隐式原型

```
构造函数有个属性 prototype,指向原型对象，显示原型
实例有个属性 __proto__，指向原型对象，隐式原型

对象的隐式原型 === 构造函数的显示原型
对象.__proto__ === 构造函数.prototype
```

#### ④ 原型链

```
对象有原型，
原型也是对象，任然有原型
一直到一个没有原型的对象
```

```
使用对象中某个属性的时候：
先从对象自身查找，如果找不到去原型上查找，如果还找不到，原型的原型，一直到顶。
都找不到，undefined
```

#### ⑤ 原型、构造函数的关系

```
对象的构造函数相同，原型也相同
构造函数的prototype指向实例的原型，实例原型的constructor指向构造函数（互相引用）
```

```
Function对象的构造函数还是Function
所以： Function.__proto__ === Function.prototype
```

#### ⑥ instanceof 判断原理

```
A instanceof B
只要B的显示原型出现在了 A的原型链上，就成立； 反之不成立。
```



### 2.2 执行上下文和执行上下文栈

#### ① 变量提升和函数提升

```
变量提升，代码正式执行之前，对变量进行提升（只提升变量的声明，不提升值）
函数提升（字面量声明）， 整个函数都提升。

函数提升优先级比变量高
```

#### ② 执行上下文

```
全局执行上下文
	① 执行代码之前，确定全局上下文对象，是window
	② 预处理
	  变量提升
	  函数提升
	  this赋值
	③ 正式执行全局上下文的代码

函数执行上下文：
	① 当函数被调用的时候，创建函数的执行上下文，确定执行上下文对象
	② 预处理
	   形参赋值
	   arguments赋值
	   局部变量提升
	   被嵌套的函数提升
	   this赋值（调用函数的对象）
	③ 正式执行上下文的代码
```

#### ③ 执行上下文栈

```
全局执行上下文进栈
	调用哪个函数，该函数的执行上下文也进栈
	调函执行结束，出栈。
	先行后出，后进先出；
全局执行上下文出栈
```



# 第十九天，JavaScript高级 课堂笔记(连续昨天一起)

### 2.3 作用域和作用域链

#### ① 作用域

```
作用域就是变量的作用范围

分类：
	全局作用域
	函数作用域（局部作用域）
	
特点：
	在函数声明的时候就决定了，跟函数在哪里调用没有关系
	
	
1. 理解
  * 就是一块"地盘", 一个代码段所在的区域
  * 它是静态的(相对于上下文对象), 在编写代码时就确定了
2. 分类
  * 全局作用域
  * 函数作用域
  * 没有块作用域(ES6有了)
3. 作用
  * 隔离变量，不同作用域下同名变量不会有冲突

```



#### ② 作用域和执行上下文的关系

```
区别1
  * 全局作用域之外，每个函数都会创建自己的作用域，作用域在函数定义时就已经确定了。而不是在函数调用时
  * 全局执行上下文环境是在全局作用域确定之后, js代码马上执行之前创建
  * 函数执行上下文环境是在调用函数时, 函数体代码执行之前创建

区别2：
	作用域是静态的，函数声明的时候决定作用域
	执行上下文是动态的，函数调用的时候创建执行上下文；函数每调用一次，创建一次执行上下文。

联系：
	执行上下文（对象）是从属于作用域的
	全局执行上下文 --> 全局作用域
	函数执行上下文 --> 函数作用域（局部作用域）
	
```



#### ③ 作用域链

```
函数内嵌套函数，产生作用域链

在函数内使用某个变量，先从本函数作用域中查找；如果查找不到取上层函数作用域查找；直到全局作用域

1. 理解
  * 多个上下级关系的作用域形成的链, 它的方向是从下向上的(从内到外)
  * 查找变量时就是沿着作用域链来查找的
2. 查找一个变量的查找规则
  * 在当前作用域下的执行上下文中查找对应的属性, 如果有直接返回, 否则进入2
  * 在上一级作用域的执行上下文中查找对应的属性, 如果有直接返回, 否则进入3
  * 再次执行2的相同操作, 直到全局作用域, 如果还找不到就抛出找不到的异常
```

```html

<script type="text/javascript">
  var a = 2;
  function fn1() {
    var b = 3;
    function fn2() {
      var c = 4;
      console.log(c);
      console.log(b);
      console.log(a);
      console.log(d);//没有找到报错
    }

    fn2();
  }
  fn1();
</script>

```



### 2.4 闭包

#### ① 什么是闭包

```
函数内嵌套函数，被嵌套的函数使用了上层函数作用域的变量，就是闭包。

闭包的条件：
	函数嵌套
	被嵌套的函数使用了上层函数作用域的变量
```

#### ② 有意义的闭包常见的应用形式

```
1. 把被嵌套的函数返回
2. 把被嵌套的函数作为回调函数（事件的回调函数、定时器）
```

```html
<body>
<!--
1. 将函数作为另一个函数的返回值
2. 将函数作为实参传递给另一个函数调用
-->
<script type="text/javascript">


   //被嵌套的函数返回
    function fn(){
      var a = 100;
      /*function fn1(){
          a = 200;
          console.log(a);
      }
      return fn1;*/

      return function(){
        console.log(a);
      }
    }

   /* var f = fn();
    f();*/

    fn()();
    //console.log(typeof f);


    //被嵌套的函数作为回调函数
    function Demo() {
      var msg = 'hello';
      function a(){
        console.log(msg);
      }
      setTimeout(a, 1000);
    }

    Demo();
</script>
</body>
```



#### ③ 闭包的作用（影响）

```
1. 函数内部的变量长时间存储在内存中（被内部的函数引用了），延长了局部变量的生命周期
2. 在函数的外部操作（读写）函数内部的数据（变量\函数）
```

```html
<body>
<!--
1. 使用函数内部的变量在函数执行完后, 仍然存活在内存中(延长了局部变量的生命周期)
2. 让函数外部可以操作(读写)到函数内部的数据(变量/函数)

问题:
  1. 函数执行完后, 函数内部声明的局部变量是否还存在?
  2. 在函数外部能直接访问函数内部的局部变量吗?
-->
<script type="text/javascript">
  function fn(){
    var a = 100;
    return function(n){
      a = n;
      console.log(a);
    }
  }

  var f = fn();

  //我在fn函数的外部
  f(200);
</script>
</body>
```



#### ④ 闭包声明周期

```
创建： 被嵌套的函数声明完就创建闭包。
销毁： 被嵌套的函数成为垃圾对象。
```

#### ⑤ 闭包：定义js模块

```
JS模块：具有特定功能的文件
把模块内所有的数据和功能封装在一个函数内（私有的）
模块向外暴露一个对象，对象中想要对外的方法和属性

暴露方式： ①直接return  ②作为window的属性
```

#### ⑥ 闭包的缺点

```
函数闭包之后，里面的变量会长时间存在于内存中，可能会造成内存泄漏

解决方案：
	闭包能不用就不用
	减少对闭包引用次数
	及时释放，把引用闭包的对象变为null（垃圾）
```





## 3 对象高级

### 3.1 创建对象

#### ① Object构造函数

```js
new Object()
```

```
适用场景： 开始不确定对象的内部数据
缺点： 添加属性方法的时候，代码比较多
```

```html
<body>
<!--
方式一: Object构造函数模式
  * 套路: 先创建空Object对象, 再动态添加属性/方法
  * 适用场景: 起始时不确定对象内部数据
  * 问题: 语句太多
-->
<script type="text/javascript">
  /*
  一个人: name:"Tom", age: 12
   */

    var person = new Object();
    person.name = 'Tom';
    person.age = 12;
    person.setName = function(name) {
      this.name = name;
    };

</script>
</body>
```



#### ② 字面量/直接量方式

```
var Name = {属性:值}
```

```
适用场景： 一开始明确对象内部的数据
缺点： 如果创建多个对象，代码量大
```

```html
<body>
<!--
方式二: 对象字面量模式
  * 套路: 使用{}创建对象, 同时指定属性/方法
  * 适用场景: 起始时对象内部数据是确定的
  * 问题: 如果创建多个对象, 有重复代码
-->
<script type="text/javascript">

    var person = {
      name:'Tom',
      age: 12,
      setName: function(name) {
        this.name = name;
      }
    };

    var person1 = {
      name:'Jack',
      age: 19,
      setName: function(name) {
        this.name = name;
      }
    };
</script>
</body>
```



#### ③ 工厂模式

```js
function factory() {
    return {
        
    }
}
var obj = factory();
```

```
适用场景： 需要创建的对象比较多
缺点： 对象的类型都是Object类型的，无法拥有自己的类型
```

```html
<body>
<!--
方式三: 工厂模式
  * 套路: 通过工厂函数动态创建对象并返回
  * 适用场景: 需要创建多个对象
  * 问题: 对象没有一个具体的类型, 都是Object类型
-->
<script type="text/javascript">
    //定义工厂函数 用于生产对象
    function createPerson(name, age) {
        return {
          name: name,
          age: age,
          setName: function(name) {
            this.name = name;
          }
        }
    }


    // 通过工厂函数 得到对象
    var p1 = createPerson('小艳艳', 18);
    var p2 = createPerson('大艳艳', 49);

    console.log(p1);
    console.log(p2);

    p1.setName('梦娜丽莎');

    console.log(p2);
    console.log(p1);


    console.log(p1 instanceof Object);
</script>
</body>
```



#### ④ 自定义构造函数

```js
function Person(){
    this.属性 = 值
}
```

```html
<body>
<!--
方式四: 自定义构造函数模式
  * 套路: 自定义构造函数, 通过new创建对象
  * 适用场景: 需要创建多个类型确定的对象
  * 问题: 每个对象都有相同的数据, 浪费内存
-->
<script type="text/javascript">

   //定义人类
    function Person(name, age){
        this.name = name;
        this.age = age;
    }

    var p1 = new Person('Tom', 10);

    console.log(p1);
    console.log(p1 instanceof Person);

</script>
</body>
```



#### ⑤ 自定义构造函数与原型相结合

```js
function Person(){
    this.属性 = 值
}
Person.prototype,getName = function(){}
```

```
属性定义在构造函数内部，方法定义在构造函数的显示原型（实例的原型）
```

```html
<body>
<!--
方式五: 构造函数+原型的组合模式
  * 套路: 自定义构造函数, 属性在函数中初始化, 方法添加到原型上
  * 适用场景: 需要创建多个类型确定的对象
-->
<script type="text/javascript">
  //定义人类
  function Person(name, age){
    this.name = name;
    this.age = age;
  }

  Person.prototype.getName = function(name){
    this.name = name;
  };

  var p1 = new Person('Tom', 10);
  var p2 = new Person('Tom', 10);

  console.log(p1);
  console.log(p2);

</script>
</body>
```



### 3.2 对象继承

#### ① 利用原型链继承

```js
function Super() {}


function Sub() {
    
}
Sub.prototype = new Super();
Sub.prototype.constructor = Sub;
```

```
让子类的显示原型=父类的实例
设置子类的显示原型的constructor指向子类

缺点：
	无法在子类实例化的时候给父类的属性赋值
```

```html
<body>
<!--
方式1: 原型链继承
  1. 套路
    1. 定义父类型构造函数
    2. 给父类型的原型添加方法
    3. 定义子类型的构造函数
    4. 创建父类型的对象赋值给子类型的原型
    5. 将子类型原型的构造属性设置为子类型
    6. 给子类型原型添加方法
    7. 创建子类型的对象: 可以调用父类型的方法
  2. 关键
    1. 子类型的原型为父类型的一个实例对象
-->

<!--
  class Person {
    private name;
    private age;

    function eat() {
    }
  }

  class Boy extends Person {
    private aaa;
  }

  class Girl extends Person {
    private bbb;
  }

-->

<script type="text/javascript">
    // 定义父类
    function Person(name, age) {
        this.name = name;
        this.age = age;
    }
    Person.prototype.say = function(){
      console.log('hello，My Name is'+this.name);
    };


    // 定义子类
    function Man(aaa, name, age) {
        this.aaa = aaa; //男人特有的属性
      /*this.name = name;
      this.age = age;*/
    }
    // 修改Man的显示原型（实例的原型）  函数的显示原型和函数互相引用
    Man.prototype = new Person();
    Man.prototype.constructor = Man;

    //创建一个男人
    var m = new Man('我是男人', '科比', 17);
    console.log(m);
    console.log(m.constructor);
    console.log(m instanceof Man);
    console.log('');


    // 定义子类 女人类
    function Woman(bbb) {
        this.bbb = bbb;

    }
    Woman.prototype = new Person();
    Woman.prototype.constructor = Woman;

    //实例化woman
    var w = new Woman('bbb');

    console.log(w);
    console.log(w.constructor);


    console.log('');
    console.log(m.constructor);
    console.log(w.constructor);

</script>
</body>
```



#### ② 在子类中调用父类

```js
function Super() {

}

function Sub() {
    Supper.call(this, ...)
}
```

```
在子类中调用父类函数，改变this指向子类实例
父类定义的方法会添加到子类实例中

缺点：
	无法继承到父类现实原型上的方法
```

```html
<body>
<!--
方式2: 借用构造函数继承(假的)
1. 套路:
  1. 定义父类型构造函数
  2. 定义子类型构造函数
  3. 在子类型构造函数中调用父类型构造
2. 关键:
  1. 在子类型构造函数中通用super()调用父类型构造函数
-->
<script type="text/javascript">
  // 定义父类
  function Person(name, age) {
    this.name = name;
    this.age = age;

    this.say = function(){
      console.log('hello，My Name is'+this.name);
    };
  }
  Person.prototype.eat = function(){
    console.log('我是'+this.name+',我能吃');
  };

  // 定义子类
  function Man(aaa, name, age) {
     //调用父类 把this指向Man的实例
     //继承父类的属性
     Person.call(this, name, age);
      //添加自己的属性
      this.aaa = aaa;

  }

  //实例化
  var m = new Man('我是男人', 'Tom', 10);

  console.log(m);
  console.log(m.name, m.age, m.aaa);
  m.say();
  m.eat();
</script>
</body>
```



#### ③ 组合方式

```js
function Super(){

}

function Sub() {
	Super.call(this)
}
Sub.prototype = new Super();
Sub.prototype.constructor = Sub;
```

```
通过子类中调用父类函数，实现父类中属性和方法的继承
通过改变原型继承父类现实原型上的数据

```

```html
<body>
<!--
方式3: 原型链+借用构造函数的组合继承
1. 利用原型链实现对父类型对象的方法继承
2. 利用super()借用父类型构建函数初始化相同属性
-->
<script type="text/javascript">
  // 定义父类
  function Person(name, age) {
    this.name = name;
    this.age = age;

    this.say = function(){
      console.log('hello，My Name is'+this.name);
    };
  }
  Person.prototype.eat = function(){
    console.log('我是'+this.name+',我能吃');
  };

  //定义子类
  function Man(aaa, name, age) {
      //继承父类实例上的属性和方法
      Person.call(this, name, age);
      //自己特有属性
      this.aaa = aaa;
  }
  // 获取父类显示原型上的方法，改变子类的显示原型
  Man.prototype = new Person();
  Man.prototype.constructor = Man;


  //实例化男人
  var m = new Man('我是', '曹操', 29);

  console.log(m.aaa, m.name, m.age);
  m.say();
  m.eat();

</script>
</body>
```





# 第二十天，JavaScript高级 课堂笔记



## 4 进程机制和事件机制

### 4.1 进程和线程

```
进程：
	程序的一次执行, 它占有一片独有的内存空间
	CPU的调度单位，执行程序开启进程来执行，是程序执行的一个完整流程。

线程：
	一个进程包含多个线程
	如果进程可以只包含一个线程，主线程
	进程和进程之间的数据无法共享
	在同一个进程内的多个线程可以共享数据
```

### 4.2 JavaScript是单线程执行

```
1. 如何证明JavaScript是单线程执行？
   设置了定时器，定时器的回调函数会等到主线程空闲且时间到执行；
   如果主线程没有空闲下来，即使定时器的时间到了，回调函数也不会执行（等到主线程空闲）。
   
2. 为什么JavaScript选择单线程？
   多线程会有线程调度以及线程开启关闭的开销
   JavaScript主要在浏览器端操作DOM完成特效，如果不是单线程，不好解决页面渲染的同步问题。
```



### 4.3 事件轮询（循环）机制

#### ① 相关概念

```
执行栈： 要执行的代码进入执行栈（从上到下执行的叫执行栈）
回调队列： 事件队列、任务队列、消息队列
管理模块： DOM事件管理、定时器管理、ajax请求管理
事件轮询： 内部不停询问元素有没有被触发事件
```



### 4.4 JS多线程

```
利用Worker可以实现多线程运算符
通过实例化一个Worker，创建一个子线程
子线程里面不允许操作DOM，也没有window
```

```
worker适合场景：
	把耗时的计算放在分线程，不会影响主线程的其他工作
	如果耗时的计算在主线程，导致页面卡顿（甚至崩溃）
	
worker的缺点：
	① 无法操作DOM
	② 无法跨域
	③ 兼容性（不是所有的浏览器都可以使用）
```

```
Worker 构造函数
Worker.prototype.postMessage(对象/变量)  向分线程发送数据
Worker.prototype.onmessage(event)     监听分线程的消息
```





# 第二十天，ECMAScript 6+课堂笔记

## 1 ECMAScript

### 1.1 ECMAScript 和 JavaScript

```
浏览器端JavaScript: ECMAScript、BOM、DOM
node端的JavaScript： ECMAScript、nodeAPI

ECMA： 欧洲计算机标准协会
ECMAScript： 一套语法标准

ECMAScript是JavaScript的规格
JavaScript是ECMAScript的实现

ECMAScript的实现： JavaScript、JScript、ActionScript(flash)
```

### 1.2 ECMAScript的重要版本

```
ECMAScript3.0  简称ES3   
ES5.0 / ES5.1  新增一些扩展
ES6	2015年6月 又叫ES2015 (以后每年6月份出一个新的版本)
ES7	ES2016
ES8 ES2017
ES9 ES2018
ES10 ES2019
```

### 1.3 学习参考网站

```
http://es6.ruanyifeng.com/
```



## 2 关键字扩展

### 2.1 let 关键字

```
用于声明变量，类似于var
```

```
特点：
	① 不能重复声明
	② let声明的变量不会提升
	③ let声明的变量可以具有块级作用域
	④ let声明的全局变量不再是顶层对象的属性
```

### 2.2 const 关键字

```
用户声明常量 
常量不可改变的量
用途： 程序的配置信息习惯用常量定义
```

```
特点：
	① 值不能修改；更不能重复声明；
	② 不会提升
	③ 具有全局、局部、块级作用域
	④ 全局的常量不是window的属性
```



## 3 对象的简写

```js
var name = 'Tome';
var age = 199;
var Name = {
    name,  //属性简写  属性值通过变量给出，而属性名与变量名同名
    age,
    say() {   //方法简写 
        
    },
    eat() {
        
    }
}
```

```html
<script>

        //工厂函数
        function PersonFactory(name, age) {

            var obj = {
                name,
                age,
                sex: 'male',
                say(){
                    console.log('My Name is '+this.name);
                }
            };

            return obj;

        }

        var p1 = PersonFactory('艳艳', 18);
        var p2 = PersonFactory('曹操', 14);

        console.log(p1);
        console.log(p2);

        p1.say();
        p2.say();
    </script>
```



## 4 变量的解构赋值

### 4.1 数组解构赋值

```js
// 1. 解构声明
let [a, b, c] = [value1, value2, value3];

// 2. 修改变量的值
[a, b, c] = [value1, value2, value3];

// 3 复杂数组 （保证两边的数组形式一致）
let [a, [b], [c, [d,e]]] = [100, [200], [300, [400, 500]]];

// 4. 声明变量的时候可以有默认值 （与函数传参类似）
// 如果右边数组成员少，有的变量会赋值undefined
// 有默认值的变量，写在后面
let [a, b=默认值] = [100]
```

```html
<script>
        //数组形式的解构赋值
        //声明变量
        let [username, age, sex] = ['张飞', 34, 'male'];
        console.log(username, age, sex);

        //修改变量的值
        [age, sex] = [57, 'female'];
        console.log(username, age, sex);

        // 复杂的数组
        let [[a], [[b],c], [[d,e,f]], h] = [[10], [[20], 30], [[40,50,60]], age];
        console.log(a, b, c, d, e, f, h);

        // 变量可以有默认值 (类似于函数传参)
        //let [width, height=100] = [400, 300];
        let [width, height=100] = [400];
        //let [width=200, height] = [400];

        console.log(width, height);


        //使用解构赋值交换两个的变量的值
        let m = 100;
        let n = 200;
        console.log(m, n);

        [m,n] = [n,m];
        console.log(m, n);

    </script>
```



### 4.2 对象解构赋值

```js
// 简写形式
{name, age} = {name: 100, age: 200}

//完整写法  冒号后面的才是变量名
{name:name, age:age} = {name: 100, age: 200}
{name:n, age:a} = {name: 100, age: 200}

//复杂形式的
 let {name1, name2:{name3, name4}} = {name1: 100, name2: {name3:200, name4:300}};
//产生 name1、name3、name4变量   

// 默认值
let {weight=400, color='red'} = {weight:600, color: '#f90'};
let {weight:weight=400, color:color='red'} = {weight:600, color: '#f90'};
```

```html
<script>
        //对象形式的结构赋值

        let {name, age} = {name:'张飞', age:45};
        console.log(name, age);

        ({age, name} = {age: 100, name:'赵云'});
        console.log(name, age);


        //完整写法
        //let {width:width, height:height} = {width: 400, height: 300};
        let {width:w, height:h} = {width: 400, height: 300};
        //console.log(width, height);
        console.log(w, h);

        //复杂
        let {name1, name2:{name3, name4}} = {name1: 100, name2: {name3:200, name4:300}};
        // {name1: name1, name2: {name3:name3, name4: name4}}

        console.log(name1, name3, name4);


        // 对象解构赋值 默认值
        //let {weight=400, color='red'} = {weight:600, color: '#f90'};
        //let {weight:weight=400, color:color='red'} = {weight:600, color: '#f90'};
        let {weight:weight=400, color} = {color: '#f90'};
        console.log(weight, color)
        
    </script>
```



### 4.3 特殊形式的对象/数组解构

#### ① 数组

```
只要是可以遍历的对象（数组和类数组对象、字符串）都可以被数组解构
```

#### ② 对象

```
任意一个数据都可以被对象解构，一切皆对象(对象有这个属性才可以解构出来)
```

```html
<body>
    <button>按钮1</button>
    <button>按钮1</button>
    <button>按钮1</button>
    <button>按钮1</button>
    <script>


        //本质上仍然是数组的解构赋值
        // 数组解构赋值， 右边是个可以遍历的数据结构就可以
        let [a,b,c,d] = 'hello';
        console.log(a,b,c,d); //hell


        var btns = document.querySelectorAll('button');
        let [e,h,i,g] = btns;
        console.log(e,h,i,g); //4个button

        console.log('');

        // 对象形式
        //let {length} = 'hello';
        // let {length:len} = 'hello';
        let {length:name} = 'hello';  //5

        console.log(name);


        let {length, forEach} = btns;
        console.log(length, forEach); //4个数量，ƒ forEach() { [native code] }方法

        let {apply, call} = function(){}

    </script>
</body>
```

#### 【重点】下列代码，得到的变量是什么？值是什么

```js
let {length:len} = 'hello';// 变量是 len   值 5

let {name: n} = {name: 'hello'}; //变量n 值是hello

let {length:l, username:u} = [10,20,30];  //变量l=3， u=undefined

```



### 4.4 函数传参解构赋值

```
函数接受参数 对象、数组 解构赋值 同给变量赋值类似
```

```html
<script>
        function fn([m,n]) {
            console.log(m,n);
        }

        fn([100, 200]);

        function demo({name, age}) {
            console.log(name, age);
        }
        demo({name: 100, age: 200});


        // 声明函数的默认值 特效插件

        //封装一个轮播图的插件
        function swiper({id, autoPlay=false, duration=3000, click=false}) {
            console.log(id, autoPlay, duration, click);
        }

        //使用插件
        // 插件的配置选项，大部分配置项有默认值
        swiper({
            id: '#myPlay',
            autoPlay: true,
            duration: 5000,
        });


        // 函数返回多个参数
        function getInfo() {

            return {
                name: '曹操',
                age: 100
            }
        }

        let {name, age} = getInfo();
        console.log(name, age);

    </script>
```



### 4.5 解构赋值应用

```
1. 交换两个变量的值
2. 函数参数的默认值
3. 函数返回多个值
4. 获取模块的方法
```

### 4.6解构赋值获取模块的方法



## 5 字符串扩展

### 5.1 模板字符串

```
两个反引号 `

特点：
	${变量} 直接解析
	${表达式} 得到表达式的结果

使用场景：
	多行字符串，直接在里面回车
	拼接多个变量
	
```

```html
<script>
        let [title, name] = ['悯农', '李白'];
        //定义字符串
        let message = `
            ${title} · ${name}
            初日日当午
            汗滴禾下土
            谁知盘中餐
            粒粒皆辛苦\n好诗
            ${100 + 100}
        `;

        console.log(message);

    </script>
```



### 5.2 字符串对象新增的方法

#### ① ES3

```
indexOf()
lastIndexOf()
substring()
substr()
slice()
split()
fromCharCode()
toUpperCase()
toLowerCase()
replace()
match()
search()
```

#### ② ES5

```
trim()  	取出两边的空格
```

#### ③ ES6+

```
startsWith() 返回布尔值 	 判断是否以某个字符串开头
endsWith()  返回布尔值	 判断是否以某个字符串结尾
includes()  返回布尔值	 判断是否包含某个字符串
repeat()	重复字符串
padStart()  ES8   补全 在前面补空格（指定的字符）
padEnd()  ES8     补全 在后面补空格（指定的字符）
matchAll()  ES10  得到所有的匹配，返回迭代器 	
trimStart()  ES10	去掉前面的空格
trimEnd()    ES10   去掉后面的空格
```

```html
 <script>
        let message = '      hello world ';

        console.log('#' + message + '#');
        console.log('#' + message.trim() + '#');
        console.log('#' + message.trimStart() + '#');
        console.log('#' + message.trimEnd() + '#');
        console.log('');

        message = message.trim();


        console.log(message.startsWith('hello'));
        console.log(message.endsWith('hello'));
        console.log(message.endsWith('ld'));
        console.log('');

        console.log(message.includes('ld'));
        console.log(message.includes('你好'));
        console.log('');


        console.log(message.repeat(10));
        console.log('');


        console.log(message.padStart(100, '#'));
        console.log(message.padEnd(100, '#'));

        console.log('');

        console.log(message.matchAll(/\w/));  //返回迭代器（是所有匹配到的结果）
    </script>
```



## 第二十天(补)，ECMAScript 6+课堂笔记



## 6 数值的扩展

### 6.1 指数运算符 (**)  ES7

```js
2 ** 4;  // 计算2的4次方
2 ** 2 ** 3； //运算顺序，先算右边的
```

### 6.2 二进制和八进制的表示

```js
//二进制
0b101010

// 八进制
0o17
/*
比以前的八进制表示方式语法更合理
在严格模式可用（0开头表示八进制，严格模式不可用）
*/
```

### 6.3 Math对象新增的方法

```
Math.trunc()  去掉小数部分
Math.sign()   判断一个数字是正数、负数、还是0
Math.cbrt()   求立方根
Math.hypot()  求所有参数的平方和的平方根（用于勾股定理计算斜边长度）
```

```html
<script>
        //去除小数部分
        console.log(Math.trunc(12.65), Math.floor(12.65));
        console.log(Math.trunc(-12.65), Math.floor(-12.65));
        console.log('');

        //判断一个数字是正数还是负数还是0
        console.log(Math.sign(45));
        console.log(Math.sign(-45));
        console.log(Math.sign(0));
        console.log(Math.sign(NaN));
        console.log('');

        // 求立方根
        //Math.sbrt(); //计算平方根
        console.log(Math.cbrt(8));
        console.log('');


        // 求所有参数平方和的平方根
        console.log(Math.hypot(1,2,3,4,5,6));
        //勾股定理  已知两个直角边的长度，求斜边
        console.log(Math.hypot(3, 4));

    </script>
```



## 7 函数扩展

### 7.1 参数默认值

```js
//ES6的写法
function fn(a,b=默认值) {
    
}

//ES6之前的写法
function fn(a,b) {
    if (b === undefined) {
        b = 默认值
    }
}
```

### 7.2 rest参数

```js
function sum(...numbers) {
    numbers; //得到一个数组，里面是所有的实参； numbers的名字只要符合标识名命名规范即可
}

/*
 与arguments类似，
 rest参数得到是数组， arguments得到是伪数组
*/
```

```html
<script>

        //计算所有参数的和
        function sum(...numbers) {
            //console.log(arguments);
            //console.log(numbers instanceof Array);

            return numbers.reduce(function(res, item){
                return res + item;
            });
        }

        console.log(sum(10,20,30,40,50,60));
    </script>
```



### 7.3 箭头函数

#### ① 语法

```js
//完整写法
(参数1， 参数2) => { 
    语句1; 
    语句2; 
}

// 如果参数只有一个 省略()
参数 => {
    语句1; 
    语句2; 
}

// 如果只有一条 返回语句
参数 => 语句;
//相当于
(参数) => {
    return 语句;
}
```

```html
<script>
        //以前定义函数的方式 （表达式方式）
        var fn01 = function(){};
        fn01();

        //箭头函数形式
        var fn02 = ()=>{};
        fn02();

        // 定义箭头函数
        var fn03 = (a, b) => {
            console.log(a);
            console.log(b);
        };
        fn03(100, 200);


        // 箭头函数简写， 如果参数只有一个，可以省略()
        var fn04 = name => {
            console.log(name);
        };
        fn04('小艳艳');

        // 如果函数体只有一条返回语句，省略{}
        /*var fn05 = (num1, num2) => {
            return num1 + num2;
        }*/
        var fn05 = (num1, num2) => num1 + num2;
        console.log(fn05(10,20));

        //只有一个参数，且只有一条返回语句
        var fn06 = num => num * num;
        console.log(fn06(6));


        console.log('');

        //适合箭头函数的场景 当回调函数
        var students = [
            {name: '曹操', age: 18},
            {name: '曹丕', age: 28},
            {name: '曹植', age: 38},
            {name: '曹睿', age: 48},
            {name: '曹真', age: 58}
        ];
        console.log(students);

        // 取出大于30岁的
        var students01 = students.filter(item => item.age > 30);
       /* students01.filter(function(itme) {
            return item.age > 30;
        });*/
        console.log(students01);

        // 过年了，每个人+1岁
        var students02 = students.map(item => {
            item.age + 1;
            return item;
        });

        console.log(students02);

    </script>
```



#### ② 特点

```
1. this指向。 与谁调用了箭头函数无关； 与声明箭头函数位置有关；
   看声明箭头函数的地方，是不是嵌套在函数内，如果嵌套在了函数内，看外层函数的this指向；如果没有被函数嵌套，指向window
   
2. 箭头函数内无法获取aruguments，可以使用rest参数

3. 箭头函数不能作为构造函数

4. 箭头函数不能作为生成器
```

#### ③ 适用场景

```
使用场景：
	作为回调函数
	
不适合的场景：
	给对象添加方法；（this指向）
	构造函数
	生成器函数
```

### 7.4 函数对象新增属性

```
name  返回函数名（声明函数时给的名字）
```

```html
<script>
        var name = 'The Window';

        //this的指向
        // 老的方式定义的函数，this指向调用函数的对象
        // 箭头函数，this指向定义函数时，this的指向 （函数的上层还是不是函数）
        var obj = {
            name: '曹操',
            age: 19,
            say: () => {
                console.log('My Name is '+this.name);
            }
        };
        obj.say();

        var obj02 = {
            name: 'Object',
            getFunc() {
                return ()=>this.name;
            }
        };

        var f = obj02.getFunc();

        console.log(f());  //Object

        /*
        * var obj02 = {
            name: 'Object',
            getFunc() {
                return ()=>{
                    return this.name
                }
            }
           };
        * */

        console.log('');
        //无法获取 arguments，可以用rest参数
        var sum = (...values) => values.reduce((res, item) => res + item);

        console.log(sum(10,20,30,40,50));

        console.log('');

        var instance01 = new function(){

        };
        console.log(instance01);
        //箭头函数不能作为构造函数
        //var instance02 = new ()=>{};


        function demo(){

        }
        var demo1 = function(){}
        console.log(f.name);//箭头的匿名函数无法获取
        console.log(demo.name);//返回函数名
        console.log(demo1.name);//返回函数名

    </script>
```



## 8 数组扩展

### 8.1 扩展运算符

#### ① 定义

```
rest参数的逆运算
把数组转为用逗号分隔的参数序列
```

#### ② 应用

```js
//1. call 数组传参
fn.call({}, ...nums);
fn.apply({}, nums);
console.log('');

//2. 计算数组中最大的元素
console.log(Math.max(...nums));
console.log('');


//3. 把一个数组的成员 追加到另一个数组的尾部
var names = ['曹操', '张仁', '刘备'];
nums.push(...names);  // nums,push('曹操', '张仁', '刘备')
console.log(nums);
console.log('');


// 4. 克隆数组
//let nums1 = nums;  //引用类型
let nums1 = [...nums];  //nums1=nums的克隆版
nums1[2]= '啦啦啦啦hello';
console.log(nums1);
console.log(nums);
console.log('');

//5. 合并数组
var newArr = [...nums, ...nums1, ...names];
console.log(newArr);
console.log('');


// 6. 把字符串和类数组对象转为数组
// 字符串转换为数组
// 类数组对象转为数组
var newArr1 = [...'hello'];
console.log(newArr1);
var btns = document.querySelectorAll('button');
console.log(btns);
console.log([...btns]);
console.log('');

```

#### ③ 解构赋值版的rest参数

```js
//与结构赋值一起使用 （结构赋值版的rest参数）
let [a, ...b] = [10,20,30,40,50,50,60];
console.log(a, b);  // a是10， b是数组
```

```html
<script>
        function fn(a, b, c) {
            console.log(a, b, c, a+b+c);
        }

        fn(10,20,30);

        var nums = [100,200,300,250];
        fn(nums);
        fn(...nums);  // 100,200,300

        console.log(nums);
        console.log(...nums); // console.log(100,200,300)


        console.log('');

        //call 数组传参
        fn.call({}, ...nums);
        fn.apply({}, nums);
        console.log('');

        //计算数组中最大的元素
        console.log(Math.max(...nums));
        console.log('');


        // 把一个数组的成员 追加到另一个数组的尾部
        var names = ['曹操', '张仁', '刘备'];
        nums.push(...names);  // nums,push('曹操', '张仁', '刘备')
        console.log(nums);
        console.log('');


        // 克隆数组
        //let nums1 = nums;  //引用类型
        let nums1 = [...nums];  //nums1=nums的克隆版
        nums1[2]= '啦啦啦啦hello';
        console.log(nums1);
        console.log(nums);
        console.log('');

        //合并数组
        var newArr = [...nums, ...nums1, ...names];
        console.log(newArr);
        console.log('');


        // 字符串转换为数组
        // 类数组对象转为数组
        var newArr1 = [...'hello'];
        console.log(newArr1);
        var btns = document.querySelectorAll('button');
        console.log(btns);
        console.log([...btns]);
        console.log('');


        //与结构赋值一起使用
        let [a, ...b] = [10,20,30,40,50,50,60];
        console.log(a, b);

    </script>
```





# 第二十一天，ECMAScript 6+课堂笔记(连续昨天一起)

### 8.2 Array函数新增方法

```
Array.from()   把类数组/字符串转为纯数组
Array.of()     创建数组，参数是数组的成员（任意个数的参数）
```

```html
<body>
    <button>按钮</button> * 6
    <script>
        var btnNodoList = document.querySelectorAll('button');
        var btnCollection = document.getElementsByTagName('button');

        console.log(btnNodoList);
        console.log(Array.from(btnNodoList));

        console.log(btnCollection);
        console.log(Array.from(btnCollection));

        console.log(Array.from('hello world'));//也能遍历为数组

        console.log('');


        //Array.of()  创建一个数组，数组的成员就是of的参数
        console.log(Array.of(10,20,30,40,'hello'));
        console.log(Array.of(100));

        // 构造函数方式创建数组
        console.log(new Array(10,20,30));
        console.log(new Array(10));
        console.log(new Array('hello'));

    </script>
```



### 8.3 Array实例新增的方法

```
find()   参数是回调函数，返回第一个满足条件的元素
findIndex()	参数是回调函数，返回第一个满足条件的元素的索引
fill()		填充数组，覆盖数组中所有的元素；适合填充 new Array（20）创建的数组
includes()   判断数组中是否包含某个元素，返回布尔值； ES7新增的
flat() 把数组拉平（多维数组变为一维数组），参数默认是1（只拉1层）， 可设置Infinity，不论维位数组 ES10新增
flatMap()	参数是回调函数，相当于map和flat的结合 ES10新增
```

```html
<script>
        var arr = [100,200,300,400,500];

        // 查找第一个满足条件的元素
        /*console.log(arr.find((item,index) => {
           return item === 200;
        }));*/
        //查找第一个>200的元素
        console.log(arr.find(item=>item>200));

        //查找第一个满足条件的索引
        console.log(arr.findIndex(item=>item>200));

        //查找某个元素第一次出现的位置
        console.log(arr.indexOf(300));
        console.log('');


        // 把稀疏数组填满
        var arr2 = new Array(20);
        console.log(arr2);
        console.log(arr2.fill(100));

        var arr3 = [10,20,30];
        //arr3[19] = 100;
        console.log(arr3);
        console.log(arr3.fill('hello'));
        console.log('');


        //判断数组是否包含某个元素
        console.log(arr.includes(200));
        console.log(arr.includes(10000));
        console.log('');


        //用于拉平数组，把多维数组变为一维数组
        var arr3 = [['a','b','c'], ['A', 'B', 'C', 'D'], 100];
        console.log(arr3);
        console.log(arr3.flat());

        var arr4 = [['a','b','c'], ['A', 'B', 'C', 'D'], [[100,200,300,400], [10,20]]];
        console.log(arr4.flat());
        console.log(arr4.flat(2));
        console.log(arr4.flat(Infinity));   //统统拉平

        console.log('');

        var res = arr3.flatMap((item,index) => {
            console.log(item,index);
            if (item instanceof Array) {
                item.push('我是追加的');
            }
            return item;
        });

        console.log(res);

    </script>
```



## 9 对象的扩展

### 9.1 属性名表达式

```js
{
    [表达式]：值,
     属性名: 值
}
```

```html
<script>
        var username = '张飞';

        //ES新语法
        var obj = {
            name: '曹操',
            [username]: '关云长',  //表达式属性可以是变量
            [10*45]: '刘备',  //表达式属性
            ['age']:100  //字符串属性
        };

        //obj[username] = '';
        obj[200+10] = 10000;

        console.log(obj);

    </script>
```



### 9.2 super 关键字

```
1. super指向调用该函数的实例的原型 
2. 只有对象的方法中才有super关键字，且简写形式定义的方法
{
	foo(){
		super;//得到super
	}
}
```

```html
<script>
        var obj = {
            name: 'caocao',
            age: 100,
            say() {
                console.log('My Name is '+this.name);
                console.log('My Name is '+super.name);
            },
            getInfo: function(){
                console.log(super.name);
            }
        };

        //在obj的原型上添加属性
        obj.__proto__.name = '吕布';

        console.log(obj);
        obj.say();

        obj.getInfo(); //这个报错，要简写才可以

    </script>
```



### 9.3 对象的扩展运算符 【...】 (ES9新增)

```
定义：
	把对象转为用逗号分隔的键值对序列
	
作用：
	对象操作 （对象合并、对象克隆）
	对象的解构赋值
```

```js
 let {age, ...b} = obj;
```

```html
<script>
        var obj = {
            name: 'caocao',
            age: 100,
            say() {
                console.log('My Name is '+this.name);
            },
            getInfo: function(){

            }
        };

     /*  console.log(...obj);
       //相当于
       console.log(name:'caocao', age:100, say:fn, getInfo:fn);*/

        // 操作对象
        //对象的克隆
        let obj2 = {...obj};
        obj2.name = '刘备';
        console.log(obj2);
        console.log(obj);
        console.log('');

        // 对象合并 如果有重名属性，后面覆盖前面的
        var obj3 = {width:100, height:200, name: '孙权'};
        var obj4 = {...obj, ...obj3};
        console.log(obj4);
        console.log('');


        //用于对象的结构赋值
        let {age, ...b} = obj;
        console.log(age);
        console.log(b);


        let {...obj5} = [10,20,30,40,40,50];
        console.log(obj5);

        let {...obj6} = 'hello world';
        console.log(obj6);

        //克隆
        //let obj7 = obj;
        let {...obj7} = obj;
        obj7.name = '贾宝玉';
        console.log(obj7);
        console.log(obj);

        let obj8 = {...obj};

    </script>
```



### 9.4 Object函数新增的方法

```
Object.is()  用于比较两个数据是否相等，返回布尔值； 类似于全等，不同点NaN和Nan相等、+0和-0不相等
Object.assign()  合并对象
Object.getOwnPropertyDescriptor()   获取某个自身属性的描述信息
Object.getOwnProppertyDescriptors()  获取对象所有自身属性的描述信息  ES8新增
Object.getPrototypeOf() 	获取对象的原型
Object.setPrototypeOf()     给对象设置原型
Object.keys()  返回数组，由对象的属性名组成。
Object.values()  返回数组，由对象的属性值组成。 ES8新增
Object.entries()  返回二维数组，由属性名和属性值 组成  ES8新增
Object.getOwnPropertyNames()   返回数组，有对象的属性名组成  (相当于keys)
Object.formEntries() 参数是二维数组，每个数组有两个成员，返回对象,就是(Object.entries（）的逆运算)  ES8新增
```

```html
<script>
       // Object.is() 判断两个值是否相等
        console.log(Object.is(100, 100));
        console.log(Object.is(100, '100'));  //false
        console.log(NaN === NaN); //false
        console.log(Object.is(NaN, NaN));  //true
        console.log(+0 === -0);  //
        console.log(Object.is(+0, -0));  //false
        console.log('');


        //对象合并
        var obj = Object.assign({name:'曹操', age: 200}, {width:200,height:300, name:'吕布'});
        console.log(obj);
        console.log('');


        //定义对象
       var obj1 = {
           name: 'caocao',
           age: 100,
           say() {
               console.log('My Name is '+this.name);
           },
           getInfo: function(){

           }
       };

       //获取自身属性的描述信息
       console.log(Object.getOwnPropertyDescriptor(obj1, 'name'));
       //console.log(Object.getOwnPropertyDescriptor(obj1, 'constructor'));
        console.log(Object.getOwnPropertyDescriptors(obj1));
        console.log('');


        // 获取对象的原型
        console.log(Object.getPrototypeOf(obj1));
        console.log('');

        //设置某个对象的原型
        Object.setPrototypeOf(obj1, {tag:10});
        console.log(obj1);
        console.log('');


        console.log(Object.keys(obj1));
        console.log(Object.values(obj1));
        console.log(Object.entries(obj1));

        console.log('');
        console.log(Object.getOwnPropertyNames(obj1));

        console.log('');
        let obj6 = Object.fromEntries([['name', '曹操平'], ['age', 100], ['scoce', 15]]);
        console.log(obj6);

    </script>
```



#### 9.4 Object实例新增的属性(一直在用)

```
__proto__  获取对象的原型
```



## 10 Class语法

### 10.1 定义类(构造函数)

```js
class 类名(构造函数名) {
    //定义属性 只声明
    name = null;
    age = null;
    
    //构造方法 实例化的时候自动调用，可以接受参数，给属性赋值
    constructor(name,age) {
        this.name = name;
        this.age = age;
    }
    
    //定义方法
    say() {
        
    }
    eat() {
        
    }   
}
```

> **注意：**
>
> class定义的类 本质还是个函数; 但是不能被调用，只能被实例化
>
> typeof 类名 === 'funciton'

### 10.2 实例化

```js
new 类名;
new 类名(构造方法的参数);
```

> **注意：**
>
> ① 类中定义的属性会添加到实例上
>
> ② 类中定义的方法会添加到原型上

```html
<script>

        //定义类
        class Person {
            //属性，会添加到实例上
            /*name = '曹操';
            age = 10;*/
            //把所有的属性在这里声明
            name = null;
            age = null;

            //定义构造方法 实例化的时候自动执行
            constructor(name, age=10) { //可以写默认值
                this.name = name;
                this.age = age;
            }

            // 方法，添加到原型上
            say() {
                console.log('MY Name is '+this.name);
            };

            eat() {
                console.log('My age is '+this.age);
            }
        }

        console.log(Person);
        console.log(typeof Person);
        console.log(Person.name);

        //不能调用
        //Person();

        // 实例化
        var p = new Person('曹操', 19);
        console.log(p);
        p.say();

        var p1 = new Person('吕布', 21);
        console.log(p1);
        p1.say();

        var p2 = new Person();
        console.log(p2);

    </script>
```



### 10.3 静态方法

```js
class Person{
	static 方法名() {
	
	}
}

Person.方法名()
```

```
静态方法没有添加给实例，添加给构造函数（类）本身
```

```html
<script>

        //定义类
        class Person {
            //属性，会添加到实例上
            /*name = '曹操';
            age = 10;*/
            //把所有的属性在这里声明
            name = null;
            age = null;

            //定义构造方法 实例化的时候自动执行
            constructor(name, age=10) {
                this.name = name;
                this.age = age;
            }

            // 方法，添加到原型上
            say() {
                console.log('MY Name is '+this.name);
            };

            eat() {
                console.log('My age is '+this.age);
            }

            //静态方法 没有添加到实例上
            static getClassName() {
                console.log('类名是 Person');
            }
        }

        //Person.getClassName = function(){}

        var p = new Person('曹操', 19);

        console.log(p);
        //p.getClassName();

        console.dir(Person);
        Person.getClassName();

    </script>
```



### 10.4 取值函数getter 和 存值函数setter

```js
class Person{
    firstName = 'Tom';
	lastName = 'NiGulasi';

	get fullName() {
        return this.firstName + '·' + this.lastName
    }

	set fullName(value){
        this.firstName = value.split('·')[0];
        this.lastName = value.split('·')[1]
    }
}

let p = new Person();

p.fullName //读写
```

```html
<script>

        //定义类
        class Person {
            //定义属性
            firstName = '尼古拉斯';
            lastName = '赵四';

            //当获取fullName属性值的时候 自动调用
            get fullName() {
                return this.firstName + '·' + this.lastName;
            }

            //当设置fullName属性值的时候 自动调用
            // 接受一个参数，是要给fullName属性设置的新值
            set fullName(val) {
                this.firstName = val.split('·')[0];
                this.lastName = val.split('·')[1];
            }
        }

        //实例化
        var p = new Person();

        console.log(p);

        console.log(p.fullName);

        p.fullName = '玛格丽特·翠花';

        console.log(p);

        console.log(p.firstName);
        console.log(p.lastName);
        console.log(p.fullName)

    </script>
```



### 10.5 继承

```
1. 使用 extends 来继承
2. 继承之后：
	子类的实例的原型指向父类的一个实例
	子类自己的原型指向父类 (静态方法也可以继承)
3. 可以在子类上添加属性和方法
4. 在子类上重写父类的方法，子类重写的方法必须调用super()
	
```

```js
class 子类 extends 父类 {
    constructor() {
        super();
    }
}
```

```html
<script>
        // 定义父类
        class Animal {
            weight = null;
            color = null;

            //构造方法
            constructor(weight, color) {
                this.weight = weight;
                this.color = color;
            }

            eat() {
                console.log('我能吃，我'+this.weight+'公斤');
            }

            sleep() {
                console.log('我能睡');
            }

            //定义静态方法
            static getInfo() {
                console.log('我是一个静态方法');
            }
        }

        // 定义子类
        class Dog extends Animal {
            //添加属性
            name = null;

            //构造方法, 重写父类的方法
            // 重写了父类方法，必须调用super() 保证
            constructor(weight, color, name) {
                super(weight, color);  //把父类的同名方法再调用一次 this指向子类实例
                this.name = name;
            }

            // 添加方法
            lookHome() {
                console.log('我叫'+this.name+',我能看家');
            }
        }

        //实例化子类
        // 父类定义的属性 添加到子类的实例上
        // 子类实例的原型 是 父类的一个实例
        // 子类本身的（隐式__proto__）原型 是 父类 （父类的静态方法，子类也可以用）
        let dog = new Dog(40, 'yellow', '旺财');

        console.log(dog);
        dog.eat();
        dog.sleep();
        dog.lookHome();
        Dog.getInfo();

        /*console.log(Dog.prototype instanceof Animal);
        Dog.getInfo();
        console.dir(Dog);
        */

    </script>
```





## 11 新增的数据类型（原始类型）

### 11.1 Symbol

```
1. 创建一Symbol数据(只能调用，不能实例化)
	Symbol()
	
2. symbol数据特点：
	① 每创建一个symbol类型的数据，都是唯一的。
	② symbol类型的数据可以作为属性名，同字符串一样
	
3. 应用：
	给对象添加属性（不会被覆盖）
	
4. 注意：
	for...in、Object.keys()、Object.values()、Object.entries()、Object.getOwnPropertyNames()  这些方法都取不到属性名是Symbol类型的属性
	
	Object.getOwnPropertySymbols()  获取类型是symbol的属性名
	Reflect.ownKeys(obj)  获取对象自身所有的属性（不论属性名时什么类型）
```

```html
<script>
        //创建一个symbol数据
        // 每创建一个symbol数据，都是唯一的
        var s1 = Symbol();
        var s2 = Symbol();

        console.log(s1, s2);
        console.log(typeof s1);  //symbol
        console.log(s1 === s2);  //false
        console.log(Object.is(s1, s2)); //false
        console.log(s1 === s1);
        console.log('');


        //可以作为对象的属性
        // 得到了一个对象，希望给对象添加属性
        var obj = {
            name: '曹操',
            age: 119,
            [s1]: '长江'
        };
        obj[s2] = '黄河'; //对象属性可读可写
        obj[Symbol()] = '雅鲁藏布江'; //以后就取不到这个属性了
        console.log(obj);
        console.log(obj[s1], obj[s2], obj[Symbol()]);

        console.log('');


        //var s3 = new Symbol(); //不能实例化 。只能调用
        var s3 = Symbol('foo');
        var s4 = Symbol('foo');
        console.log(s3, s4);
        console.log(s3 === s4);


        console.log('');

        console.log(Object.keys(obj)); //属性名是symbol类型的 取不到的
        console.log(Object.values(obj));
        console.log(Object.entries(obj));
        console.log(Object.getOwnPropertyNames(obj));
        console.log(Object.getOwnPropertySymbols(obj));
        console.log(Reflect.ownKeys(obj));
        console.log('');
        // for ... in 获取不到
        for (var i in obj) {
            console.log(i);
        }

    </script>
```



### 11.2 BigInt （ES10）

#### ① 安全数

```
通过 Number.MAX_SAFE_INTEGER 和 Number.MIN_SAFE_INTEGER  两个属性获得
如果整数超过了这个范围，无法按照整型的方式存储，计算会造成不精确
```

#### ② BigInt类型

```js
// 1. 字面量
var b = 100n

// 2 转换函数
var b = BigInt(1000)
```

```
bigInt类型的数据适合比较大的数字运算
bigInt类型的数据只能和BigInt类型的数据运算
```

```html
<script>
       console.log(Number.MAX_SAFE_INTEGER);
       console.log(Number.MIN_SAFE_INTEGER);

       console.log(2 ** 60);  //并不是按照整数的形式保存的，按照浮点数形式保存

        console.log(Number.MAX_SAFE_INTEGER + 10);//计算出错
        console.log(Number.MAX_SAFE_INTEGER + 1);//计算出错
        console.log(Number.MAX_SAFE_INTEGER + 3);//计算出错

        console.log(2 ** 53 - 1 + 2);
        console.log(2 ** 53 - 1 + 20);

        //对于大数字的运算 bigint类型
        console.log('');

        console.log(typeof Number.MAX_SAFE_INTEGER);
        console.log(typeof BigInt(Number.MAX_SAFE_INTEGER));
        console.log(typeof 100n);
        console.log('');

        //bigint类型的数据和number类型数据无法相互运算
        var b1 = BigInt(Number.MAX_SAFE_INTEGER);

        console.log(b1 + 10n);
    </script>
```



## 12 Set 和 Map

### 12.1 Set

#### ① 描述

```
无序且不重复的多个值的集合
```

#### ② 创建一个Set类型的数据

```js
new Set(); //创建的是空的Set
new Set(数组);  //把数组变为Set，去掉重复的值
new Set(类数组)
```

#### ③ Set实例的方法

```
add(value)   	添加一个值
delete(value)   删除一个值
has(value)		判断是否存在某个值
clear() 		删除所有的值
keys()			返回遍历器
values()        返回遍历器
entries()       返回遍历器
forEach()		用于遍历
size 属性  获取Set成员的个数
```

#### ④ Set应用

```
1. 实现数组去重
```

```html
<script>
        // 创建一不空的Set 参数写数组
        var s = new Set([100,200,300,400,300,500,500,500]);
        console.log(s);

        //给set添加一个值
        s.add('曹操');
        s.add(100);
        console.log(s);

        // 删除set中一个值
        s.delete(100);
        s.delete('曹操');
        console.log(s);

        // 判断是否存在某个值
        console.log(s.has(200));
        console.log(s.has(100));

        //清空
        s.clear();
        console.log(s);
        console.log('');


        s = new Set([100,200,300,400,300,500,500,500,{},[]]);
        console.log([...s.keys()]);
        console.log([...s.values()]);
        console.log([...s.entries()]);
        console.log('');

        s.forEach(item=>{
            console.log(item);
        });
        console.log('');

        console.log(s.size);

    </script>
```



### 12.2 Map

#### ① 描述

```
Object对象是一种键值对(key-value)的集合，属性名就是键（key）,属性值就是值（value） 
Map类似于对象，也是键值对的集合，对象的Key只能是字符串和Symbol类型， Map的Key可以是任意类型
```

#### ② 创建Map

```js
// 创建空的
new Map()

// 创建的时候，指定初始值
new Map([
    [key,value],
    [key,value]
]);
```

#### ③ Map实例的方法

```
get(key)		获取指定key的值
set(key,value)  设置或添加某个key的值
delete(key)     删除指定的某个key和他值
clear()			清空所有
has(key)		判断某个key是否存在
keys()		    返回遍历器，所有key的集合
values()		返回遍历器，所有值的集合
entries()		返回遍历器，所有key-value的集合（二维）
forEach()		用于遍历
```



## 作业（在下面总结的地方）

```
1. 拉平数组， 不用flat()
2. 总结一下JS中声明变量的方式
3. 如何做到深度克隆
```

```js
let sons = ['曹丕', '曹植', '曹冲'];
let sister = {name:'曹芹', age:18};
var obj = {
    name: '曹操',
    age: 100,
    sons,
    sister 
}

// 克隆对象 （浅克隆） 
let obj1 = {...obj}
obj1.sister.name = '曹花';

console.log(obj.sister.name);
```



# 第二十二天，ECMAScript 6+课堂笔记(连续昨天一起)

## 13 iterator 遍历器/迭代器

### 13.1 iterator对象

#### ① 什么是遍历器对象

```
遍历器对象就是一种可以遍历的对象
每个遍历器对象都有一个next()方法
遍历器对象内部存在一指针， 指向起始指向遍历器的第一个数据， 调用next(),会取出指针指向的数据，并且指针下移。
```

#### ② 如何得到一个遍历器对象

```
array类型、Set类型、Map类型的对象，都有三个方法， keys()、values()、entries() 都返回iterrator对象
字符串的 matchAll() 也返回iterrator对象
```

#### ③ for ... of

```
可以使用 for ... of 对象遍历iterrator对象
```

#### ④ 遍历器对象可以转为数组

```
[...iterrator对象]
Array.from(iterration对象)
```

```html
<script>
        // set map array
        // keys()  values()  entries()

        let arr = [100,200,300,400,500];
        let arrIterator = arr.values();  //返回一个遍历器


        console.log(arrIterator);

        //遍历器对象 有next方法() 可以被多次调用
        // 存在一个指针，起始指向第一个值，调用next().取出这个值，并让指针下移；
        console.log(arrIterator.next());
        console.log(arrIterator.next());
        console.log(arrIterator.next());
        console.log(arrIterator.next());
        console.log(arrIterator.next());
        console.log(arrIterator.next());
        console.log(arrIterator.next());
        console.log('');

        //自定义循环 遍历一下遍历器对象
        var set = new Set([100,200,300,400,500]);
        var setIterrator = set.keys();
        let res = null;
        do {
            res = setIterrator.next();
            if (res.value !== undefined) {
                console.log(res.value);
            }
        } while(!res.done);
        console.log('');


        // for ... of 遍历 遍历器
        let arrIter = arr.keys();
        for (let i of arrIter) {
            console.log(i);
        }
        console.log('');

        let arrEnterisIter = arr.entries();
        for (let i of arrEnterisIter) {
            console.log(i);
        }
        console.log('');


        //遍历器对象转为数组的
        console.log([...arr.values()]);
        console.log(arr);

        let s = new Set([1,2,3]);
        console.log([...s.entries()]);

        console.log(Array.from(arr.entries()));

    </script>
```



### 13.2 iterable  可遍历对象

#### ① 什么是 iterable 可遍历对象

```
把部署了 iterator 接口的数据结构，称之为'iterable'（可遍历对象）
可以使用 for...of 遍历 iterable对象

iterator接口部署在了数据结构的Symbol.iterator属性上

一个对象，只有具有Symbol.iterator属性，且该属性指向一个返回遍历器的函数； 该对象就是 iterable(可遍历对象）。
```

#### ② 原生实现了iterator接口的数据结构 （可遍历对象）

```
Array
Set
Map
String
Arguments
NodeList
HTMLcollection
```

#### ①有iterable接口的数据

```html
<body>
    <button>按钮</button> * 6
    <script>
       let arr = [100,200,300,400,500];
       for (let i of arr) {
           console.log(i);
       }
       console.log('');


       let s = new Set(['a','b','c']);
       for (let i of s) {
           console.log(i);
       }
       console.log('');

       let m = new Map();
       m.set('name', '曹操');
       m.set('age', 100);
       for (let i of m) {
           console.log(i);
       }
       console.log('');

       var btns = document.querySelectorAll('button');
       for (let i of btns) {
           console.log(i);
       }
       console.log('');


       var str = 'helloworld';
       for (let i of str) {
           console.log(i);
       }

    </script>
</body>
```



#### ②iteartor接口

```html
<script>
       let arr = [100,200,300,400,500];

       console.log(arr);

       console.log(Symbol.iterator); //Symbol类型的数据
       console.log(arr[Symbol.iterator]);
       console.log('');


       let obj = {name:'曹操', age: 19};
       //填一个属性Symbol.iterator, 指向一个函数，函数要返回遍历器，返回函数需要 * 
       obj[Symbol.iterator] = function* (){

       };

       for (let i of obj) { //还不能遍历，因为里面还没有yiele      
           console.log(i);
       }

    </script>
```

#### ③可以使用解构赋值

```html
<script>
       let arr = [100,200,300,400,500];
       let arrIterator = arr.entries();

       let [a,b,c] = arrIterator;
       console.log(a,b,c); //100,200,300

       let list = [...arrIterator]; //数组

    </script>
```



## 14 generator 生成器

### 14.1 什么是生成器

```
生成器就是生成遍历器的函数
```

### 14.2 定义生成器

```js
function* 生成器名() {
     yield 值;
     yield 值;
     yield 值;
     yield 值;
}
```

### 14.3 yield 关键字

```
yeild关键返回一个值， 遍历的时候每次得到就是yield的值
调用next(),执行到yield就会停止； 下一次调用next(),执行到下一个yield停止
```

> 调用生成器函数的时候，函数内不会执行
>
> 当调用next()的时候，才开始执行生成器函数内的代码； 执行到yield停止；

```html
<script>
        //定义一生成器函数 generator
        function* helloGenerator() {
            console.log('我是一个生成器');
            yield '曹操';

            console.log('我也是一个生成器');
            yield '吕布';
            yield '刘备';
            yield '孙权';
            yield '诸葛亮';

            return 'hello world';  //return后面的代码同样不会执行

            yield '小乔';
            yield '大乔';
        }


        //调用生成器函数，返回一个iterator对象
        let helloIterator = helloGenerator();

        console.log(helloIterator);  //输出一个遍历器
        console.log('');

        console.log(helloIterator.next());
        console.log(helloIterator.next());
        // console.log(helloIterator.next());
        // console.log(helloIterator.next());
        // console.log(helloIterator.next());
        // console.log(helloIterator.next());
        // console.log(helloIterator.next());

        console.log('');

        //遍历以上的代码
        /*for (let i of helloIterator) {
            console.log(i);
        }*/

    </script>
```



### 14.4 使用生成器函数给对象部署iterator接口

```html
<script>
        let obj = {
            name: '曹操',
            age: 12,
            sorce: 90,
            height: 170
        };

        //把obj变为一个 iterable
        // 部署iterator接口
        obj[Symbol.iterator] = function* (){
           for (let i in obj) { 
               yield [i,obj[i]];  //i就是属性名，相当于是索引，obj[i]是属性值
           }
        };

        for (let i of obj) {
            console.log(i);
        }

</script>
```



## 15 模块

### 15.1 模块中导出数据

```js
// 模块内部
function say() {}
function eat() {}

export {
	say,
    eat
}
```

### 15.2 导入模块

```js
import {say, eat} from '模块文件路径';
```





## 16 总结

### 16.1 ECMAScript中数据类型

```
原始类型（值类型）： string、number、boolean、null、undefined、symbol、bigint
对象类型（引用类型）： array、object、regexp、set、，map......
```

### 16.2 ECMAScript中声明变量的方式

```
1、 var
2、 function
3、 let
4、 const (常量)
5、 class
6、 import
```

### 16.3 实现数组扁平化的方式

```js
let arr = [['a', 'b', 'c'], [10, [100, 200,300]], [['A','B'], ['一', '二','三']], 1000];

//1. 使用flat()  默认只能拉平二维数组
arr.flat(Infinity)

//2. 利用字符串的join方法  缺点：数组的元素都会变为字符串类型
arr.join().split(',')

//3. 自定义递归函数
function flatArray(array) {
    //创建一个空数组
    let res = [];
    // 遍历传进来的数组
    for (var i = 0; i < array.length; i ++) {
        //判断数组的元素还是不是数组
        if (array[i] instanceof Array) {
            res = res.concat(flatArray(array[i]));
        } else {
            res.push(array[i]);
        }
    }
    //返回新数组
    return res;
}
```

### 16.4 实现对象拷贝（克隆）的方式 （浅拷贝）

```
数组Array:
let arr = [100,200,300,400];
1. [...arr]
2. arr.concat()  不写参数 数组合并方式
3. arr.splice(0) / arr.substring(0) / arr.substr(0)  数组截取方式

对象Object:
let obj = {name: '曹操', age: 100};
1. {...obj}
2. Object.assign(obj)   对象合并方式
```



### 16.5 实现对象的深度克隆（深拷贝）

```js
 let sons = ['曹丕', '曹植', '曹冲'];
        let sister = {name:'曹芹', age:18};
        var obj = {
            name: '曹操',
            age: 100,
            sons,
            sister,
            say() {},
            eat() {}
        };

// 1. 借助于JSON  无法拷贝方法，适合于纯数据对象
JSON.parse(JSON.stringify(obj));

// 2. 递归函数实现
//定义函数 获取对象的构造函数（类）名
function getObjectClass(obj) {
    return Object.prototype.toString.call(obj).slice(8,-1)
}
//深拷贝的函数
function deepClone(obj) {
    //判断obj是对象是数组还是其他
    if (getObjectClass(obj) === 'Object') {
        var res = {};   //创建空的对象
    } else if (getObjectClass(obj) === 'Array') {
        var res = [];   //创建空数组
    } else {
        return obj;
    }
    //对传入的对象(遍历)进行遍历
    for (let i in obj) {
        res[i] = deepClone(obj[i]);
    }
    //返回新数组或对象
    return res;
}
```

### 16.6 遍历对象属性的方式

```
1. for ... in  遍历自身以及原型上可以被遍历的属性,属性名是symbol类型不可以
2. Object.keys()、Object.value()、Object.entries()    自身的属性，属性名是symbol类型不可以
3. Object.getOwnPropertyNames()     自身属性名的集合， 属性名是symbol类型不可以
4. Object.getOwnPropertySymbols()   自身属性名时symbol类型的属性名的集合
5. Reflec.ownKeys()    自身所有的属性名的集合 （字符串和symbol都可以）
```



# 第二十三天PC项目课堂笔记

```
example.fuming.site
```



## 1 滚轮事件

```
mousewheel;   //用于chrome和IE
DOMMouseScroll;  //用于firefox	只能使用addEventListener监听
```

```
获取滚轮滚动方向：
	event.wheelDelta;  //chrome和IE
    	120表示向上滚动， -120表示向下滚动
    evnet.detail;  //firefox的用法
    	3表示向下滚动  -3表示向上滚动
```

```js
 var box = document.getElementById('box');
  //ie/chrome
  box.onmousewheel = scrollMove;
  //firefox
  if(box.addEventListener){
    box.addEventListener('DOMMouseScroll',scrollMove);
  }
​
  function scrollMove(event) {
    event = event || window.event;  //兼容 ie 或者 
​
    var flag = '';
    if(event.wheelDelta){
      //ie/chrome
      if(event.wheelDelta > 0){
        //上
        flag = 'up';
      }else {
        //下
        flag = 'down'
      }
    }else if(event.detail){
      //firefox
      if(event.detail < 0){
        //上
        flag = 'up';
      }else {
        //下
        flag = 'down'
      }
    }
​
    switch (flag){
      case 'up':
        //盒子高度减小
        box.style.height = box.offsetHeight - 10 + 'px'
        break;
      case 'down':
        //盒子高度增加
        box.style.height = box.offsetHeight + 10 + 'px'
        break;
    }
​
    //取消默认行为
    event.preventDefault && event.preventDefault();
    return false;
  }
```

#### 代码示例

```html
<head>
    <meta charset="UTF-8">
    <title>滚轮事件</title>
    <style>
        #box {
            position: absolute;
            left: 0;
            right: 0;
            top: 0;
            bottom: 0;
            margin: auto;
            width: 300px;
            height: 300px;
            background: #f90;
        }
    </style>
</head>
<body>
    <div id="box"></div>
    <script>
        var box = document.querySelector('#box');

        //chrome ie
        box.addEventListener('mousewheel', scrollMove);
        //firefox
        box.addEventListener('DOMMouseScroll', scrollMove);

        // 滚轮滚动函数
        function scrollMove(event) {
            //判断是往上滚动还是往下滚动
            var tag = null;  //标记滚轮往上滚还是往下滚
            if (event.wheelDelta) {  //chrome ie
                if (event.wheelDelta > 0) {
                    tag = 'up';
                } else {
                    tag = 'down';
                }
            } else if (event.detail) { //firefox
                if (event.detail > 0) {
                    tag = 'down';
                } else {
                    tag = 'up';
                }
            }
            //根据滚动方向，实现相应的操作
            if (tag === 'up') {
                box.style.width = box.offsetWidth + 5 +'px';
                box.style.height = box.offsetHeight + 5 +'px';
            } else if (tag === 'down') {
                box.style.width = box.offsetWidth - 5 +'px';
                box.style.height = box.offsetHeight - 5 +'px';
            }
        }

    </script>
</body>
</html>
```



## 2. 节流和防抖

### 2.1 节流 throttle

#### 原理

```
持续触发事件，一定的时间间隔内，只能触发一次。
两次事件触发的时间间隔必须大于一定的时间，否则将无法触发。
```

#### 代码示例

```js
var prev = Date.now();
var delay = 1000; //最小时间间隔
box.addEventListener('scroll', function(){
    var now = Date.now();
    if (now-prev < delay) {
        return false;
    }
    //再执行事件的相关逻辑
    
    //重新设时间
    prev = now;
})
```

```html
<head>
    <meta charset="UTF-8">
    <title>滚轮事件</title>
    <style>
        input {
            width: 400px;
            padding:10px;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
    <input type="text" id="myInput">
    <script>
        /**
         * 持续触发事件，保证一段时间内只触发一次。
         * 两次事件的时间间隔只有达到一定时间才能触发。
         * */

        //获取元素
        var myInput = document.querySelector('#myInput');
        //监听事件 事件节流方式，1s之内只能触发一次
        var prev = Date.now(); //上一次触发时间
        var delay = 1000; //最小时间间隔
        myInput.addEventListener('keyup', function(){
            //记录此时的事件
            var now = Date.now();
            //两次事件的时间间隔 >= 1s种才能触发
            if (now - prev < delay) {
                return false;
            }
            //事件的逻辑
            console.count(); //会将调用的次数输出到控制台
            //更新一下时间
            prev = now;
        });
    </script>
</body>
</html>
```



### 2.2 防抖 debounce

#### 原理

```
触发事件之后，逻辑延迟执行，如果在一定时间内，再次触发了事件，清除上一次的定时，重新计时。
```

#### 代码示例

```js
var delay = 1000;
var timeId = null;
box.addEventListener('scroll', function(){
   	//先清空上一次的定时
    clearTimeout(timeId);
    //延迟执行
    timeId = setTimeout(function(){
        //事件逻辑
    }, delay)
});
```

```html
<head>
    <meta charset="UTF-8">
    <title>滚轮事件</title>
    <style>
        input {
            width: 400px;
            padding:10px;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
    <input type="text" id="myInput">
    <script>
        /**
         * 触发事件后，代码延迟执行；
         * 持续触发事件，如果一定时间间隔内事件没有再次触发，执行事件逻辑；如果一定时间间隔内容事件再次触发，再次延迟一段事时间执行。
         * */

        //获取元素
        var myInput = document.querySelector('#myInput');
        //事件防抖
        var delay = 1000;
        var timeId = null;
        myInput.addEventListener('keyup', function(){
            //清除掉上次的定时
            clearTimeout(timeId);
            //事件逻辑延迟执行
            timeId = setTimeout(function(){
                console.count();
            }, delay);
        });

    </script>
</body>
</html>
```

## 3 audio 音频播放

### 3.1 audio标签

```html
<audio src="音乐地址(mp3)" controls></audio>
```

### 3.2 DOM API

```
paused  属性 标识是否是暂停状态
play()   播放音频
pause()  暂停播放
```

```html
 // 背景音乐
<html>
    <script>
        (function () {
            var bgMusic = document.querySelector('.bg-music');//获取音乐标签父级
            var audio = document.querySelector('audio'); //获取音乐标签

            bgMusic.addEventListener('click', function () {
                if (audio.paused) {
                    audio.play();//播放
                    bgMusic.classList.add('played');
                } else {
                    audio.pause(); //暂停
                    bgMusic.classList.remove('played');
                }
            })
        })();
        <script>
<html>
```



## 4 过渡事件

```
transitionstart  //过度开始
transitionend    //过度结束
transitioncancel //过度失败
```



## 4. 删除元素的方法

```
remove()  删除的自己
```

```html
<html>
	<script>
//开机动画
        (function () {
            //获取相关元素
            var bootMask = document.querySelector('#bootMask');
            var bootMaskDown = document.querySelector('#bootMask .boot-mask-down');
            var bootMaskUp = document.querySelector('#bootMask .boot-mask-up');
            var bootMaskLine = document.querySelector('#bootMask .boot-mask-line');

            //定义所有的图片
            var arr = ['bg1.jpg','bg2.jpg','bg3.jpg','bg4.jpg','bg5.jpg','about1.jpg','about2.jpg','about3.jpg','about4.jpg','worksimg1.jpg','worksimg2.jpg','worksimg3.jpg','worksimg4.jpg','team.png','greenLine.png'];
            // 定义变量，计算下载成功图片的个数
            var loaded = 0;
            // 创建图片元素，加载图片
            arr.forEach(function(item) {
                //创建img元素
                var imgNode = document.createElement('img');
                //设置图地址
                imgNode.src = 'img/'+item;
                //监听事件 图片下载完毕
                imgNode.addEventListener('load', function(){
                    //下载数量 +1;
                    loaded ++;
                    //计算加载的比例
                    var scale = loaded / arr.length;
                    // 变化进度条的长度
                    bootMaskLine.style.width = scale * 100 + '%';
                });
            });

            bootMaskLine.addEventListener('transitionend', function(){
                //如果加载完毕了
                if (loaded >= arr.length) {
                    //开门
                    bootMaskUp.style.height = '0';
                    bootMaskDown.style.height = '0';
                    //删除进度条
                    bootMask.removeChild(bootMaskLine);

                }
            });

            //bootMaskDown 过渡结束
            bootMaskDown.addEventListener('transitionend', function(){
                //删除bootMask
                bootMask.remove(); //删除自己，注意兼容性
            });
	<script>
<html>
```

jQuery 教程资料

```
http://learn.fuming.site/front-end/jQuery/
```

[http://learn.fuming.site/front-end/jQuery/]:



## 总结

### async

```
js按照从上到下，顺序执行
      js没有阻塞布局，渲染
      js阻塞 html 解析
    
    为什么script放在body下面？
      因为js可能要操作DOM
      js阻塞 html 解析，导致页面会没有结构

    async 异步的： 让js谁先加载完毕，谁就先执行    
      async 既不阻塞 页面渲染 也不阻塞 html 解析   

    什么时候用async？ -> 一般放在head中，加快解析
      如果js代码没有依赖关系，用async
      优点：js加载速度快，不阻塞html渲染  

    defer 和 async差不多，不同的是 defer中的js 必须按照从上到下，顺序执行
      一般不用
```

### requestAnimationFrame()

```html
 <script>
    const box = document.getElementById('box');

    let x = 0;

    move();

    function move() {
      // 动画最流畅，性能最好
      window.requestAnimationFrame(function () {
        // 这个函数会在下一次重排重绘之前调用（将当前函数操作dom导致的重排重绘和下一次重排重绘合并成一次）
        // 执行动画
        x++;
        box.style.transform = `translateX(${x}px)`;
        if (x >= 1000) {
          return;
        }
        move();
      })
    }
  </script>
```

