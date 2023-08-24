---
title: vue基础
cover: https://images.pexels.com/photos/11035366/pexels-photo-11035366.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2
tags: 前端
---
## vue安装

#### 安装项目脚手架

```bash
npm i vue@latest
#然后会出现以下可选项，如果不确定就no
#✔ Project name: … <your-project-name>
#✔ Add TypeScript? … No / Yes
#✔ Add JSX Support? … No / Yes ......
```



#### 安装依赖并启动开发服务器

```bash
> cd <your-project-name>
> npm install
> npm run dev 
> npm run build #构建项目
```



#### 修改package.json的scripts

```bash
"scripts": {
    "start": "vite --open", #添加这个
    "build": "vite build",
    "preview": "vite preview"
  }
```



## 创建应用

### main.js里面这样写

```bash
import { createApp } from 'vue'
// 从一个单文件组件中导入根组件
import App from './App.vue'  #至于根组件叫什么名字可以自己决定，在index.html里面
const app = createApp(App) #创建应用实例
app.mount('#app') #挂载应用
```



### 创建组件(组合式API/单文件组件)

```vue
<scripts setup>
    <!--
    这里写js代码，这里声明的变量在模板中可以访问,
    但想要创建响应式的变量还需要使用reactive或ref,
    区别：-reactive()参数只能是对象不能是基本数据类型
         -ref()参数既可以是对象也可以是基本数据类型(会自动封装进一个对象里面)
    -->
</scripts>

<template>
    <!-- 这个叫模板,写html,里面可以渲染数据 -->
    {{ 这里可以写变量 }}
</template>

<style scoped>
    /*这里不填:表示全局生效
       scoped:此页面内生效
       module:模块css
    */

</style>
```



### 模板语法

- #### 文本插值

```vue
<template>
<h1>你好,{{ name }}</h1>
</template>
```

- #### 插入html

```vue
<p>
    <span v-html="rawHtml"></span>
</p>
<!-- 采用这种方式是为了防止注入 -->
```

- #### attribute绑定

```vue
<div v-bind:id="box"></div>
<!--
	因为{{}}不能在html的属性中使用，所以如果想要将某个属性的值绑定为某个变量(这里是box)
	需要采用v-bind,v-bind可以省略,如下:
-->
<div :id="box"></div>

<!--布尔型attribute-->
<button :disabled="isButtonDisabled">Button</button>
```

- #### 动态绑定多个值

```javascript
const Attrs = {
  id: 'container',
  class: 'wrapper'
}
//假如想要将多个属性一次性绑定给某个元素，用如下的方法
```

```vue
<div v-bind="Attrs"></div>
```

- #### 动态参数（可变属性名）

```vue
<a v-bind:[attributeName]="url"> ... </a>
<!-- 简写 -->
<a :[attributeName]="url"> ... </a>

<!--相似地，你还可以将一个函数绑定到动态的事件名称上-->
<a v-on:[eventName]="doSomething"> ... </a>
<!-- 简写 -->
<a @[eventName]="doSomething">
```

- #### 其他指令

```vue
<!-- 
	v-if:用于条件性地渲染一块内容,可配合v-else-if,v-else使用
	v-on:绑定事件，可简写为@,如@click
	v-for:用于遍历渲染
	v-slot:具名插槽,可简写为#
	这里简单演示一下各自的用法:
-->
<h1 v-if="isshow">Vue is awesome!</h1>
<h1 v-else>Oh no 😢</h1>
------------------------------
<button @click="fun"/>
------------------------------
<ul>
    <li v-for="(item,index) of arr(数组名)">{{ item.productname }}</li>
</ul>
------------------------------
<BaseLayout>
  <template v-slot:header><!-- v-slot:可简写为# -->
    <!-- header 插槽的内容放这里 -->
  </template>
</BaseLayout>
```



### 动态组件

- 通过 Vue 的 `<component>` 元素和特殊的 `is` attribute 实现

```vue
<component :is="组件名称"></component>
<!--
也可以使用 is attribute 来创建一般的 HTML 元素
-->
```



### 事件绑定

vue的事件绑定方式有两种：内联事件处理器和方法事件处理器

```vue
const fun=(msg)=>{
	alert(msg)
}
<!--
方法事件处理器：
一般没有参数的时候用这种好,当然如果非要用这种方式处理有参数的，可以用bind或箭头函数传参
访问事件对象的方式与原生js一样
-->
<button @click="fun">click me</button>

<!--
内联事件处理器：
有参数的时候用这种方便
-->
<button @click="fun('哈哈哈')">click me</button>

<!--
内联事件处理器访问事件对象用$event
-->
<button @click="warn('Form cannot be submitted yet.', $event)">
  Submit
</button>
```



### 条件渲染

有**v-if**和**v-show**两种条件渲染的方法，**区别**如下：

v-if直接控制dom元素的有无，而v-show是通过display:none控制的元素的显示与否

#### 官方解释：

`v-if` 是“真实的”按条件渲染，因为它确保了在切换时，条件区块内的事件监听器和子组件都会被销毁与重建。

`v-if` 也是**惰性**的：如果在初次渲染时条件值为 false，则不会做任何事。条件区块只有当条件首次变为 true 时才被渲染。

相比之下，`v-show` 简单许多，元素无论初始条件如何，始终会被渲染，只有 CSS `display` 属性会被切换。

总的来说，`v-if` 有更高的切换开销，而 `v-show` 有更高的初始渲染开销。因此，如果需要频繁切换，则使用 `v-show` 较好；如果在运行时绑定条件很少改变，则 `v-if` 会更合适。



### v-if和v-for

同时使用v-if和v-for是不被允许的，可以使用如下这种方式：

```vue
<!--
控制数组中某些的显示与否
-->
<template v-for="todo in todos">
  <li v-if="!todo.isComplete">
    {{ todo.name }}
  </li>
</template>
<!--
或者控制整个的显示与否如下：
-->
<template v-if="isShow">
  <li v-for="item of list">
    {{ item.name }}
  </li>
</template>
```



### 计算属性

```vue
const amount=computed(()=>{
	return unitprice*quantity;
})
```

一般可以配合vue的css的v-bind()方式动态设置样式，但是注意要通过计算属性加“em”等单位



### 生命周期

```vue
onMounted(() => {
<!--
onMounted在组件挂载完成后执行(比如请求数据api)
-->
})

onUpdated(()=>{
<!--
onUpdated组件因为响应式状态变更而更新其 DOM 树之后调用
注意：不要在 updated 钩子中更改组件的状态，这可能会导致无限的更新循环
-->
})

onUnmounted(()=>{
<!--
在组件实例被卸载之后调用
-->
})
```



### CSS模块

```vue
<template>
  <p :class="classes.red">red</p>
</template>

<style module="classes">/*如果不指定名称，上面就要写成$style.red*/
.red {
  color: red;
}
</style>
```



### 依赖注入

**为什么需要依赖注入？**

答：因为有些情况下组件和组件隔了好几代，用props来传递数据非常麻烦，而依赖注入就可以跨越n个父子组件直接传递数据

```vue
<script setup>
import { provide } from 'vue'
provide(/* 注入名 */ 'message', /* 值 */ 'hello!')  //提供依赖
</script>

<script setup>
import { inject } from 'vue'
const message = inject('message')   //注入
</script>
```



### 侦听器

**为什么需要侦听器？**

计算属性允许我们声明性地计算衍生值。然而在有些情况下，我们需要在状态变化时执行一些“副作用”：例如更改 DOM，或是根据异步操作的结果去修改另一处的状态。

```vue
watch(obj, (newValue, oldValue) => {
<!--
1.在obj发生变化时触发回调函数
2.watch 的第一个参数可以是不同形式的“数据源”：它可以是一个 ref (包括计算属性)、一个响应式对象、一个 getter 函数、或多个数据源组成的数组
3.注意，你不能直接侦听响应式对象的属性值，需要用一个返回该属性的 getter 函数如：() => obj.count
-->
})
```



### 模板引用

#### why need it?

答：虽然 Vue 的声明性渲染模型为你抽象了大部分对 DOM 的直接操作，但在某些情况下，我们仍然需要直接访问底层 DOM 元素。要实现这一点，我们可以使用特殊的 `ref` attribute

```vue
<script setup>
import { ref, onMounted } from 'vue'
    
// 声明一个 ref 来存放该元素的引用
// 必须和模板里的 ref 同名
const input = ref(null)

onMounted(() => {
  input.value.focus()
})
</script>

<template>
  <input ref="input" />
</template>
```

#### v-for中的模板引用

当在 `v-for` 中使用模板引用时，对应的 ref 中包含的值是一个数组，它将在元素被挂载后包含对应整个列表的所有元素