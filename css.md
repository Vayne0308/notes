CSS介绍

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

##### line-height：行高(继承)

* 用来控制行高，一行文的高度。规范来说就是两行文字基线之间的距离

* line-height和内联元素连接非常紧密，行高直接决定了内联元素占用的高度（不包括替换元素）

* 值：(不支持负值)
  * ·normal：执行浏览器默认值，在各个浏览器中不同，并且还受字体的影响
  * 数字：没有单位，比如1.5  就是当前元素文字大小的1.5倍
  * 百分比：也是相对于当前元素的文字大小计算的，很少使用
  * 长度：带单位，直接设置行高

* 行距与半行距
  * 行距是上边一行文字的底线和下边一行文字的顶线之间的距离
  * 半行距 就是行距的一半; 让行高减去一行文字的高度，得到的值除以2，就是半行距
  * 一行文字的上边和下边分别是两个半行距
  * 半行距高度*2 + 文字的字号  = 行高

* 使用line-height对**单行文字**（也可以是**内联元素**）做垂直居中

* em方框：对于一个字，用户代理先生成一个方框（即em框），这个框有底线，基线，中线和顶线四个构成

>* 对于span换行来说，设置display为inline-block 再设置vertical-align:middle，垂直居中才生效
>
>```
>span{
>    line-height: 1.2;
>    display: inline-block;   /*将元素设置为行内块*/
>    vertical-align: middle;  /*让元素自身的中线进行lineheight对齐*/
>}
>```

##### vertical-align:水平对齐

* 默认情况下，在一个行框中，所有内容都是基线对齐

* 但是图片没有基线，所以就把图片的底部当成了基线对了（幽灵空白）

* vertical-align 可以设置让一个元素以自身的哪一个位置对齐

* 值：
  * baseline 基线对齐
  * top  让元素顶部与整行的顶部对齐
  * bottom 让元素底部与整行的底部对齐

> 图片在父级垂直居中

````
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>让图片在父级垂直居中</title>
    <style>
        .box{
            height: 500px;
            background-color: red;
            line-height: 500px;
        }
        .box img{
            height: 200px;
            vertical-align: middle;

        }
    </style>
</head>
<body>
<div class="box">
    <img src="../images/05.jpg" alt="">
</div>
</body>
</html>
````

> 去除图片默认间隙
>
> * 因为图片底部默认和行框的文字基线对齐，所以图片和行框底部有一定的间隙
> * 就算行框只有一个图片，间隙也存在。是因为在当前行框内，如果存在一个行内块元素的时候，就会渲染一个看不见摸不着的节点。这个节点拥有当前元素的字号大小，行高等信息。这个节点被称作为“幽灵空白节点”
> * 去除间隙的方法：

    1、  display:block;
        图片底部能够和文字的基线对齐，是因为图片默认的vertical-align为baseline
        但是verticle-align这个属性只有行内元素和行内块元素支持，块级元素是失效的
        所以将img设置为块元素属性 就可以不用基线对齐了
        也可以理解为：因为改成块，解决了幽灵空白节点的问题
        并且没有元素和他在个行框
    2、设置verticle-align不为baseline 比如 top bottom middle都可以
    3、空白是文字有字号大小，撑开了当前的em方框
    	直接让字号大小变成0，文字就没有大小了，也就是幽灵空白节点文字大小变成0了，也不会撑开间隙了
    	主要针对于没有文字的行框
    4、改变文字的高度  
    	文字的高度可以由line-height来控制
       	让line-height：0 也可以解决问题
    5、浮动

##### text-decoration：文本修饰（不继承）

* 虽然不继承，但是延伸到后代元素，因为后代元素属于这个元素的下划线范围

* none：取消下划线
* underline:下划线
* overline:上划线
* line-through：删除线
* text-decoration其实是一个简写的属性
  * text-decoration-line：上划线 下划线 删除线
  * text-decoration-color：颜色
  * text-decoration-style：实线solid  虚线dashed 点线dotted 波浪线wavy

##### text-indent：首行文本缩进
* 单位是px ：缩进的像素 ，固定的单位，字号大小改变 还需要重新书写px

* em单位：  em是一个相对单位，1em=当前文字的字号大小  如果缩进两个文字 那么2em

* 只针对块级元素生效

#####  text-align : 水平对齐(继承)

* 规定行内的内容如何相对于它的块级父元素水平方向对齐
* 并不是控制元素自己的对齐，只是控制它里边的行内容水平方向对齐
* 对齐方式：
  * left：默认 左对齐
  *  center：居中
  *  right：右对齐

* text-align:justify  两端对齐
  * 两端对齐只针对于英文等字母语言 其他语言无效
  * 英文在一行书写的时候，最后位置可能放不下一整个单词，那么整体的单词就会换行
  * 导致每一行文本末尾参差不齐，所以需要两端对齐

###### 字符和词间距：

>* 在html中，英文数字的组合,只要没有空格都会被当做是一个单词;
>
>​    在汉字中，虽然不会把多个汉字连在一起当做是一个单词
>
>​    但是仍然词间距的时候 ，只改变空格隔开的间距
>
>* letter-spacing:控制字符间距
>* word-spacing:控制词间距

###### 最小宽度/最小高度

> 当浏览器缩小窗口，生成横向滚动条的时候，元素设置width：100%的宽度  是屏幕的宽度，当滑动横向滚动条的时候，这个元素的宽度没有达到主要内容1000px的要求，所以可以给该元素设置最小宽度  min-width：1000px

#### CSS背景类设置

###### 背景颜色设置：

* background-color:颜色值（和color的颜色一致 十六进制 rgba hsl 颜色单词）

###### 背景图的设置：

* 背景图路径：
  * background-image:url(路径) 背景图引入后 默认原点在元素的左上角
  * 在html中，由左至右 是x轴方向    由上至下 是y轴方向  x和y的交叉是原点
* 背景图定位：
  * background-position：x轴方向位置  y轴方向位置
  * 值的写法：
    * px
    * 百分比  百分比是参照于 容器的总宽度-图片的总宽度
    * 其他写法：
      * x：center left right
      * y: center top  bottom

* 背景图平铺方式：
  * background-repeat:控制背景图片是否平铺
    * no-repeat：不平铺
    * repeat：x和y都平铺（默认）
    * repeat-x：只有x轴平铺
    * repeat-y：只有y轴平铺

* 背景图的合写（一般我们都使用合写）
  * background：color    image     position     repeat；
  * 都可以进行省略

#### CSS其他样式的设置

###### overflow属性：
* 元素超出父级，不会影响父级的兄弟元素位置
* overflow属性定义一个内容太大无法适应容器的时候应该怎么做
* 设置给被超出的元素
  * visible：默认，内容不会被修剪，而是显示在元素的框外
  * hidden:超出内容被修剪，修剪掉的内容不可见，并且没有滚动条
  * scroll：超出内容被修剪，浏览器显示滚动条方便查看被修剪的内容
  * auto：浏览器定夺，如果内容超出就生成滚动掉，否则不生成

* overflow：auto和scroll的区别：
  * auto:是自动生成滚动条，不超出不生成 超出才生成
  *  scroll：无论是否超出都会生成滚动条

* overflow-x，overflow-y：只控制x和y的超出情况

######  visibility属性：

* 控制元素显示或者隐藏

* hidden:控制元素隐藏
  * 保留原来的位置，其他元素的布局没有发生改变
  * 相当于此元素变透明
  * visibility属性是继承的，里边的子元素也全部都继承属性，并且隐藏了
  * 如果给子元素设置visible覆盖，那么子元素可以进行显示

* visible：让visibility：hidden隐藏的元素显示

######  display属性：

* 指定了元素的显示类型，包含两种基础特征，用于规定元素生成什么样子的盒模型
  * 外部显示类型：定义元素怎么样参加流体布局
  * 内部显示类型：定义了元素内 子元素的布局方式

*  block：让元素以块标签属性显示（block-block）
*  inline：让元素以行元素属性显示（inline-inline）
*  inline-block：让元素以行内块的属性显示
  * inline控制行内显示
  * block控制可以设置宽高
*  none: 让元素隐藏，包含子孙元素全部隐藏，并且不会占用任何位置，在DOM也访问不到可视化宽高（就算设置了宽高，使用js的offsetWidth和offsetHeight都获取不到宽高）

* display和visibility隐藏的区别：

  ```
  1、visibility可以继承，子元素是因为继承了才隐藏,可以覆盖继承，子元素即可显示
  	display不能被继承，而是直接带着所有内部元素直接隐藏
  2、visibility隐藏，原来空间仍然保留
  	display隐藏，原来空间消失被占用
  3、js可以获取到visibility隐藏元素的可视化宽高
  	js不可以获取到display隐藏元素的可视化宽高
  ```

###### opacity透明度：

* 指定了一个元素的透明度
* 当opacity作用在某一个元素上的时候，把这个元素和里边的内容当成一个整体看待
* 即使里边的元素没有继承opacity。它也和父级有一样的透明度

* opacity的取值是 1-0

  * 1代表完全不透明
  * 0代表完全透明

* opacity和rgba和hsla透明的区别：

  ````    
  1、rgba和hsla只是一个颜色，是属性的取值，比如color  background-color，所以只是对颜色的一个处理
  2、opacity是一个属性，透明是直接设置给元素的，并不会对元素的某部分进行控制
  ````

## 盒子模型

####  盒子模型的概念：

* 在html中，把每一个元素都当做成一个盒子，拥有盒子的平面外形和空间
* 盒模型由内容（content）+内边距（padding）+边框（border）+外边距（margin）4部分构成
  * 内容区域：你书写的内容或者子元素能够显示的区域
  * 内边距：撑开内容与边框的距离
  * 边框：元素的边框
  * 外边距：撑开元素和其他元素之间的距离

   ####  盒子模型-内容区域（在标准盒子模型下）：
* 标准盒子模型下设置的width和height都是content（内容）区域的宽高

    width：默认是auto。auto分为4种情况：
        1.fill-available：充分利用可使用空间（块标签）
        2.fit-content:收缩到合适（浮动，定位）
        3.min-content:收缩到最小（表格中常见）
        4.max-content:超出容器限制（英文单词较长，或者设置了不换行，就会超出容器限制）


    height：
    	auto：其高度由内部元素堆叠而成，也就是内部元素撑起来的
#### 盒子模型-外边距（在标准盒子模型下）：

* 设置一个元素外边距的宽度。外边距可以理解为当前元素与父级或其他兄弟级元素的距离。
* 值可以是一个px单位，也可以是一个百分比

* margin分4个方向
  * margin-left、margin-right、margin-top、margin-bottom
  * 每个方向的值都可以单独的设置
  * margin-left、margin-top是让自身元素靠右 靠下
  * margin-bottom、margin-right是让其他元素 靠右  靠下

* margin的简写：
  * margin后跟4个值： 分别代表  上 右  下  左
  * margin后跟3个值： 分别代表  上   左右   下
  * margin后跟2个值： 分别代表  上下     左右
  * margin后跟1个值： 分别代表  上下左右
  * 当右边不要  左边出现auto 剩余空间就会直接给左边

* margin: 0 auto居中:

  ```
  在正常的布局中，块级元素具有满屏的属性，也就是在水平方向上占满父级的宽度
  满屏以后，内部元素的内容+内边距+边框+外边距 刚好是等于父级的内容区域的大小
  所以当水平方向上的 宽度 边框 内边距都是固定值的时候
  在水平方向上margin设置auto的时候，默认左右平分剩余空间，达到水平居中效果
  ```

  >垂直方向上的 margin ： auto 0 为什么不行？
  >
  >相对于水平方向来说，块元素在垂直方向上并没有满屏的属性，margin默认在上下的值都是0
  >
  >无论是否设置垂直方向的auto，表现出来的都是元素多高就占用多少，并没有剩余空间去平分            

* margin的父级塌陷：
  * 当一个父级中第一个元素的margin-top会塌陷给父级，最后一个元素的margin-bottom会塌陷给父级
  * 防止父级和其他元素之间的间隙过大，当第一个和最后一个子元素的margn塌陷给父级以后，父级就可以和兄弟元素在垂直方向上进行叠加
  * 避免父级塌陷：
    * 给父级设置一个边框  边框的宽度不能为0。防止影响视觉，可以设置透明（transparent）颜色
  * 开启BFC（块级格式化上下文）

* margin对元素的影响和支持性：（margin都为正值的时候）

  * 对块标签/行内块而言

    ```
    margin-left：元素右移动
    margin-top：元素下移动
    margin-right：如果右边有元素  后边的元素右移动
    margin-bottom：如果下边有元素  后边的元素下移动
    margin垂直方向叠加,父级塌陷
    ```

  * 对行标签

    ```
    margin在垂直方向上不生效
    水平方向:
        margin-left：元素右移动
        margin-right：如果右边有元素  后边的元素右移动
    ```

* 负margin的基础用法

  * margin-left为负：

    ```
    元素向左移动，并且原来的位置不保留（后边元素会紧跟上一起移动），
    元素向左移动，并不会挤到前边的兄弟元素，而是覆盖前边的兄弟元素
    ```

  * margin-right为负：

    ```
    元素视觉大小不发生变化
    但是元素实际所占用的空间变小，后边元素会跟上来 或者是撑不开父级宽度
    假如元素width为100px  设置marginright为-20  元素实际大小是80px
    ```

  * margin-top为负：

    ```
    元素向上移动，并且原来的位置不保留（下边元素会紧跟上一起移动），
    元素向上移动，并不会挤到上边的兄弟元素，而是覆盖上边的兄弟元素
    ```

  * margin-bottom为负：

    ```
    元素视觉大小不发生变化
    但是元素实际所占用的空间变小，下边元素会跟上来 或者是撑不开父级高度
    假如元素height为100px  设置marginbottom为-20  元素实际大小是80px
    ```

#### 盒子模型-边框（在标准盒子模型下）：

* border-width:边框宽度
* border-style:边框样式  solid 实现   dashed  虚线    dotted  点线
* border-color：边框颜色

* 合写：border：border-width  border-style border-color     
* 注意：

  * 边框是在margin里边
  * 背景颜色在边框中显示（实线的时候，我们看不到）
  * 背景图片原点没有从边框开始  而是从padding开始的，但是可能会平铺到边框中

* 边框画三角形

      原理：当内容非常小的时候，
        上下左右边框重合，重合部分就会平分为两半，
        这个时候，整个边框就分为了4个三角形 
     <style>
         .box{
         width: 0;
         height: 0;
         border: 100px solid #000;
         border-top-color: transparent;
         border-bottom-color: #ff8d9e;
         border-left-color: transparent;
         border-right-color:transparent;
  
        transform: rotate(0deg);
        }
     </style>
#### 盒子模型-内边距（在标准盒子模型下）：

* padding的写法和margin基本一摸一样

* padding主要撑开内容之间的距离

* 背景颜色可以显示在padding中，也可以显示在border中

* 背景图片的原点，其实默认在 padding的左上角

* padding的支持性：
  *  块标签：四个方向都支持
  * 行标签：
    * 水平方向直接支持
    * 垂直方向也支持设置，但是不能撑开元素的距离
  * padding不支持负值
  * padding也不去设置auto 不支持

* padding作用可以扩大点击区域

>padding和margin的使用场景:
>
>​	padding：撑开内容与边框的距离 padding中会显示背景颜色和背景图片
>
>​	margin：撑开元素之间距离
>
>日常使用过程中，可以按照下边方式来使用：
>
>padding和margin都可以撑开元素之间的距离。
>
>​	padding主要用来撑开父子之间的距离
>
>​	margin主要用来撑开兄弟之间的距离

####  怪异盒模型：

* 元素所占用的空间大小为：内容（content+padding+border）+外边距（margin）

* 怪异盒模型设置的width是 content+padding+border整体的宽度

* 将一个元素设置盒模型显示
  * box-sizing属性：
    * content-box:标准盒模型
    *  border-box:怪异盒模型

>1、在html中，把每一个元素都当做成一个盒子，拥有盒子的平面外形和空间
>
>2、盒子模型由 内容（content）、内边距（padding）、边框（border）、外边距（margin）四个构成
>
>3、盒子模型分为怪异盒子模型和标准盒子模型
>
>4、标准盒子模型的所占用空间的计算方式是 content+padding+border+margin
>
>​      怪异盒子模型所占的的空间计算方式是 content+margin（content内容是包含内容内边距和边框的）
>
>5、使用box-sizing属性可以切换盒子模型的方式

## 浮动

*  浮动的概念：让元素脱离文档流，按照指定的方向发生移动，遇到父级的边界或者是上一个浮动元素或者是上一个不浮动兄弟元素就停下来

* 高度塌陷：浮动元素以后，脱离父级内容区域，父级没有内容撑开自身的高度

  ​                    父级的兄弟元素是 按照父级的位置进行布局的，所以页面会乱掉

* 浮动对元素的影响:

  * 块标签：

    ```
    不再独占一行
    仍然可以设置宽和高
    构成了BFC，不再进行父级塌陷
    完美支持margin和padding
    ```

  * 行标签：

    ```
    可以设置宽高
    完美支持padding和margin
    ```

* 浮动元素 不会超过自己的上一个不浮动兄弟元素
* 浮动元素 不出超出父级容器
* 浮动元素在父级的content-box中进行浮动

* 清除浮动的方法：
  * 清除浮动：清除浮动不是不让元素浮动，而是清除浮动对父级带来的影响

  ```
1、给浮动元素的父级设置高度height（不推荐使用）
	缺点：很多情况下 高度都是不缺定的  所有不适用
2、以浮制浮，给浮动元素的父元素设置浮动，原理是开启BFC（不推荐使用）
	缺点：只有在父级需要浮动的时候，可以这么清除，否则父级的浮动会影响布局
3、overflow：hidden；给父级设置，原理也是开启BFC（可以使用）
	优点：简单快捷
	缺点：元素超出的时候，会隐藏超出部分
4、br清除浮动：在浮动元素的后边书写一个br。br中书写clear属性，值为both
	缺点：增加不必要的元素，不符合样式与结构相分离的要求
5、clear清浮动法：给浮动元素的下边添加一个块元素，书写样式clear:both
	缺点：增加额外的结构，不符合语义化标准
6、after伪元素清浮动（推荐）
	可以给所有浮动元素的父级一个  clearFix的类名
	当一个元素需要清除浮动的时候  直接设置clearFix类名即可
    .clearFix:after{
        content:"\200B";  必须拥有content属性   内容为空
        display: block;   必须块标签才能清浮动
        height: 0;          高度为0 不占用空间
        clear: both;        清除浮动
    }
    .clearFix{  //兼容ie
        *zoom:1;    //*是css  hack 只有ie6.7 认识
        ie6、7 不支持伪元素，所以需要开启元素的haslayout来清除浮动
    }              
  ```





##　ps切图简单操作

```
 1、ctrl+h  去除辅助线
 2、在工具栏第五个右键 选择切片工具（以后可以使用快捷键c）
 3、按住alt  滑动滚轮可以放大缩小图片
 4、按住空格  可以进行拖拽图片

切图：
    png的图 首先要去掉其他的图层才能切除透明图
        1、选择工具栏 第一个移动工具
        2、按住alt键  在你要选择的图片上右键
        3、右边的图层工具栏 会自动跳到当前的图层选项
        4、按住alt键 点击你选择图层的眼睛 进行反选关闭其他图层
        5、使用切片工具进行对图片选中（精确）
        6、切图并保存：ctrl+shift+alt+s 一起按  弹出保存窗口
        7、如果是png 则在预设中选择png24  如果是jpg  则选择 jpeg高
        8、点击存储
        9、更改名字  选择选中的切片
        10、保存路径在桌面
        11、保存以后在桌面上会新建一个images的文件夹，里边放的是你的切图

    切图完成后：选择历史记录 返回最原始图片


    选择颜色 使用吸管（快捷键 i）
    选择文字 使用文字工具 （快捷键 t）
```

## 定位

* 除非专门指定，否则所有框都在普通流中定位。也就是说，普通流中的元素的位置由元素在 HTML 中的位置决定。

* 定位的基本思想很简单，它允许你定义元素框相对于其正常位置应该出现的位置，或者相对于父元素甚至浏览器窗口本身的位置

* 通过使用 position 属性，我们可以选择 4 种不同类型的定位

  * position属性是把元素放置到一个静态的、相对的、绝对的、或固定的位置中

  * position属性的四个值分别对应static、relative、absolute、fixed

  * left、right、top、bottom

    * 单位为 px 或 百分比都可以

      ```
      left 和 right 的百分比相对于参考物的width
      top和botton的百分比是相对于参考物的height
      无论任何方向的padding或margin都是参照元素的width来计算的
      ```

    * left 和 right 同时设置时只有left有效

    * top 和bottom一起设置时只有top有效

#### position:relative：让元素相对定位

* 元素先放置在未添加定位时候的区域，然后再不改变页面布局的情况下：

  * 其他元素没有受到任何影响
  * 自身原来的位置也保留
  * 和浮动可以一起使用

  ```
  left:   设置元素 左边缘 到 原来左边缘位置 的距离
  right:   设置元素 右边缘 到 原来右边缘位置 的距离
  top:   设置元素 上边缘 到 原来上边缘位置 的距离
  bottom:   设置元素 下边缘 到 原来下边缘位置 的距离
  在相对定位中：left为正 元素向右走
  在相对定位中：top为正 元素向下走
  ```

#### position:absolute：绝对定位

* 绝对定位的元素 相对于它的包含块进行定位

* 不预留任何的空间（脱离页面流）

* 通过指定当前元素 相对于其包含块偏移的量 来确定当前元素的位置

* 绝对定位以后，浮动失效。margin padding仍然可以使用

  * left: 0;：让定位元素的左边距离包含块左边为0
  * top: 0：让定位元素的上边距离包含块上边为0

  ```
  包含块：
  如何确定一个元素的包含块，完全取决于它自身的position属性：
      1、如果一个元素自身的position属性是 static或者是relative：
      	它的包含块就是离他最近的祖先元素或者是格式化上下文。
      2、如果一个元素自身的position属性是absolute，
      	它的包含块就是离他最近的 拥有定位属性（值不为static）的元素
      3、如果一个元素自身的position属性是fixed
      	它的包含块就是viewport（视口）
      4、补充：如果一个元素的position属性是absolute 或者是 fixed 在下边几种情况下，
      	包含块会发生改变
          ①当祖先元素的 拥有 transform 或 perspective 属性 并且值不为none的时候
              它也是被当做包含块
          ②当祖先元素 拥有filter属性的时候（值不为none）  它也可以被当做包含块
      5、如果由内向外找不到包含块条件的元素，那么html（根元素）被称作为初始包含块    
  ```

 #### position:fixed：固定定位
* 不为元素预留空间（脱离页面流）
* 相对于视口（viewport）的位置来定位元素的
* 滚动页面滚动条的时候，视口不发生改变，元素位置也不会改变

 ## z-index属性

* 指定了一个定位属性的元素 及其后代 的层叠顺序
* 只有**定位元素**（非static值）拥有 z-index属性
* z-index的值没有单位  理论上来说 z-index的值大的元素 会覆盖小的元素
* 定位元素默认的z-index 的值 是  auto
* 如果一个拥有z-index属性的定位元素中 子元素也设置了z-index

​                那么子元素会重新创建一个层叠上下文，子元素的z-index只能在当前的层叠上下文中对比排列

* 元素层叠顺序：

​       z-index为负<background<border<块级元素<浮动元素<内联元素<没有设置z-index的定位元素<z-index为正

>如果想让一个元素拥有z-index属性，并且还不想影响它的其他正常布局，
>
>我们可以给这个元素一个 position：relative;

## a标签的4个伪类

####  link：当有链接属性时

####  visited：当连接被访问过以后

####  hover：当连接被鼠标悬浮的时候

####  active：当连接在激活状态的时候

    位置不能互换：
        这4个选择器 优先级是一样的。
        顺序改变就可能后边覆盖前边的
        比如visited写在最后，那么当连接北方问过后，访问过后的颜色就会覆盖hover和active
    
        记忆：爱恨法则   love-hate

> ！！！hover适用于多数其他元素，并且伪元素也可以使用               

## 精灵图（雪碧图、css sprites）

* 是一种网页图片的应用处理方式，允许将一个页面中很多零星的小图片包含到一张大图中去，当访问页面的时候，就不会一张张的去请求显示图片
* 对于当前的网络来说，小于200k的文件加载速度是一样的
* 通过background-position属性 将图片定位到需要的位置即可

    优点：
        1、减少图片大小
        2、减少服务器请求次数
## 伪元素

* 可以理解为“虚假的元素”，
* 他们虽然会在内容元素的前后插入额外的元素，但并不会在文档中生成，在文档的源代码当中并不能够找到它们
* 虽然在结构上是虚假元素，但是在表现上和普通元素没有什么区别，能为它们添加任何样式，比如改变文字颜色、添加背景、调整字体大小等等

* 伪元素必须拥有content属性 ，才能生效

* 伪元素默认是一个行内元素

* 伪元素对其他属性基本都是支持的

  - after:在当前元素的最后边插入一个伪元素
  - before：在当前元素的最前边插入一个伪元素

  ```
  .box:before{
  	content:"hahahah";
  }
  ```

  * first-letter伪元素：把一个块级元素的第一个文字选中，可以单独进行控制
  *  first-line伪元素：把一个块级元素的第一行选中，单独进行控制

  ```
  p:first-letter{
      font-size: 30px;
      color: #fff;
  }
  p:first-line{
      font-size: 24px;
      color: yellow;
  }
  ```

## css hack

由于不同的厂商的浏览器，或者是同一个浏览器不同的版本（ie），对css的解析和认识不完全一样，可能会导致不同浏览器显示的效果不相同，那么我们需要针对某个浏览器，去写不同的样式，让代码能够兼容所有的浏览器

 比如：

* after伪元素清浮动，只有ie8及以上支持，所以要针对ie6、7书写一个开启haslayout

* *代表ie6,7  zoom代表开启haslayout  所以可以书写  *zoom：1；

​                那么这个代码只有ie 6 7 认识

* 为什么使用css hack
  * 第一种理解：让我们css 的代码兼容不同的浏览器
  * 第二种理解：我们可以为不同的浏览器定制不同的样式

## 粘连布局

* 又称作  stick footer布局

  * 如果页面不够长的话  footer粘在视窗的底部
  *  如果页面内容长度超出，footer就会被页面向下推送出去

  ```
  方法1：
      给inner最小高度是 100%
      让footer给margin-top：-50 上去  （main元素和footer重叠）
      给main元素一个padding-bottom 50px   就算重叠  文字也显示不到padding中
  ```

  ```
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>粘连布局</title>
      <meta name="viewport" content="width=device-width,initial-scale=1">
      <style>
          *{
              margin: 0;
              padding: 0;
          }
          html,body{
              height: 100%;
          }
          .outer{
              height: 100%;
          }
          .inner{
              min-height: 100%;
          }
          .main{
              padding-bottom: 50px;
          }
          footer{
              height: 50px;
              background-color: #5ab3f4;
              margin-top: -50px;
          }
      </style>
  </head>
  <body>
      <div class="outer">
          <div class="inner">
              <div class="main">
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
              </div>
          </div>
          <footer></footer>
      </div>
  </body>
  </html>
  ```

  ```
  方法二：
      给inner设置最小高度是100%
      给inner设置padding-bottom是50px
      给inner设置为 怪异盒子模型：box-sizing：border-box
      让footermargin-top为负 上来
  ```

  ```
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>粘连布局</title>
      <meta name="viewport" content="width=device-width,initial-scale=1">
      <style>
          *{
              margin: 0;
              padding: 0;
          }
          html,body{
              height: 100%;
          }
          .outer{
              height: 100%;
          }
          .inner{
              min-height: 100%;
              padding-bottom: 50px;
              /*设置为怪异盒子模型的方式：
              高度就包含了padding  总共加起来是百分百  并且main不会显示在inner的padding中*/
              box-sizing: border-box;
          }
          .main{
  
          }
          footer{
              height: 50px;
              background-color: #5ab3f4;
              margin-top: -50px;
          }
      </style>
  </head>
  <body>
      <div class="outer">
          <div class="inner">
              <div class="main">
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
              </div>
          </div>
          <footer></footer>
      </div>
  </body>
  </html>
  ```

  ```
   粘连布局方法3：
       直接计算inner的最小盖度是  100% - 50px
       footer在main元素小的时候，刚好跟着inner  在最下边。否则就被inner撑下去
  ```

  ```
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>粘连布局</title>
      <meta name="viewport" content="width=device-width,initial-scale=1">
      <style>
          *{
              margin: 0;
              padding: 0;
          }
          html,body{
              height: 100%;
          }
          .outer{
              height: 100%;
          }
          .inner{
              min-height: calc(100% - 50px);
          }
          .main{
  
          }
          footer{
              height: 50px;
              background-color: #5ab3f4;
          }
      </style>
  </head>
  <body>
      <div class="outer">
          <div class="inner">
              <div class="main">
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
                  main区域 <br>
              </div>
          </div>
          <footer></footer>
      </div>
  </body>
  </html>
  ```

  >calc方法：calc()
  >        我们可以把它当做一个函数，其实他是calculate（计算）缩写。
  >        是css3提供的一个新功能，主要用来计算长度
  >        我们可以用它来给padding  margin width height font-size等等计算大小值 值是一个动态的
  >
  >
  >    1、使用+ - * /进行运算
  >    2、可以使用百分比  px  em  rem等单位
  >    3、可以单位混合计算
  >    4、在使用的时候，尽量在 +  -  * / 前后添加一个空格

## 样式重置（css reset）

* 将html的默认样式全部去掉，需要的时候我们自行添加。
* 统一页面风格
* 为什么是使用样式重置：

    1、多数元素拥有自己的默认样式，并且我们很多都不需要
    2、默认样式在不同浏览器中呈现的也不一定相同，就会导致浏览器展示页面不相同的现象
    3、整个页面中 固定的风格代码，可以在样式重置中直接书写，不用每一个都设置

* 为什么不适用 *{margin：0；padding:0;}


    1、样式重置简单，不够完整  一些demo可以使用，真正项目不推荐使用，请使用css reset
    2、* 通配符 匹配所有的标签，影响很大 效率很低


    normalize.css是什么？
       	normalize觉得，存在即合理。保留了应该存在的默认样式，并且把每一个默认样式在浏览器中中统一了
    normalize和reset的对比：
        1、保护了有用的默认样式，不像reset那样全部去掉
        2、修复浏览器自身的bug，保证了默认样式在浏览器中的一致性
        3、拥有详细的文档
        4、模块化 被拆分成多个模块  我们可以在当前项目中移除 永远不会使用的模块
        5、优化css效果
## 空元素和替换元素

#### 空元素

* 在html中 ，一个不可能存在子节点（注释节点，文本节点，元素节点）的元素就叫做空元素

* 通常在空元素上使用 闭合标签 是无效的

  ​        <input type="text"></input> =======>闭合标签无效

* 如：br、hr、img、input、link、meta、source

#### 替换元素

* 浏览器根据元素的标签和属性，来决定元素具体显示的内容

* 如：img、input、textarea、select、video、iframe是替换元素

​        audio、canvas标签在某些时候也是替换元素

## BFC：（Block Formatting Content）

* 块级格式化上下文
              是页面可视化css渲染的一部分，是块盒子布局的一块区域
              这个区域是相对外界独立的
* 构成BFC的条件：
          1、根元素（html）
          2、浮动元素（float属性不是none的）
          3、绝对定位和固定定位元素（position属性s是fixed 和 absolute的时候）
          4、行内块标签（display属性是inline-block）
          5、overflow属性不是visible的时候
          6、display其他属性（flex、gird、flow-root、table-cell、table-caption、table、table-row、table-row-group、table-header-group、table-footer-group）
* BFC主要解决的问题：
      1、清除浮动：BFC区域的高度计算会把浮动元素计算在内
      2、解决父级塌陷：BFC构成独立的区域，里外的元素应该互补影响
      3、识别浮动的兄弟元素



