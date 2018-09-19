---
title: React生命周期
comments: true
tags: ['react','学习笔记','挖坑之后']
---
## React生命周期
***第一步上图***  
![生命周期](http://p2dhba8jd.bkt.clouddn.com/react%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)

**装配** 这些方法会在组件实例被创建和插入DOM中时被调用：
> 
1. constructor()   
2. componentWillMount() 
3. render()
4. componentDidMount()

**更新** 属性或状态的改变会触发一次更新。当一个组件在被重渲时，这些方法将会被调用：
> 
1. componentWillReceiveProps()
2. shouldComponentUpdate()
3. componentWillUpdate()
4. render()
5. componentDidUpdate()

**卸载** 当一个组件被从DOM中移除时，该方法被调用：
> componentWillUnmount()

**每一个组件还提供了其他的API：**
> 
1. setState()
2. forceUpdate()

**类属性**
> 
1. defaultProps
2. displayName


**实例属性**
> 
1. props
2. state

* * *
#### render()
是一个组件必须的，该函数是纯净的，不应该改变组件的状态。
#### constructor()  
构造函数是初始化状态的合适位置，当定义了构造函数，需要首先调用super(props),否则this.props在构造函数中就是未定义。
#### componentWillMount()
在页面mount之前被调用，在render()方法之前调用，在该方法里可以使用setState()进行state的同步，由于当前页面还没有render,所以不会进行页面的重新渲染。  
**注意后台请求不应该写在这里，因为请求是异步的，可能会因为网络等原因出现白屏等**
#### componentDidMount()
在render()之后被调用，在该方法中使用setState()进行state的同步，会产生页面的重新渲染。因为执行该方法的时候，页面dom已经渲染完成。
#### componentWillReceiveProps(nextProps)
页面第一次渲染的时候不执行该方法，当子组件接收的父组件的属性 *(可能发生变化时)发生变化时* ，直接该方法。直接通过判断this.props和nextProps是否相同，直接相应的setState方法进行状态的更新。  
**注意即使属相未发生任何变化，React也可能会调用该方法**  
#### shouldComponentUpdate(nextProps, nextState)
当接收到新属性或者新状态的时候，该方法在调用，在render()之前。若该方法返回true则该组件进行重新渲染，返回false则告诉react更新可以忽略该组件。需要在该方法里进行this.props和nextProps以及this.state和nextState的比较。   
**如果该方法返回false，则componentWillUpdate和componentDidUpdate将不会执行**
#### componentWillUpdate()
在渲染前被立即调用， *不能在该方法中使用this.setState(),如果需要响应属相的变化，要使用componentWillReceiveProps()*  
#### componentDidUpdate()
在更新发生后立即被调用，并且该方法不会再初始化渲染时被调用。
#### componentWillUnmount()
在组件被卸载和销毁之前立即调用，可以在该方法里处理任何必要的清理工作，例如解绑定时器，取消网络请求等。
#### forceUpdate()
默认情况下,当你组件的state或者props改变时，你的组件将会重绘。然后，如果它们隐式的改变（在对象深处的数据改变了但是没有改变对象本身）或者你的render方法依赖于其他的数据，可以调用forceUpdate()来告诉react它需要重新运行render()
* * * 
### setState(updater, [callback])
**异步** setState操作是一次请求而不是立即执行更新的，React将一个需要改变的变化存放在组件的state对象中，采用队列处理。为了更为客观的性能，React不会保证在setState之后，能够立即拿到改变的结果。   
在同一周期(一个方法内？？)内的多次setState()方法调用可能会被合并到一起。    
**同步** 可以使用componentDidUpdate或者setState的callback，可以保证在setState方法之后取到最新的this.state。

***state是该组件的特定数据，若你不在render()方法中使用它，就不应该把他放在state里***


