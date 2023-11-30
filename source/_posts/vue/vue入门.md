---
title: 写vue遇到的问题
cover: 
tags: [Vue]
---

## 生成自然数数组用来拼接

```vue
new Array(6).fill(0).map((_,index)=>prefix+(index+1))
<!--
注意new之后还是要fill的，fill啥不重要，关键是要fill
-->
```



## vue-router

### 1.安装

```bash
npm i vue-router
```

### 2.新建一个index.js或者routes.js

```js
const routes = [
  { path: '/', component: MoonVue },
  { path: '/page1', component: Page1 },
  { path: '/page2', component: Page2 },
  { path: '/page3', component: Page3 }
]
//把想用到的路由写到这里
const router = createRouter({
  history: createWebHistory(),
  routes
})

export default router
```

### 3.在main.js里面使用

```js
app.use(router)
```

### 4.router-view路由占位符

```vue
<Datalist :data="listdata"></Datalist>
<router-view></router-view>
<!--
路由占位符顾名思义，你想让这个路由出现在什么位置你就把router-view写哪
-->
```

### 5.Datalist组件里面是遍历数组生成router-link

```vue
<ListItem v-for="item of data" width="14" height="2">
      <router-link :to="item.path" class="link">{{ item.label }}</router-link>
</ListItem>
<!--
其实关键就是router-link和router-view
-->
```

