---
layout: post
title:  "React练习秒表"
categories: Other
tags: Other
author: Liu
description: 
---
## 一个空的组件

    class Beacon extends React.Component{
        render(){
            return null;
        }

        componentDidMount(){
            const beacon=new Image();
            beacon.src='https://domain.name/beacon.gif'
        }
    }

Beacon 的componentDidMount函数中创造了一个Image对象,访问了一个特定的图片资源,这样就可以对应服务器上留下日志记录,用于记录这一次网页访问.

    <div>
        <Beacon />
    </div>

## 一步步写秒表

### 写一个概念上的类,StopWatch

class StopWatch extends React.Component{
    render(){
        //TODO:返回所有JSX
    }
}

    class StopWatch extends React.Component{
        render(){
            //TODO:返回所有JSX
            const majorClock=this.renderMajorClock();
            constcontrolButtons=this.renderControlButtons();
            const splitTimes=this.renderSplitTimes();
            
            return (
                <div>
                    {majorClock}
                    {controlButtons}
                    {splitTimes}
                </div>
            )
        }

        //其他的render
        renderMajorClock(){
            //TODO:返回数字时钟的JSX
        }

        renderControlButtons(){
            //TODO:返回两个按钮的JSX
        }

        renderSplitTimes(){
            //TODO:返回所欲计次时间的JSX
        }
    }

用上面这一块儿方法组织代码,实现出来的这些renderXXXX函数访问的是同样的props和state,这样导致这些函数耦合在一起.更好的方式是:

class StopWatch extends React.Component{
    render(){
        return (
            <div>
                <majorClock>
                <ControlButton>
                <SplitTimes>
            </div>
        )
    }
}

const MajorClock=(props)=>{
    //TODO:返回数字时钟的JSX

}

const ControlButtons=(props)=>{
    //TODO:返回两个按钮的JSX
}

const SplitTimes=(props)=>{
    //TODO:返回所有计次时间的JSX
}


创造了三个组件,MajorClock,ControlButtons,SplitTimes  这三个,我们暂时不知道他们是否该有自己的state,现在先假设没有.用函数形式的无状态组件搞一下.

### 按照数据边界来分割组件

这里给出了一个关于数据边界的概念,并且将上面这三个组件所需的数据关系列了一下:
(怎么插入图片来着,忘了)

![image](./微信图片_20190918144626.png)

渲染MajorClock,需要的是当前展示的时间,在点击'启动'按钮之后,这个时间就是不断增长的
渲染ControlButtons,这个这两个按钮显示什么内容,是由当前状态来决定,是否启动,是否是激活状态来决定Buttons 显示的内容.Buttons是秒表中唯一有用户输入的组件,对按钮按键会改变秒表的状态.
计次时间,SplitTimes方法,需要渲染多个时间,可以想象,需要有一个数组来记录所有计次时间.
从图片上的表格来看,只有是否启动这个标志符(activated)会影响两个组件,但这个标志符的数据量很小,true/false就可以表示.

### 确定state的位置

假如用MajorClock这个组件包含一个state状态来记录时间,这个state是组件的内部状态,只能通过组件自己来更新.需要MajorClock用一个setTimeout或者setInterval来持续更新这个state.但是另一个组件ControlClock需要一个方法暂停这个更新.这些过程有些繁琐.

需要将数据状态向上层提取.在秒表 这个应用中,上层应用是StopWatch,我们让StopWatch来存储时间状态.

StopWatch中利用setTimeout或者setInterval来更新state,每一次更新引发一次重新渲染.渲染的时候,把当前时间值传递给MajorClock就完事了.

关于ControlButtons对状态的控制,让StopWatch传递函数类型props给ControlButtons,当特定按钮点击后,回调这个函数.StopWatch就知道何时停止更新或启动setTimeout或者setInterval,这一切都封装在StopWatch中.

还有SplitTimes,它需要一个数组记录所有计次时间,这些数据也应该放在StopWatch中维护.然后通过props传递给SplitTimes,这个SplitTimes只单纯的做渲染就足够了.

### 组件props的设计

当我们确定了组件结构和state之后,接下来需要设计props.
MajorClock以来当前时间,只需要一个props.

    const MajorClock=({milliseconds})=>{
        //TODO:返回数字时钟的JSX
    };

    MajorClock.propTypes={
        milliseconds:PropTypes.number.isReaquired
    };

然后是ControlButtons,这个组件徐亚根据当前是否是启动状态的来呈现不同的按钮,所以需要props来表示是否启动.我们将它命名为activated.

此外,StopWatch还需要传递回调函数给ControlButtons,所以还需要支持函数类型的props,分别代表ControlButtons可以执行的几个动作:
启动,start
停止,pause
计次,split
复位,reset

带有回调函数的props,这类props有一个统一的前缀,比如on,或者handle,这里用的on,所以ControlButtons的接口就是下面这样的:

    const ControlButtons=(props)=>{
        //TODO:返回两个按钮的JSX
    };
    ControlButtons.propTypes={
        activated:PropTypes.bool,
        onStart:PropTypes.func.isRquired,
        onPause:PropTypes.func.isRquired,
        onSplite:PropTypes.func.isRquired,
        onReset:PropTypes.func.isRquired,
    };

最后SplitTimes,PropTypes也支持数组类型的定义.

    const SplitTimes=(props)=>{
        //TODO:返回计次的时间数组形成的JSX
    };
    SplitTimes.propTypes={
        splits:PropTypes.arrayOf(PropTypes.number)
    };

## 第三段

在使用create-react-app创建一个项目后,在src文件夹中创建了三个.js文件,以组件的名称命名的.
充分做到了解耦,代码复用的原则.



### 关于constructor

这是惯用的东西
conistructor(props){
    super(props);
    this.state={..}

}

这个教程中推崇这样写

    constructor(){
        super(...arguments)
    }

目的在于如果后期代码有升级换代,这套构造函数依然正确.

还可以避免写继承类的constructor
使用属性初始化搞定,效果是一样的

    class StopWatch extends React.Component{
        state={
            isStarted:false,
            startTime:null,
            currentTime:null,
            splits:[],
        }
    }


### 关于绑定

正常的写法
constructor(){
    super(...arguments)

    this.onSplit=this.onSplite.bind(this);
}

再如:
更好的方法同样使用属性初始化,就像是初始化state一样的.利用等号直接初始化onSplit,如下:

onSplit=()=>{
    this.setState({
        splits:[...this.state.splits,this.state.currentTime-this.state.startTime]
    });
}

像上面这样写,就不需要constructor,函数体内的this绝对是当前组件对象.

## 踩了几个坑

const MajorClock=({milliseconds=0})=>{
    return <h1>{ms2Time(milliseconds)}</h1>
}

这个milliseconds=0,没有加{},导致传参失败.然后milliseconds始终是个空对象,空集合,取到的是数字就是错误值.一直算不对.
加上{}后,直接出现了数字.

还有 
在App.js中导入StopWatch文件的时候出错
应该这样写
import StopWatch from './StopWatch';
但是写成了
import'./StopWatch';
直接导致之下代码的StopWatch未定义.

## 现在,无法启动

重新敲了整个流程,感觉到了什么东西被漏掉了,
大概率是漏掉了,最开始的一块儿东西,确定各个props类型的时候写的那一块儿东西.加上这一块儿东西应该会对.
写一点儿对props和constructor的理解.
constructor()是一个函数,传参进去props,此时,对props进行构造.
首先继承,super(...arguments)
然后,添加this.state={},花括号里添加自定义的的一些字段.这里添加的

    this.state={
                isStarted:false,
                startTime:null,
                currentTime:null,
                splits:[],
            };

然后,绑定,注意绑定的过程是在constructor函数内部进行的.
