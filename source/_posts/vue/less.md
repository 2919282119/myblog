---
title: Less入门
cover: https://less.bootcss.com/public/img/less_logo.png
tags: CSS

---

## 安装Less

```bash
npm i less -g
```



## 概览

- **变量**
- **混合**
- **嵌套**
- **运算**
- 函数
- 命名空间与访问符
- 映射
- 作用域
- 导入



### 变量

直接上代码

```less
@width: 10px;
@height: @width + 10px;

#header {
  width: @width;
  height: @height;
}
```



### 混合

混合（Mixin）是一种将一组属性从一个规则集包含（或混入）到另一个规则集的方法

```less
.bordered {
  border-top: dotted 1px black;
  border-bottom: solid 2px black;
}

#menu a {
  color: #111;
  .bordered();//这样使用
}
```



### 嵌套

```less
#header {
  color: black;
}
#header .navigation {
  font-size: 12px;
}
```

以上代码用Less可以简化成如下效果

```less
#header {
  color: black;
  .navigation {
    font-size: 12px;
  }
}
```

还可以使用此方法将**伪选择器**（pseudo-selectors）与混合（mixins）一同使用

```less
.clearfix {
  display: block;
  zoom: 1;

  &:after {    //& 表示当前选择器的父级
    content: " ";
    display: block;
    font-size: 0;
    height: 0;
    clear: both;
    visibility: hidden;
  }
}
```



### 运算

算术运算符 `+`、`-`、`*`、`/` 可以对任何数字、颜色或变量进行运算。如果可能的话，算术运算符在加、减或比较之前会进行单位换算。计算的结果以最左侧操作数的单位类型为准。如果单位换算无效或失去意义，则忽略单位。

```less
@conversion-1: 5cm + 10mm; // 结果是 6cm
@incompatible-units: 2 + 5px - 3cm; // 结果是 4px
```

乘法和除法不作转换。因为这两种运算在大多数情况下都没有意义，一个长度乘以一个长度就得到一个区域。

```less
@base: 2cm * 3mm; // 结果是 6cm
```



### 函数

- if

  ```less
  @some: foo;
  div {
      margin: if((2 > 1), 0, 3px);
      color:  if((iscolor(@some)), @some, black);
  }
  ```

- length

  ```less
  @list: "banana", "tomato", "potato", "peach";
  n: length(@list);//4
  ```

- extract

  ```less
  @list: apple, pear, coconut, orange;
  value: extract(@list, 3);//value: coconut;
  ```

- range

  ```less
  value: range(4);//value: 1 2 3 4;
  value: range(10px, 30px, 10);//value: 10px 20px 30px;
  ```

- each

  ```less
  @selectors: blue, green, red;
  
  each(@selectors, {
    .sel-@{value} {
      a: b;
    }
  });
  /*.sel-blue {
    a: b;
  }
  .sel-green {
    a: b;
  }
  .sel-red {
    a: b;
  }*/
  ```

- 还有很多，不再赘述



### 命名空间与访问符

有时，出于组织结构或仅仅是为了提供一些封装的目的，你希望对混合（mixins）进行分组。

```less
#bundle() {
  .button {
    display: block;
    border: 1px solid black;
    background-color: grey;
    &:hover {
      background-color: white;
    }
  }
  .tab { ... }
  .citation { ... }
}
//现在，如果我们希望把 .button 类混合到 #header a 中，我们可以这样做：
#header a {
  color: orange;
  #bundle.button();  // 还可以书写为 #bundle > .button 形式
}
```



### 映射

```less
#colors() {
  primary: blue;
  secondary: green;
}

.button {
  color: #colors[primary];
  border: 1px solid #colors[secondary];
}
```



### 作用域

```less
@var: red;

#page {
  @var: white;
  #header {
    color: @var; // white
  }
}
```



### 导入

你可以导入一个 `.less` 文件，此文件中的所有变量就可以全部使用了。如果导入的文件是 `.less` 扩展名，则可以将扩展名省略掉

```less
@import "library"; // library.less
@import "typo.css";
```

