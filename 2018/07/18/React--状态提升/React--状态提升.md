---
title: React状态提升 数据流 
comments: true     
tags: ['react','学习笔记','Demo']  
data: 2018.07.18
---


### React 状态提升 数据流
**在看项目代码的时候，发现自己有好多东西都忘记(只能说之前掌握的也不是很好😅)。本次的查漏补缺主要是针对React的相关知识进行的，主要学习途径是[React官网](https://doc.react-china.org/docs/lifting-state-up.html),学习方法不再是以往的只看不动手。**

自己动手实现官网上的demo,在实现的过程中能够发现很多细节上的问题。
#### 状态提升

*质量比数量更重要* --真正的掌握了一个知识点，也好过走马观花的看了一本书。

[Demo](https://codepen.io/anon/pen/rrLQVq)使用在线代码编辑工具，codepen   也不知道能不能看👀👀

* **状态提升：**通过将state数据提升至离需要这些数据组件最近的父组件来完成，这就是数据提升过程。

#### 数据流
**react中的数据流是单向的，是从上向下的：即从父组件向子组件的方向**   
state和props是react数据流中最重要的概念。其中state是组件本身的数据发生变化，存放的是和页面渲染相关的数据；而props是父子组件的通信。


* **props:** 如果顶层(父)组件初始化props，那么React会向下遍历整颗组件树，重新渲染相关的子组件。props在子组件中是只读的。
	* 父组件更新子组件，通过传递props就可以了
	* 子组件更新父组件状态:需要父组件传递回调函数给子组件，子组件调用触发即可。[Demo](https://codepen.io/anon/pen/jpMxWX?editors=1010)
* **state:**表示的是每个组件中内部的的状态，这些状态只在组件内部改变。
	* 可以通过setState异步方法改变组件内部state的值，组件重新渲染。由于setState是异步方法，故一个生命周期中的所有setState将进行合并执行。（异步操作队列）

*把组件看成是一个函数，那么他接受props作为参数，内部由state作为函数的内部参数，返回一个虚拟dom的实现*

JSX注释  {/**/}
nodemodules是怎么


