typora-root-url: image

typora-root-url: image

## React

### 1.React入门

#### 1.1介绍描述

* 用于构建用户界面的JavaScript库（只关注于view）
* 由Facebook开发，开源免费

#### 1.2 React的特点

* 声明式编码
  * 命令式编程（Imperative）：通过详细的代码命令机器怎么（How）去处理一件事情以达到你想要的结果（What）；
  * 声明式编程（ Declarative）：只告诉你想要的结果（What），机器自己摸索过程（How）

* Component-Based(组件化编码)
* React Native
  * 可以将js代码转换为原生移动应用

* 支持客户端与服务器渲染
* 高效
  * 虚拟(virtual)DOM, 不总是直接操作DOM
  * DOM Diff算法, 最小化页面重绘, 减少重排重绘的次数

#### 1.3 React的基本使用

* 新建html文件
* 相关js库
  * react.js: React的核心库
  * react-dom.js: 提供操作DOM的react扩展库
  * babel.min.js: 解析JSX语法代码转为纯JS语法代码的库

* 引入相关js库

  ```js
  <script src="../js/react.development.js"></script>
  <script src="../js/react-dom.development.js"></script>
  <script src="../js/babel.min.js"></script>
  ```

* 编码

  ```html
  <body>
      <div id="test"></div>
      <script type="text/babel">     //必须声明babel
         // 创建虚拟DOM元素
        const vDom = <h1>Hello React</h1> // 千万不要加引号
         // 渲染虚拟DOM到页面真实DOM容器中
        ReactDOM.render(vDom, document.getElementById('test'))
      </script>
  </body>
  ```

#### 1.4 React jsx

* 虚拟DOM

  * React提供了创建虚拟DOM对象两种方式：

    * React自带的方案  React.createElement（纯JS，一般不用）

      ```js
      // 创建虚拟DOM对象
      const  = React.createElement('p', null, 'I Love You');
      const vDom1 = React.createElement('div', {id: 'title1', className: 'title'}, vDom3);
      ```

    * JSX语法: 用来简化创建虚拟DOM对象
      * 以 < 开头，会标签语法解析。如果是html同名标签，就解析成同名元素。如果不是，就会当做组件解析。
      * 以 { 开头，里面代码会当做js代码解析

      ```js
      <h1 id='myTitle'>{title}</h1>
      ```

  * 虚拟DOM对象最终都会被React转换为真实的DOM

  * 我们编码时基本只需要操作react的虚拟DOM相关数据, react会转换为真实DOM变化而更新界面

* JSX（JavaScript XML）

  * react定义的一种类似于XML的JS扩展语法: XML+JS
  * 作用: 用来创建react虚拟DOM(元素)对象（简化）
  * 标签名任意: HTML标签或其它标签
  * 标签属性任意: HTML标签属性或其它

  * 基本语法规则
    * 遇到 <开头的代码, 以标签的语法解析: html同名标签转换为html同名元素, 其它标签需要特别解析
    * 遇到以 { 开头的代码，以JS语法解析: 标签中的js代码必须用{ }包含
  * babel.js的作用
    * 浏览器不能直接解析JSX代码, 需要babel转译为纯JS的代码才能运行
    * 只要用了JSX，都要加上type="text/babel", 声明需要babel来处理

* 渲染虚拟DOM(元素)

  * 语法:  ReactDOM.render(virtualDOM, containerDOM) 

  * 作用: 将虚拟DOM元素渲染到页面中的真实容器DOM中显示

  * 参数说明
    * 参数一: 纯js或jsx创建的虚拟dom对象
    * 参数二: 用来包含虚拟DOM元素的真实dom元素对象(一般是一个div)

* 案例

  ```js
  <!DOCTYPE html>
  <html>
  
      <head>
        <meta charset="UTF-8">
        <title>02_JSX_DEMO</title>
      </head>
  
      <body>
        <h2>前端JS框架列表</h2>
        <div id="example1"></div>
        <script src="../js/react.development.js"></script>
        <script src="../js/react-dom.development.js"></script>
        <script src="../js/babel.min.js"></script>
        <script type="text/babel">
          // 1.数据
          const data = ['jquery', 'boostrap', 'express', 'mysql', 'react'];
  
          /*map 长度不变，值变
            filter 长度变，值不变
            reduce 长度变，值也变
          */
          // 2.map遍历，返回一个新数组，新数组每一项值看遍历的返回值
          const result = data.map((item, index) => {
            return <li key={index}>{item}</li>;
          })
  
          // 3.创建虚拟DOM对象
          // 如果数据是数组，会自动展开,而对象不能渲染
          const vDom = <ul className="list">{result}</ul>;
  
          // 4.渲染到页面上
          ReactDOM.render(vDom, document.getElementById('example1'));
  
          // render方法做了什么事？ 将虚拟DOM对象对应创建真实DOM元素，插入到页面的指定容器中
          /*上述步骤234可以合并简写为以下：
           ReactDOM.render(<ul>
             {
               data.map((item, index) => <li key={index}>{item}</li>)
             }
           </ul>, document.getElementById('example1'));
          */
        </script>
      </body>
  </html>
  ```

#### 1.5模块与组件和模块化与组件化

* 模块
  * 向外提供特定功能的js程序, 一般就是一个js文件
  * 为什么:  js代码更多更复杂
  * 作用: 复用js, 简化js的编写, 提高js运行效率

* 模块化(详见node)

  * 模块化:把一个庞大的js文件中每个功能拆分成多个功能,每个功能形成一个js文件,最终使用特定的语法引入这些js文件,此时形成模块化

   * nodejs内部会帮助我们把每个js文件变成对应的一个模块

   * 模块化有一个主文件(入口文件)：index.js/main.js/app.js，所有的模块都要通过入口文件来进行加载

   * 模块化:模块的定义和引入模块

      * 模块定义：定义模块,并暴露出去
         * 语法:
            * module.exports
            * exports
      * 引入模块:在某个js文件(某个模块)引入其他的模块
         * 语法:
            * const 变量名 = require(路径)

   * 每个模块内部的数据都是私有的,外部是不可见的,想要让外部使用,必须要暴露出去

  * 当应用的js都以模块来编写的, 这个应用就是一个模块化的应用

    >总结:
    >
    >如果只要暴露一个内容:module.exports=xxx--->xxx-------->最常用
    >
    >如果要暴露多个内容: exports.xxx=xxx->{xxx}
    >
    >其他方式:---->es6的对象简写语法
    >
    >module.exports={xxx}--------->多的时候这种比较好
    >
    >注意问题: require(路径可以省略.js后缀名字)，但是路径中的相对路径必须要写, ./ 不能省略
    >
    >模块分三种:
    >
    >​	1.自己定义的，引入路径必须以./或者../ 这种开头的
    >
    >​	2.nodejs自带的:直接写名称即可
    >
    >​	3.第三方的-->npm 下载的

  * 模块化的方式:

    - 1.CommonJS模块化

      - CommonJS是属于同步加载，AMD是属于异步加载

      - CommonJS可以直接在服务器端中执行,不能直接在浏览器端执行,如果想要在浏览器端执行,需要使用Browserify就可以了

        ```js
        // CommonJS-Node
        
        // 引入模块 index.js
        const m1 = require('./module1.js') // 引入模块暴露的内容
        const m2 = require('./module2.js')
        console.log(m1) // [Function: sum] 是一个函数.函数名为sum
        console.log(m2) //{ sub: [Function: sub] } 是一个对象,对象中有一个方法sub方法
        console.log(m1(10, 20));
        console.log(m2.sub(100, 10));
        
        //module1.js
        function sum (a, b) {
          return a + b
        }
        // module.exports = sum
        // 注意问题:
        module.exports.sum=sum // 外部报错信息: { sum: [Function: sum] } 此时暴露出去的是对象,外部如果想要使用,需要通过对象.sum()才能使用呢
        
        //module2.js
        function sub (a, b) {
          return a - b
        }
         exports.sub = sub
        // 注意 
        // exports=sub // 暴露出去的是一个空对象,是不能使用的 报错信息:m2.sub is not a function
        ```

    - 2.ES6模块化

      - ES6模块化不能直接在服务器端执行,也不能直接在浏览器端执行,需要使用Babel进行编译,之后才可以在服务器端执行,通过Browserify可以在浏览器端执行

    - 3.AMD

      - AMD可以直接在浏览器端中执行,但是需要配合require.js文件

    - 4.CMD

      - AMD和CMD是为了直接在浏览器中执行而诞生的
      - CMD可以直接在浏览器端中执行,但是需要配合sea.js文件

* 组件

  - 用来实现特定(局部)功能效果的代码集合(html/css/js)
  - 为什么: 一个界面的功能更复杂
  - 作用: 复用编码, 简化项目编码, 提高运行效率

* 组件化

  * 当应用是以多组件的方式实现, 这个应用就是一个组件化的应用

### 2.React面向组件编程

#### 2.1 基本使用

*  创建组件两种方式：

  * 工厂函数组件（简单组件）

    ```js
    <!DOCTYPE html>
    <html>
        <head>
          <meta charset="UTF-8">
          <title>03_component_basic</title>
        </head>
        <body>
          <div id="example"></div>
    
          <script type="text/javascript" src="../js/react.development.js"></script>
          <script type="text/javascript" src="../js/react-dom.development.js"></script>
          <script type="text/javascript" src="../js/babel.min.js"></script>
    
          <script type="text/babel">
          	//工厂函数组件
            function FuncComponent(){
            	return <h1>工厂函数组件</h1>
            }
            
            //普通调用函数，得到返回的虚拟DOM对象，在渲染到页面的指定容器中
            ReactDOM.render(<funcComponent />,document.getElementById('example'))
          </script>
       </body>   
    </html>
    ```

  * ES6类组件（复杂组件）

    ```js
    <!DOCTYPE html>
    <html>
        <head>
          <meta charset="UTF-8">
          <title>03_component_basic</title>
        </head>
        <body>
          <div id="example"></div>
    
          <script type="text/javascript" src="../js/react.development.js"></script>
          <script type="text/javascript" src="../js/react-dom.development.js"></script>
          <script type="text/javascript" src="../js/babel.min.js"></script>
    
          <script type="text/babel">
          		//ES6类组件
              class ClassComponent extends React.Component{
                  return <h1>ES6组件</h1>
              }
          	
          		// new调用类，得到实例对象。调用实例对象的render方法，得到返回的虚拟DOM对象，在渲染到页面的指定容器中
              ReactDOM.render(<ClassComponent />,document.getElementById('example'))
          </script>
       </body>   
    </html>
    ```

* 三大主要事项

  * 组件名首字母必须大写 

    * 如果组件首字符是小写，会当做html同名标签解析，因为没有这个组件标签，所以解析不了，会报错)

    * 如果组件首字符是大写，会当做组件解析)

  * 渲染的虚拟DOM元素的标签必须带结束符：自结束标签或双标签  

    * 不能是单标签，没有结束符

  * 如果要渲染多个元素，必须有且只有一个根元素

* render()渲染组件标签的基本流程
  * React内部会创建组件实例对象
  * 得到包含的虚拟DOM并解析为真实DOM
  * 插入到指定的页面元素内部

#### 2.2 组件的三大属性

* state 状态

  * 理解
    * state是组件对象最重要的属性, 值是对象(可以包含多个数据)
    * 组件被称为"状态机", 通过更新组件的state来更新对应的页面显示(重新渲染组件)
  * 什么时候使用state

    * 只要用户页面发生更新（变化），就要通过更新state来更新页面变化

  * state的值类型是什么

    * 如果页面有两种变化，一般用 Boolean

  * 编码操作

    ```
    1.初始化状态:
      constructor (props) {
        super(props)
        this.state = {
          stateProp1 : value1,
          stateProp2 : value2
        }
      }
    2.读取某个状态值
      this.state.statePropertyName 
    3.更新状态---->组件界面更新
      this.setState({
        stateProp1 : value1,
        stateProp2 : value2
      })
    
    ```

  * 案例

    ```js
    <!DOCTYPE html>
    <html>
        <head>
          <meta charset="UTF-8">
          <title>07_component_state</title>
        </head>
        <body>
          <div id="example"></div>
    
          <script type="text/javascript" src="../js/react.development.js"></script>
          <script type="text/javascript" src="../js/react-dom.development.js"></script>
          <script type="text/javascript" src="../js/babel.min.js"></script>
    
          <script type="text/babel">
            /*
          	需求: 自定义组件, 功能说明如下
                1. 显示h2标题, 初始文本为: 你喜欢我
                2. 点击标题更新为: 我喜欢你
            */
              //1.定义组件
              class Like extends React.Component{
                  //初始化状态
                  constructor(){
                      super();  //调用父类的constructor
                      this.state = {
                          isLikeMe:true
                      }
                     /*
                      // 改变函数的this指向
                      // bind不会改变原函数的this，返回一个改变this指向新函数
                      const newFn = this.handleClick.bind(this); 
                      // 覆盖原函数
                      this.handleClick = newFn;
                      console.log(this);
    				*/
          			this.handleClick = this.handleClick.bind(this);
                  }
                  
                  //实例对象的方法,在React组件方法（除constructor、render外），this都是undefined
                  handleClick(){
                      //获取state状态
                      const { isLikeMe } = this.state;
                      
                      //更新state状态
                      this.setState({
                          isLikeMe = !islikeMe
                      })
                  }
                  
                  render(){
                      //获取state
                      const { isLikeMe } = this.state;
                      
                      return <h1 onclick={this.handleClick}>{isLikeMe?'我喜欢你':'你喜欢我'}</h1>
                  }
              }
          	
          	  // 渲染组件
              ReactDOM.render(<Like />, document.getElementById('example'));
              
          </script>  
       </body>   
    </html>
    ```

    ```js
    //案例简写
    <!DOCTYPE html>
    <html>
        <head>
          <meta charset="UTF-8">
          <title>07_component_state</title>
        </head>
        <body>
          <div id="example"></div>
    
          <script type="text/javascript" src="../js/react.development.js"></script>
          <script type="text/javascript" src="../js/react-dom.development.js"></script>
          <script type="text/javascript" src="../js/babel.min.js"></script>
    
          <script type="text/babel">
            /*
          	需求: 自定义组件, 功能说明如下
                1. 显示h2标题, 初始文本为: 你喜欢我
                2. 点击标题更新为: 我喜欢你
            */
            
            //1.定义组件
              class Like extends React.component{
                  //3.初始化state状态
                  state = {
                      isLikeMe: true
                  }
                  //4.实例对象的方法
                  handleClick=()=>{
                      //获取state状态
                      const { isLikeMe } = this.state;
                      //更改state状态
                      this.setState({
                          isLikeMe: !isLikeMe
                      })
                  }
                  render(){
                     //获取state状态
                      const { isLikeMe } = this.state;
                      
                     return <h1 onclick={this.handleClick}>{isLikeMe ? '我喜欢你':'你喜欢我'}</h1> 
                  } 
              }
              
             //2.渲染组件
              ReactDOM.render(<Like />,document.getElementById('example'))
           </script>
       </body>   
    </html>             
    ```

* props 属性

  * 理解

    * 每个组件的实例对象都会有props(properties的简写)属性
    * 组件标签的所有属性都保存在props中

  * 作用

    * 通过标签属性从组件外向组件内传递变化的数据
    * 注意: 组件内部不要修改props数据

  * 编码操作

    ```
    1.内部读取某个属性值
    	this.props.propertyName
    2.对props中的属性值进行类型限制和必要性限制
        原来方案：
        Person.propTypes = {
            name: PropTypes.string.isRequired,
            age: PropTypes.number.isRequired
        }
        最新方案：
        static propTypes = {
            name: PropTypes.string.isRequired,
            age: PropTypes.number.isRequired
        }
    3.扩展属性: 将对象的所有属性通过props传递
    	<Person {...person}/>
    4.默认属性值
        原来方案：
        Person.defaultProps = {
        	name: 'Mary'
        }
        最新方案：
        static defaultProps = {
        	name: 'Mary'
        }
    
    5.组件类的构造函数
    constructor (props) {
        super(props)
        console.log(props) // 查看所有属性
    }
    ```

  * 案例

    ```js
    <!DOCTYPE html>
    <html>
        <head>
          <meta charset="UTF-8">
          <title>04_component_props</title>
        </head>
        <body>
          <div id="example"></div>
    
          <script type="text/javascript" src="../js/react.development.js"></script>
          <script type="text/javascript" src="../js/react-dom.development.js"></script>
          <script src="../js/prop-types.js"></script>
          <script type="text/javascript" src="../js/babel.min.js"></script>
    
          <script type="text/babel">
    	  /*
       	 需求: 自定义用来显示一个人员信息的组件, 效果如页面. 说明
          1). 如果性别没有指定, 默认为男
          2). 如果年龄没有指定, 默认为18
        */
              const data = {
                  name:'jack',
                  age: 18,
                  sex: '男'
              }     
              //1.定义组件
    		  class Person extends React.Component{
              	// static关键字用来定义类的静态属性/方法
          		// 实例对象获取不到
                  //2.属性值进行类型限制和必要性限制
                  static propTypes = {
                      name: PropTypes.string.isRequired,
                      age: PropTypes.number,
                      sex: PropTypes.string
                  }
    			  //3.设置默认属性值
                  static defaultProps = {
                    age: 20,
                    sex: '女'
                  }
    			 //4.组件类的构造函数
    			  constructor(props) {
                    super(props);
                // super(props); 就是为了能在 constructor 中获取props（如果不穿参就获取不到）
                    console.log(this.props);
         		  }
    			  render(){
        			//5.读取props
                      const {name,age,sex} = this.props;
                      return <ul>
                          <li>姓名：{name}</li>
                          <li>性别：{sex}</li>
                          <li>年龄：{age}</li>
                          </ul>
                  }
              }
    		  
    		  //渲染组件
              // ReactDOM.render(<Person name={data.name} age={data.age} sex=
              //{data.sex}/>, document.getElementById('example'));
    		  ReactDOM.render(<Person {...data}>,document.getElementById('example'))
       	  </script>
       </body>   
    </html>     
    ```

* refs属性

  * 组件内的标签都可以定义ref属性来标识自己
    * <input type="text" ref={this.createRef}/> (推荐使用)
    * <input type="text" ref={input => this.funcRef = input} /> 
    * <input type="text" ref="stringRef" /> (即将废弃)
    * 回调函数在组件初始化渲染完或卸载时自动调用
  * 在组件中可以通过this.createRef.current / this.funcRef / this.stringRef来得到对应的真实DOM元素
  * 作用: 通过ref获取组件内容特定标签对象, 进行读取其相关数据
  * 如果触发事件的目标元素就是要获取的元素，用event.target；反之，就用ref

* 事件处理

  * 通过onXxx属性指定组件的事件处理函数(注意大小写)
    * React使用的是自定义(合成)事件, 而不是使用的原生DOM事件
    * React中的事件是通过事件委托方式处理的(委托给组件最外层的元素)
  * 通过event.target得到发生事件的DOM元素对象
    <input onFocus={this.handleFocus}/>
    handleFocus(event) {
            event.target  //返回input对象
    }

  > 强烈注意:
  > 1.组件内置的方法中的this为组件实例对象
  > 2.在组件类中自定义的方法中this为undefined
  > 3.强制绑定this: 通过函数对象的bind()
  > 4.箭头函数(ES6模块化编码时才能使用)

  * 案例

    ```js
    <!DOCTYPE html>
    <html>
        <head>
          <meta charset="UTF-8">
          <title>07_component_refs</title>
        </head>
        <body>
          <br>
          <div id="example"></div>
          <script type="text/javascript" src="../js/react.development.js"></script>
          <script type="text/javascript" src="../js/react-dom.development.js"></script>
          <script type="text/javascript" src="../js/babel.min.js"></script>
    
          <script type="text/babel">
            /*
            需求: 自定义组件, 功能说明如下:
              1. 界面如果页面所示
              2. 点击按钮, 提示第一个输入框中的值
              3. 当第2个输入框失去焦点时, 提示这个输入框中的值
           */
           
              //1.定义组件
              class Form extends React.Component{
                  /* constructor() {
            			super();
                    // React.createRef();每次调用都会创建一个新对象
                    this.createRef = React.createRef();
                    //console.log(this.createRef); // {current: null}
          			} 
                  */
                  createRef = React.createRef();
    			  
                  handleClick = ()=>{
    				//提示输入框输入的内容
                      const value = this.createRef.current.value;
                      alert(value);
                      this.createRef.current.value='';
                  }
                  
                  handleBur = (event)=>{
                      /*
                      如果触发事件的目标元素就是要获取的元素，用event.target
                      反之，就用ref
                    */
                      alert(event.target.value);
                      event.target.value='';
                  }
                  
                  render(){
                      return <div>
                          	<input type="text" ref={this.createRef}/>
                            <button onClick={this.handleClick}>点击提示数据</button>
                            <input type="text" placeholder="失去焦点提示数据" onBlur={this.handleBlur}/>    
                          </div>
                  }
              }
           	  //渲染组件
              ReactDOM.render(<Form/>,document.getElementById('example'))
          
       	  </script>
       </body>   
    </html>    
    ```

#### 2.3 组件的组合

* 收集表单数据

  * 理解
    * 问题: 在react应用中, 如何收集表单输入数据
    * 包含表单的组件分类
      * 受控组件: 通过state和onChange事件的方式来自动收集表单数据
      * 非受控组件: 需要时才通过ref收集表单数据，需要操作DOM元素，React认为性能不好。不建议使用ref操作DOM元素

  * 案例

    ```js
    <!DOCTYPE html>
    <html>
        <head>
          <meta charset="UTF-8">
          <title>09_form</title>
        </head>
        <body>
          <div id="example"></div>
    
          <script type="text/javascript" src="../js/react.development.js"></script>
          <script type="text/javascript" src="../js/react-dom.development.js"></script>
          <script type="text/javascript" src="../js/babel.min.js"></script>
          <script type="text/babel">
            /*
              需求: 自定义包含表单的组件
                1. 界面如下所示
                2. 输入用户名密码后, 点击登陆提示输入信息
                3. 不提交表单
          */
                //1.定义组件
              class Form extends React.Component{
                  //初始化state状态
                  state ={
                  	username: '',
                    password: ''
                  }
                  
                  handleSubmit = (e)=>{
    				  //禁止默认行为
                      e.preventDefault();
                      //收集表单数据
                      const {username，password}= this.state;
                      alert(`用户名: ${username}  密码: ${password}`);
                      //更新state状态
                      this.setState({
                          username: '',
                    	  password: ''
                      })  
                  }
                  /*
                   // 输入用户名触发的事件
                    usernameChange = (e) => {
                      // 获取输入的值
                      const value = e.target.value;
                      // 更新为state
                      this.setState({
                        username: value
                      })
                    }
    
                    passwordChange = (e) => {
                      // 获取输入的值
                      const value = e.target.value;
                      // 更新为state
                      this.setState({
                        password: value
                      })
                    }
    				*/
                    // 高阶函数：执行函数返回值是一个函数
                    // 作用：给内部函数传参
                    // 闭包的典型应用
                    handleChange = (key) => {
                      return (e) => {
                        // 获取输入的值
                        const value = e.target.value;
                        // 更新为state
                        this.setState({
                          // 内部函数通过闭包得到外部函数的参数
                          [key]: value
                        })
                      }
                    }
                  render(){
                      return <form action="/" onSubmit={this.handleSubmit}>
                          	<input type="text" onChange=		
                                {this.handleChange('username')} value={username}/>
                            <input type="password" onChange=		
                                {this.handleChange('password')} value={password}/>
                            <input type="submit" value="登录"/>        
                          </form>
                  }
              }
          	  //渲染组件
          	  ReactDOM.render(<Form />,document.getElementById('example'))
       	  </script>
       </body>   
    </html>  
    ```

* 组件化编码流程（核心思想）

  * 1.拆分组件
    *  按照**js功能**或**用户界面的变化**来拆 
    * 默认情况下，最外面是**App组件**
  * 2.实现静态组件

    * 将组件全部定义好，样式/结构写完
  * 3.实现动态组件
    * 要不要定义state? 
      * 如用户界面发生了变化，需定义state，否则不需要
    * 需定义state时，state值的类型是什么? 
      * 如果是两种变化，用布尔值
      * 如果N种，用对象/数组。使用数组方便遍历展示

  * 4.state定义在哪里（哪个组件）?

    * 如果state只有一个组件使用，就定义在这个组件中

    * 如果state有多个组件使用，就定义在它们公共的父组件App组件中

  * 5.完成js功能

  * 6.更新state的方法定义在哪？

    * state在哪里，更新的方法就在那里

    ​            state在哪里，更新的方法就在那里

    案例

    ```js
    <!DOCTYPE html>
    <html>
        <head>
          <meta charset="UTF-8">
          <title>05_components_composing</title>
        </head>
        <body>
          <div id="example"></div>
    
          <script type="text/javascript" src="../js/react.development.js"></script>
          <script type="text/javascript" src="../js/react-dom.development.js"></script>
          <script type="text/javascript" src="../js/prop-types.js"></script>
          <script type="text/javascript" src="../js/babel.min.js"></script>
          <script type="text/babel">
          	//父组件
          	calss App extends React.Component{
                state = {
                    todoList:[
                    	'吃饭~',
              			'睡觉~',
              			'打豆豆~'    
                    ]
                }
                //更新state的方法
                add = (todo)=>{
                    //获取state状态
                    const { todoList }=this.state;
                    //更新state状态
                    this.setState({
                        todoList:[todo,..todoList]
                    })
                }
                render(){
                    //获取state的状态
                    const {todoList} = this.state;
                  return <div>
                  	<h1>Todo List</h1>
                  	<Add add={this.add} length={todoList.length}/>
                  	<List todoList={todoList}/>
                  </div>
                }
          	}
          	//添加列表组件
          	class Add extends React.Component{
                static propTypes = {
                    add:PropTypes.func.isRequired,
                    length: PropTypes.number.isRequired
                }
    			inputRef = React.creatRef()
    			
                addTodo = ()=>{
    				const input = this.inputRef.current;
                    const value = input.value.trim();
                    // 如果值为空，就啥也不做
                    if(!value) return;
                    this.props.add(value);
                    //清空输入的值
                    input.value = '';
                }
                render(){
                   return <div>
                   	<input type="text" ref={this.inputRef}/>
                   	<button onClick={this.addTodo}>add#{this.props.length}</button>
                   </div>
                }
          	}
          	//列表组件
          	class List extends React.Component{
                // 声明属性的类型和必要性限制
                static propTypes = {
                    todoList: PropTypes.array.isRequired
                }
                render(){
                    //获取props
                  	const { todoList } = this.props;  
                    renturn <ul>
                        	// 数据动态展示
                			todoList.map((todo, index) => <li key={index}>{todo}</li>)
                        </ul>
                }
          	}
            
            // 渲染
       		ReactDOM.render(<App />, document.getElementById('example'));
          </script>
       </body>   
    </html>  
    ```

### 3.组件的生命周期

* 组件对象从创建到死亡它会经历特定的生命周期阶段
* React组件对象包含一系列的勾子函数(生命周期回调函数), 在生命周期特定时刻回调
* 我们在定义组件时, 可以重写特定的生命周期回调函数, 做特定的工作

#### 3.1生命周期流程图(旧)

![生命周期-旧](/生命周期-旧.png)

* 初始化渲染
  * constructor:（只会执行一次）
    * 过去：1. 初始化state 2. 绑定函数this 3. 初始化ref
    * 现在：没啥用了
  * componentWillMount
    * 没啥用，所以即将被废弃（新react版本不能使用）
  * render
    * 返回要渲染的虚拟DOM对象
  * componentDidMount:（只会执行一次）
    * 在组件渲染完毕触发的。
    * 作用：
      * 用来发送ajax请求
      * 设置定时器
      * 绑定事件
      *  ...

  > 面试题：为什么请求在  componentDidMount 发送？而不在 constructor componentWillMount？
  >
  > 1、请求只要发送一次。 所以这个函数只能执行一次。而在新版本React，componentWillMount可能会执行多次，所以排除。
  >
  > 2、请求完数据后可能要操作DOM。而 constructor componentWillMount 因为还没有渲染，不能操作DOM，所以排除。
  >
  > 3、componentDidMount能让渲染速度更快。如果在 constructor componentWillMount 干活，会影响渲染速度

* 更新

  * 1.父组件渲染导致子组件更新
    * componentWillReceiveProps
      * 在此阶段，可以获取父组件传递的props
      * 如果子组件state的变化和父组件传递的props有关系。更新state
      * 作用： 如果子组件state由父组件传递的props来生成，就要使用当前生命周期函数
      * 问题：在新版本中，可能会调用多次。所以被废弃了
    * shouldComponentUpdate
      * 性能优化：决定组件是否需要重新渲染
    * componentWillUpdate
      * 没啥用。即将被废弃
    * render
    * componentDidUpdate
      * 每次更新时需要做一些事。
  * 2.组件调用setState更新
    * componentWillUpdate
    * render
    * componentDidUpdate
  * 3.组件调用forceUpdate更新
    * componentWillUpdate
    * render
    * componentDidUpdate

​          componentWillUpdate

* 卸载
  * componentWillUnmount 组件将要卸载
    * 做一些收尾工作：
      * 1.清除定时器
      * 2.取消没有结果的ajax请求  xhr.abort()
      * 3.解绑事件(React事件不用解绑。自定义事件)
      * 4....
  * ReactDOM.unmountComponentAtNode(box); 卸载组件，box为插入的真实dom元素

* 重要生命周期函数：
  * componentDidMount
  * componentWillUnmount
  * shouldComponentUpdate

* 即将废弃：
  * componentWillMount
  * componentWillReceiveProps
  * componentWillUpdate

#### 3.2生命周期流程图(新)

![生命周期-新](/生命周期-新.png)

* 初始化渲染
  * constructor
  * static getDerivedStateFromProps
    * 作用：在渲染之前更新state
    * 根据props来生成state
  * render
  * componentDidMount

* 更新
  * static getDerivedStateFromProps
  * shouldComponentUpdate
  * render
  * getSnapshotBeforeUpdate
    * 可以提前操作DOM。操作完后再更新（一般用的很少）
  * componentDidUpdate 

* 卸载

  * componentWillUnmount

  案例

  ```js
  <!DOCTYPE html>
  <html lang="en">
      <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
      </head>
      <body>
        <div id="example"></div>
        <script type="text/javascript" src="../js/react.development.js"></script>
        <script type="text/javascript" src="../js/react-dom.development.js"></script>
        <script type="text/javascript" src="../js/babel.min.js"></script>
        <script type="text/babel">
        	/*
        	需求: 自定义组件
            1. 让指定的文本做显示/隐藏的渐变动画
            2. 切换持续时间为2S
            3. 点击按钮从界面中移除组件界面
        	*/
            const box = document.getElementById('example');
  
            class LifeCycle extends React.Component {
                //初始化state状态
                state = {
                    opacity: 1
                }
  			  //设置定时器
               componentDidmount(){
                   this.timeId = setInterval(()=>{
                       //获取state
                       let {opacity} = this.state;
                       opacity -= 0.01;
                       //判断
                       if(opacity<=0){
                           opacity = 1;
                       }
                       //更新state的状态
                       this.setState({
                           opacity
                       })
                   },1000/60)
               }
               goDie = ()=>{
  				ReactDOM.unmountComponentAtNode(box);
               }
  			 //清除定时器
                componentWillUnmount(){
  				clearInterval(this.timeId);
               }
                render(){
                    //获取state的状态
                    const {opacity} = this.state;
                    return <div>
                        	<h1 style={{opacity}}>React太难了</h1>
  						button onClick = {this.goDie}>不活了</div>
                        </div>
                }
            }
     	  </script>
     </body>   
  </html>        
  ```

### 4.虚拟DOM与DOM Diff算法

#### 4.1 虚拟DOM和真实DOM

* 真实DOM元素

  ```
  <div id='root'>
  	<h1 class='title'>真实DOM</h1>
  </div>
  ```

* 虚拟DOM就是一个对象，用来存储真实DOM元素的信息

  ```
  {
      tag: 'div',
      props:{
          id:'root'
      },
      children:[
          {
              tag:'h1',
              props:{
                  className:'title'
              },
              children:[
                  '真实DOM'
              ]
          }
      ]
  }
  ```

#### 4.2 虚拟DOM Diff算法

​	传统的 diff 算法性能开销大，无法满足大规模 DOM 操作需求。 React 通过制定大胆的策略，将性能开销降到最低。

##### diff 策略

1. Web UI 中 DOM 节点跨层级的移动操作特别少，可以忽略不计。
2. 拥有相同类的两个组件将会生成相似的树形结构，拥有不同类的两个组件将会生成不同的树形结构。
3. 对于同一层级的一组子节点，它们可以通过唯一 id 进行区分。

基于以上三个前提策略，React 分别对 tree diff、component diff 以及 element diff 进行算法优化，事实也证明这三个前提策略是合理且准确的，它保证了整体界面构建的性能。

##### tree diff

基于策略一，React 对树的算法进行了简洁明了的优化，即对树进行分层比较，两棵树只会对同一层次的节点进行比较。

既然 DOM 节点跨层级的移动操作少到可以忽略不计，针对这一现象，只会对相同颜色方框内的 DOM 节点进行比较，即同一个父节点下的所有子节点。当发现节点已经不存在，则该节点及其子节点会被完全删除掉，不会用于进一步的比较。这样只需要对树进行一次遍历，便能完成整个 DOM 树的比较。

![](https://pic1.zhimg.com/80/0c08dbb6b1e0745780de4d208ad51d34_hd.png)

**问题：如果出现了 DOM 节点跨层级的移动操作，性能不好！**

![](https://pic2.zhimg.com/80/d712a73769688afe1ef1a055391d99ed_hd.png)

如上图所示：React diff 的执行情况：create A -> create B -> create C -> delete A

由此可发现，当出现节点跨层级移动时，并不会出现想象中的移动操作，而是以 A 为根节点的树被整个重新创建，这是一种影响 React 性能的操作，因此 React 官方建议不要进行 DOM 节点跨层级的操作。

> 注意：在开发组件时，保持稳定的 DOM 结构会有助于性能的提升。例如，可以通过 CSS 隐藏或显示节点，而不是真的移除或添加 DOM 节点。

#####　component diff 

React 是基于组件构建应用的，对于组件间的比较所采取的策略也是简洁高效。

- 如果是同一类型的组件，按照原策略继续tree diff。
- 如果不是，则将该组件判断为 dirty component，从而替换整个组件下的所有子节点。
- 对于同一类型的组件，有可能其 Virtual DOM 没有任何变化，如果能够确切的知道这点那可以节省大量的 diff 运算时间，因此 React 允许用户通过 shouldComponentUpdate() 来判断该组件是否需要进行 diff。

##### element diff

如下图，老集合中包含节点：A、B、C、D，更新后的新集合中包含节点：B、A、D、C，此时新老集合进行 diff 差异化对比，发现 B != A，则创建并插入 B 至新集合，删除老集合 A；以此类推，创建并插入 A、D 和 C，删除 B、C 和 D。

![](https://pic2.zhimg.com/80/7541670c089b84c59b84e9438e92a8e9_hd.png)

React 发现这类操作繁琐冗余，因为这些都是相同的节点，但由于位置发生变化，导致需要进行繁杂低效的删除、创建操作，其实只要对这些节点进行位置移动即可。

针对这一现象，React 提出优化策略：**允许开发者对同一层级的同组子节点，添加唯一 key 进行区分，虽然只是小小的改动，性能上却发生了翻天覆地的变化！**

新老集合所包含的节点，如下图所示，新老集合进行 diff 差异化对比，通过 key 发现新老集合中的节点都是相同的节点，因此无需进行节点删除和创建，只需要将老集合中节点的位置进行移动，更新为新集合中节点的位置，此时 React 给出的 diff 结果为：B、D 不做任何操作，A、C 进行移动操作，即可。

![](https://pic4.zhimg.com/80/c0aa97d996de5e7f1069e97ca3accfeb_hd.png)

问题：如下图所示，若新集合的节点更新为：D、A、B、C，与老集合对比只有 D 节点移动，而 A、B、C 仍然保持原有的顺序，理论上 diff 应该只需对 D 执行移动操作，然而由于 D 在老集合的位置是最大的，造成 D 没有执行移动操作，而是 A、B、C 全部移动到 D 节点后面的现象。

![](https://pic1.zhimg.com/80/7b9beae0cf0a5bc8c2e82d00c43d1c90_hd.png)

> 建议：在开发过程中，尽量减少类似将最后一个节点移动到列表首部的操作，当节点数量过大或更新操作过于频繁时，在一定程度上会影响 React 的渲染性能。

##### 总结

- React 通过分层求异的策略，对 tree diff 进行算法优化；
- React 通过相同类生成相似树形结构，不同类生成不同树形结构的策略，对 component diff 进行算法优化；
- React 通过设置唯一 key的策略，对 element diff 进行算法优化；
- 建议，在开发组件时，保持稳定的 DOM 结构会有助于性能的提升；
- 建议，在开发过程中，尽量减少类似将最后一个节点移动到列表首部的操作，当节点数量过大或更新操作过于频繁时，在一定程度上会影响 React 的渲染性能。

### 5 react应用（基于react脚手架）

#### 5.1 使用create-react-app创建react应用

* react脚手架

  * xxx脚手架: 用来帮助程序员快速创建一个基于xxx库的模板项目

    * 包含了所有需要的配置

    * 指定好了所有的依赖

    * 可以直接安装/编译/运行一个简单效果

  * react提供了一个用于创建react项目的脚手架库: create-react-app

  * 项目的整体技术架构为:  react + webpack4 + es6 + eslint + babel

  * 使用脚手架开发的项目的特点: 模块化, 组件化, 工程化

* 创建项目并启动

  ```
  npm install -g create-react-app   //全局安装脚手架
  create-react-app hello-react	 //创建脚手架项目
  cd hello-react
  npm start     //运行脚手架
  ```

* react脚手架项目结构

  ```
  ReactNews
  	|--node_modules---第三方依赖模块文件夹
  	|--public
  		|-- index.html-----------------主页面
  	|--src------------源码文件夹
  		|--components-----------------react组件
  		|--index.js-------------------应用入口js
  	|--.gitignore------git版本管制忽略的配置
  	|--package.json----应用包配置文件 
  	|--README.md-------应用描述说明的readme文件
  ```

  ###### 案例-评论管理

  ```js
  /*
  实现思路：按照组件编码思想
      拆分组件
      应用组件: App
      	* state: comments/array
      添加评论组件: CommentAdd
      	* state: username/string, content/string
      	* props: add/func
      评论列表组件: CommentList
      	* props: comment/object, delete/func, index/number
      评论项组件: CommentItem
      	* props: comments/array, delete/func
  */
  ```

  ```js
  //1.index.js文件，脚手架webpack的入口文件
  import React from 'react';
  import ReactDOM from 'react-dom';
  
  import App from './App';
  
  //渲染App组件
  ReactDOM.render(<App />,document.getElementById('app'))
  ```

  ```js
  //2.App.jsx文件
  import React,{Component} from 'react';
  
  import CommentAdd from '../component/CommentAdd'；
  import CommentList from '../component/CommentList'；
  
  export default class App extends Component{
      //初始化state状态
      state = {
          comments：[{
              username:'李华'，
              content: 'good',
              id: 1
      	}]
      }
      //在app上设置一个方法，state在哪，操作state的方法就在哪
      add=(comment)=>{
         //获取state的状态 
          const {comments} = this.state;
          //更新state状态
          this.setState({
              comments:[comment,...[comments]]
          })
      }
      //在app上设置一个删除方法，state在哪，操作state的方法就在哪
      del=(id)=>{
         //获取state的状态 
          const {comments} = this.state; 
          //更新state状态
          this.setState({
              comments:comments.filter((comment) => comment.id !== id)
          })
      }
      render(){
          //获取state状态
          const {comments} = this.state;
          return <div>
              	<h1>请发表对React的评论</h1>
          		<CommentAdd add={this.add}/>
              	<CommentList comments={comments} del={this,del}/>
              </div>
      }
  }
  ```

  ```jsx
  //3.CommentAdd中的index.jsx文件
  import React,{Component} from 'react';
  import PropTypes from 'prop-types'
  
  export default class CommentAdd extends Commponent {
      //设置属性
      static propTypes ={
          add:PropTypes.func.isRequired
      }
  	//设置state状态
  	state ={
      	username：'',
          content:''
      }
  	id = 2;
  	//获取表单输入的内容
      handleChange=(key)=>{
          return e=>{
              //设置state状态
              this.setState({
                  [key]:e.target.value
              });
          }
      }
  	//点击按钮，添加评论回调函数
      addComment=(e)=>{
  		e.preventDefault();   //阻止表单提交默认行为
          //收集表单输入的数据
          const {username,content}=this.state;
          //判断
          if(!username || !content) return;
          //添加评论
          this.props.add({username,content,id:this.id++});
          //清空表单数据
          this.setState({
              username:'',
              content:''
          });
      }
      render(){
          const { username, content} = this.state;
          return <form onSubmit={this.addComment}>
          	用户名：
              <input 
              	placeholder='用户名'
                  onChange={this.handleChage('username')}
                  value={username}
              />
              评论内容：
              <textarea 
              	rows='6'
             		placeholder='评论内容'
                  onChange={this.handleChage('content')}
                  value={content}
              ></textarea>
              <button type='submit'>提交</button>
          </form>
      }
  }
  
  ```

  ```jsx
  //4.CommentList中的index.jsx文件
  import React,{Component} from 'react';
  import PropTypes from 'prop-types';
  
  import CommentItem from '../CommentItem'
  
  export default class CommentList extends Component {
      //设置属性
      static propTypes = {
          commments:PropTypes.array.isRequired,
          del:PropTypes.func.isRequired
      }
      render(){
          //获取comments的属性值
          const {comments,del} = this.props;
          const isDisplay = comments.length ? 'none' : 'block';
          return <div className='col-md-8'>
              <h3 className='reply'>评论回复：</h3>
              <h2 style={{ display: isDisplay }}>暂无评论，点击左侧添加评论！！！</h2>
              <ul className='list-group'>
                  {comments.map((comment)=>{
                      return <Item comment={comment} key={comment.id} del={del}/>
                  })}
              </ul>
            </div>
      }
  }
  
  ```

  ```jsx
  //5.CommentItem中的index.jsx文件
  import React,{Component} from 'react';
  import PropTypes from 'prop-types';
  
  export default class CommentItem extends Component {
      //设置属性定义
      static propTypes = {
          comment:PropTypes.object.isRequired,
          del: PropTypes.func.isRequired
      }
  	//删除
      delComment=()=>{
  		const {id,username}= this.props.comment;
          
          if (!window.confirm(`您确认要删除${username}的评论吗?`)) return;
  
      	this.props.del(id);
      }
      render(){
          //获取属性值
          const { username，content } = this.props
          return <li className='list-group-item'>
              <div className='handle'>
                <button' onClick={this.delComment}>删除</button>
              </div>
              <p className='user'>
                <span>{username}</span>
                <span>说:</span>
              </p>
              <p className='centence'>{content}</p>
            </li>
      }
  }
  
  ```

#### 5.2 React ajax

* React本身只关注于界面, 并不包含发送ajax请求的代码

* 前端应用需要通过ajax请求与后台进行交互(json数据)

* react应用中需要集成第三方ajax库(或自己封装)

##### 常用的ajax请求库

###### jQuery

* 比较重, 如果需要另外引入不建议使用

###### axios

* 轻量级, 建议使用

* 封装XmlHttpRequest对象的ajax

* promise风格

* 可以用在浏览器端和node服务器端

* 查看文档地址：https://github.com/axios/axios

* 下载axios文件或cdn引入：npm i  axios

  ```js
  //get请求1
  axios.get('/user?ID=12345')
    .then(function (response) {
      console.log(response);
    })
    .catch(function (error) {
      console.log(error);
    });
  
  //get请求2
  axios.get('/user', {
      params: {
        ID: 12345
      }
    })
    .then(function (response) {
      console.log(response);
    })
    .catch(function (error) {
      console.log(error);
    });
  
  //post请求
  axios.post('/user', {
      firstName: 'Fred',
      lastName: 'Flintstone'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
  ```

######  axios拦截器

* 是一个拦截请求/响应的函数

* 作用：

  * 作为请求拦截器：设置公共的请求头 / 参数...
  * 作为响应拦截器：

* 执行流程；
  * 执行请求拦截器函数
  * 发送请求
  * 执行响应拦截器函数（接受到了响应）
  * 执行 axiosInstance().then()/catch()

  > axios发送POST请求，
  >   默认的content-type： application/json 请求体是json
  >   有可能发送POST请求，需要的Content-type是 application/x-www-form-urlencoded
  >
  > ```js
  > //json请求类型时的请求体参数设置
  > data: {
  >         username: 'admin',
  >         password: 'admin'
  >       }
  > //若是form表单类型    
  > data: 'username=admin&password=admin',
  > headers: {
  >         'content-type': 'application/x-www-form-urlencoded'
  >     } 
  > 1.为了实现可以满足以上两种方式，一般在设置请求体参数时还是使用对象的方式，在拦截器时对data数据转换
  > data: {
  >         username: 'admin',
  >         password: 'admin'
  >       }
  > 2.只有在post请求下才需要改
  > if (config.method === 'post') {
  >         // 修改请求参数
  >         /*
  >         {
  >           username: 'admin',
  >           password: 'admin'
  >         }
  >           --->  'username=admin&password=admin'
  >         */
  >         // ['username', 'password']
  >         const keys = Object.keys(config.data);
  >         const data = keys
  >           .reduce((prev, curr) => {
  >             prev += `&${curr}=${config.data[curr]}`;
  >             return prev;
  >           }, '')
  >           .slice(1);
  >         config.data = data;
  >         config.headers['content-type'] = 'application/x-www-form-urlencoded';
  >       }
  > 
  >       return config;
  >     }
  > ```

  ```js
  //1.引入axios是Axios的实例，里面包含axios默认配置
  import axios from 'axios';
  
  //2.自己创建axios实例，可以修改axios默认配置
    const axiosInstance = axios.create({
      baseURL: '/api', // 基础路径（公共路径）: 后面所有请求路径都会以 baseURL 开头
      timeout: 20000, // 20s: 请求超时时间: 请求一旦超过10s还没有响应，就会自动中断请求
      headers: {
        // 公共的请求头
        // 参数必须写死
      }
    });
  
    //3.设置拦截器
  
    //3.1请求拦截器(在发送请求之前调用)
    axiosInstance.interceptors.request.use(
      //3.1.1 设置发送请求，代码成功（还没有发送请求）
      config => {
        /* config是一个对象，里面包含所有发送请求的配置
           修改config配置
           添加动态headers参数
  	  */
        // console.log(config);
        //有token才添加动态headers参数
        if (token) {
          config.headers.authorization = `Bearer ${token}`;
        }
  
        /*
          看接口是否是必须使用'application/x-www-form-urlencoded'发送请求
        */
        if (config.method === 'post') {
          // 修改请求参数
          /*
          {
            username: 'admin',
            password: 'admin'
          }
            --->  'username=admin&password=admin'
          */
          // ['username', 'password']
          const keys = Object.keys(config.data);
          const data = keys
            .reduce((prev, curr) => {
              prev += `&${curr}=${config.data[curr]}`;
              return prev;
            }, '')
            .slice(1);
          config.data = data;
          config.headers['content-type'] = 'application/x-www-form-urlencoded';
        }
  
        return config;
      }
      //3.1.2 设置发送请求，代码失败，一般是不会有问题的，所以这个函数没啥用
      (error) => {
        // error失败的原因，返回一个失败的promise对象
        return Promise.reject(err);
      } 
    );
  
    //3.2 响应拦截器(返回响应之后，触发axiosInstance.then/catch之前调用)
    /*
      统一处理错误
    */
    axiosInstance.interceptors.response.use(
      // 请求/响应成功 --> 2xx
      response => {
        if (response.data.status === 0) {
          return response.data.data;
        } else {
          // 功能失败
          return Promise.reject(response.data.msg);
        }
      },
      // 请求/响应失败 --> 4xx 5xx
      err => {
        /*
          Network Error 网络错误  err.message
          err.response.status === 401  / err.message 401  没有token/token有问题
          "timeout of 10ms exceeded" err.message  请求超时
  
          根据不同的错误，返回不同的错误提示
        */
        // console.log('响应拦截器失败回调触发了~');
        // console.dir(err);
  
        const errCode = {
          401: '没有权限访问当前接口',
          403: '禁止访问当前接口',
          404: '当前资源未找到',
          500: '服务器发生未知错误，请联系管理员'
        };
  
        let errMessage = '';
  
        if (err.response) {
          // 说明接受到了响应，响应是失败的响应
          // 根据响应状态码判断错误 401 403 404 500
          errMessage = errCode[err.response.status];
        } else {
          // 说明没有接受到响应，请求就失败了
  
          if (err.message.indexOf('Network Error') !== -1) {
            errMessage = '网络连接失败，请重连网络试试~';
          } else if (err.message.indexOf('timeout') !== -1) {
            errMessage = '网络超时，请连上wifi重试~';
          }
        }
  
        return Promise.reject(errMessage || '发生未知错误，请联系管理员');
      }
    );
  
  let token = '';
    let id = '';
  
    const handleClick1 = () => {
      //4.发送请求使用axiosInstance
      axiosInstance({
        method: 'POST',
        url: '/login',
        data: {
          username: 'admin',
          password: 'admin'
        }
          
        // data: 'username=admin&password=admin',
          
        /* 拦截器在发送请求前已经在config中添加勒动态headers参数
        headers: {
          'content-type': 'application/x-www-form-urlencoded'
        } */
      })
        .then(response => {
          console.log(response);
  
          /* if (response.data.status === 0) {
            token = response.data.data.token;
            message.success('登录成功');
          } else {
            message.error(response.data.msg);
          } */
        })
        .catch(err => {
          console.log(err);
          message.error(err);
        });
    };
  ```

  

###### fetch

* 原生函数, 但老版本浏览器不支持

* 不再使用XmlHttpRequest对象提交ajax请求

* 为了兼容低版本的浏览器, 可以引入兼容库fetch.js

* 查看文档：https://github.github.io/fetch/

  ```js
  //get请求
  fetch(url).then(function(response) {
    return response.json()
  }).then(function(data) {
    console.log(data)
  }).catch(function(e) {
    console.log(e)
  });
  
  //post请求
  fetch(url, {
    method: "POST",
    body: JSON.stringify(data),
  }).then(function(data) {
    console.log(data)
  }).catch(function(e) {
    console.log(e)
  })
  ```

  ###### 案例1:搜索匹配的最受关注的库

  ```js
  /*
  需求:
    1. 界面效果如下
    2. 根据指定的关键字在github上搜索匹配的最受关注的库
    3. 显示库名, 点击链接查看库
    4. 测试接口: https://api.github.com/search/repositories?q=r&sort=stars
  */
  <!DOCTYPE html>
  <html>
      <head>
        <meta charset="UTF-8">
        <title>11_ajax</title>
      </head>
      <body>
        <div id="example"></div>
  
        <script type="text/javascript" src="../js/react.development.js"></script>
        <script type="text/javascript" src="../js/react-dom.development.js"></script>
        <!-- <script src="https://cdn.bootcss.com/axios/0.19.0/axios.min.js"></script> -->
        <script src="https://cdn.bootcss.com/fetch/2.0.4/fetch.min.js"></script>
        <script type="text/javascript" src="../js/babel.min.js"></script>
        <script type="text/babel">
            class MostStar extends React.Component{
                state={
                    isLoading:false, //是否在请求中
                    repo:{
                        name:'',
                        url:''
                    }
                }
  				
  			//发生ajax请求，需在componentDidMount回调函数中
              componentDidMount(){
  				//发送请求前，切换成loading
                  this.setState({
                      isLoading: true
                  })
                  /*
                  //通过axios请求库
                 axios.get('https://api.github.com/search/repositories?q=r&sort=stars')
                     .then((response)=>{
                     		const {name,html_url} = response.data.items[0];
                     		//请求成功，将loading切换成false
                         this.setState({
  							isLoading:false, 
                              repo:{
                                  name,
                                  url:html_url
                              }
                         })
                 		})
                  	.catch((err)=>{console.log(err)})	
                   */
                  //通过fetch请求库发送请求
                  fetch('https://api.github.com/search/repositories?q=r&sort=stars')
                  	// 将响应数据转换成json --> 对象
                  	.then((response)=>response.json())
                      .then(()=>{
                      	const {name,html_url} = response.data.items[0];
                     		//请求成功，将loading切换成false
                          this.setState({
                              isLoading:false, 
                              repo:{
                                  name,
                                  url:html_url
                              }
                          })
                 		 })
                  	.catch((err)=>{console.log(err)})
              }
              render(){
  				/* isLoading: loading 对this.state进行结构赋值，提取isLoading属性，赋值
                  给变量loading （将isLoading重命名为loading）
        			 repo : { name, url } 对this.state进行结构赋值，提取repo属性，在repo
                  进行结构赋值，提取name,url属性
                  */
                const { isLoading: loading, repo : { name, url }} = this.state;
  
                if (loading) {
                  return <h1>loading...</h1>;
                } else {
                  return <h1>Most Star Repo is <a href={url}>{name}</a></h1>
                }
  
              }
            }
            
            ReactDOM.render(<MostStar />,document.getElementById('example'))
        </script>
  	</body>
  </html>
  ```

  ###### 案例2-获取github用户名及头像等信息

  ```js
  //拆分组件
  App
      * state: searchName/string
  Search
      * props: setSearchName/func
  List
      * props: searchName/string
          * state: firstView/bool, loading/bool, users/array, errMsg/string
  ```

  ```js
  //index.js文件
  import React from 'react';
  import ReactDom from 'react-dom';
  
  import App from './App';
  
  ReactDom.render(<App />, document.getElementById('app'))
  ```

  ```jsx
  //APP.jsx文件
  import React, { Component } from 'react';
  
  import Search from './components/search';
  import List from './components/list';
  
  export default class App extends Component {
    state = {
      searchName: ''
    }
    // 更新state的方法
    update = (searchName) => {
      this.setState({
        searchName
      })
    }	
    
    render() {
      return (
        <div className='container'>
          <Search update={this.update}/>
          <List searchName={this.state.searchName}/>
        </div>
      );
    }
  }
  ```

  ```jsx
  //Search.jsx文件
  import React, { Component } from 'react';
  import PropTypes from 'prop-types';
  
  export default class Search extends Component {
    static propTypes = {
      update: PropTypes.func.isRequired
    };
  
  state = {
      searchName: ''
    };
  
    search = () => {
      // 获取用户输入的值
      const { searchName } = this.state;
      
      if (!searchName) return;
  
      // 调用父组件方法
      this.props.update(searchName);
    };
  
    handleChange = e => {
      this.setState({
        searchName: e.target.value
      });
    };
  
    render() {
      return (
        <section className='jumbotron'>
          <h3 className='jumbotron-heading'>Search Github Users</h3>
          <div>
            <input
              type='text'
              placeholder='enter the name you search'
              onChange={this.handleChange}
            />
            <button onClick={this.search}>Search</button>
          </div>
        </section>
      );
    }
  }
  ```

  ```jsx
  //List.jsx文件
  import React, { Component } from 'react';
  import PropTypes from 'prop-types';
  import axios from 'axios';
  
  export default class List extends Component {
    static propTypes = {
      searchName: PropTypes.string.isRequired
    };
  
    state = {
      isLoading: false,
      users: []
    };
  
    UNSAFE_componentWillReceiveProps(nextProps) {
      console.log(nextProps); // 代表最新的props {searchName: 'aaa'}
      // console.log(this.props); // 代表上一次的props
  
      // 发送请求之前更新成 loading 状态
      this.setState({
        isLoading: true
      });
      // 发送请求，请求数据
      axios
        .get('https://api.github.com/searchssss/users', {
          params: {
            q: nextProps.searchName
          }
        })
        .then(response => {
          // map方便遍历想要保留的数据
          // console.log(response.data);
          
          const result = response.data.items.map(item => {
            return {
              name: item.login,
              url: item.html_url,
              img: item.avatar_url
            };
          });
          // console.log(result);
  
          // 更新state
          this.setState({
            users: result,
            isLoading: false
          });
        })
        .catch(error => {
  
          this.setState({
            isLoading: false
          })
          
          alert('网络出现故障~');
        });
    }
  
    render() {
      const { isLoading, users } = this.state;
  
      if (isLoading) {
        return <h1>loading...</h1>;
      }
  
      if (users.length) {
        return (
          <div className='row'>
            {users.map((user, index) => {
              return (
                <div className='card' key={index}>
                  <a href={user.url}>
                    <img src={user.img} style={{ width: 100 }} />
                  </a>
                  <p className='card-text'>{user.name}</p>
                </div>
              );
            })}
          </div>
        );
      }
  
      return <h1>enter name to search</h1>;
    }
  }
  ```

### 6.重要技术总结

#### 6.1 组件间通信

- 一般数据-->父组件传递数据给子组件-->子组件读取数据
- 函数数据-->子组件传递数据给父组件-->子组件调用函数

###### 通过props传递

* 适用于父子组件间通信

* 共同的数据放在父组件上，特有的数据放在自己组件内部（state）
* 通过props可以传递一般数据和函数数据，只能一层一层传递

###### 使用消息订阅(subscribe)-发布(publish)机制

* 适用于祖孙组件间通信

* 工具库: PubSubJS

* 下载: npm install pubsub-js --save

* 使用: 

  * import PubSub from 'pubsub-js' //引入

  * PubSub.subscribe('delete', function(data){ });  //订阅(接收数据)

  * PubSub.publish('delete', data)   //发布消息


###### redux

###### context

* 一般使用redux，content为了开发库而使用

- 适用于祖孙组件间通信

- react的内置方案，因此不需要下载依赖

- 步骤：

  - 创建context文件夹user.js文件

    - 初始化context

      ```js
      //初始化context
      
      import { createContext } from 'react';
      
      // 创建context
      const userContext = createContext();
      
      export default userContext;
      ```

  - 设置state初始化状态

    ```js
    //App.js
    state = {
        user: {
          name: 'laofu',
          age: 40
        },
        food: 'apple'
      };
    ```

  - 在App.js引入userContext

    - userContext是一个对象，对象上有两个组件
          Provider 提供者（发布消息）
          Consumer 消费者（订阅消息）

    ```js
    import userContext from './context/user';
    ```

  - 给子组件传递数据

    - Provider组件可以给其子组件传递数据 ，将user数据传递给 需要使用这个数据的子组件

    ```js
    render() {
        return (
            <div>
                App...
                {/* 
                      Provider组件可以给其子组件传递数据 
                      将user数据传递给 需要使用这个数据的子组件
                    */}
                {/* <foodContext.Provider > */}
                <userContext.Provider value={this.state.user}>
                    <A />
                </userContext.Provider>
            {/* </foodContext.Provider> */}
            </div>
        );
    }
    ```

  - 子组件需对其消费操作

    ```js
    import userContext from '../../context/user';
    
    render() {
        return (
          	/*
            <div>
            <userContext.Consumer>
              {// 内部会调用下面函数，调用函数时，会将Provider传递的数据作为参数传入}
              user => {
                console.log(user);
                // 返回值就是要渲染的内容
                return (
                  <div>
                    <p>姓名: {user.name}</p>
                    <p>年龄: {user.age}</p>
                  </div>
                );
              }}
            </userContext.Consumer>
    	 </div>
    	 */
             //简单方式
             static contextType = userContext;
            // 内部Provider提供的值就会挂载到this.context上
            const user = this.context;
              <div>
                <div>
                  <p>姓名: {user.name}</p>
                  <p>年龄: {user.age}</p>
                </div>
              </div>
    	)
    }
    ```

    

#### 6.2 ES6常用新语法

* 定义常量/变量:  const/let
* 解构赋值: let {a, b} = this.props   import {aa} from 'xxx'  function ({name, age}) {}
* 对象的简洁表达: {a, b, c(){}}
* 箭头函数: 
  * 常用场景
    * 组件的自定义方法: xxx = () => {}
    * 参数匿名函数
  * 优点:
    * 简洁
    * 没有自己的this,使用引用this查找的是外部this

* 扩展(三点)运算符: 拆解对象(const MyProps = {}, <Xxx {...MyProps}>)

* 类:  class/extends/constructor/super/static

* ES6模块化:  export default | import

### 7. react-router5

##### react-router

* react的一个插件库
* 专门用来实现一个SPA应用
* 基于react的项目基本都会使用的库

##### SPA

* 单页web应用（single page web application）
* 整个应用只有一个完整的页面
* 点击页面中的链接都不会刷新页面，本身也不会向服务器发送请求
* 当点击路由链接时，只会做页面的局部更新，网址也会对应的改变
* 数据都需要通过ajax请求获取，并在前端异步展现

#####　路由

* 什么是路由

  * 一个路由就是一个映射关系(key:value)

  * key为路由路径, value可能是function/component

* 路由分类

  * 后台路由: node服务器端路由, value是function, 用来处理客户端提交的请求并返回一个响应数据

  * 前台路由: 浏览器端路由, value是component, 当请求的是路由path时, 浏览器端前没有发送http请求, 但界面会更新显示对应的组件 

* 后台路由

  * 注册路由: router.get(path, function(req, res))

  * 当node接收到一个请求时, 根据请求路径找到匹配的路由, 调用路由中的函数来处理请求, 返回响应数据

* 前端路由

  * 注册路由: <Route path="/about" component={About} />

  * 当浏览器的hash变为#/about时, 当前路由组件就会变为About组件

* 前端路由的原理

  * history库

    * 网址: <https://github.com/ReactTraining/history>

    * 管理浏览器会话历史(history)的工具库

    * 包装的是原生BOM中window.history和window.location.hash

  * history API

    * History.createBrowserHistory():  得到封装window.history的管理对象

    * History.createHashHistory():  得到封装window.location.hash的管理对象

      >history模式和hash模式的区别：
      >
      >1、兼容性：hash模式兼容性好，history模式兼容性较差
      >
      >2、美观：hash模式不美观 - 多一个#
      >
      >3、hash模式因为有#，所以不能使用锚点功能
      >
      >一般使用history模式

    * history.push(): 添加一个新的历史记录

    * history.replace(): 用一个新的历史记录替换当前的记录

    * history.goBack(): 回退到上一个历史记录

    * history.goForword(): 前进到下一个历史记录

    * history.listen(function(location){}): 监视历史记录的变化

    ```js
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <title>history test</title>
    </head>
    <body>
      <p><input type="text"></p>
      <a href="/test1" onclick="return push('/test1')">test1</a><br><br>
      <button onClick="push('/test2')">push test2</button><br><br>
      <button onClick="back()">回退</button><br><br>
      <button onClick="forword()">前进</button><br><br>
      <button onClick="replace('/test3')">replace test3</button><br><br>
    
      <script type="text/javascript" src="https://cdn.bootcss.com/history/4.7.2/history.js"></script>
      <script type="text/javascript">
        let history = History.createBrowserHistory() // 方式一
        // history = History.createHashHistory() // 方式二
        // console.log(history)
    
        function push (to) {
          history.push(to)
          return false
        }
    
        function back() {
          history.goBack()
        }
    
        function forword() {
          history.goForward()
        }
    
        function replace (to) {
          history.replace(to)
        }
    
        history.listen((location) => {
          console.log('请求路由路径变化了', location)
        })
      </script>
    </body>
    </html>
    ```

##### 路由相关组件

* 下载react-router-dom:
  npm install --save react-router-dom

* App中引入组件：

  ```
  import {
        BrowserRouter as Router, // 引入 BrowserRouter 重命名为 Router
        HashRouter,
        Route,
        Redirect,
        Switch
  } from 'react-router-dom';
  ```

###### 组件

* BrowserRouter history模式

* HashRouter hash模式

  * Router 要求必须在最外面使用。（目的：为了包裹所有组件 --> 为了让其他所有组件都是Router的子组件，这样就能得到history对象）

* Route  根据url的变化加载组件  

  * path参数：路径，以该路径开头就可以匹配
  * exact参数：必须是path参数路径才可以匹配
  * component参数：跳转的组件

  ```
  <Route path='/about' component={About} />
  ```

* Redirect 重定向: 能匹配所有路径，匹配上就修改url地址

  ```
  <Redirect to='/about' />
  ```

* Switch  切换。

  * 正常情况下，可以匹配多个Route
  * 加了Switch，就只能匹配一个, 从上到下匹配

  ```
  <Switch>
      <Route path='/about' component={About} />
      <Route path='/home' component={Home} />
      <Redirect to='/about' />
  </Switch>
  ```

* NavLink 

  * 更新浏览器历史记录
  *  在Link基础上，多一个 active class 

* Link

  * 不会刷新页面，不会跳转网址，不会发送请求。

  * 只能更新 浏览器历史记录（url地址） 

* 更新浏览器历史记录有两种方式：

  * NavLink / Link  ：适用于仅更新记录不进行任何操作

  * this.props.history.push('/home')

* 路由组件

  * 凡是通过Route加载的组件，就叫做路由组件

  * 路由组件就有三个属性：
    * history 用来控制浏览器历史记录
      * push 添加历史记录
      * replace 替换历史记录
      * goBack 回退
      * goForward 前进
      * listen 监听历史记录的变化
    * location
      * pathname 路径
      * state 
    * match
      * params: {id: 1}

### 8.react-ui-antd

* material-ui(国外)
  * 官网: <http://www.material-ui.com/#/>
  * github: <https://github.com/callemall/material-ui>

* ant-design(国内蚂蚁金服)
  * PC官网: <https://ant.design/index-cn>
  * Github:https://github.com/ant-design/ant-design/>

#### ant-design使用

* 搭建antd的基本开发环境

  * 下载：npm install antd --save

* 使用antd组件库

  ```js
  //index.js文件
  import React from 'react';
  import ReactDOM from 'react-dom'
  import App from "./App"
  // 引入整体css
  import 'antd/dist/antd.css'
  
  ReactDOM.render(<App />, document.getElementById('root'))
  ```

  ```js
  //App.jsx文件
  import React, {Component} from 'react'
  // 分别引入需要使用的组件
  import { Button, message } from 'antd'
  
  export default class App extends Component {
    handleClick = () => {
      message.success('点击按钮~~', 2);
    }
  
    render() {
      return (
        <div>
          <Button type="primary" onClick={this.handleClick}>提交</Button>
        </div>
      )
    }
  }
  ```

* 实现按需打包(组件js/css)

  * 下载依赖包：yarn add react-app-rewired customize-cra babel-plugin-import --dev

  * 修改默认配置:  

    ```js
    //package.json文件
    "scripts": {
      "start": "react-app-rewired start",
      "build": "react-app-rewired build",
      "test": "react-app-rewired test"
    }
    ```

    ```js
    //config-overrides.js文件
    const { override, fixBabelImports } = require('customizecra');
    
    module.exports = override(
      fixBabelImports('import', {
        libraryName: 'antd',
        libraryDirectory: 'es',
        style: 'css',
      }),
    );
    ```

    ```jsx
    //App.jsx文件
    // import 'antd/dist/antd.css'
    
    import {Button, message} from 'antd'
    ```

* 自定义主题

  * 下载依赖包：yarn add less less-loader --dev

  * 修改默认配置: 

    ```js
    //config-overrides.js 文件
    const { override, fixBabelImports } = require('customizecra');
    
    module.exports = override(
      fixBabelImports('import', {
        libraryName: 'antd',
        libraryDirectory: 'es',
        style: true,
      }),
      addLessLoader({
        javascriptEnabled: true,
        modifyVars: { '@primary-color': '#1DA57A' },
      }),
    );
    
    ```

### 9.redux

#### redux

* redux的概念

  * redux是一个独立专门用于做状态管理的js库（不是react插件库）
  * 它可以用在react、angular、vue等项目中，但一般与react配合使用
  * 作用：集中式管理react应用中多个组件共享的状态

* redux的工作流程

  ![redux工作流程图](/redux工作流程图.png)

* 何时使用
  * 总体原则: 大型项目状态管理复杂才用
  * 某个组件的状态，需要共享
  * 某个状态需要在任何地方都可以拿到
  * 一个组件需要改变全局状态
  * 一个组件需要改变另一个组件的状态

* 下载依赖包：npm install --save redux

* redux的核心API

  * createStore()

    * 作用：创建包含指定reducer的store对象

    * 编码

      ```js
      //引入createStore
      import {createStore} from 'redux';
      
      //引入
      import counter from './reducers/counter';
      ```

  * store对象

    * 作用：redux库核心的管理对象
    * 核心方法：
      * store.getState() 读取状态数据
      * store.dispatch(action) 触发更新状态数据
      * store.subscribe(listener) 监听状态数据的变化

  * applyMiddleware()

    * 作用：应用上基于redux的中间件（插件库）

    * 编码

      ```js
      import {createStore, applyMiddleware} from 'redux'
      import thunk from 'redux-thunk'  // redux异步中间件
      const store = createStore(
        counter,
        applyMiddleware(thunk) // 应用上异步中间件
      )
      ```

  * combineReducers()

    * 作用：合并多个reducer函数

    * 编码

      ```js
      import { combineReducers } from 'redux';
      
      export default combineReducers({
        user,
        chatUser,
        chat
      })
      ```

* redux的三个核心概念

  * action

    * 用来创建action对象工厂函数模块

    * action: {type: 操作类型, data: 操作数据}

    * 同步action creators：返回值action对象

    * 异步action creators：返回值是函数，函数接受dispatch作为参数

    * 编码

      ```
      const increment = (number) => ({type: 'INCREMENT', data: number})
      ```

  * reducer

    * 用来根据之前的状态（prevState）和action来生成新状态(newState) 函数模块

    * 编码

      ```js
      export default function counter(state = 0, action) {
          switch (action.type) {
              case 'INCREMENT':
              	return state + action.data
              case 'DECREMENT':
              	return state - action.data
              default:
              	return state
          }
      }
      ```

  * store

    * 用来集中式管理状态数据

    * 包含操作状态数据的方法

    * store.getState() 读取状态数据

    * store.dispatch(action) 触发更新状态数据

    * store.subscribe(listener) 监听状态数据的变化

    * 编码

      ```js
      import { createStore, applyMiddleware } from 'redux';
      import thunk from 'redux-thunk';
      import { composeWithDevTools } from 'redux-devtools-extension';
      import reducers from './reducers';
      
      // 创建store对象
      const store = createStore(
        reducers,
        // 区分环境
        process.env.NODE_ENV === 'development'
          ? composeWithDevTools(applyMiddleware(thunk))
          : applyMiddleware(thunk)
      );
      // 暴露
      export default store;
      ```

    ###### 案例-简单的点击添加功能

    ````js
    //1.下载依赖包：npm install --save redux
    ````

    ```js
    //src中的index.js文件
    import React from 'react';
    import ReactDOM from 'react-dom';
    
    import App from './App.jsx';
    
    ReactDOM.render(<App />,document.getElementById('root'));
    ```

    ```js
    //src中的redux文件夹中的action-type.js文件
    /**
     * 用来定义action的type类型常量模块
     */
    
    export const INCREMENT = 'INCREMENT';
    export const DECREMENT = 'DECREMENT'; 
    
    ```

    ```js
    //src中的redux文件夹中的action.js文件
    /**
     * 用来创建action对象工厂函数模块
     * action: {type: 操作类型, data: 操作数据}
     */
    import {INCREMENT,DECREMENT} from './action-type';
    
    //生产加法的action对象 工厂模块
    /* function increment(data) {
      return {
        type: 'INCREMENT',
        data
      }
    } */
    export const increment = data => ({type:INCREMENT,data});
    
    //生产减法的action对象 工厂模块
    export const decrement = data =>({type:DECREMENT,data});
    ```

    ```js
    //src中的redux文件夹中的store.js文件
    /**
     * 用来集中式管理状态数据
     * 包含操作状态数据的方法
     * store.getState() 读取状态数据
     * store.dispatch(action) 触发更新状态数据
     * store.subscribe(listener) 监听状态数据的变化
     */
    
    import { createStore } from 'redux';
    import { reducers } from './reducers';
    
    //创建store对象
    const store = creatStore(reducers);
    //暴露
    export default store；
    ```

    ```js
    //src中的redux文件夹中的reducers.js文件
    /**
     * 用来根据之前的状态（prevState）和action来生成新状态(newState) 函数模块*/
    
    import {INCREMENT,DECREMENT} from './action-type';
    // reducer函数名称一般和要管理的状态数据的名称一致
    // 在reducer中对状态数据进行初始化
    
    function number(prevState = 0,action){
         switch (action.type) {
            case INCREMENT:
              return prevState + action.data;
            case DECREMENT:
              return prevState - action.data;
            default :
              return prevState;  
          }
    }
    export default number;
    ```

    ```js
    //src中的App.js文件
    import React, {Component} from 'react';
    
    import store from './redux/store';
    import { increment, decrement } from './redux/actions';
    
    export default class App extends Component{
        //初始化状态
        state = {
        	value： 1
        }
    	//受控组件函数
        handleChange = (e)=>{
    		//获取复选框的内容
            const value = e.target.value;
            //更新state状态
            this.setState({
                value: +value    //value是一个string类型
            })
        }
    	//添加方法
        increment = ()=>{
            //获取state状态
            const {value} = this.state;
            // 更新redux的状态数据
        	// 调用actions生成action对象
            const action = increment(value);
            // 再调用dispatch方法，触发更新
        	// 内部调用reducer函数生成newState
            store.dispatch(action);
        };
    	//更新state生成newState
    	componentDidMount() {
            store.subscribe(() => {
              // 函数中就要重新渲染组件
              // 只会重新渲染App组件
              this.setState({});
            });
          }
        
    	//减少的方法
    	decrement = () => {
            const { value } = this.state;
            store.dispatch(decrement(value));
          };
    	//奇数才加
          incrementIffOdd = () => {
            const number = store.getState();
            /* if (number % 2 === 1) {
    
            } */
            if (number & 1) {
              const { value } = this.state;
              store.dispatch(increment(value));
            }
          };
    	  //异步添加
          incrementAsync = () => {
            setTimeout(() => {
              const { value } = this.state;
              store.dispatch(increment(value));
            }, 1000)
          }
          
        render(){
            const number = store.getState();
            return <div>
            <p>click {number} times</p>
            <select onChange={this.handleChange}>
              <option value='1'>1</option>
              <option value='2'>2</option>
              <option value='3'>3</option>
            </select>
            <button onClick={this.increment}>+</button>
            <button onClick={this.decrement}>-</button>
            <button onClick={this.incrementIffOdd}>increment if odd</button>
            <button onClick={this.incrementAsync}>incrememt async</button>
          </div>
        }
    }
    ```

#### react-redux

* redux存在的问题
  * redux和react组件代码重复率有点多
  * 编码不够简洁
* recat-redux概念
  * 一个react插件库
  * 专门用来简化react应用中使用redux
* React-Redux将所有组件分成两大类
  * UI组件
    * 只负责 UI 的呈现，不带有任何业务逻辑
    * 通过props接收数据(一般数据和函数)
    * 不使用任何 Redux 的 API
    * 一般保存在components文件夹下
  * 容器组件
    * 负责管理数据和业务逻辑，不负责UI的呈现
    * 使用 Redux 的 API
    * 一般保存在containers文件夹下

* 相关API

  * Provider

    * 让所有组件都可以得到state数据

      ```
      <Provider store={store}>
           <App />
      </Provider>
      ```

  * connect()

    * 用于包装 UI 组件生成容器组件

      ```
      import { connect } from 'react-redux'
          connect(
              mapStateToprops,
              mapDispatchToProps
      )(Counter)
      ```

    * mapStateToprops()

      * 将外部的数据（即state对象）转换为UI组件的标签属性

        ```
        const mapStateToprops = function (state) {
            return {
            	value: state
            }
        }
        ```

    * mapDispatchToProps()

      * 将分发action的函数转换为UI组件的标签属性

      * 简洁语法可以直接指定为actions对象或包含多个action方法的对象

* 使用react-redux

  * 下载依赖：npm install --save react-redux

  * 优化redux案例

    ```js
    //src中的index.js文件
    import React from 'react';
    import ReactDOM from 'react-dom';
    
    //引入react-redux
    import { Provider } from 'react-redux';
    //Provider专门给子组件提供store对象,还需引入store对象
    import store from './redux/store';
    
    import App from './App.jsx';
    
    //Provider专门给子组件提供store对象,所有组件都是子组件
    ReactDOM.render(
        <Provider store={store}>
        	<App />			
        </Provider>,document.getElementById('root'));
    ```

    ```js
    //src中的redux文件夹中的action-type.js文件
    /**
     * 用来定义action的type类型常量模块
     */
    
    export const INCREMENT = 'INCREMENT';
    export const DECREMENT = 'DECREMENT'; 
    ```

    ```js
    //src中的redux文件夹中的action.js文件
    /**
     * 用来创建action对象工厂函数模块
     * action: {type: 操作类型, data: 操作数据}
     */
    import {INCREMENT,DECREMENT} from './action-type';
    
    //生产加法的action对象 工厂模块
    /* function increment(data) {
      return {
        type: 'INCREMENT',
        data
      }
    } */
    export const increment = data => ({type:INCREMENT,data});
    
    //生产减法的action对象 工厂模块
    export const decrement = data =>({type:DECREMENT,data});
    ```

    ```js
    //src中的redux文件夹中的store.js文件
    /**
     * 用来集中式管理状态数据
     * 包含操作状态数据的方法
     * store.getState() 读取状态数据
     * store.dispatch(action) 触发更新状态数据
     * store.subscribe(listener) 监听状态数据的变化
     */
    
    import { createStore } from 'redux';
    import { reducers } from './reducers';
    
    //创建store对象
    const store = creatStore(reducers);
    //暴露
    export default store；
    ```

    ```js
    //src中的redux文件夹中的reducers.js文件
    /**
     * 用来根据之前的状态（prevState）和action来生成新状态(newState) 函数模块*/
    
    import {INCREMENT,DECREMENT} from './action-type';
    // reducer函数名称一般和要管理的状态数据的名称一致
    // 在reducer中对状态数据进行初始化
    
    function number(prevState = 0,action){
         switch (action.type) {
            case INCREMENT:
              return prevState + action.data;
            case DECREMENT:
              return prevState - action.data;
            default :
              return prevState;  
          }
    }
    export default number;
    ```

    ```js
    //src中的App.js文件
    
    import React, {Component} from 'react';
    
    //引入connect,用于包装子组件为一个容器
    import {connect} from 'react-redux';
    
    
    
    import store from './redux/store';
    import { increment, decrement } from './redux/actions';
    
    class App extends Component{
        //初始化状态
        state = {
        	value： 1
        }
    	//受控组件函数
        handleChange = (e)=>{
    		//获取复选框的内容
            const value = e.target.value;
            //更新state状态
            this.setState({
                value: +value    //value是一个string类型
            })
        }
    	//添加方法
        increment = ()=>{
            //获取state状态
            const {value} = this.state;
         /*   // 更新redux的状态数据
        	// 调用actions生成action对象
            const action = increment(value);
            // 再调用dispatch方法，触发更新
        	// 内部调用reducer函数生成newState
            store.dispatch(action);
          */
            
            this.props.increment(value);
        };
    	/* 已经绑定更新
    	//更新state生成newState
    	componentDidMount() {
            store.subscribe(() => {
              // 函数中就要重新渲染组件
              // 只会重新渲染App组件
              this.setState({});
            });
          }
        */
    	//减少的方法
    	decrement = () => {
            const { value } = this.state;
            /*store.dispatch(decrement(value));*/
            
            this.props.decrement(value);
          };
    	//奇数才加
          incrementIffOdd = () => {
            /*const number = store.getState();*/
              
              const {number} = this.props;
            /* if (number % 2 === 1) {
    
            } */
            if (number & 1) {
              const { value } = this.state;
              /*store.dispatch(increment(value));*/
                
                this.props.increment(value);
            }
          };
    	  //异步添加
          incrementAsync = () => {
            setTimeout(() => {
              const { value } = this.state;
              /*store.dispatch(increment(value));*/
                
               this.props.increment(value); 
            }, 1000)
          }
          
        render(){
            //const number = store.getState();
            //store对象已成为App的属性
             const {number} = this.props;
            return <div>
            <p>click {number} times</p>
            <select onChange={this.handleChange}>
              <option value='1'>1</option>
              <option value='2'>2</option>
              <option value='3'>3</option>
            </select>
            <button onClick={this.increment}>+</button>
            <button onClick={this.decrement}>-</button>
            <button onClick={this.incrementIffOdd}>increment if odd</button>
            <button onClick={this.incrementAsync}>incrememt async</button>
          </div>
        }
    }
    
    //将redux管理的state，以props方式传递给UI组件，App是UI组件
    //作用：让容器组件给UI组件传递管理的状态数据
    const mapStateToProps = (state)=>{
        //state就是store.getState()的返回值
        return {
            number: state
        }
    }
    
    //将更新的redux的state数据的方法，以props方式传递给UI组件
    //作用：让容器组件给UI组件传递管理的状态数据的方法
    const mapDispatchToProps = (dispatch)=>{
        //dispatch就是store.dispatch
        return {
            increment:(data)=>{
                dispatch(increment(data));
            }
            decrement:(data)=>{
                dispatch(decrement(data));
            }
        }
    }
    
    //使用connect方法，需调用两次,第二次参数为App组件，生成一个容器组件(AppContainer)
    const AppContainer = connect(
    	mapStateToProps,
        mapDispatchToProps
    )(APP)；
    
    //暴露的是容器组件
    export default AppContainer;
    ```

    ```js
    //将redux管理的state，以props方式传递给UI组件，App是UI组件
    //作用：让容器组件给UI组件传递管理的状态数据
    const mapStateToProps = (state)=>{
        //state就是store.getState()的返回值
        return {
            number: state
        }
    }
    
    //将更新的redux的state数据的方法，以props方式传递给UI组件
    //作用：让容器组件给UI组件传递管理的状态数据的方法
    const mapDispatchToProps = (dispatch)=>{
        //dispatch就是store.dispatch
        return {
            increment:(data)=>{
                dispatch(increment(data));
            }
            decrement:(data)=>{
                dispatch(decrement(data));
            }
        }
    }
    
    //使用connect方法，需调用两次,第二次参数为App组件，生成一个容器组件(AppContainer)
    const AppContainer = connect(
    	mapStateToProps,
        mapDispatchToProps
    )(APP)；
    
    //以上代码可以简化为
    const AppContainer = connect(
    	(state)=> {number:state},
        {
            increment,
            decrement
        }
    )(App)
    ```

#### react 异步编程

* react-redux存在的问题
  * redux默认不能处理异步操作
  * 应用中又需要在redux中执行异步任务（ajax，定时器）

* 异步中间件

  * 下载依赖：npm install --save redux-thunk

  * 优化redux案例异步操作

    ```js
    //src中的redux文件夹中的store.js文件
    /**
     * 用来集中式管理状态数据
     * 包含操作状态数据的方法
     * store.getState() 读取状态数据
     * store.dispatch(action) 触发更新状态数据
     * store.subscribe(listener) 监听状态数据的变化
     */
    
    import { createStore, applyMiddleware } from 'redux';
    import { reducers } from './reducers';
    //引入异步插件
    import thunk from 'redux-thunk';
    //创建store对象
    const store = creatStore(reducers,applyMiddleware(thunk));
    //暴露
    export default store；
    ```

    ````js
    //src中的redux文件夹中的action.js文件
    /**
     * 用来创建action对象工厂函数模块
     * action: {type: 操作类型, data: 操作数据}
     * 同步action creators：返回值action对象
     * 异步action creators：返回值是函数，函数接受dispatch作为参数
     */
    import {INCREMENT,DECREMENT} from './action-type';
    
    //生产加法的action对象 工厂模块
    /* function increment(data) {
      return {
        type: 'INCREMENT',
        data
      }
    } */
    export const increment = data => ({type:INCREMENT,data});
    
    //生产减法的action对象 工厂模块
    export const decrement = data =>({type:DECREMENT,data});
    
    export const incrementAsync = data =>{
        return dispatch => {
            //异步操作
            setTimeout(()=>{
                //dispatch就是触发更新的方法
            	dispatch(increment(data));
            },1000);
        }
    }
    ````

    ```js
    //App.js
    import { increment, decrement, incrementAsync } from './redux/actions';
    //异步加的方法
    incrementAsync = () => {
        const { value } = this.state;
        this.props.incrementAsync(value);
      };
    
    const AppContainer = connect(
      // 状态数据
      state => ({ number: state }),
      // 更新状态数据的方法
      {
        increment,
        decrement,
        incrementAsync
      }
    )(App);
    ```

#### redux调试工具

* 安装chrome浏览器插件

  * redux-devtools

* 下载依赖：npm install --save-dev redux-devtools-extension

* 编码

  ```js
  //src中的redux文件夹中的store.js文件
  /**
   * 用来集中式管理状态数据
   * 包含操作状态数据的方法
   * store.getState() 读取状态数据
   * store.dispatch(action) 触发更新状态数据
   * store.subscribe(listener) 监听状态数据的变化
   */
  
  import { createStore, applyMiddleware } from 'redux';
  import { reducers } from './reducers';
  //引入异步插件
  import thunk from 'redux-thunk';
  //引入调试插件
  import { composeWithDevTools } from 'redux-devtools-extension'
  //创建store对象
  const store = creatStore(
      reducers,
     	// 区分环境
      process.env.NODE_ENV === 'development'
          ? composeWithDevTools(applyMiddleware(thunk))
          : applyMiddleware(thunk)
  );
  //暴露
  export default store；
  ```

#### 高阶函数

* 高阶组件（HOC high order component）

  * 概念：本质上就是一个函数，执行函数接受一个组件(被包装组件)作为参数，返回值是一个新组件(包装组件)

* 作用：复用多个组件的代码（提取公共代码去复用）

  ###### 案例-登录注册

  ```js
  //index.js文件
  import React from 'react';
  import ReactDOM from 'react-dom';
  
  import App from './App'
  
  ReactDOM.render(<App />,document.getElemnetById('root'))
  ```

  ```js
  //App.jsx文件
  import React,{Component} from 'react';
  import Login from './login';
  import register from './register';
  
  export default class App extends Component {
    render() {
      return (
        <div>
          <Login />
          <Register />
        </div>
      );
    }
  }
  ```

  ```js
  //login.jsx文件
  import React,{Component} from 'react';
  import withFrom '../with-form';
  
  class Login extends Component{
      /*复用代码
      state = {
          username: '',
          password: ''
      }
      handleChange = (key)=>{
          return (e)=>{
              this.setState({
                  [key]:e.target.value
              })
          }
      }
      handleSubmit = (e)=>{
          e.preventDefault();
          const {username,password} = this.state;
          aiert(`用户名：${username},密码：${password}`)
      }
      */
      render(){
          const { handleChange, handleSubmit } = this.props;
          
          return <div>
              /*<h1>登录</h1>  复用代码*/
          	<form onSubmit={handleSubmit}>
              	用户名：<input type="text" onChange={handleChange(username)}/><br/>
                  密码：<input type="password" onChange={handleChange(password)}/><br/> 
                  <input type="submit" value="登录" /><br/>
              </form>
          </div>
      }
  }
   
  export default withForm(Login);
  ```

  ```js
  //register.js文件
  import React,{Component} from 'react';
  import withFrom '../with-form';
  
  class Register extends Component{
      /* 复用的代码
      state = {
          username: '',
          password: '',
          rePassword: ''
      }
      handleChange = (key)=>{
          return (e)=>{
              this.setState({
                  [key]:e.target.value
              })
          }
      }
      handleSubmit = (e)=>{
          e.preventDefault();
          const {username,password} = this.state;
          aiert(`用户名：${username},密码：${password},确认密码: ${rePassword}`)
      }
      */
     render() {
      const { handleChange, handleSubmit } = this.props;
  
      return (
          /*<h1>登录</h1>  复用代码*/
        <form onSubmit={handleSubmit}>
          用户名: <input type='text' onChange={handleChange('username')} />
          <br />
          密码:
          <input type='password' onChange={handleChange('password')} />
          <br />
          确认密码:
          <input type='password' onChange={handleChange('rePassword')} />
          <br />
          <input type='submit' value='注册' />
        </form>
      );
    }
  }
  const NewCom = withForm(register);
  
  export default NewCom; 
  ```

  ```js
  //创建文件夹with-xx/index.js文件
  //执行函数接受一个组件(被包装组件)作为参数，返回值是一个新组件(包装组件)
  export default function withForm(WrapperComponent){
      return class extends Component{
          
            // 给组件命名， displayName优先级比组件名称name更高 一般：功能+包含组件名
            static displayName = `Form(${WrappedComponent.displayName ||
              WrappedComponent.name ||
              'Component'})`;
          //包装组件内复用代码
            state = {
                  username: '',
                  password: '',
                  rePassword: ''
              }
              handleChange = (key)=>{
                  return (e)=>{
                      this.setState({
                          [key]:e.target.value
                      })
                  }
              }
              handleSubmit = (e)=>{
                  e.preventDefault();
                  const {username,password} = this.state;
                  aiert(`用户名：${username},密码：${password},确认密码: ${rePassword}`)
              }
          render(){
              return <WrapperComponet 
              	handleSubmit={this.handleSubmit}
                	handleChange={this.handleChange}
              />
          }
      }
  }
  ```

  ```js
  //创建文件夹with-xx/index.js文件
  /* 复用h1标题内容
  	函数科里化：fn(a, b, c) --> fn(a)(b)(c)
  	在外层包装一层函数进行复用
  */
  
  //login.js 文件暴露方式：
  export default withForm({title: '用户登录'})(Login);
  //register.js文件暴露方式：
  const NewComp = withForm({ title: '用户注册' })(Register);
  export default NewComp;
  
  export default function withForm({ title }) {
      //执行函数接受一个组件(被包装组件)作为参数，返回值是一个新组件(包装组件)
    return function(WrappedComponent) {
      return class extends Component {
        // 新组件（包装组件）内部复用代码
        // 给组件命名， displayName优先级比组件名称name更高
        static displayName = `Form(${WrappedComponent.displayName ||
          WrappedComponent.name ||
          'Component'})`;
  
        state = {
          username: '',
          password: '',
          rePassword: ''
        };
  
        handleSubmit = e => {
          e.preventDefault();
          // 获取表单数据
          const { username, password, rePassword } = this.state;
  
          alert(`用户名: ${username}  密码: ${password} 确认密码: ${rePassword}`);
        };
  
        handleChange = key => {
          return e => {
            this.setState({
              [key]: e.target.value
            });
          };
        };
  
        render() {
          return (
            <div>
              <h1>{title}</h1>
              <WrappedComponent
                handleSubmit={this.handleSubmit}
                handleChange={this.handleChange}
                {...this.props}
              />
            </div>
          );
        }
      };
    };
  }
  ```


#### 装饰器

* 使暴露方式更简洁

* 装饰器语法会帮你在调用一次，将装饰的**类**作为参数传入并将最终返回值暴露出去

* 一般使用高阶组件都会使用装饰器语法

* 下载依赖 ：yarn add babel-pligin-import  customize-cra react-app-rewired -D 

  ​	@babel/plugin-proposal-decorators

* 配置文件：在github中搜索customize-cra库，查看api文档进行配置

  ```js
  //config-overrides.js文件
  const { override, addDecoratorsLegacy, addWebpackAlias } = require('customize-cra');
  
  const { resolve } = require('path');
  
  module.exports = override(
    // 添加 ES7 装饰器语法支持
    // @babel/plugin-proposal-decorators
    addDecoratorsLegacy(),
    /*配置路径别名，使引用路径时更简单 
      如：import Login from '$comp/login';
  	import Register from '$comp/register';
    */
    addWebpackAlias({
      '$comp': resolve(__dirname, 'src/components'),
    }) 
  );
  ```

  ```js
  //package.json文件
  "scripts": {
      "start": "react-app-rewired start",
      "build": "react-app-rewired build",
      "test": "react-app-rewired test",
      "eject": "react-scripts eject"
    },
  ```

  ```js
  //login.js文件
  /*装饰器语法会帮你在调用一次，将装饰的类作为参数传入并将最终返回值暴露出去
   少调用一次
  */
  @withForm({ title: '用户登录' })
  // export default withForm({title: '用户登录'})(Login);
  export default Login;
  
  //register.js文件
  @withForm({ title: '用户注册' })
  // const NewComp = withForm({ title: '用户注册' })(Register);
  // export default NewComp;
  export default Register;
  ```

#### 组件间通信-context(一般使用redux，content为了开发库而使用)

* 适用于祖孙组件间通信

* react的内置方案，因此不需要下载依赖

* 步骤：

  * 创建context文件夹user.js文件

    * 初始化context

      ```js
      //初始化context
      
      import { createContext } from 'react';
      
      // 创建context
      const userContext = createContext();
      
      export default userContext;
      ```

  * 设置state初始化状态

    ```js
    //App.js
    state = {
        user: {
          name: 'laofu',
          age: 40
        },
        food: 'apple'
      };
    ```

  * 在App.js引入userContext

    * userContext是一个对象，对象上有两个组件
          Provider 提供者（发布消息）
          Consumer 消费者（订阅消息）

    ```js
    import userContext from './context/user';
    ```

  * 给子组件传递数据

    * Provider组件可以给其子组件传递数据 ，将user数据传递给 需要使用这个数据的子组件

    ```js
    render() {
        return (
            <div>
                App...
                {/* 
                      Provider组件可以给其子组件传递数据 
                      将user数据传递给 需要使用这个数据的子组件
                    */}
                {/* <foodContext.Provider > */}
                <userContext.Provider value={this.state.user}>
                    <A />
                </userContext.Provider>
            {/* </foodContext.Provider> */}
            </div>
        );
    }
    ```

  * 子组件需对其消费操作

    ```js
    import userContext from '../../context/user';
    
    render() {
        return (
          	/*
            <div>
            <userContext.Consumer>
              {// 内部会调用下面函数，调用函数时，会将Provider传递的数据作为参数传入}
              user => {
                console.log(user);
                // 返回值就是要渲染的内容
                return (
                  <div>
                    <p>姓名: {user.name}</p>
                    <p>年龄: {user.age}</p>
                  </div>
                );
              }}
            </userContext.Consumer>
    	 </div>
    	 */
             //简单方式
             static contextType = userContext;
            // 内部Provider提供的值就会挂载到this.context上
            const user = this.context;
              <div>
                <div>
                  <p>姓名: {user.name}</p>
                  <p>年龄: {user.age}</p>
                </div>
              </div>
    	)
    }
    ```

    

  ```js
  //index.js文件
  import React from 'react';
  import ReactDOM from 'react-dom';
  
  import App from './App';
  
  ReactDOM.render(<App />, document.getElementById('root'));
  ```

  ```js
  //App.jsx文件
  import React, { Component } from 'react';
  
  import A from './components/a';
  /*
    userContext是一个对象，对象上有两个组件
      Provider 提供者（发布消息）
      Consumer 消费者（订阅消息）
  */
  import userContext from './context/user';
  import foodContext from './context/food';
  
  
  export default class App extends Component {
      state = {
          user: {
            name: 'laofu',
            age: 40
          },
          food: 'apple'
        };
      
      render() {
          return (
            <div>
              App...
              {/* 
                Provider组件可以给其子组件传递数据 
                将user数据传递给 需要使用这个数据的子组件
              */}
  			//多个content文件时
              {/* <foodContext.Provider > */}  
                <userContext.Provider value={this.state.user}>
                  <A />
                </userContext.Provider>
              {/* </foodContext.Provider> */}
  
            </div>
          );
        }
      }
  ```

  ```js
  //A.jsx文件 子组件
  import React, { Component } from 'react';
  
  import B from '../b';
  
  export default class A extends Component {
    render() {
      return (
        <div>
          A....
          <B />
        </div>
      );
    }
  }
  ```

  ```js
  //B.jsx文件 孙子组件
  import React, { Component } from 'react';
  
  import userContext from '../../context/user';
  import foodContext from '../../context/food';
  
  // 如果组件要使用多个context，就要下面这种
  export default class B extends Component {
    render() {
      return (
        <div>
          B....
          <userContext.Consumer>
            {// 内部会调用下面函数，调用函数时，会将Provider传递的数据作为参数传入
            user => {
              console.log(user);
              // 返回值就是要渲染的内容
              return (
                <div>
                  <p>姓名: {user.name}</p>
                  <p>年龄: {user.age}</p>
                </div>
              );
            }}
          </userContext.Consumer>
          <foodContext.Consumer>
            {food => {
              console.log(food);
            }}
          </foodContext.Consumer>
        </div>
      );
    }
  }
  
  // 如果组件只要使用一个context，就要下面这种
  /* export default class B extends Component {
    static contextType = userContext;
    // static contextType = foodContext;
  
    render() {
      // 内部Provider提供的值就会挂载到this.context上
      // console.log(this);
      // console.log(this.context);
      const user = this.context;
  
      return (
        <div>
          B....
          <div>
            <p>姓名: {user.name}</p>
            <p>年龄: {user.age}</p>
          </div>
        </div>
      );
    }
  } */
  ```

  ```js
  //创建context文件夹下的user.js
  /*
    初始化context
  */
  import { createContext } from 'react';
  
  // 创建context
  const userContext = createContext();
  
  export default userContext;
  ```

  ```js
  //创建context文件夹下的food.js
  /*
    初始化context
  */
  import { createContext } from 'react';
  
  // 创建context
  /*
    createContext(defaultValue)
  
    defaultValue什么时候生效：
      当你不是用Provider，只使用Consumer组件，才生效
  */
  const foodContext = createContext('banana');
  
  export default foodContext;
  ```

#### 自定义redux-createStore方法

```js
//myReadux/index.js
/*
redux向外暴露是 {createStore}
*/

export function createStore(reducers){
    
    / 集中式储存状态的容器
  	let currentState = undefined;
    // 存储 listener 函数的数组
  	const listeners = [];

    //获取redux管理的状态数据
    function getState(){
        return currentState;
    }
    
    //触发redux状态的更新
    function dispatch(action){
        //触发reducer函数的调用
        const newState = reducers();
        // 更新store对象状态数据(只能更新redux的数据，不能更新组件)
        currentState = newState ;
        // 想办法调用 listener（listener里面会封装this.setState）
    	// 调用 listener 就可以更新组件
        listeners.forEach(listener => listener());
    }
    
    //当状态数据更新时，触发监听的回调函数
    function subscribe(listener){
        listeners.push(listener);
    }
    
    // 初始化状态数据
  	currentState = reducers(currentState, { type: '@@INIT-REDUX-XXXXX' });
    
    return {
        getState,
        dispatch,
        subscribe
    }
}
```

### 总结

* 获取redux数据两种方式：
  * connect 用于组件
  * store.getState 用于非组件

* 获取访问地址；location.pathname 
  * 将来会给Login/Home组件使用。所以向外暴露的是CheckLogin组件，
  * CheckLogin组件引用在Route上，所有具体路由组件特点

* 跳转网址有两种方式：
  * Redirect    用于render方法中
  * this.props.history.push/replace    用于非render方式中

* withRouter   给子组件传递路由组件的三大属性

  ```js
  import { withRouter } from 'react-router-dom'
  
  @withRouter 
  class ...
  ```

  

