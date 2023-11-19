---
title: pinia状态管理
cover: https://img2.baidu.com/it/u=1158466549,33886806&fm=253&fmt=auto&app=138&f=PNG?w=1000&h=500
tags: [Vue]
---
## 状态管理
**为什么需要状态管理？**

答：有些时候在很多页面或组件中需要共用同一个状态，而组件的层级结构可能比较复杂，无法简单地通过props,emits或依赖注入来实现，这时候就需要状态管理，将共用的状态放到一个状态仓库(store)中，这里使用状态管理工具pinia
```javascript
//1.安装pinia
npm i pinia
//2.在main.js引入createPinia
import {createPinia} from "pinia";
//3.创建pinia实例并使用
const pinia=createPinia()
app.use(pinia)
//4.新建store实例
//新建一个store文件夹，下面新建一个store.js
```
**新建store写法**
```js
//选项式api写法(第二个参数是一个对象)
export const store=defineStore("count",{
  state:()=>({
    count:100
  })
  getters:{//计算属性
    double:(state)=>state.count*2
  }
  actions:{
    increment(){
      this.count++;
    }
  }
})
//组合式api写法(第二个参数是一个函数)
export const store=defineStore("count",()=>{
  const state=reactive({
    count:100
  })
  const increment=()=>{
    count++;
  }
  //这个最后要return {state,increment}
})
```
### store的解构
- store本来就是一个reactive响应式数据
- 通过store.name拿到的是响应式的数据
- 但通过解构拿到的属性和方法就不再是响应式的数据了(因为原理是代理模式)
  - 如果你非要解构还想要响应式数据，如下：
  ```vue
  const {name,age}=storeToRefs(store)
  ```
  - 注意使用storeToRefs解构不包括方法

### store的修改
- 可以直接修改（方便但不好控制）
- 通过`store.$patch()`修改
  - 可以传入一个新对象(可以修改一个或多个属性)
  - 可以传入一个方法，针对修改数组
    - `(state)=>{state.skills.push("打篮球")}`
    - 其实和直接`store.skills.push("打篮球")`效果一样
- `store.$reset()`可以恢复默认值

### store的订阅(监听)
- 就是说当store发生变化时你想要执行什么相应的操作
```vue
store.$subscribe((mutation,state)=>{
  <!--
  参数：
  1.mutation:修改的相关信息
  2.state:顾名思义最新的state
  相应操作
  但注意不要在这里修改该store
  因为会递归无限调用造成栈溢出
  -->

},{detached:true})
```
  - 设置`detached:true`之后该订阅不随着组件的卸载而卸载
