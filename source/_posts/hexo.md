---
title: hexo页面"小姿势"
cover: https://images.pexels.com/photos/209235/pexels-photo-209235.jpeg?auto=compress&cs=tinysrgb&w=600
tags: [前端,静态网页]
---
## .md的front-matter

- 举例如下：

```mark
---
title: page1
date: 2023/8/8 14:02
cover: https://w.wallhaven.cc/full/d6/wallhaven-d6w763.jpg
tags: [hobby,study]
categories:
- study
- math
---
```



### tags

- 可以在markdown文件的front-matter中设置tags，有两种设置方式：

#### 第一种写法

```markdown
---
tags 
- hobby
- study
---
```

#### 第二种写法

```markdown
---
tags: [hobby,study]
---
```

- 两种方式效果是一样的，第二种会简单一些
- 各个标签不存在层级关系（区别于categories）
- 作用：可以根据tag找到相关的页面



### categories

- 类似于tags，区别就是有层级关系
- 写法类似于tag，但意义不同：

```markdown
---
categories:
- study
- math
---
```

```mark
---
categories: [study,math]
---
```

- 都表示将当前页面添加到study类的math子类中


