---
title: 弄清原理之React Router 
tags: 适配,  进阶
date: 2018-5-6
grammar_cjkRuby: true
---

## 弄清原理之React Router

###  1. 概念

在web应用开发过程中，路由系统是不可或缺的一部分，路由简单来说就是当url发生变化时，web界面也会随之改变。react 也有自己的路由系统，那就是 react router 路由系统。

###  2. 基本原理

url  和ui 是意义对应的关系，记当你输入Url 时，就回渲染对应 react component

![基本原理](https://www.github.com/aa875982361/plingWeb/raw/master/markdown/1525588546705.jpg)

接下来然我们看看组件层面的实现原理

![实现原理](https://www.github.com/aa875982361/plingWeb/raw/master/markdown/1525588577206.jpg)

以browserHistory(一种history类型:一个 history 知道如何去监听浏览器地址栏的变化， 并解析这个 URL 转化为 location 对象)为例 :

- browserHistory进行==路由state==管理,主要通过sessionStorage

``` js?linenums
//保存　路由state(router state)
function saveState(key, state) {
  ...
  window.sessionStorage.setItem(createKey(key), JSON.stringify(state));
}
//读取路由state
function readState(key) {
  ...
  json = window.sessionStorage.getItem(createKey(key));
  return JSON.parse(json);
}
```
其中saveState函数传进来的state是个json对象，如：

``` javascript
{route: '/about'} ///假设此时的location为'/about'
```
- 进行路由匹配，最终渲染对应的组件

``` javascript
const About = React.createClass({/*...*/}) //About 组件
const Inbox = React.createClass({/*...*/}) //Inbox 组件
const Home = React.createClass({/*...*/}) //Home组件
 render() {
    let Child
    switch (this.state.route) {
      case '/about': Child = About; break;
      case '/inbox': Child = Inbox; break;
      default:      Child = Home;
    }

    return (
      <div>
        <h1>App</h1>
        <ul>
          <li><a href="#/about">About</a></li>
          <li><a href="#/inbox">Inbox</a></li>
        </ul>
        <Child/>
      </div>
    )
  }
})

React.render(<App />, document.body)
```


































































参考链接：[弄清原理之React Router](https://www.jianshu.com/p/6f8babea6243)