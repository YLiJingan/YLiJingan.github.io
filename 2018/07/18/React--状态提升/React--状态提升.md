---
title: React状态提升   
comments: true     
tags: ['react','学习笔记','Demo']  
data: 2018.07.18
---


### React 状态提升
**在看项目代码的时候，发现自己有好多东西都忘记(只能说之前掌握的也不是很好😅)。本次的查漏补缺主要是针对React的相关知识进行的，主要学习途径是[React官网](https://doc.react-china.org/docs/lifting-state-up.html),学习方法不再是以往的只看不动手。**

自己动手实现官网上的demo,在实现的过程中能够发现很多细节上的问题。

*质量比数量更重要* --真正的掌握了一个知识点，也好多走马观花的看了一本书。

[Demo](https://codepen.io/anon/pen/rrLQVq)使用在线代码编辑工具，codepen   也不知道能不能看👀👀

* **状态提升：**通过将state数据提升至离需要这些数据组件最近的父组件来完成，这就是数据提升过程。

