## CSS介绍
#### 层叠样式表 Cascading Style Sheets
* 是一种用来表现HTML（标准通用标记语言的一个应用）或XML（标准通用标记语言的一个子集）等文件样式的计算机语言
* css用于控制页面中元素的样式，控制页面的外观、颜色、布局等设置
#### css引入的方式
##### 内联式（行内引入）
* 直接在html标签中书写css
 * 样式内容书写在html标签的style属性中，多个css样式可以写在一起，使用分号隔开
 * 样式书写格式：样式名:样式值; (注意全部是英文半角符号)
* 内联式特点：
 * 冗余代码多，代码量大
 * 不利于维护和修改
 * 优先级相对来说较高，个别特殊的效果可以使用，但是不要滥用
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>内联式引入css</title>
</head>
<body>
    <ul>
        <li style="background-color: green;width: 100px;height: 100px;float: left;margin: 10px;color: #fff;text-align: center;line-height: 100px;"></li>
    </ul>
</body>
</html>
```
##### 嵌入式（头部引入）
* 使用css选择器选择你要控制的元素，然后书写样式；把样式书写在style标签中，然后把style标签放在head标签中
* 样式书写格式：
        选择器{
            样式名1:样式值1;
            样式名2:样式值2;
        }
* 嵌入式引入特点：
 * 便于维护和修改
 * 代码量少
 * 页面达到了样式与结构相分离
* style标签放在head标签的原因
 * 便于维护

   * 放在其他位置后期维护的时候需要花费时间去寻找代码书写位置
 * 不会引起页面的回流（重排）和重绘
  * 页面从上至下去解析，假设style标签写在body后边，读取这个style之前，整个网页的文档已经渲染的差不多了，发现还有style标签，页面就会重新计算页面的样式，然后重新渲染，所以会引起重绘和重排，网页可能出现闪烁，并且加载变慢

    ```
    网页是DOM tree 和 样式结构 结合以后构建的render tree（渲染树），浏览器就是根据render tree来绘制页面的
    回流（重排）：当render tree中的一部分或者是全部，因为元素的尺寸、布局、隐藏等等改变引起页面的重新渲染（重新构建绘制）
    重绘：当render tree中一些元素需要更新属性，这些更新的属性只会影响元素的外观、风格，不会影响元素的布局
    ```
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>嵌入式引入css</title>
    <style>
        li{
            color:red;
            background-color: yellow;
        }
    </style>
</head>
<body>
<ul>
    <li></li>
</ul>
</body>
</html>
```
##### css外部式引入
* 在外部新建一个css文件（后缀是.css），把样式写在外部的css文件中（外部css书写方法和嵌入式方法一样）
* 当一个页面需要外部css的时候，可以使用link标签把css引入进来，link标签书写的位置应该和嵌入式的style是一样的
* link标签的属性
 * href:相关联css的路径
 * rel：stylesheet  link引入的css和当前的文档html进行关联
 * type：text/css  引入的格式是text文本，是css文本
* 外部式引入特点：
 * 将html和css完全分离成两个文件
 * 一个css文件可以控制多个html文件
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" type="text/css" href="./index.css">
</head>
<body>
    <div></div>
</body>
</html>
```
* 引入外部的css还可以在使用@import方法，在style标签中引入，方式如下：
    ```
    @import "index.css";
    @import url(index.css);
    @import url("index.css");
    ```
* link引入和@import引入的对比：
 * 适用的范围不同
   * @import在style标签中引入，也可以在外部的css文件中书写
   * link只能在html中书写引入
 * 功能范围不同
    * link属于html标签
    * @import只是css提供的引入css的功能
 * 加载顺序不同
    * 页面在加载的时候，link引入的css会同时被加载
    * @import引入的css只有等页面全部下载完成以后才进行加载，所以可能会出现闪烁
 * 兼容性不同
  * link都支持
  * @import低版本ie不支持
 * 使用JS控制样式
  * JS只能控制link标签
  * @import是不能够被JS控制的
## CSS选择器
* 选择器是css中用来选择需要被设置样式的元素  
#### 基础选择器
###### id选择器  
* 给元素设置id属性，然后通过#+id属性值的方式来选择这个元素
* 选择器命名：
 * id就像我们的身份证号，是不允许重复的
 * 一个元素只能有一个id属性
 * id命名规范建议（类名相同）
  * 不能以数字开头，只能是字母、下划线、减号、$符号开头
  * 后边可以是数字字母下换线$号（header1 outer1 header-nav  header_nav）
  * 不要出现空格，一定要有自己的含义
###### 类选择器 
* 可以给不同的元素，进行分组
* 所有类名相等的元素，是一组的，可以进行控制样式
* 给要被分组的元素设置class属性，选择器中使用 .+ class属性值来选择元素
* 类名不一定是多个，也可以是一个
* 一个class可以设置多个类名，但是只能有一个class属性，class属性的值可以用空格隔开，就代表书写多个类名
###### 标签名选择器
* 通过标签名来选择元素
* 会选择页面中（控制条件中）所有的这个标签的元素
----
>基本选择器的优先级排名：!important > 行内书写 > id > 类 > 标签名 > 通配符 > 继承 > 默认样式
#### 基础层次选择器
###### 后代选择器
* 后代选择器使用 空格间隔开（A B：在A元素中寻找后代（不一定是儿子）是B的元素）
###### 子代选择器
* 子代选择器使用 > 间隔开（A>B：在A元素中寻找儿子辈元素 是B的元素）
###### 相邻兄弟选择器
* 相邻兄弟选择器使用 + 间隔开（A+B：在A元素的下边紧贴着A的元素 并且是B  才能被选中）
###### 通用兄弟选择器
* 相邻兄弟选择器使用 ~ 间隔开（A~B：在A元素的下边兄弟元素 并且是B  就能被选中）
####  群组选择器
* 将多个选择器使用 ，隔开,可以同时对多个选择器设置样式
* 如果多个元素有相同的样式，方法有两种
 * 使用一个共同的类名
 * 使用群组选择器
---
 >选择器的优先级
 >* 相同优先级的选择器生效方式：
 > * 当优先级相同的时候，在后边书写的样式优先级高
 > * link其实也是把样式关联上，选择器优先级相同的情况写，后写的生效            
 >* 选择器优先级的权重计算：
 >  行内样式： 1000
 >  id：100
 >  类：10
 >  标签名：1           
#### 属性选择器
    ELE[attr]:元素拥有attr属性 就会被选择
    ELE[attr=val]:元素拥有attr属性并且属性值为val，才会被选择
    ELE[attr^=val]:元素拥有attr属性并且属性值以val为开头的，才会被选择
    ELE[attr$=val]:元素拥有attr属性并且属性值以val为结尾的，才会被选择
    ELE[attr*=val]:元素拥有attr属性并且属性值包含val的，才会被选择
#### 伪类选择器
* 伪类选择器存在的意义是为了通过选择器，格式化DOM树以外的信息,以及不能被常规选择器获取到的信息
 * a标签的4种状态（被访问前，被访问后，鼠标激活，鼠标悬浮），不存在于DOM树中
 * 不能被常规获取，想要获得第一个子元素，无法通过常规的css选择器获取，只能通过伪类选择器来获取
###### 表单伪类选择器
    :read-only  选取不可被用户编辑的可输入表单
    :read-write 选取可以被用户编辑的表单元素
    :checked    选取任何被选中的单选和多选框
    :disabled   选取被禁用的表单元素
    :enabled    选取未被禁用的表单元素
    :focus      选取获取焦点的表单元素
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表单伪类选择器</title>
    <style>
        input:read-only{
            background-color: yellow;
        }
        /*目前这个选择器在火狐还是私有的，所以需要添加火狐前缀*/
        input:-moz-read-only{
            background-color: yellow;
        }

        input:read-write{
            background-color: green;
        }
        input:-moz-read-write{
            background-color: green;
        }

        /*单选框多选框默认不能设置背景和背景颜色*/
        input[type=checkbox]{
            background-color: red;
        }

        input[type=checkbox]:checked+label{
            color: red;
        }

        input:disabled{
            background-color: #0D1635;
        }

        input:enabled{
            width: 300px;
            height: 60px;
        }

        input:focus{
            background-color: pink;
        }
    </style>
</head>
<body>
    <form action="###">
        请输入用户名：
        <input type="text" readonly value="请输入啊">
        请输入姓名：
        <input type="text">
        请输入密码：
        <input type="password">
        请输入电话号码：
        <input type="tel" disabled>

        请选择你喜欢的水果：
        <input type="checkbox" id="foods1" name="foods">
        <label for="foods1">苹果</label>
        <input type="checkbox" id="foods2"name="foods">
        <label for="foods2">梨</label>
        <input type="checkbox" id="foods3"name="foods">
        <label for="foods3">香蕉</label>
    </form>
</body>
</html>
```
###### 结构的伪类选择器
* 伪类选择器的权重按照类来计算(:not除外)
```
:first-child  选取一组兄弟元素中的第一个元素。在选择器模块的level4版本中，前边可以不添加元素，代表通配符所有
            比如 ul :first-child(选择ul中后代元素中 是第一个的)
:first-of-type  选取一组元素中，同类型的的第一个元素
:last-child     选取一组兄弟元素中的第最后一个元素
:last-of-type   选取一组元素中，同类型的的最后一个元素
:nth-child(an+b) 先找到当前元素的所有兄弟元素，然后按照顺序依次从0开始排序，被选择到的结果就是符合小括号中的值
    2n+1 奇数
    2n   偶数
    odd  奇数
    even 偶数
    num  直接写数字
    -n+3  选取前3个
:nth-last-child(an+b):在所有的兄弟节点中由后向前匹配 其他和nth-child一样
:nth-of-type(an+b):先找到当前元素的所有同类型兄弟元素，然后按照顺序依次从0开始排序，被选择到的结果就是符合小括号中的值
:nth-last-of-type(an+b):在所有的同类型的兄弟节点中由后向前匹配 其他和nth-of-type一样
:only-child     匹配没有任何兄弟元素的元素
:only-of-type    代表一个元素没有同类型的兄弟元素
:not(X)  X是一个选择器，选择所有元素中 排除X所代表元素的元素（这个not伪类，它的权重计算完全是看X的权重）
:empty  选取没有子元素的元素 子元素包括元素和文本（空格和回车都包含）
```
> ###### 浏览器内核及前缀
> ```
> IE：    trident内核     -ms-
> Edge：  webkit内核      -webkit-
> firfox：gecko内核       -moz-
> safari：webkit内核      -webkit
> Chrome：早版本使用webkit  后和Opera共同开发新内核 Blink（基于webkit）  -webkit-
> Opera老内核presto  老前缀是 -o-（现在可以不用考虑）
> ```
> ###### div+css（xhtml+css）布局相对于table布局的优点
> ```
> 1、改版的时候更方便  只需修改css
> 2、页面加载速度更快，结构更加清晰，页面更加简洁
> 3、表现形式和结构相分离
> 4、易于优化（SEO），排名更靠前 CSS样式         
> ```

## CSS样式

#### CSS字体类样式

##### color: 设置文字颜色（继承）

* 可以直接设置颜色的名字（开发中很少使用，因为不精确）
  * red green yellow pink blue grey purple orange lightblue lightgreen greenyellow  yellowgreen

* 设置为三原色：  红r  绿g  蓝b
  * 所有颜色都是由这三种颜色调制出来的
  * 每一个颜色的值都是 0-255之间，如rgb(30,120,200)
  * 颜色还可以设置不透明度 opacity  opacity的值是1-0
  * 颜色如果需要书写透明度 可以使用 rgba(20,111,111,.7)

* 颜色还可以设置为十六进制（不能设置透明度）
  * \#加上16进制的颜色值  6位
    * \#112233--> 11代表red的十六进制值  22代表green颜色的十六进制值  33代表blue颜色十六进制值
  * 十六进制颜色提供简写：当12位一样并且34位一样并且56一样的时候 可以每一位简写一个
    * \#112233-->#123
    * \#aabb11-->#ab1
    * \#000000-->#000
    * \#111222-->#111222

* HSL设置颜色
  * H代表Hue 色调 0和360代表红色  范围是[0,360] 120代表绿色 240代表蓝色
  * S代表Saturation 饱和度  0-100%
  * L代表Lightness 亮度 0-100%
  * HSLA() 中 hsl代表的意思不变  a代表透明度  [1,0]

* 继承 inherit

> * a标签比较特殊，如果a标签没有href属性，那么继承颜色生效；
>
> * 如果a标签拥有href属性，a标签链接的自带样色会盖过继承。
>
> * a的4个状态（有链接、被点击后、点击中、鼠标悬浮）是有自己的样式的，只能通过伪类来控制这4中样式
>
>  所以在开发中给a标签设置颜色，需要直接对a标签进行设置

##### font-famliy：设置字体(继承)

* 常见中文字体："Microsoft YaHei"、"SimHei"、"SimSun"

* 但是我们设置的字体用户可能没有，我们需要设置备用字体
  * 在font-famliy后书写多个字体，使用逗号隔开，浏览器会依次检测支持为止，否则将执行默认字体

    ```
    font-family: "SimHei","SimSun","Microsoft YaHei";
    ```

* 目前常用的字体可以分为5大类
  * serif：衬线字体族
  * sans-serif：无衬线字体族
  * cursive:手写体族
  * monospace：等宽字体族
  * fantasy：梦幻字体族

######  外部字体包的引入：
* 外部引入的字体包和某一个元素没有任何关系，而是本页面都可以使用这个字体
*  原来我们页面自带的字体包都有自己的名字，我们首先给引进来的字体包起一个名字
* 在css中使用@font-face来引入外部字体包，font-face中有一个font-famliy属性 是给字体包起名字的，还要使用src：url（）来引入字体包
* 根据你起得名字，来使用字体包

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>外部引入字体包</title>
    <style>
        @font-face {
            font-family: "jier";
            src:url("../abc.ttf");
        }
        .outer{
            font-family: "jier";
        }
    </style>
</head>
<body>
    <div class="outer">
        看我的表演 我是非主流子
    </div>
</body>
</html>
```

##### font-size：字号设置(继承)

* 常用的单位是px、em、rem  当然也有不用的 cm in等等

* 可以设置小数（低版本ie不支持）

* 字号最好不要设置为奇数

* 一般来说汉字是正方形的，宽高就等于字号大小。但是实际文字占用的高度要大于字号大小，根据字体的不同，文字上下有一定的不能控制的间隙。因为文字的大小是基于4线格的（顶线 中线 基线 底线） 汉字并不能完整的填充满四线格

* 浏览器都有自己的默认字号大小和最小字号
  * 谷歌浏览器默认字号大小是16px
  * 谷歌浏览器支持的最小字号 多数是12px
  * 如果设置12以下，字体不支持
  * 如果设置字号为0，那么文字高度为0  消失

##### font-style：字体风格（继承）

* normal：正常

  * 多数元素的默认值

  * 对于默认倾斜或斜体的元素  i   var  em 可以调整成正常非倾斜样式

* italic ：斜体
  * 让元素呈现斜体  一般指的是一个字体
  * 在字体设计的过程中，会对一个文字设计 正常体  斜体 粗体 等状态，而italic只是选择让使用斜体显示

* oblique 让常规字体进行倾斜（强行让当前文字变倾斜）
  * oblique 后可以跟一个旋转角度  以deg为单位
    *  谷歌只支持0deg
    * 火狐只支持汉字和-90---90度的设置

* 对于上边两种倾斜版本，使用上没有什么区别（italic会占用高度较小）

##### font-weight：字体的粗细(继承)

* 用来定义字体的粗细其实目前浏览器只支持3个级别  细 正常 粗
  * normal：正常粗细  可以将默认加粗的字体进行改变为正常 比如 b strong
  * bold：加粗
  * bolder：相对父级来说的，比父级要粗一个级别
  * lighter：相对父级来说，比父级细一个级别

* 100-900 整除100的整数：
  * 浏览器只支持 细 粗 正常3个 
    * 100-300 是细
    * 400-500 正常
    * 600-900 加粗

##### font合写

* font-style    font-weight   font-size/line-height    font-famliy
  * font合写必须要书写 font-size 和font-famliy  否则合写不生效
  * font合写其实在实际项目中使用的很少，一般我们要分开设置

#### CSS文本类样式

