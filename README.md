# vue_advanced

the basic practice of vue app

1. 模版语法

    Vue 将模板编译成虚拟 DOM 渲染函数。结合响应系统，Vue 能够智能地计算出最少需要重新渲染多少组件，并把 DOM 操作次数减到最少。

1.1 插值表达式

1.2 关于修饰符
修饰符 (Modifiers) 是以半角句号 . 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定;
.prevent 修饰符告诉 v-on 指令对于触发的事件调用 event.preventDefault():

```javascript
    <form v-on:submit.prevent="onSubmit">...</form>
```

1.3计算属性vs模版方法vs侦听属性

计算属性是基于依赖进行缓存的，如果依赖值没有发生变化，不会去执行计算属性对应的getter函数；

模版方法在每次触发重新渲染时，都会执行;

侦听属性： Vue 通过 watch 选项提供了一个更通用的方法，来响应数据的变化。当需要在数据变化时执行异步或开销较大的操作时，这个方式是最有用的。

1.4 Class 与 Style 绑定

v-bind:class 指令也可以与普通的 class 属性共存, 支持字符串，对象和数组;

1.5 事件绑定以及修饰符

1.6 表单输入绑定
通过v-model 指令在表单元素上创建双向数据绑定；

v-model 会忽略所有表单元素的 value、checked、selected 特性的初始值而总是将 Vue 实例的数据作为数据来源；

1.7 关于组件

(1) 插槽

(2) 自定义组件

(3) 动态组件

(4) 组件注册
全局注册：
Vue.component('my-component-name', {
  // ... 选项 ...
})
注意： 全局注册的行为必须在根 Vue 实例 (通过 new Vue) 创建之前发生；

局部注册：
var ComponentA = { /* ... */ }
new Vue({
  el: '#app',
  components: {
    'component-a': ComponentA,
    'component-b': ComponentB
  }
})

![局部组件注册说明](./src/images/vue-partial-component.png)

[业务组件局部注册，基础组件全局注册的最佳实践:](https://github.com/chrisvfritz/vue-enterprise-boilerplate/blob/master/src/components/_globals.js)

(5) 组件的属性(props)
属性值的验证（主要用于开发环境）;
属性值的替换和合并：class和style一般会合并，其它特性往往会替换；
![属性合并](./src/images/vue-props.png);
禁用特性继承:通过inheritAttrs: false 和 $attrs，你就可以手动决定这些特性会被赋予哪个元素。

（6）自定义事件
推荐使用kebab-case的事件名，大小写不敏感（dom模版会把事件名转为小写）；
