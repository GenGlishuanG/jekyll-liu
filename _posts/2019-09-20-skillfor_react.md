---
layout: post
title:  "React2"
categories: Other
tags: Other
author: Liu
description: 
---
# 2019年09月20日

## 我在这个坑里呆了很久了

最简单的定义组件的方法是写一个 JavaScript 函数:

    function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
    }

你也可以用一个 ES6 的 class 来定义一个组件:

    class Welcome extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}</h1>;
    }
    }

严格的规则： 所有 React 组件都必须是纯函数，并禁止修改其自身 props 。

我在父级组件中定义了一个方法,
onTestchange=()=>{
    alert('a')
}

然后在子级组件中使用该方法.

`<a onClick={this.onTestchange}>点击</a>`

调用是不成功的  
原因是定义的地方和使用的地方处在不同的类当中,不能直接使用.
需要中间的桥梁来传参.

应该这样写

父组件中:

    onTestchange=()=>{
        alert("a");
        this.setState({cc:'bb',});
    }  //d定义了方法
    render(){
        return(
            <div>
                <Test  //调用子组件
                    state={this.state}
                    onTestchange={this.onTestchange}  
                    //j将之前声明的方法传参给子组件
                />
            </div>
        )

    }

子组件中:

    class Test extends React.Component{  
        render(){
            return (
                <div>
                    <p><a  onClick={()=>alert('a')}>点击弹窗</a></p>
                    <a  onClick={this.props.onTestchange}>改变</a>
                    //子组件调用父组件声明的方法的时候要考虑到包含关系,
                </div>
            ) 
        }
    }

这样就做到了子组件像父组件传参,

子组件可以写成函数式组件:

    const Test=(props)=>{      
        console.log(props)
            return (
                <div>
                    <h1>h1</h1>
                    <h2>props</h2>
                    <h2>{props.state.cc}</h2>
                    <p><a  onClick={()=>alert('a')}>点击弹窗</a></p>
                    <a  onClick={props.onTestchange}>改变</a>
                </div>
            ) 
    }

一样的
全部的内容如下:

## 如果想在网页中直接搞react

倒包到script标签内

    <script src="https://cdn.staticfile.org/react/16.4.0/umd/react.development.js"></script>
    <script src="https://cdn.staticfile.org/react-dom/16.4.0/umd/react-dom.development.js"></script>
    <script src="http://static.runoob.com/assets/react/browser.min.js"></script>

三个包都要,缺一不可

这里复制了菜鸟教程里的一段代码,(https://www.runoob.com/try/try.php?filename=react-event1)
然后添加了一个子组件,让子组件能接收父组件给的state参数,并返回至h2标签,

    <!DOCTYPE html>
    <html>

    <head>
        <meta charset="UTF-8">
        <title>Document</title>
        <script src="https://cdn.staticfile.org/react/16.4.0/umd/react.development.js"></script>
        <script src="https://cdn.staticfile.org/react-dom/16.4.0/umd/react-dom.development.js"></script>
        <script src="http://static.runoob.com/assets/react/browser.min.js"></script>
    </head>

    <body>
        <h2>标题222</h2>
        <div id="root"></div>
        <div id="example"></div>
    <script type="text/babel">
    class Toggle extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            isToggleOn: true,
            cc:'a',
        };
        // 这边绑定是必要的，这样 `this` 才能在回调函数中使用
        this.handleClick = this.handleClick.bind(this);
    }

    handleClick() {
        this.setState(prevState => ({
        isToggleOn: !prevState.isToggleOn
        }));
    }

    render() {
        return (
        <div>
        <button onClick={this.handleClick}>
            {this.state.isToggleOn ? 'ON' : 'OFF'}
        </button>
        <Test 
            state={this.state}
        />
        </div>
        );
    }
    }

    function Test(props) {
        return (
            <div>
                <h2>{props.state.cc}</h2>
            </div>
        )
    }

    ReactDOM.render(
    <Toggle />,
    document.getElementById('example')
    );
    </script>
    </body>

    </html>

好,就这些

    <!DOCTYPE html>
    <html>

    <head>
        <meta charset="UTF-8">
        <title>Document</title>
        <script src="https://cdn.staticfile.org/react/16.4.0/umd/react.development.js"></script>
        <script src="https://cdn.staticfile.org/react-dom/16.4.0/umd/react-dom.development.js"></script>
        <script src="http://static.runoob.com/assets/react/browser.min.js"></script>
    </head>

    <body>
        <h2>标题222</h2>
        <div id="root"></div>
        <script type="text/babel">
            class Toggle extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            cc:'a',  
        };
        this.onTestchange=this.onTestchange.bind(this);
    }
        onTestchange() {
            this.setState({cc:'bb',});
        } 
        // onTestchange=()=>{
        //     // alert("a");
        //     this.setState({cc:'bb',});
        // }//直接使用箭头函数绑定

    render() {
        return (
        <div>
            <h1>标题</h1>
        <Test 
            state={this.state}
            onTestchange={this.onTestchange}
        />
        </div>
        );
    }
    }

    function Test (props)  {
        return (
            <div>
                <h2>{props.state.cc}</h2>
                <button onClick={props.onTestchange}>dianji </button>
            </div>
        )
    }

    ReactDOM.render(
    <Toggle />,
    document.getElementById('root')
    );
    </script>
    </body>

    </html>

这一段和上面一段的区别在于,实现了一个点击更换属性的事件.
向button绑定一个onClick事件,使他调用onTestchange方法,该方法执行this.setState({})方法,改变cc的属性,使之变成'bb';
需要注意的是:

1. 绑定的时候,不能使用箭头函数直接绑定
2. 定义子组件的时候不能直接使用`const Test()=>{}`这样的箭头函数去定义组件

原则就是:在html文档中,使用箭头函数就是废.

之下,开始重写秒表!
 