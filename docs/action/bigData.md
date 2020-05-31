# 大数据量的渲染优化

## 分页

## 长列表

无法使用分页的情况下

### 懒渲染

在滚动到页面底部的时候，再去加载剩余的数据。这是一种前后端共同优化的方式，跟分页很像。

实现思路：监听父元素的 `scroll` 事件（一般是 window），通过父元素的 scrollTop 判断是否到了页面底部，如果到了页面底部，就加载更多的数据。

### 可视区域渲染

## 虚拟列表

### 什么是虚拟列表

## 树

### tree 数据和 DOM 结构的扁平化

### 类虚拟列表方案

## vue 组件

tree 的性能缓慢原因，树以及它为什么能够解决初始大数据渲染的原因（重绘），然后应用到自己写的 tree 中。

关于这个性能问题，是因为那边有个目录树有 2000+子节点，用 iview 自带的 tree 组件加载非常卡顿，根本无法使用。iview 的 tree 组件我之前优化过源码，但是 2000+的子节点一样会存在性能问题，这和 vue 和作者设计有关，引起卡顿原因：

            1、折叠节点一次就要重新递归一次
            2、数据改变，vue就要触发收集依赖相关函数，和computed的回调函数，1个子节点1个函数，1个函数耗时6ms，1000*6ms = 6000ms === 6s，所以加载很慢

<!-- ## 虚拟 DOM，考虑放到 Vue 框架内 -->