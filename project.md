---
typora-root-url: image
---

#### 项目描述

* 什么项目
  * 此项目为一个前后台分离的后台管理的SPA, 包括前端PC应用和后端应用

* 实现了什么功能
  * 包括用户管理 / 商品分类管理 / 商品管理 / 权限管理 / 国际化 / 自定义换肤等功能模块

* 使用了什么技术栈
  * 前端: 使用React全家桶 + Antd + Axios + ES6 + Webpack + Echarts等技术
  * 后端: 使用Node + express + mysql等技术

* 使用了什么模式开发
  * 采用模块化、组件化、工程化的模式开发

#### 技术选型

* 一般由项目经理统筹使用何种技术栈进行开发

#### 前端路由

* 一般由项目经理搭建，有时也需要前端自行搭建

  ![前端路由](/前端路由.png)

#### API接口

* 全称：前后台交互API接口

* 前后台交互的请求地址(url)、请求方式(get/post)、请求参数及特殊请求参数等组成的就是API接口

* 多个API接口组成的文件生成API文档

* API文档

  * 服务器地址

  | 开发服务器 | <http://localhost:5000> |
  | :--------- | ----------------------- |
  | 线上服务器 | http://47.103.203.152   |

  * 公共请求参数
    * 每个接口需要的Header参数值（登录接口不需要）：

  | 参数名称      | 类型   | 是否必选 | 描述        |
  | ------------- | ------ | -------- | ----------- |
  | authorization | String | Y        | 登录的token |

  例如： authorization: Bearer token

  * API接口

    * 请求地址：/api/login

    * 请求方式：POST

    * 参数类型

    | 参数名称 | 类型   | 是否必选 | 描述   |
    | -------- | ------ | -------- | ------ |
    | username | string | Y        | 用户名 |
    | password | string | Y        | 密码   |

    * 返回示例

      ```
      成功：
      {
         "status": 0,
         "data": {
           "user": {
             "username": "admin",
             "createTime": 1547381117891,
             "menus": ["/"]
      },
      "token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVkNmEyYTU2OTZiODExMjEzYzI2Yjg3ZiIsImlhdCI6MTU2NzM4ODUwOCwiZXhwIjoxNTY3OTkzMzA4fQ.XF42Fq6mESxStnAVEF-bmYEfAHDCvPMb__wkwOkyeOk"
         }
      }
      
      
      失败:
      {
         "status": 1,
          "msg": "用户名或密码不正确!"
      }
      ```

#### 测试接口

* 测试接口/对接口/调接口/联调

* 使用postman调试工具

* 使用

  * new/+ 创建测试

    ![测试接口1](/测试接口1.png)

       {        "status": 1,         "msg": "用户名或密码不正确!"   }   

#### 项目准备

* git操作

  - 项目经理（技术总监）

    - 创建仓库
    - 创建初始化项目
    - 初始化项目提交到仓库中保管

  - 开发者

    - 获取仓库代码

      - https
        - 项目经理提供：仓库地址 和 用户名/密码
      - ssh
        - 项目经理提供：仓库地址
        - 开发者提供：ssh pub（公钥）
      - git clone 仓库地址

    - 选择分支

      - 项目经理帮你创建xxx分支
        - git fetch origin xxx:xxx 拉取远程分支xxx到本地分支xxx上
        - git checkout xxx 切换到xxx分支
        - 进行开发
      - 项目经理没有帮你创建
        - git checkout -b xxx 创建并切换到xxx分支（将当前分支内容复制到xxx分支上）
        - 进行开发

    - 进行开发

      - 本地版本控制
        - git add .
        - git commit -m 'xxx'
      - 提交到远程仓库
        - git push origin xxx
        - 有可能提交失败
          - 网络问题 （等等试试）
          - 本地没有进行版本控制 
          - 远程仓库有更新 git pull origin xxx 

      ```
      git常用指令
      * git config --global user.name "username"  //配置用户名
      * git config --global user.email "xx@gmail.com" //配置邮箱
      * git init  //初始化生成一个本地仓库 
      * git add *   //添加到暂存区 
      * git commit –m “message”  //提交到本地仓库 
      * git remote add origin url  //关联到远程仓库 
      * git push origin master  //推送本地master分支到远程master分支 
      * git checkout -b dev  //创建一个开发分支并切换到新分支 
      * git push ogigin dev  //推送本地dev分支到远程dev分支
      * git pull origin dev  //从远程dev分支拉取到本地dev分支
      * git clone url  //将远程仓库克隆下载到本地
      * git checkout -b dev origin/dev // 克隆仓库后切换到dev分支
      ```

* 项目源码基本目录设计

  * 基本结构

    ![项目基本结构](/项目基本结构.png)

#### 项目开发

##### 下载需要的技术栈依赖及配置项

* 配置antd

  * 下载antd：yarn add antd

  * 配置antd，查看官网（在create-react-app中使用）使用最新配置

    * 高级配置1-对 create-react-app 的默认配置进行自定义

      * 下载依赖：yarn add react-app-rewired customize-cra

      * 配置package.json文件

        ```js
        "scripts": {
        -   "start": "react-scripts start",
        +   "start": "react-app-rewired start",
        -   "build": "react-scripts build",
        +   "build": "react-app-rewired build",
        -   "test": "react-scripts test",
        +   "test": "react-app-rewired test",
        }
        ```

    * 高级配置2-按需加载组件代码和样式的 babel 插件

      - 下载依赖：yarn add babel-plugin-import

      - 在项目根目录创建一个 `config-overrides.js` 用于修改默认配置

        ```js
        + const { override, fixBabelImports } = require('customize-cra');
        
        + module.exports = override(
        +   fixBabelImports('import', {
        +     libraryName: 'antd',
        +     libraryDirectory: 'es',
        +     style: 'css',
        +   }),
        + );
        ```

    * 高级配置3-自定义主题需要用到 less 变量覆盖功能

      - 下载依赖：yarn add less less-loader

      - 修改 `config-overrides.js`文件配置

        ```js
        - const { override, fixBabelImports } = require('customize-cra');
        + const { override, fixBabelImports, addLessLoader } = require('customize-cra');
        
        module.exports = override(
          fixBabelImports('import', {
            libraryName: 'antd',
            libraryDirectory: 'es',
        -   style: 'css',
        +   style: true,
          }),
        + addLessLoader({
        +   javascriptEnabled: true,
        +   modifyVars: { '@primary-color': '#1DA57A' },
        + }),
        );
        ```

      - 高级配置4-装饰器语法兼容及webpack路径别名

        - 下载依赖：yarn add @babel/plugin-proposal-decorators

        - 修改 `config-overrides.js`文件配置

          ```js
          const {
            override,
            fixBabelImports,
            addLessLoader,
            addDecoratorsLegacy,
            addWebpackAlias
          } = require('customize-cra');
          
          module.exports = override(
            // 按需加载
            fixBabelImports('import', {
              libraryName: 'antd',
              libraryDirectory: 'es',
              style: true
            }),
            // 自定义主题
            addLessLoader({
              javascriptEnabled: true,
              modifyVars: { '@primary-color': '#1DA57A' }
            }),
            // ES7 装饰器语法兼容
            // @babel/plugin-proposal-decorators
            addDecoratorsLegacy(),
            // 配置webpack路径别名
            addWebpackAlias({})
          );
          ```

* 配置路由router

  * 下载路由：yarn add react-router-dom

  * 配置App.js组件

    ```js
    import React, { Component } from 'react';
    import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
    
    import Home from './components/home';
    import Login from './components/login';
    
    export default class App extends Component {
      render() {
        return (
          <Router>
            {/* <Switch> */}
              <Route path='/' exact component={Home} />
              <Route path='/login' exact component={Login} />
            {/* </Switch> */}
          </Router>
        );
      }
    }
    ```

* 配置redux

  * 下载依赖：yarn add redux  redux-thunk redux-devtools-extension

  * 配置redux文件，包含store.js、actions.js、action-type.js、reducers.js文件

    ```js
    /**
    store.js文件
     * 用来创建store对象
     */
    import { createStore, applyMiddleware } from 'redux';
    import thunk from 'redux-thunk';  //异步中间件
    import { composeWithDevTools } from 'redux-devtools-extension';  //redux调试工具，需配合谷歌redux-devtools插件一起使用
    
    import reducers from './reducers';
    
    export default createStore(
      reducers,
      process.env.NODE_ENV === 'development'
        ? composeWithDevTools(applyMiddleware(thunk))
        : applyMiddleware(thunk)
    );
    ```

    ```js
    /**
    reducer.js文件
     * 用来根据prevState和action生成newState函数模块
     */
    import { combineReducers } from 'redux';
    
    function aaa(prevState = 111, action) {
      switch (action.type) {
        default:
          return prevState;
      }
    }
    
    function bbb(prevState = 222, action) {
      switch (action.type) {
        default:
          return prevState;
      }
    }
    
    export default combineReducers({
      aaa,
      bbb
    });
    ```

#####　使用antd开发登录页面

```js
//login组件
import React, { Component } from 'react';

import { Form, Input, Button, Icon } from 'antd';

// 图片必须引入，才会被webpack打包
import logo from './logo.png';
import './index.less';

@Form.create()
class Login extends Component {
  // 自定义表单校验规则
  validator = (rule, value, callback) => {
    /*
      rule.field 获取表单key
      value 获取表单value
    */
    // console.log(rule, value);

    const name = rule.field === 'username' ? '用户名' : '密码';

    const reg = /^\w+$/;

    if (!value) {
      // 输入值为空
      callback(`${name}不能为空`);
    } else if (value.length < 4) {
      callback(`${name}必须大于4位`);
    } else if (value.length > 15) {
      callback(`${name}必须小于15位`);
    } else if (!reg.test(value)) {
      callback(`${name}只能包含英文、数字、下划线`);
    }
    /*
      callback() 调用不传参，代表表单校验成功
      callback(message) 调用传参，代表表单校验失败，会提示message错误
    */
    // 必须要调用，否则会出问题
    callback();
  };

  render() {
    // getFieldDecorator 高阶组件：用来表单校验
    const { getFieldDecorator } = this.props.form;

    return (
      <div className='login'>
        <header className='login-header'>
          <img src={logo} alt='logo' />
          <h1>React项目: 后台管理系统</h1>
        </header>
        <section className='login-section'>
          <h3>用户登录</h3>
          <Form className='login-form'>
            <Form.Item>
              {getFieldDecorator('username', {
                rules: [
                  /* {
                    required: true,
                    message: '用户名不能为空'
                  },
                  {
                    min: 4,
                    message: '用户名必须大于3位'
                  },
                  {
                    max: 15,
                    message: '用户名必须小于15位'
                  },
                  {
                    pattern: /^\w+$/,
                    message: '用户名只能包含英文、数字、下划线'
                  } */

                  {
                    validator: this.validator
                  }
                ]
              })(
                <Input
                  prefix={
                    <Icon type='user' style={{ color: 'rgba(0,0,0,.25)' }} />
                  }
                  placeholder='用户名'
                />
              )}
            </Form.Item>
            <Form.Item>
              {getFieldDecorator('password', {
                rules: [
                  {
                    validator: this.validator
                  }
                ]
              })(
                <Input
                  prefix={
                    <Icon type='lock' style={{ color: 'rgba(0,0,0,.25)' }} />
                  }
                  placeholder='密码'
                />
              )}
            </Form.Item>
            <Form.Item>
              <Button className='login-form-btn' type='primary'>
                登录
              </Button>
            </Form.Item>
          </Form>
        </section>
      </div>
    );
  }
}

// Form.create()(Login) 高阶组件：给Login传递form属性
// export default Form.create()(Login);
export default Login;
```

* 需注意以下几点

  * 在登录组件中使用图片时，需引入图片

    ```js
    // 图片必须引入，才会被webpack打包
    import logo from './logo.png';
    ```

  * 书写样式需放在当前组件中，使用时也需将index.less/css文件引入

    ```
    import './index.less';
    ```

  * 如是组件外的样式，需在项目文件创建index.less/css文件，在src创建的入口index.js文件中引入

  * 根据antd文档在Form表单中查看文档

  * 表单验证的方式：找到form表单校验规则

    ```js
    1.Form.create()(Login) 高阶组件：给Login传递form属性
    2.const { getFieldDecorator } = this.props.form;
    	getFieldDecorator 高阶组件：用来表单校验
    3.①方式1：使用已知规则，存在缺陷，会重复校验，简单的会使用，一般使用自定义表单校验
       {getFieldDecorator(
          'username', 
          {rules: [{ required: true, message: 'Please input your username!' },...]}
          )(<input>)
       }
      ②方式2：自定义方法
       	// 自定义表单校验规则
      	validator = (rule, value, callback) => {
        /*
          rule.field 获取表单key，value 获取表单value
        */
        const name = rule.field === 'username' ? '用户名' : '密码';
        const reg = /^\w+$/;
            
        if (!value) {
          // 输入值为空
          callback(`${name}不能为空`);
        } else if (value.length < 4) {
          callback(`${name}必须大于4位`);
        } else if (value.length > 15) {
          callback(`${name}必须小于15位`);
        } else if (!reg.test(value)) {
          callback(`${name}只能包含英文、数字、下划线`);
        }
        /*
          callback() 调用不传参，代表表单校验成功
          callback(message) 调用传参，代表表单校验失败，会提示message错误
       	  必须要调用，否则会出问题，callback();
        */
     	};
    	
    	{getFieldDecorator(
          'username', 
          {rules: [{ validator: this.validator }]}
          )(<input>)
       }
    4.export default Form.create()(Login);
    ```

    

