# 什么是VirtualDOM？

简单理解为就是一个javascript对象

### 面临的问题

> 受制于标准的原因，DOM 是非常复杂的，所以我们要尽可能减少对DOM的操作。传统的思路是当状态发生改变时就重新渲染 DOM，后来发现很多情况下状态的改变并不会引起页面完全改变，一般只需要做部分修改就可以

### MVVM的思路

> 一些MVVM框架（例如Vue）提出的解决方案是绑定状态（model）和DOM中对应的部分，在某个状态发生改变时去改变其对应的节点，而AngularJS则采用脏检查的方式来寻找需要重新渲染的DOM节点

### VirtualDOM

> VirtualDOM的思路则更加直接，在状态发生改变时，将其变化反映到一个JavaScript对象（即VirtualDOM）上，然后将这个对象和老对象进行比较得出差异，并将差异应用到真实DOM上，来将DOM操作控制在最小

[VirtualDOM算法实现分析](https://github.com/CodeFalling/wiki/issues/4)
