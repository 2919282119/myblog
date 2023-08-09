---
title: vue基础
cover: https://images.pexels.com/photos/11035366/pexels-photo-11035366.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2
tags: 前端
---
## vue安装

##### 安装项目脚手架

```bash
npm i vue@latest
#然后会出现以下可选项，如果不确定就no
#✔ Project name: … <your-project-name>
#✔ Add TypeScript? … No / Yes
#✔ Add JSX Support? … No / Yes ......
```



##### 安装依赖并启动开发服务器

```bash
> cd <your-project-name>
> npm install
> npm run dev 
> npm run build #构建项目
```



##### 修改package.json的scripts

```bash
"scripts": {
    "start": "vite --open", #添加这个
    "build": "vite build",
    "preview": "vite preview"
  }
```



## 创建应用

##### main.js里面这样写

```bash
import { createApp } from 'vue'
// 从一个单文件组件中导入根组件
import App from './App.vue'  #至于根组件叫什么名字可以自己决定，在index.html里面
const app = createApp(App) #创建应用实例
app.mount('#app') #挂载应用
```



##### 创建组件(组合式API/单文件组件)

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



##### 模板语法

- 文本插值

```vue
<template>
<h1>你好,{{ name }}</h1>
</template>
```

- 插入html

```vue
<p>
    <span v-html="rawHtml"></span>
</p>
<!-- 采用这种方式是为了防止注入 -->
```

- attribute绑定

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

- 动态绑定多个值

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

- 动态参数（可变属性名）

```vue
<a v-bind:[attributeName]="url"> ... </a>
<!-- 简写 -->
<a :[attributeName]="url"> ... </a>

<!--相似地，你还可以将一个函数绑定到动态的事件名称上-->
<a v-on:[eventName]="doSomething"> ... </a>
<!-- 简写 -->
<a @[eventName]="doSomething">
```

- 其他指令

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

