---
title: ES6,ES7
comments: true
tags: ['JS基础','ES6','ES7']
---
## ES6,ES7查漏补缺
### Object.assign
*该方法用于将所有可枚举属性的值从一个或多个源对象复制到目标对象。最终返回目标对象*	
>语法
>Object.assign(target,...sources)	
	
[demo](https://jsbin.com/tuxozur/1/edit?html,js,output)	
	
* 目标对象与源对象有相同属性，源对象属性将覆盖目标该属性的值
* 该方法只后拷贝对象自身的并且可以枚举的属性到目标对象
* Object.assign是浅拷贝，拷贝的是属性值。假如源对象的属性值是一个指向对象的引用，则只能拷贝那个引用值
* 继承属性和不可枚举属性是不能拷贝的
* 原始类型会被包装成对象，null和undefined会被忽略
* 异常会打断后续拷贝任务


[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)	
### promise(es6),Generator函数,async/await(es7)
***都是用来解决回调地狱的问题,异步函数调用***
#### promise
本质上，promise是某个函数返回的对象，你可以把回调函数绑定到这个对象上，而不是把函数当做函数参数使用。
		
*promise会带来一些保证：*   

* 在JavaScript事件队列的当前运行完成之前，回调函数永远不会被调用。
* 通过.then形式添加的回调函数，甚至都在异步操作完成之后才被添加的函数，都会被调用。
* 通过多次调用.then，可以添加多个回调函数，它们会按照插入顺序并且独立运行。

**promise最直接的好处就是链式调用。**	
***链式调用***		
连续执行两个或者多个异步操作，这种情况下，每一个后来的操作都在前面的操作执行成功之后，带着上一步操作所返回的结果开始执行。我们可以通过创造一个promise chain来完成这种需求。

* then函数会返回一个新的promise，跟原来的不同	
* 每一个promise代表了链中另一个异步过程的完成
* 一定要返回promise，不然的话回调不会形成链式，错误也获取不到（当省略{}时，箭头函数将隐式返回）。
* 在一个失败操作（即一个 catch）之后可以继续使用链式操作，即使链式中的一个动作失败之后还能有助于新的动作继续完成。
* 在传统的回调写法中，failureCallback会被多次调用。一个promise链式调用遇到错误会查找链式低端,寻找catch来代替当前操作执行。


#### Generator函数
generator最大的特点是可以交出函数的执行权（即暂停执行）  

```  
function* helloWorldGenerator() {
    yield 'hello';
    yield 'world';
    return 'ending';
   }

 var hw = helloWorldGenerator();

console.log(hw.next());
// { value: 'hello', done: false }

console.log(hw.next());
// { value: 'world', done: false }

hw.next()
// { value: 'ending', done: true }

hw.next()
// { value: undefined, done: true }
```

* generator函数使用function* 来进行标识	
* 异步需要暂停的地方，使用yield语句注明
* 

#### async/await(es7语法糖)	
async是generator函数的语法糖。		
async function 函数声明将定义一个异步函数，返回 AsyncFunction 对象。 
   
```
var asyncReadFile = async function (){	
  var f1 = await readFile('/etc/fstab');
  var f2 = await readFile('/etc/shells');
  console.log(f1.toString());
  console.log(f2.toString());
};
```
async函数就是将Generator函数的星号（*）替换成async，将yield 替换成 await，仅此而已。
   
***async优点***	          

* 内置执行器
* 更好的语义
* 更广的实用性	

await 命令后面的 Promise 对象，运行结果可能是 rejected，所以最好把 await 命令放在 try...catch 代码块中。     
await 命令只能用在 async 函数之中，如果用在普通函数，就会报错。




















