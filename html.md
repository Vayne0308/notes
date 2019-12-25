## HTML
#### HTML基础
* HTML（hypertext Markup Language）超文本标记语言
* 负责网页的三要素中的结构
* html使用标签的形式来标识网页中的不同组成部分
* 一个最基本的HTML页面
```
<!DOcTYPE html>
<!--DOCTYPE（document type）： 文档类型
版本声明，声明版本是html5。
给浏览器声明，告诉浏览器应该按照html5的规范来解析当前的文档。
若不声明，那么按照什么规范解析，就看浏览器心情，可能会导致浏览器进入怪异模式，从而导致页面无法正常显示
<!DOCTYPE html> 不是html标签，他只是一条浏览器的指令，在所有版本中，这条指令对大小写都不敏感-->
<html lang="en">
<!--lang是语言  en是英语  告诉浏览器本网页是英文网页  ch是中文-->
<!--lang是html的属性   en是lang属性的值-->

<!--HTML 标记标签通常被称为 HTML 标签 (HTML tag)-->
<!--html标签是网页结构的最外层 里边包含两个标签  body 和 head -->
<head>
    <!--head代表网页的头部，不会显示网页中，只要包含网页的元信息，标题，引入外部文件等等-->
    <meta charset="UTF-8">
    <!--meta标签是控制网页的元信息
    元信息就是信息的信息（关于当前网页的信息）
    charset代表字符编码，utf-8是万国码-->
    <title>html的编码结构</title>
    <!--title是网页的标题-->
</head>
<body>
    <!--在html中，所有我们能够看到的内容全部书写在body中-->
</body>
</html>
```
#### HTML标签
##### 块标签
* 独占一行 换行显示
* 可以设置宽高
* 块标签可以嵌套块标签和行标签（p标签、h标签都只能嵌套行标签）
>###### div标签
>* 没有任何具体的含义，主要用于网页的布局
>* 通过一个一个的div将页面划分为不同的部分，之后在针对部分进行开发
>###### 标题标签（h标签）
>* 在HTML中，一共有六级标签（h1-h6），在显示效果上h1最大，h6最小，默认加粗并且有一点间隙
>* h1标签最重要，表示网页中主要的内容，一个页面中只能写一个h1标签，h1经常用在网页的标题或者是logo上
>###### 段落标签（p标签）
>* p标记中的文字默认会独占一行，并且段与段之间会有一定间距
>* 在HTML中字符间写再多的空格，浏览器只会当成一个空格解析，换行也会当成一个空格解析
>* 页面中使用br标签来表示一个换行，它是一个单标签，也是一个空元素，另外hr标签可以在页面生成一条水平线
>###### ol标签
>* 表示多个有序的列表项，显示出是带有编号的列表
>* ol元素前边的编号可以是任何的形式,我们可以通过css的list-style-type属性控制 
>###### ul元素
>* 表示多个无序的列表项,显示出是带有项目符号列表 
>* ul元素前边的符号可以是任何的形式,我们可以通过css的list-style-type属性控制
>* 无论是ol还是ul 里边的每一项都是一个li标签
>###### dl dt dd组合标签
>* dl是包含术语和对术语描述的列表，通常用来展示词汇表或者是对内容的解释
>* dl是定义的列表的外层包裹
>* dt是被解释的 术语
>* dd是解释的内容
>* dt和dd是兄弟关系，父元素只能是dl;dl的子元素只能是 dt和dd
##### 行标签
* 行内显示 超出换行
* 不能设置宽和高
* 行标签只能嵌套行标签，不能嵌套块标签（a标签可以包含任意标签，除自身外）
>###### span标签：
>* 没有任何特殊的含义
>* 主要是为了增加额外的结构，方便我们控制样式或者是数据
>* 使用要求：在其他语义化标签不适用的情况下再使用
>###### b i u 标签
>* b标签呈现加粗状态
>* i标签呈现倾斜状态
>* u标签呈现下划线状态
>* 这三个标签是吸引读者到需要注意的内容上，这些仅仅是添加了一些样式而已，只是表现层，尽管如此，我们也不必为了加粗倾斜等元素 而去使用b i u等标签，替代的方法是使用css
>* 在目前使用最多的是i标签-通常在开发过程中，小图标之类的元素我们习惯用i标签来表示
>###### em strong var 标签
>* em标签：强调作用，标出用户着重需要阅读的内容，但是主要也给SEO（搜索引擎优化）强调，呈现的是倾斜的状态
>* strong标签：强调（更强的强调）作用，表示文本十分重要，主要也给SEO（搜索引擎优化）强调，呈现的是一个加粗
>* var标签：并没有起到强调或提示用户注意的作用，默认倾斜
>###### a标签
>* a标签就是超链接，用来做跳转，可以创建通向其他网页、文件 同一个页面的位置、邮件地址或者其他url链接、链接电话、链接短信
>* a标签的href属性，用来写地址。如果是网络地址 需要些全http://或者https://协议；如果写本地地址，使用相对路径即可
>* title属性：是鼠标悬浮在a链接上的时候，对当前链接的提示信息，弹窗显示
>* target属性：_self:在当前标签页跳转；_blank:在新的标签页打开跳转
>* download属性：书写下载文件的路径，那么可以直接下载。但需要注意的是a标签必须书写href属性，哪怕为空都可以执行download下载，否则a标签不具有任何功能
>* 锚链接：在a标签的href中书写 #+名字；在相对应的跳转点标签书写id属性值为锚链接中的名字；这样点击锚链接就能跳转到相对应的位置
##### 行内块标签
* 既拥有块标签属性可以设置宽高，也拥有行属性的行内显示
* 可以设置宽高
* 行内显示
>###### img标签：
>* 单标签，属于替换元素(<img>\<br>都属于空元素)，代表文档中的一个图像
>* src属性：图片路径 可以书写网络路径地址 也可以书写本地相对路径
>* title属性：当鼠标悬浮在图像上的时候，对图像的解释
>* alt属性：
>   1、定义了描述图像的替换文本
>    2、网络错误，路径错误等等图片没有正确加载的时候显示
>    3、alt属性还和SEO相关，爬虫到当前页面，并不会读取图片，而是读取img的src属性来确定图片信息
>* width/height:
>   1、img标签除了能够使用css设置宽高以外，自身也拥有width和height属性，可以设置宽和高
>    2、如果说只设置了宽度或者高度，那么另外一个将按照图片比例进行缩放
>    3、自身的width/height是不书写单位的
>    4、如果宽度和高度都一起设置，图片的宽高比例可能会改变
>    5、当自身的宽高属性和css设置的冲突以后，css的优先级较高
>* 图片常见的格式：
>  1、jpeg（jpg）：一般图像(当图片不透明的时候，尽量选用jpg，因为jpg占用的大小比png小)
>  2、png：        透明图
>  3、gif：        动图
##### 表单标签
>###### form标签
>* 为用户创建html表单,表单可以向服务器发送数据,form标签中可以包含很多表单元素
>* action属性：
>   表单提交的地址
>* method属性：
>  表单提交的方式  数据传输的方式
>   常见的两种方式是: get和post
>  * get可以当成小汽车：数据少,数据直接在地址栏上显示（不安全）
>  * post可以当成大货车：数据多  数据发送相对于get安全一点
>
```
  <form action="http://www.baidu.com" method="get">
    <input type="submit" value="提交">
  </form>
```
>###### input标签
>* type类型的值不一样，呈现的状态也是不一样的
>* name属性就是给表单起一个名字（自己命名，一般是后台提供）
>* value属性就是表单的值，可以预定义，也可以等待用户输入name和value就构成了一个键值对，如果构不成一个键值对，就不会进行提交
>* type类型有以下几种：
>   * text：单行文本输入框（文本域）
>       * 没有长度和内容限制，只能输入一行，明文显示
>       * 表单提交都是以键值对的形式提交的  比如  user = xiaoming
>   * password：密码输入框
>       * 默认把输入的内容呈现出小黑点
>   * radio：单选框
>       * 书写name属性后，可以进行单选
>       * 应书写value值，是向后台提供的数据
>       * 在input前写的内容，和input没有任何关系，只不过让用户视觉上觉得有关联
>   * checkbox：多选框
>   * file: 上传文件按钮
>   * hidden：提交隐藏内容
>       * 在表单提交过程中有的数据需要提交，但是不需要用户输入或者是修改，那么直接使用隐藏域提交
>   * button: 单纯的按钮
>       * 没有任何作用和功能，只是长了按钮的样子
>       * 如果需要添加功能，可以使用js
>       * value值是按钮中的文字
>   * reset: 重置按钮
>       * 当重置按钮被点击，就会重置当前reset所在的表单，变成默认的状态
>   * submit：提交按钮
>       * input标签的type类型是submit代表提交  value是按钮显示的内容
>       * 提交按钮只会提交当前按钮所在的form表单中的内容
>       * 如果没有form标签，表单提交失效
```
<form action="http://www.baidu.com" method="get">
    请输入用户名：
    <input type="text" name="user" value="xiaoming">
    <br>

    请输入密码：
    <input type="password" name="pass" value="">
    <br>

    请选择性别：
    男：<input type="radio" name="sex" value="男">
    女：<input type="radio" name="sex" value="女">
    未知：<input type="radio" name="sex" value="未知">
    <br>

    选择你最喜欢的语言：
    PHP：<input type="checkbox" name="lang" value="PHP">
    JAVA：<input type="checkbox" name="lang" value="JAVA">
    JS：<input type="checkbox" name="lang" value="JS">
    HTML：<input type="checkbox" name="lang" value="HTML">
    <br>

    请上传你的照片：
    <input type="file" name="photo">
    <br>

    <input type="hidden" name="id" value="00000000001">

    <input type="button" value="点我啊" id="btn">

    <br>

    <input type="reset" value="重置啊">

    <input type="submit" value="提交">
</form>
<script>
    var oBtn = document.getElementById("btn");
    oBtn.onclick = function () {
        alert("hello world");
    }
</script>
```
>###### select&option 下拉列表
>* option代表列表的每一项
>   * 显示出来的值应该放在option标签中
>   * 提交的内容是放在option的value属性中
>* select是列表的外层
>   * 表单的name是在select中书写
>###### textarea 多行文本输入框
>* 右下角可以放大缩小
>* cols和rows用来控制宽和高
>   * cols代表一行有几个字符（一个汉字算两个字符）
>   * rows代表总共几行，超出是要生成滚动条的
>   * 我们很少这样控制，主要通过css的width和height控制
>* textarea没有value属性，输入的值直接就是textarea标签中的内容
```
<form action="###" method="get">
    请选择你喜欢的城市
    <select name="city" >
        <option value="北京">北京</option>
        <option value="上海">上海</option>
        <option value="深圳">深圳</option>
    </select>
    <br>
    请说出你对我们的留言：
    <textarea name="message" cols="30" rows="10" ></textarea>

    <input type="submit" value="提交">
</form>
```
>###### button标签
>* 使用场景可以在表单中提交、重置  也可以做单纯的按钮
>* button的type类型控制按钮是做什么的
>   * type：submit  默认 提交当前的表单
>   * type：reset 重置当前的表单
>   * type:button 单纯的按钮  没有任何功能
>* button和input做按钮的区别？
>   * input是单标签 不能嵌套任何元素
>   * button是双标签 双标签中可以嵌套其他元素
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>button</title>
</head>
<body>
    <form action="###" method="get">
        <input type="text" name="user" value="">

        <button type="button">点击我呀</button>
        <button type="button">
            <img src="../images/06.png" alt="">
        </button>
    </form>
</body>
</html>
```
>###### label标签                        
>* label元素：为表单元素定义标注（点击标注的信息，可以让表单元素获取焦点）
>   * 获取焦点：当表单元素变成一个可以输入的状态的时候，被称作为获取焦点
>   * 失去焦点：当表单元素失去可以输入状态的时候，被称作为失去焦点
>* 两种使用方法：
>   * label标签包含住标注元素，让label标签的for属性 和 相对应的表单元素的id属性 值相等
>   * label标签包住整个标注元素和相对应的表单元素,label不能出现for属性
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>button</title>
</head>
<body>
    <form action="###" method="get">
        <!--方法1-->
        <label for="user">请输入用户名：</label>
        <input type="text" name="user" value="" id="user">

        <!--方法2-->
        <label>
            男 <input type="radio">
        </label>

        <button type="submit">点击我呀</button>
    </form>
</body>
</html>
```
>* label元素：对select标签，只能获取焦点，但是不能把列表下拉出来
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>button</title>
</head>
<body>
    <form action="###" method="get">
        <label for="city">选择城市</label>
        <select name="city" id="city">
            <option value="北京">北京</option>
            <option value="上海">上海</option>
            <option value="广州">广州</option>
        </select>
        
        <label for="mes">留言</label>
        <textarea name="mes" id="mes" cols="30" rows="10"></textarea>
        <button type="submit">点击我呀</button>
    </form>
</body>
</html>
```
>###### tabel标签        
>* 表格书写：
>   * table是表格的最外层
>   * caption：表格的标题 一般写在表格的最上边
>   * tr就是表格的每一行
>   * th表示表头单元格  默认居中和加粗
>   * td表示普通单元格
>* 表格默认没有边框，宽度也是内容撑开的
>* table标签的属性：
>   * width：设置表格的宽度，每一列的内容都是自适应分配
>   * border：给表格设置边框  值为数字 代表外边框的宽度
>   * 表格的外层和单元格都设置上了边框，但是单元格的边框永远是1，外层边框是border属性的值
>   * border-collapse:collapse  css设置给border元素，用来合并边框
>   * cellpadding:设置单元格与内容之间的间隙
>   * cellspacing:设置单元格与单元格之间的距离(单元格不合并 才有效果)
>* 合并单元格：
>   * colspan:设置跨列，谁合并，给谁设置
>   * rowspan：设置跨行
>* 表格的优化：使用thead、tbody、tfoot标签包裹tr标签使其更具有语义化
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>table</title>
</head>
<body>
    <table width="400" border="1" style="border-collapse:collapse;" cellpadding="10" cellspacing="0">
        <caption>0225班就业表</caption>
        <tr>
            <th colspan="2">学生就业就业薪资</th>
            <th>备注</th>
        </tr>
        <tr>
            <td>小王</td>
            <td>12</td>
            <td></td>
        </tr>
        <tr>
            <td>老王</td>
            <td rowspan="2">13</td>
            <td></td>
        </tr>
        <tr>
            <td>王中王</td>
            <td></td>
        </tr>
        <tr>
            <td>大王</td>
            <td>15</td>
            <td></td>
        </tr>
    </table>
</body>
</html>
```
##### iframe标签
* 创建一个包含另外一个文档的内联框架，就是把其他的html页面嵌入到当前的页面中
* src是嵌入html的地址，可以是网络，也可以是本地服务器
* width和height属性来设置内联框架的宽高
* iframe拥有自己的DOM树，也有自己的会话历史记录，页面中的每一个iframe都会占用额外的计算机资源
* 为了性能，我们尽量少的去书写iframe
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset=UTF-8>
    <tItle>Title</tItle>
</head>
<body>
    <div>
        <h1>学习iframe标签</h1>
        <div>
            哈哈哈哈
            <iframe src="./05.table元素.html" width="300"></iframe>
            <iframe src="./05.table元素.html" width="300"></iframe>
        </div>
    </div>
</body>
</html>
```
##### H5新增语义化标签(结构标签)
>###### header标签
>* 用来定义文档（网页或者是某一个段落）的页眉（头部）
>* 可能包含一些标题元素，也可能包含其他元素，比如logo、搜索框、作者信息等等
>* 完成的网页或者是完整的块（网页的一个独立区域）是头部、内容、 尾部组成的（并不是强制）
>* header不是一个独立的分块，而是属于独立分块的头部
>* 整个页面没有header限制个数，可以使用多个
>###### footer标签
>*　footer标签代表一个网页或者章节内容的底部区域（页脚）
>*　footer通常包含章节的作者，版权数据和文章的其他链接
>*　其他和header同理，比如不是独立的区域，应该是隶属于一个章节或者是网页
>###### nav标签：
>* 目的：给文档提供导航列表
>* 导航可以分为：菜单、目录表、索引
>* 并不是所有的导航都需要用nav标签，只是当前页面中比较重要的热门的可以使用nav，比如在底部导航，就没有必要加入链接
>* 一个网页可能会有多个导航，比如整个网页的导航，也可以是某一块区域的导航
>* nav使用有两种方法：
>* 当nav中的导航列表是静态的，nav中直接嵌套a标签使用即可
>* 当nav中的导航是动态的（需要滑动查看更多，主要出现在移动端），nav中最好嵌套ul>li>a标签
>###### section标签
>* section是html中一个独立的区域，没有其他语义，一般会包含一个独立的标题
>* 假设有一个效果，上边是nav导航栏，导航栏一般对对应一个区域，用来显示这个导航到的内容，这个区域我们就可以使用section
>* section主要是对网页进行分块，也可以对网页中的某块内容进行分块
>* 通常一个完成的section是有标题和内容组成的，不推荐给没有标题的区域设置section
>* 如果想要给一个内容设置有个容器用来书写样式，那么还是推荐使用div
>###### article标签
>* 代表文档、页面、或程序中，可以独立的完整的被外部引用的内容
>* 比如一篇博客、一篇文章、一段用户的评论、一个日历插件，或者是其他独立内容
>* 一般来说，一个article也有自己的头部header，或者是footer
>* article和section区别
>   * article元素可以看做是特殊的section，但是强调独立性比section更强
>   * section主要强调分段分块，article是强调很强的独立性
>   * 原则上来说能用article的时候，也可以使用section，但是假设用article更合适，请使用article
>* div和article和section对比
> * div、section、article语义依次递增
>    * div没有任何的语义，仅仅是用作样式，可以用在任何场景，但是我们容易看不清上下文关系
>    * 对于主题性的区域，我们可以使用section
>    * 加入这个区域可以脱离上下文，作为完整独立的内容存在，使用article
>
>##### aside标签
>
>* 表示一个和其余页面内容几乎无关的区域
>* 被认为是独立于内容的一部分，并且可以拆出来而不会使整体收到影响，通常表现为侧边栏
>* 这个里边的内容和其他元素内容关联性不强
````
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>header标签</title>
</head>
<body>
    <div>
        <!--头部区域-->
        <header>
            <h1>你看我像不像logo</h1>
            <!--导航区域-->
            <nav>
                <a href="###">news</a>
                <a href="###">my</a>
                <a href="###">tiyu</a>
            </nav>
        </header>
        <!--内容区域-->
        <section>
            <h2>这里是评论区域</h2>
            <article>
                <h3>评论人：张三</h3>
                <p>今天天气真好</p>
            </article>
            <article>
                <h3>评论人：李四</h3>
                <p>今天天气真好</p>
            </article>
            <article>
                <h3>评论人：王五</h3>
                <p>今天天气真好</p>
            </article>
        </section>
        <!--侧边栏-->
            <aside>
                我是侧边栏内容
            </aside>
        <!--底部区域-->
        <footer>
            <div>
                <h3>友情链接</h3>
                <a href="###">百度</a>
                <a href="###">阿里巴巴</a>
                <a href="###">阿里妈妈</a>
            </div>
        </footer>
    </div>
</body>
</html>
​```

````
##### H5新增语义化标签（媒体标签）
>###### figure标签（标题+图片）
>* 代表一块独立的内容，是一个独立的引用单元
>* 这个标签在主文中用来引用 图片、插画、表格、代码段等等信息
>* 一般会在figure元素中插入figcaption元素（标题元素），将figcaption代表的标题与figure内容相关联
>* 如果是单独一张图片 或者 单独的表格等等，那么直接使用相应的标签即可，如果存在图片和标题，那么请使用figure标签
````
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>figure</title>
</head>
<body>
    <figure>
        <figcaption>海贼王的图片</figcaption>
        <img src="../images/05.jpg" alt="" width="300">
    </figure>
</body>
</html>

​```
````

>###### source 标签
>* 因为没有任何的视频格式可以兼容所有浏览器，我们也不能同一个视频书写多个video标签
>* 可以在video标签中书写source标签，source用来引入不同的视频格式
>* 浏览器会依次检测视频哪一个支持，如果支持，就不再向下寻找
>###### video标签
>* src属性：视频的路径 如果只有src属性，那么现实的是视频的封面
> * src是书写在source标签中
>* width：给视频设置宽度  只设置宽度  高度自适应
>* height：给视频设置高度 这设置高度  宽度自适应
> * 设置宽高是不会视频变形，只要宽高有一个达到设置的要求，视频就停止等比缩放，让视频在另一个没有充满的方向上居中
>* controls：显示播放控件
>* autoplay：视频自动播放 （浏览器限制不允许自动播放  但是当设置为静音的时候，自动播放生效）
>* muted：  设置静音
>* loop：   设置循环播放
>* preload：
> * none：提示作者认为用户不需要查看该视频，服务器也想要最小化访问流量；换句话说就是提示浏览器该视频不需要缓存。
> * metadata: 提示尽管我们认为用户不需要查看该视频，不过抓取元数据（比如：长度）还是很合理的。
> * auto: 用户需要这个视频优先加载；换句话说就是提示：如果需要的话，可以下载整个视频，即使用户并不一定会用它。
>* poster： 引入一个图片或者广告视频，作为视频的封面

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>视频引入</title>
</head>
<body>
    <video controls muted loop preload="auto" poster="../images/06.png">
        <source src="../images/source/test.mp4">
        <source src="../images/source/test.webm">
        <source src="../images/source/test.ogv">
        垃圾 给你一个链接 自己体会 <a href="">点击下载新版浏览器</a>
    </video>
</body>
</html>
```


>###### audio标签
>* 几乎所有的属性都和video标签重合
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>音频</title>
</head>
<body>
    <audio controls autoplay muted preload="metadata" loop>
        <source src="../images/source/music/BIGBANG%20-%20Let's%20not%20fall%20in%20love.mp3">
        <source src="../images/source/music/BIGBANG%20-%20Let's%20not%20fall%20in%20love.ogg">
        <source src="../images/source/music/BIGBANG%20-%20Let's%20not%20fall%20in%20love.webm">
        垃圾
    </audio>
</body>
</html>
```
##### H5新增语义化标签（其他标签）
>###### mark标签
>* 为引用的内容进行标记或突出显示文本，用来表示和上下文之间的关联性
>* 突出显示的文本通常可能和用户当前的活动等有一定的关联性
>* 比如，用户搜索的时候，它可以显示搜索之后的关键字
>* 不要把mark和 em、strong进行混淆;em、strong都是表示文本在上下文的重要性，而mark只是为了表示关联性
>* mark标签是行内标签，默认黄色背景颜色
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>mark元素</title>
</head>
<body>
    <input type="text" value="下雨">
    <p>今天晚上可能会<mark>下雨</mark>，明天中秋节晴朗</p>
</body>
</html>
```
>###### time标签
>* 用来表示24小时制 或者是 一个公历时间
>* 作用：以机器可读的格式去表示日期和时间，安排日程表的应用就可以使用这个time标签
>* 通用时间格式  XXXX-XX-XX XX:XX:XX
>* 两种用法：
>   * time标签直接包含时间
>   * 使用datetime属性来表示时间
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>time标签</title>
</head>
<body>
    <div>
        <!-- 主题区域-->
        <section>
            <h2>这里是评论区域</h2>
            <article>
                <h3>评论人：张三</h3>
                <p>今天天气真好</p>
                <p><time>2019-9-12 19:00:00</time></p>
            </article>
        </section>
    </div>
</body>
</html>
```
>######　datalist标签
>* 包含了一组option元素，代表是列表可选的值
>* 和input进行相关联，用来配套使用
>* input中的list属性 == datalist的id属性
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>datalist元素</title>
</head>
<body>
    <input list="city" type="text">
    <datalist id="city">
        <option value="河南">河南</option>
        <option value="河北">河北</option>
        <option value="湖北">湖北</option>
        <option value="湖南">湖南</option>
        <option value="胡建">胡建</option>
    </datalist>
</body>
</html>
```
>###### progress标签
>* 主要用来显示一项任务的完成程度
>* 规范没有规定默认的样式，所以各个浏览器默认的样式不一定相同
>* 属性:
>   * value：是当前进度的值
>   * max：是总进度的长度


```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>progress元素</title>
</head>
<body>
    <progress max="100" value="80"></progress>
</body>
</html>
```
>###### ruby 注释标签
>* 通过rt标签对ruby标签的内容进行注释
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>注释标签</title>
</head>
<body>
    <p>
        <ruby>蠡<rt>li</rt></ruby>
    </p>
</body>
</html>
```
##### H5新属性
>###### input新类型
>* 如果input的新类型不被浏览器所支持，那么他会默认显示成text文本框
>* input的新类型大多数都被谷歌浏览器支持，如果开发移动端，只要谷歌支持即可，因为所有安卓系统内置浏览器都是chrome
>* type旧类型：
>   * text：       文本框
>   * password：   密码框
>   * radio：      单选框
>   * checkbox：   多选框
>   * hidden：     隐藏域
>   * file：       文件域
>     * 文件域 的 accept属性书写 image/*  代表接受任何格式的图片
>       * capture=camera  代表从相机拍照接收
>       * capture=photo  代表从相册选取照片
>       * 但是在pc端的表现都是选取文件
```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>调用本地相册和相机</title>
    </head>
    <body>
        <input type="file" accept="image/*" capture="camera">

        <input type="file" accept="image/*" capture="photo">
    </body>
    </html>
```
>  * * button：     按钮
>
>     * reset：      重置按钮
>     * submit：     提交按钮
>  * type新类型
>     * color：      用来引入或者打开指定颜色的控件
>     * date：       日期的控件（年月日）
>     * week：       日期的控件（年周）（火狐不支持）
>     * month：      日期的控件（年月）（火狐不支持）
>     * email：      编辑email的字段
>        * 自带验证，但是验证不完整，一般还是自己书写
>        * 在移动端上 有相对应的自动弹出键盘包含 @ .com 等按键
>     * number：     用来输入数字的控件
>        * 多了一个上下的按键，可以增加和降低数字大小
>        * 验证必须是数字
>        * 其他属性
>          * min：最少数量
>          * max：最大数量
>          * value：当前数量
>          * step：每次累加累减数量
>     * search：     用来搜索框，当用户输入内容后，在末尾有一个删除按钮，单击可以删除输入好的文字
>     * tel：        电话号码输入框
>     * url：        url地址
>     * range：      输入一个拖拽的控件
>        * 属性：
>          * max：最大值
>          * min：最小值
>          * step：每次走的最小单位
>          * value：当前值
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>新type类型-input</title>
</head>
<body>
    <form action="###" method="get">
        请选择你喜欢的颜色：
        <input type="color" name="color">
        <br>

        请选择你的出生日期：
        <input type="date" name="brithday">
        <br>

        请输入当前的周数：
        <input type="week" name="week">
        <br>

        请输入你几月生日：
        <input type="month" name="month">
        <br>

        请输入您的邮箱地址：
        <input type="email" name="email">
        <br>

        请选择您购买的数量：
        <input type="number" name="num" min="2" max="10" step="2">
        <br>

        请在本框中进行检索：
        <input type="search" name="sear">
        <br>

        请输入您的电话号码：
        <input type="tel" name="tel">
        <br>

        请输入你的个人博客的网址：
        <input type="url" name="url">
        <br>

        请选择：
        <input type="range" name="range" min="30" max="100" value="50">
        <br>
        <br>
        <button>提交</button>
    </form>

</body>
</html>
```
>###### 表单元素新属性
>* placeholder：    占位符
>* autocomplete：   是否提示用户曾经输入过的值  默认是on  关闭是off
>* autofocus：      默认自动获取焦点
>   * 他有唯一一个值是autofocus
>   * h5规范允许 当属性名和属性值相等的时候  可以直接书写属性名即可
>   * 在js中，h5允许以布尔值的形式控制属性开启或关闭,也就是在js中给autofocus属性设置值为true（真，打开）或者是 false（假，关闭）,但是在元素的属性中 不允许使用true或者是false来控制开启或关闭
>   * 如果多个表单书写autofocus，那么以第一个书写的为准
>* required：       必填项，当提交的时候，此表单必须填写
>* disabled：       禁用任何表单元素，这个元素就被禁止输入或选择等等操作
>   * 使用disabled禁用表单，表单元素是不会在被提交了
>* checked：        单选框或多选框 默认被选中
>* readonly：       对于可编辑的表单来说 表示不能再次被编辑  但是是可以被提交的
>   * 对单选多选按钮不支持
>* form：           
>   * 如果input存在form属性，表示当前的input属于某一个表单,此时form表单的id的值 就是这个input的值,那么form表单 和当前的input就进行关联了,无论input书写在哪里，都能随着表单发送数据
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表单元素的新属性</title>
</head>
<body>
<form action="###" method="get" id="form1">
    请输入用户名：
    <input type="text" name="user" placeholder="请输入用户名" autofocus autocomplete="on">
    <br>

    请输入密码：
    <input type="text" name="pass" value="123456" autofocus required>
    <br>

    请确认性别：
    男：<input type="radio" name="sex" value="男" disabled checked>
    女：<input type="radio" name="sex" value="女" disabled>
    <br>


    请确认年龄：
    大于30岁：<input type="radio" name="age" value="30-" checked readonly>
    小于30岁：<input type="radio" name="age" value="30+" readonly>

    请输入邮箱：
    <input type="email" name="email" value="lipeihua@atguigu.com" readonly>

    <br>
    <button>提交</button>
</form>

<!--在form表单外有一个input，但是想点击form中的提交按钮的时候，把这个input也给提交了，form属性就这样使用-->
<input type="hidden" name="id" form="form1" value="12587">
</body>
</html>
```
>###### select、option的新属性：
>* selected： 默认选中项
>* multiple： 让select可以进行多选（按住ctrl键进行多选）
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>select元素的属性</title>
</head>
<body>
<form action="###" method="get">
    请选择你喜欢的食物：
    <select name="food" id="" multiple>
        <option value="肉">肉</option>
        <option value="鸡蛋">鸡蛋</option>
        <option value="水果" selected>水果</option>
        <option value="骨头">骨头</option>
    </select>
    <button>提交</button>
</form>
</body>
</html>
```
#### HTML相关规范
##### 书写规范

* 标签的换行写法
* 双标签需要关闭
* 对代码进行缩进
* 标签的正确嵌套
* 合理加注释
* a标签不能嵌套a标签
* ......
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>html书写规范</title>
</head>
<body>

    <!--标签的换行写法-->
    <div>
        <p>
            今天的天
            <span>真的好啊</span>
        </p>
    </div>

    <!--标签需要关闭-->
    <p>
        <span>哈哈哈哈哈</span>
        <em>呵呵呵呵</em>
    </p>

    <!--代码缩进使用tab键
        tab每次缩进空格数量一样，我们可以设置。也为了方便代码合并
        shift+tab是向前缩进
    -->
    <!--标签的正确嵌套-->
        <ul>
            <li></li>
            <li></li>
        </ul>
        <dl>
            <dt></dt>
            <dd>

            </dd>
        </dl>

    <!--合理加注释-->

    <!--a标签不能嵌套a标签-->
    <a href="">
        <a href=""></a>
    </a>

</body>
</html>
```
#####  HTML实体(特殊符号)
* 在html中，会把一个或多个空格或回车解析成一个空格显示
* 在html中,特殊符号，一般不会直接书写，而是使用代表这个符号的实体（编码）
   * 空格： \&nbsp;
   * 大于：\&gt;
   * 小于：\&lt;
   * 版权：\&copy;
   * 双引号：\&quot;
##### 为何使用语义化标签
* 语义化标签更具有可读性，便于团队的开发和维护
* 没有css的情况下，网页也能很好的呈现出内容结构和代码结构
* 关于SEO，搜索引擎更能理解到网页中各部分之间的关系，更准确更快速搜索信息