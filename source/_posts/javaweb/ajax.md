---
title: ajax
cover: https://cdn0.iconfinder.com/data/icons/badges-26/54/markdown-format-mark-down-arrow-sign-badge-1024.png
tags: javaweb 

---

原始的前端数据通过form表单action传给后端，但这样会造成全部刷新，通过异步ajax可以实现局部刷新，

以下是通过原生js实现的ajax:

- 表单元素不是设置name而是id或class，绑定事件函数，函数里通过document.getEle……拿到表单数据
- 然后通过xmlHttpRequest对象的方法（连接，发送，接收相应数据（通过回调函数onreadystatechange））

<img src="https://afly0321.oss-cn-hangzhou.aliyuncs.com/img/image-20230903171202050.png" alt="image-20230903171202050" style="zoom: 33%;" />